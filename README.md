Vue相关问题
==========================

1.vue的生命周期
-------------------

beforeCreate/created/beforeMount/mounted/beforeUpdate/updated/beforeDestory/distory.整个生命周期分为初始化、运行中、销毁。首先，通过`new Vue()`，开始初始化事件和生命周期，然后执行`beforeCreate`钩子函数，这个时候，数据没有挂载，无法访问到数据和真是DOM.然后执行`created`函数，这个函数内数据已经挂载完成，此时可以修改数据，不会引起其他生命周期函数。一般在这里请求数据。接下来编译模版，编译模版为虚拟DOM，并放入到render函数中准备渲染。然后执行`beforeMount`函数，此时虚拟DOM已经完成，马上进行渲染。在这里更改数据，不会触发updated.接下来开始render，渲染出真实DOM，然后执行`mounted`函数，此时，组件已经出现在页面中，数据和真实DOM以及事件已经处理好。当组件或实例的数据变更之后，会立即执行`beforeUpdate`,然后vue的虚拟DOM机制会重新构建虚拟DOM，与上一次的虚拟DOM树，利用diff算法进行比对后，重新渲染。当更新完成后，执行`updated`函数，数据已经更改完成，DOM也重新render完成，可以操作更新后的虚拟DOM.如果组件销毁时，会执行`beforeDestory`，在这里一般清除定时器或清除绑定事件。然后执行`destoryed`函数。

2.双向数据绑定是想
-------------------------

>1.[参考](https://www.cnblogs.com/zhuzhenwei918/p/7309604.html)