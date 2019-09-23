

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

**Table of Contents** _generated with [DocToc](http://doctoc.herokuapp.com/)_

- [js-Program 牛客 js 编程题收集](#js-Program牛客js编程题收集)
   - [如果数组中存在 item，则返回元素在数组中的位置，否则返回 -1](#如果数组中存在item则返回元素在数组中的位置索引否则返回-1)
   - [计算给定数组 arr 中所有元素的总和](#计算给定数组arr中所有元素的总和)
   - [移除数组 arr 中的所有值与 item 相等的元素。不要直接修改数组 arr，结果返回新的数组](#移除数组arr中的所有值与item相等的元素不要直接修改数组arr结果返回新的数组)
   - [去掉数组重复项，并生序排序](#去掉数组重复项并生序排序)
  
<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# js-Program 牛客 js 编程题收集

牛客网的编程题，做完顺便总结笔记，便于记忆

## 如果数组中存在item，则返回元素在数组中的位置（索引），否则返回-1

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

## 计算给定数组arr中所有元素的总和

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
 
 ## 移除数组arr中的所有值与item相等的元素.不要直接修改数组arr，结果返回新的数组

```
/* 1. 遍历比较，不同放到一个新的数组返回*/
   function remove(arr, item) {
       var Arr = [];  //看到一些用 var Arr = new Array();
       for(var i = 0; i < arr.length; i++){
           if(arr[i] != item){
               Arr.push(arr[i]);
            }
       }
       return Arr;
   }

/*2. slice() 方法，slice() 方法可从已有的数组中返回选定的元素*/

   function remove(arr, item){
      var Arr = arr.slice(0);     // slice(0),将整个数组拷贝到Arr新数组
      for(i = 0; i < Arr.length; i++){
          if(Arr[i] == item){
              Arr.splice(i, 1);   // 存在相同的就删了，splice(i, 1)
              i--;             //这里的i--不太懂
          }
      }
       return Arr;
   }

/*3. filter() 方法，filter() 方法使用指定的函数测试所有元素，并创建一个包含所有通过测试的元素的新数组。返回true是表示保留该元素（通过测试，该元素保留至新数组），false时表示移除该元素 */
   function remove(arr,item) {
       if(!Array.prototype.filter){
           return false;
       }else{
           return arr.filter(function(ele){
                return ele != item;
           })
      }
   };
   console.log(remove([2,4,7,23,1,56],7));
```

## 去掉数组重复项，并生序排序

```
/*indexOf 遍历判断*/
   function text(arr){
      if(!Array.prototype.indexOf){
         return false;
       }else{
          var result = [];
          for(var i = 0; i < arr.length; i++){
              if(result.indexOf(arr[i]) == -1){
                  result.push(arr[i]);
              }
          }
          return result.sort(function(a, b){
              return a - b;        // 生序排序
              /*return b - a;  则为降序排序*/
          });
      }
   };

/*ES6 方法，使用 Set 去重 */
   function text(arr){
      if(!Set){
         return false;
       }else{
          let Arr = [...new Set(arr)];
          return Arr.sort(function(a, b){
              return a - b;
          })
      }
   };

```











