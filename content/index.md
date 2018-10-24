### API规则使用规范

## 图形学概述

### 图形学包含哪些内容

### 分别是什么意思？

### 我们要如何利用图形学来进行项目开发

### Threejs架构设计

### Threejs原理

源码实例：
https://github.com/mrdoob/three.js/commits/dev?after=d0156cf32ea1e805994cdf8cbe43fb1078570f0b+20140

源码解读：

* 第一个commit
https://github.com/mrdoob/three.js/commit/a90c4e107ff6e3b148458c96965e876f9441b147

  * 创建一个Class对象，暴露出extend方法
  * 创建一个Vector3，继承Class类，来实现顶点的创建逻辑
  * 创建一个Camera对象，由Vector3继承扩展
  * 创建一个Face3对象，由Vector3继承扩展
  * 创建一个Face4对象，由Vector3继承扩展
  * 创建一个Geometry对象，由Vector3继承扩展
  * 创建一个Matrix3对象，由Vector3继承扩展

---

参考资料：
[https://threejs.org/](https://threejs.org/)
[threejs github](https://github.com/mrdoob/three.js/)


```js
(function() {
    var lastTime = 0;
    var vendors = ['webkit', 'moz'];
    for(var x = 0; x < vendors.length && !window.requestAnimationFrame; ++x) {
        window.requestAnimationFrame = window[vendors[x]+'RequestAnimationFrame'];
        window.cancelAnimationFrame =
          window[vendors[x]+'CancelAnimationFrame'] || window[vendors[x]+'CancelRequestAnimationFrame'];
    }

    if (!window.requestAnimationFrame)
        window.requestAnimationFrame = function(callback, element) {
            var currTime = new Date().getTime();
            var timeToCall = Math.max(0, 16 - (currTime - lastTime));
            var id = window.setTimeout(function() { callback(currTime + timeToCall); },
              timeToCall);
            lastTime = currTime + timeToCall;
            return id;
        };

    if (!window.cancelAnimationFrame)
        window.cancelAnimationFrame = function(id) {
            clearTimeout(id);
        };
}());
```
