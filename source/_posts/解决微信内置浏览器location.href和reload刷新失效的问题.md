---
title: 解决微信内置浏览器location.href和reload刷新失效的问题
date: 2016-11-02 15:30:28
tags: [微信, 微信内置浏览器, 刷新, location.reload, location.href]
---
`location.reload()`和`location.href`是常用的刷新页面的方法，但是在Android微信内置浏览器中就失效了。
<!--more-->
当我们想通过点击页面中的一个按钮或者链接来刷新页面时，我们通常会用`location.reload()`或者`location.href = 'current url'`来实现页面刷新。但是此方法在Android微信内置浏览器中会失效，而在其他浏览器（不管是PC还是mobile）以及iOS微信内置浏览器中都没有这个问题，初步推断是Android微信内置浏览器缓存了当前页面的URL。

为了解决此类问题，我们可以在URL中添加时间戳或者随机数。由于只有Android微信内置浏览器才有这个BUG，我们先要判断当前打开页面的浏览器是否为Android微信内置浏览器。如果是，再向URL中添加时间戳或随机数。

在这里，我用添加时间戳的方式来实现：

```javascript
function isAndroidWechat() {

  // 第一个条件用来判断是否为Android系统，第二个用来判断是否为微信
  return (/android/.test(navigator.userAgent.toLowerCase()) &&
    /micromessenger/.test(navigator.userAgent.toLowerCase()));
}

function updateURL(url, args, hash) {

  // 时间戳参数，默认是"t"
  let key = (args || 't') + '=';

  /**
   * 如果使用路由（比如react-router）跳转并刷新，
   * 则需要将目标hash也传递过来（比如event.currentTarget.hash），
   * 一般用不到这个参数，可直接省略
   */
  let router = hash || location.hash;

  // 匹配规则
  const reg = new RegExp(key + '\\d+');

  // 获取当前时间
  let timestamp = +new Date();

  if (url.indexOf(key) > -1) {

    // 如果有时间戳，则直接更新
    return url.replace(reg, key + timestamp);

  } else {

    // 如果没有时间戳，则加上时间戳
    if (url.indexOf('\?') > -1) {
      let urlArr = url.split('\?');

      if (urlArr[1]) {
        return urlArr[0] + '?' + key + timestamp + '&' + urlArr[1];
      } else {
        return urlArr[0] + '?' + key + timestamp;
      }
    } else {

      // 使用hash路由的情况
      if (url.indexOf('#') > -1) {
        return url.split('#')[0] + '?' + key + timestamp + router;
      } else {
        return url + '?' + key + timestamp;
      }
    }
  }
}

function reloadPage() {

  if (isAndroidWechat()) {

    // 先添加时间戳
    location.href = updateURL(location.href);

    // 然后强制刷新
    location.reload(true);
  } else {

    // 直接强制刷新
    location.reload(true);
  }
}


/**
 * 当使用react-router路由跳转到子页面时，
 * 或者类似的跳转需要重新刷新页面来达到重新渲染组件的目的，
 * 也需要添加时间戳或随机数。
 *
 * 由于该问题是react-router引起的，
 * 与Android微信内置浏览器URL缓存类似，
 * 所以也可以用这个方法
 *
 * 这个问题大家可以忽略，只使用上面的reloadPage即可
    function reloadPage(event) {
      // 阻止默认行为
      event.preventDefault();

      // 先添加时间戳
      location.href = updateURL(location.href);

      // 然后强制刷新
      location.reload(true);
    }
 */
```

