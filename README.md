

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
   - [删除数组arr第一个元素。不要直接修改数组arr，结果返回新的数组](#删除数组arr第一个元素不要直接修改数组arr结果返回新的数组)
   - [合并数组arr1和数组arr2。不要直接修改数组arr，结果返回新的数组](#合并数组arr1和数组arr2不要直接修改数组arr结果返回新的数组)
   - [在数组arr的index处添加元素item。不要直接修改数组arr，结果返回新的数组](#在数组arr的index处添加元素item不要直接修改数组arr结果返回新的数组)
   - [统计数组arr中值等于item的元素出现的次数](#统计数组arr中值等于item的元素出现的次数)
   - [找出数组arr中重复出现过的元素](#找出数组arr中重复出现过的元素)
   - [为数组arr中的每个元素求二次方。不要直接修改数组arr，结果返回新的数组](#为数组arr中的每个元素求二次方不要直接修改数组arr结果返回新的数组)
   - [在数组arr中，查找值与item相等的元素出现的所有位置](#在数组arr中查找值与item相等的元素出现的所有位置)
   - [修改js代码中parseInt的调用方式，使之通过全部测试用例](#修改js代码中parseInt的调用方式，使之通过全部测试用例)
   - [计时器](#计时器)
   - [流程控制，fizzBuzz函数](#流程控制fizzBuzz函数)
   - [将数组arr中的元素作为调用函数fn的参数](#将数组arr中的元素作为调用函数fn的参数)
   - [将函数fn的执行上下文改为obj对象](#将函数fn的执行上下文改为obj对象)
   - [返回函数，实现函数functionFunction](#返回函数实现函数functionFunction)
   - [使用闭包，实现函数makeClosures函数](#使用闭包实现函数makeClosures函数)
   - [使用arguments](#使用arguments)
   - [或运算](#或运算)
   - [且运算](#且运算)
   - [模块，完成函数createModule函数](#模块完成函数createModule函数)
   - [二进制转换](#二进制转换)
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
//arrayObject.slice(start,end):返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。
   function remove(arr, item){
      var Arr = arr.slice(0);     // slice(0),将整个数组拷贝到Arr新数组
      for(i = 0; i < Arr.length; i++){
          if(Arr[i] == item){
              Arr.splice(i, 1);   // 存在相同的就删了，splice(i, 1),i位置元素删除；splice(i,0,n):在i位置插入一个n元素
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

## 删除数组arr第一个元素。不要直接修改数组arr，结果返回新的数组

```
/*迭代循环*/
   function curtail(arr) {
       var Arr = [];
       for(var i = 1; i < arr.length; i++){
           Arr.push(arr[i]);
       }
       return Arr;
   }

```

## 合并数组arr1和数组arr2。不要直接修改数组arr，结果返回新的数组

```
/**/
   function concat(arr1, arr2) {
       if(!Array.prototype.concat){
           return false;
       }else{
           var Arr = [];
           Arr = arr1.concat(arr2);
           return Arr;
       }
   }

```

## 在数组arr的index处添加元素item。不要直接修改数组arr，结果返回新的数组

```
/*1.slice+splice*/
   function insert(arr, item, index) {
       var Arr = arr.slice(0);
       Arr.splice(index, 0, item);
       return Arr;
   };

/*2.利用slice+concat*/
   function insert(arr, item, index) {
       return arr.slice(0,index).concat(item,arr.slice(index));
   }
   
/*3.利用concat +splice*/
   function insert(arr, item, index) {
       var newArr=arr.concat();
       newArr.splice(index,0,item);
       return newArr;
   }
   
/*4.push.apply+splice*/
   function insert(arr, item, index) {
       var newArr=[];
       [].push.apply(newArr, arr);
       newArr.splice(index,0,item);
       return newArr;
   }
   
/*5.普通的迭代拷贝*/
   function insert(arr, item, index) {
       var newArr=[];
       for(var i=0;i<arr.length;i++){
           newArr.push(arr[i]);
       }
       newArr.splice(index,0,item);
       return newArr;
   }

```

## 统计数组arr中值等于item的元素出现的次数

```
/*循环对比*/
function count(arr, item) {
    var count = 0;
    for(var i = 0; i < arr.length; i++){
        if(arr[i] == item){
            count += 1;
        }
    }
    return count;
}

```

## 找出数组arr中重复出现过的元素

```
/*双层循环对比查找*/
function duplicates(arr) {
    var newArr = [];
    for(var i = 0; i < arr.length - 1; i++){
        for(var j = i + 1; j < arr.length; j++){
            if(arr[i] == arr[j] && newArr.indexOf(arr[i]) == -1){
                newArr.push(arr[i]);
            }
        }
    }
    return newArr;
}

/*2.先对数组进行排序，判断前一个与后一个相等且没有保存的情况下，再把元素放到数组中去。*/
function duplicates(arr) {
    var newArr=[];
    arr.sort();
    for(var i =0;i<arr.length;i++){
        if(arr[i]==arr[i+1]&&(newArr.indexOf(arr[i])==-1) ){
            newArr.push(arr[i]);
            i++;

        }
    }

    return newArr;
}
```

## 为数组arr中的每个元素求二次方。不要直接修改数组arr，结果返回新的数组

```
/*1.for循环*/
   function square(arr) {
      var newArr = [];
       for(var i = 0; i < arr.length; i++){
           newArr.push(arr[i] * arr[i]);
       };
       return newArr;
   }

/*2.map()*/
    function square(arr) {
      return arr.map(function (ele) {
          return ele*ele;
      });
   }

/*3.fotEach遍历*/
   function square2(arr) {
      var a = [];
      arr.forEach(function (ele) {
          return a.push(ele*ele)
      })
      return a;
   } 
```

## 在数组arr中，查找值与item相等的元素出现的所有位置

```
/*迭代循环*/
   function findAllOccurrences(arr, target) {
       var indexArr = [];
       for(var i = 0; i < arr.length; i++){
           if(arr[i] == target){
               indexArr.push(i);
           }
       }
       return indexArr;
   }

```

## 修改js代码中parseInt的调用方式，使之通过全部测试用例

```
//parseInt(string, radix) : 函数可解析一个字符串，并返回一个整数。
//当忽略参数 radix , JavaScript 默认数字的基数如下:
//如果 string 以 "0x" 开头，parseInt() 会把 string 的其余部分解析为十六进制的整数(十六进制转为十进制）。
//如果 string 以 0 开头，那么 ECMAScript v3 允许 parseInt() 的一个实现把其后的字符解析为八进制或十六进制的数字。
//如果 string 以 1 ~ 9 的数字开头，parseInt() 将把它解析为十进制的整数。

/*为设置radix时*/
   function parse2Int(num) {
       var reg = /[a-zA-Z]/g;
      var res = new RegExp(/^(?![^a-zA-Z]+$)/);
      if(res.test(num)){
       //匹配参数中所有大小写字母，如果有就删了字母，并将参数用该字母拆分成多个元素放在数组中，parseInt该数组第一个元素
         return parseInt(num.split(reg)[0]);
      }
       //如果不含字母，直接parseInt
       return parseInt(num);
   }
   
/*当设置了radix时，遇到非数字字符会直接忽略后面的字符*/
   function parse2Int(num) {
       return parseInt(num,10);
   }
   
```

## 计时器

```
//实现一个打点计时器，要求
   1、从 start 到 end（包含 start 和 end），每隔 100 毫秒 console.log 一个数字，每次数字增幅为 1
   2、返回的对象中需要包含一个 cancel 方法，用于停止定时操作
   3、第一个数需要立即输出
   
/*1.setTimeout函数*/
   function count(start, end) {
       if(start <= end){
           console.log(start++);
           st = setTimeout(function(){
               count(start, end);
           }, 100);
       }
       return {
           cancel: function(){
               clearTimeout(st);
           }
       }
   }

/*2.setInterval函数*/
   function count(start, end) {
       console.log(start++);
       var timer = setInterval(function () {
           if (start <= end) {
               console.log(start++)
           } 
       }, 100);
       return {
           cancel: function () {
               clearinterval(timer)
           }
       }
   }
```

## 流程控制，fizzBuzz函数

```
/*1.按照流程条件判断*/
//百度答案也是这样，但牛客没通过验证
   function fizzBuzz(num) {
       if(num%3==0&&num%5==0){
           return "fizzbuzz";
       }else if(num%3==0){
           return "fizz";
       }else if(num%5==0){
           return "buzz";
       }else if(typeof(num)!="number"){
           return false;
       }else{
           return num;
       }
   }

/*2.*/
   function fizzBuzz(num){
    if(num && typeof num == 'number'){
        if(num % 3 == 0 && num % 5 == 0){
            return 'fizzbuzz'
        }else if(num % 3 == 0){
            return 'fizz'
        }else if(num % 5 == 0){
            return 'buzz'
        } else{
            return num;
        }
     }else{
        return false;
    }
```

## 将数组arr中的元素作为调用函数fn的参数

```
//一般情况下都是对象调用函数，但此处是函数调用数组对象,用call(), apply()。第一个参数是传给当前函数对象。但是call()需要将参数挨个列出，apply直接传入数组对象
   function argsAsArray(fn, arr) {
      return fn.apply(this,arr);
   }

```

## 将函数fn的执行上下文改为obj对象

```
//
   function speak(fn, obj) {
      return fn.call(obj);
   }

//三种方案
//apply
   function speak(fn, obj) {
       return fn.apply(obj);
   }

//call
   function speak(fn, obj) {
       return fn.call(obj);
   }
   
//bind
   function speak(fn, obj) {
       return fn.bind(obj)();
   }
```

## 返回函数，实现函数functionFunction

```
/**/
//实现函数 functionFunction，调用之后满足如下条件：
1、返回值为一个函数 f
2、调用返回的函数 f，返回值为按照调用顺序的参数拼接，拼接字符为英文逗号加一个空格，即 ', '
3、所有函数的参数数量为 1，且均为 String 类型

   function functionFunction(str) {
      var f = function(s){
         return str + ', ' + s;
      }
      return f;
   }
   
//一个闭包就搞定了
   function functionFunction (arg1) {
       return function(arg2){
           return arg1 + ', ' + arg2;
       };
   }
```

## 使用闭包，实现函数makeClosures函数

```
//实现函数 makeClosures，调用之后满足如下条件：
1、返回一个函数数组 result，长度与 arr 相同
2、运行 result 中第 i 个函数，即 result[i]()，结果与 fn(arr[i]) 相同

//看到题目我首先想到的是使用闭包时因为作用域链引来的副作用，（闭包只能得到包含函数中变量的最后一个值）如果直接用下面第一种写法会导致result中每个函数的参数都是arr[arr.length],在《JavaScript高级程序设计》书中提到的最典型的解决此问题的方法就是用一个立即执行的匿名函数代替闭包负值给数组，这个匿名函数有一个参数num，因为函数参数是按值传递的所以传递给num的就是当前for循环的值。接下来的是根据其他小伙伴的解决方案进行的总结，提供给新来的小伙伴一个总结，页方便自己以后看
此外ES5提供了bind方法，apply(),call(),bind()方法在使用时如果已经对参数进行了定义
又因为在此问题中用的是数组并且需要的是arr[i]所以用forEach()方法就不用考虑第一段中提到的问题


//这种是错误的写法会导致result中每个函数的参数都是arr[arr.length]
   function makeClosures(arr, fn) {
       var result = new Array();
        for(var i=0;i<arr.length;i++){
           result[i] = function(){
               return fn(arr[i]);            
           };
       }
       return result;
    }

//参考《JavaScript高级程序设计》的典型方法
   function makeClosures(arr, fn) {
       var result = new Array();
       for(var i=0;i<arr.length;i++){
           result[i] = function(num){
               return function(){
                   return fn(num);

               }
           }(arr[i]);
       }
       return result;
   }

//使用ES5的bind()方法
   function makeClosures(arr, fn) {
       var result = new Array();
       for(var i=0;i<arr.length;i++){
           result[i] = fn.bind(null,arr[i]);
       }
       return result;
   }

//使用forEach()
   function makeClosures(arr, fn) {
       var result = new Array();
       arr.forEach(function(curr){
           result.push(function(){return fn(curr)});
       })
       return result;
   }
```

## 使用arguments

```
//函数 useArguments 可以接收 1 个及以上的参数。请实现函数 useArguments，返回所有调用参数相加后的结果。本题的测试参数全部为 Number 类型，不需考虑参数转换。

   function useArguments() {
      var result = 0;
         for(var i = 0; i < arguments.length; i++){
            result += arguments[i];
         }
      return result;
   }
   
   function useArguments() {
       var arr=Array.prototype.slice.call(arguments)//把arguments类数组转化为数组
       return eval(arr.join("+"));//求和
   }
```

## 或运算

```
//返回参数 a 和 b 的逻辑或运算结果
   function or(a, b) {
      return a || b
   }
```

## 且运算

```
//返回参数 a 和 b 的逻辑且运算结果
//且运算符"&&"的运算规则是：如果第一个运算子的布尔值为true，则返回第二个运算子的值（注意是值，不是布尔值）；如果第一个运算子的布尔值为false，则直接返回第一个运算子的值，且不再对第二个运算子求值。
   function and(a, b) {
      return a && b;
   }
```

## 模块，完成函数createModule函数

```
//完成函数 createModule，调用之后满足如下要求：
1、返回一个对象
2、对象的 greeting 属性值等于 str1， name 属性值等于 str2
3、对象存在一个 sayIt 方法，该方法返回的字符串为 greeting属性值 + ', ' + name属性值

//原型模式：
   function createModule(str1, str2) {
       function Obj()
       {
           this.greeting = str1;
           this.name = str2;
       }
       Obj.prototype.sayIt = function(){return this.greeting + ", " + this.name;}
       return new Obj(); 
   }

//构造函数模式：
   function createModule(str1, str2) {
       function Obj()
       {
           this.greeting = str1;
           this.name = str2;
           this.sayIt = function(){return this.greeting + ", " + this.name;}
       }
       return new Obj();   
   }

//创建对象模式：
   function createModule(str1, str2) {
       function CreateObj()
       {
           obj = new Object;
           obj.greeting = str1;
           obj.name = str2;
           obj.sayIt = function(){return this.greeting + ", " + this.name;}
           return obj;
       }
       return CreateObj();   
   }

//字面量模式：
   function createModule(str1, str2) {
       var obj =
         {
             greeting : str1,
             name : str2,
             sayIt : function(){return this.greeting + ", " + this.name;}
         };
       return obj;   
   }

```

## 二进制转换

```
//获取数字 num 二进制形式第 bit 位的值。注意：
1、bit 从 1 开始
2、返回 0 或 1
3、举例：2 的二进制为 10，第 1 位为 0，第 2 位为 1

   function valueAtBit(num, bit) {
      var str = num.toString(2).split('').reverse();
      return str[bit-1];
   }
   
```

## 

```
//

```

## 

```
//

```



