# 其他综合面试题汇总
---
### 1.某公司1到12月份的销售额存在一个对象里面，如下：{1:222, 2:123, 5:888}`，请把数据处理为如下结构：[222,123,null,null,888,null,null,null,null,null,null,null]
   - **解析：**<br>
```js
const obj = {1:222, 2:123, 5:888};
const result = Array.from({length:12},(item,index)=>(obj[index+1]?obj[index+1]:null));
console.log(result)
```

### 2.给定两个数组[1, 2, 2, 1], [2, 2],来计算他们的交集？
  - **解析：**<br>
```js
let arr1 = [1,2,2,3];
let arr2 = [2,2];

const mixedOfArr = function(arr1,arr2){
  // 创建新数组
  let result = [];
  // 拷贝新数组待用
  let arr1New = arr1.slice();
  let arr2New = arr2.slice();
  return function(){
    let a1 = arr1New[0];//每次取数组第一个
    let index = arr2New.indexOf(a1);//获取在第二个数组中的下标
    if(index>-1){
      // 第二个数组中若存在
      result.push(a1);
      //删除第二个数组中存在的元素
      arr2New.splice(index,1);
    }
    //删除第一个数组中遍历过的元素
    arr1New.splice(0,1);
    if(arr1New.length==0||arr2New.length==0){
      //若其中一个数组遍历完，则返回数据
      arr1New = null;
      arr2New = null;
      return result;
    }else{  
      // 否则递归 匿名函数递归调用
      return arguments.callee()
    }
  }
}
console.log(mixedOfArr(arr1,arr2)());
```

