

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

**Table of Contents** _generated with [DocToc](http://doctoc.herokuapp.com/)_

- [js-Program 牛客 js 编程题收集](#js-Program牛客js编程题收集)
   - [如果数组中存在 item，则返回元素在数组中的位置，否则返回 -1](#如果数组中存在item则返回元素在数组中的位置索引否则返回-1)
   - [计算给定数组 arr 中所有元素的总和](#计算给定数组arr中所有元素的总和)
   - [移除数组 arr 中的所有值与 item 相等的元素。不要直接修改数组 arr，结果返回新的数组](#移除数组arr中的所有值与item相等的元素不要直接修改数组arr结果返回新的数组)
   - [去掉数组重复项，并生序排序](#去掉数组重复项并生序排序)
   - [移除数组 arr 中的所有值与 item 相等的元素，直接在给定的 arr 数组上进行操作，并将结果返回](#移除数组arr中的所有值与item相等的元素直接在给定的arr数组上进行操作并将结果返回)
   - [在数组arr末尾添加元素item。不要直接修改数组arr，结果返回新的数组](#在数组arr末尾添加元素item不要直接修改数组arr结果返回新的数组)
   - [删除数组 arr 最后一个元素。不要直接修改数组 arr，结果返回新的数组](#删除数组arr最后一个元素不要直接修改数组arr结果返回新的数组)
   - [在数组arr开头添加元素item。不要直接修改数组arr，结果返回新的数组](#在数组arr开头添加元素item不要直接修改数组arr结果返回新的数组)
   - [](#)
   - [](#)
   - [](#)
   - [](#)
  
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

## 移除数组arr中的所有值与item相等的元素，直接在给定的arr数组上进行操作，并将结果返回

```
/*splice(i, 1)方法删除相同元素位置，作用于原数组*/
/*与上面一题相似，只是这里要求在原数组直接修改*/
   function removeWithoutCopy(arr, item) {
       for(var i = 0; i < arr.length; i++){
           if(arr[i] === item){      //这里可以是 == ， 但不能是 = ；
               arr.splice(i, 1);
               i--;       //这里的i--可有可无；
           }
       }
       return arr;
   }

```

## 在数组arr末尾添加元素item。不要直接修改数组arr，结果返回新的数组

 ```
 
 /*1.使用slice浅拷贝+push组合*/
   function append(arr, item) {
       var Arr = arr.slice(0);
       Arr.push(item);
       return Arr;     //这里不能直接return Arr.push(item);合一起；
   }

/*2.通常的for循环*/
   function append(arr, item) {
       var Arr = [];
       for(var i = 0; i < arr.length; i++){
           Arr.push(arr[i]);
       }
       Arr.push(item);
       return Arr;
   }
   
/* 3.使用concat将传入的数组或非数组值与原数组合并,组成一个新的数组并返回*/
   function append(arr, item) {
       return arr.concat(item);
   }

```

## 删除数组arr最后一个元素。不要直接修改数组arr，结果返回新的数组

```
/*1.普通迭代，1个元素，push到一个新的空数组*/
   function truncate(arr) {
       var Arr = [];
       for(var i = 0; i < arr.length - 1; i++){
           Arr.push(arr[i]);
       }
       return Arr;
   }

/*2.slice浅拷贝，再删去最后一个*/
   function truncate(arr) {
       var Arr = arr.slice(0);     //同 var Arr = arr.concat();
       var len = arr.length - 1;
       Arr.splice(len, 1);
       return Arr;
   }
/*3.单独使用slice方法*/
   function truncate(arr) {
      // slice方法不会改变原数组数据
      return arr.slice(0,-1);
   }
   
/*4.filter方法*/
   function truncate(arr) {
          if(!Array.prototype.filter){
              return false;
          }else{
             //val:当前元素值  i:当前元素索引  arr1:当前数组
             return arr.filter(function (val,i,Arr) {
                   return i!=Arr.length-1;
               })
         }
      };
   
/*5.split+join*/
   function truncate(arr) {
      var Arr = arr.join().split(',');
      //join() 方法连接成一个字符串
      //split() 方法用于把一个字符串分割成字符串数组,','处进行分割。
      //删除最后一个元素
      //push是在最后面增加一个元素，pop是指删除最后一个元素；
      //unshift是在最前面添加一个元素；shift是指删除第一个元素；两者返回的都是所删除的元素
      Arr.pop();
      return Arr;  //答案正确，但返回的是字符串的数组
   }
   
/*扩展了解：js字符数组转化为数字数组，即['1','2','3'] => [1,2,3]

['1','2','3'].map(Number) // [1,2,3]

['1','2','3'].map((value)=>{
  return parseInt(value)
}) // [1,2,3]
                    
JSON.parse('[' + String(['1', '2', '3']) + ']') // [1,2,3]

eval('[' + String(['1', '2', '3']) + ']') // [1,2,3]
    
```


## 在数组arr开头添加元素item。不要直接修改数组arr，结果返回新的数组

```
/*1.循环迭代赋值*/
   function prepend(arr, item) {
       var Arr = [];
       Arr.push(item);     //放到空数组最后面，就相当于第一个元素
       //上面两句也可以合一起：var Arr = [item]; 
       for(var i = 0; i < arr.length; i++){
           Arr.push(arr[i]);
       }
      return Arr;
   }

/*2.concat() 方法，对两个数组进行连接*/
   function prepend(arr,item) {
          if(!Array.prototype.concat){
              return false;
          }else{
              return [item].concat(arr);
         }
    };
    
/*3.使用push.apply:将b追加到a里面，如果a为数组，也可以写成a.push(b)*/
   function prepend(arr, item) {
      var Arr = [item];
      //使用此方法改变的数组是arr1，arr数组不变
      [].push.apply(Arr,arr);    //Arr.push(arr);
      return Arr;
   }
   
/*4.使用unshift:在数组头部插入指定元素*/
   function prepend(arr, item) {
      var Arr = arr.slice(0);
      //var Arr = arr.join().split(',');这个先转换成字符串了，后面得return Arr.map(Number);
      Arr.unshift(item);
      return Arr;
   }

```


##

```
/**/


```

## 








