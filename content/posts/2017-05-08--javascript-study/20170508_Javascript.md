---
title: JavaScript 學習(1)
subTitle: JavaScript 學習(1)
category: "sayings"
cover: photo-1463852247062-1bbca38f7805-cover.jpg
---

早期JS寫法

## 早期JS Function寫法
```javascript
    ...  
    function foo() {
        //...
    }    
    function bar(){
        //...
    }
```
- 缺點: Global 容易汙染 命名容易重複

## 簡單封裝：Namespace 模式
```javascript
    var MYAPP = {
        foo: function(){},
        bar: function(){}
    }

    MYAPP.foo();
```
- 減少 Global 上的變量數目
- 本質是對象，一點都不安全

## 匿名閉包
```javascript
    var Module = (function() {
        var _private = 'safe now';
        var foo = function(){
            console.log(_private);    
        }
   
        return {
            foo: foo
        }
    })()

    Module.foo();
    Module._private //undefined
```
- 函數是Javascript唯一的 Local Scope

## 另外
```javascript
    var Module = (function($) {
        var _$body = $('body');
        var foo = function() {
            console.log(_$body);
        }
       
       //Revelation Pattern
       return {
          foo: foo
       }
    })(jQuery)

    Module.foo()
```