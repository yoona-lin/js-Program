
**Table of Contents** _generated with [DocToc](http://doctoc.herokuapp.com/)_

- [js-Program 牛客 js 编程题收集](#js-Program牛客js编程题收集)
  - [1.如果数组中存在 item，则返回元素在数组中的位置，否则返回 -1](#1.如果数组中存在item则返回元素在数组中的位置否则返回-1)
  
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

