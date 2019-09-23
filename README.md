

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

**Table of Contents** _generated with [DocToc](http://doctoc.herokuapp.com/)_

- [js-Program 牛客 js 编程题收集](#js-Program牛客js编程题收集)
   - [1.如果数组中存在 item，则返回元素在数组中的位置，否则返回 -1](#1如果数组中存在item则返回元素在数组中的位置否则返回-1)
   - [2.计算给定数组 arr 中所有元素的总和](#2计算给定数组arr中所有元素的总和)
  
<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# js-Program 牛客 js 编程题收集

牛客网的编程题，做完顺便总结笔记，便于记忆

## 1.如果数组中存在 item，则返回元素在数组中的位置（索引），否则返回 -1

```
function indexOf(arr,item){
  if(Array.prototype.indexOf){
    /*判断浏览器是否支持indexOf方法*/
    return arr.indexOf(item); //输出位置的话最好加一
  }else{
    for(var i = 0; i < arr.length; i++){
      if(arr[i] === item){
        return i;  //这里说出输出索引会准确一点
        /*return ++i; //则输出为位置  */
      }
    }
  }
  return -1;
}
```

## 2.计算给定数组 arr 中所有元素的总和

```
/*1.遍历数组*/
  function sum(arr) {
      var result = 0;
      for(var i = 0; i < arr.length; i++){
          result = arr[i] + result;
      }
      return result;
  }

/*2.ES6 eval() 方法，eval是对某个字符串进行计算：eval（'2+2'）===输出为4 */
  function sum(arr) {
    if(!eval){
      alert("浏览器不支持eval方法");
    }
  else{
      //alert(eval(arr.join('+')));
      console.log(eval(arr.join('+')));
      //join() 将数组的每个元素都转为字符串,如果 join()里面不加任何参数，用法与toString()一样
  }
  };

/*3.forEach 方法，reduce:计算数组元素相加后的总和 */
  function sum(arr) {
    if(!Array.prototype.forEach){
      alert("浏览器不支持forEach方法");
    }
  else {
      var sum=0;
      arr.forEach(function (val,i) {
          sum+=val;
      })
   return sum;
    }
  }; 

/*4.reduce 方法*/
  function sum(arr) {
    if(!Array.prototype.reduce){
      alert("浏览器不支持reduceh方法");
    }
  else {
    return arr.reduce(function (one,two) {
       return one + two;
    })
  }
  }; 
  
 ```

