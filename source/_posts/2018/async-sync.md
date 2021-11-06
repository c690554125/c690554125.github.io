---
title: 异步和同步
date: 2018/12/30
---

## 同步函数
>调用即可立即得到结果，不用等待


```js
  function syncFn() {
    console.log('我是同步，立刻得到结果')
  }
```

## 异步函数
>调用后不能立即得到结果，需要等待一段时间或者是下一轮**tick**(事件循环的一轮叫做一个tick)
>这里需要注意的是：异步函数的代码通常有2个部分组成，**现在运行的代码**和**将来运行的代码**，异步函数并不是整体都是异步的。


### 点击事件
```js
  function asyncFn1() {
    document.querySelector('.oDiv').addEventListener('click', function(){
      console.log('别惊讶，点击事件也算异步'); // 将来运行的代码
    })
  }
```


### 定时器事件
```js
  function asyncFn2() {
    setTimeout(function(){
      console.log('定时器，绝对的异步函数')  // 将来运行的代码
    }, 0)
  }
```


### ajax事件
```js
  function asyncFn3() {
    // 假设引入了jQuery
    $.ajax({
      url: 'xxx',
      type: 'post',
      dataType: 'json',
      success: function(){
        console.log('ajax异步请求') // 将来运行的代码
      },
      fail: function(){
        console.log('wrong')
      }
    })
  }
```

### Promise
```js
  // ES6中新增的Promise
  function asyncFn4() {
    return new Promise(function(resolve, reject) {
      // do something
      // 将来运行的代码 start ↓
      if(true){
        resolve(data);
      }else {
        reject(error);
      }
      // 将来运行的代码 end ↑
    })
  }
```

同步和异步函数也是事件循环中不可缺少的重要概念，对事件循环的运行机制有很大帮助。所以一定要清楚辨认哪些是异步，哪些是同步。
