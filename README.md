## interview
  1、最高效拿下技术面试（The most efficient to win the technical interview）
  
  2、整理最有效的部分，比较难理解的内容
  
  3、面试心得和面试过程也会说一下
  

## 进度 
  当前多篇文章在csdn和掘金已经发布，会整理之后，也在github同步
  
## 专题
  Csdn地址：https://blog.csdn.net/weixin_43815680/article/details/108506250

  博客地址（完善中）：https://huanhunmao.github.io/
  
  掘金：https://juejin.cn/post/6907573102511816712

  知乎：https://www.zhihu.com/people/got-81

  B站：https://www.bilibili.com/video/BV1gi4y177ZW
  
  
  
## 算法 系列之 easy部分
  1、连续子数组最大和
  
  输入一个整型数组，数组里有正数也有负数。数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。要求时间复杂度为 O(n).
  
  算法解决：
  ```
  function FindGreatestSumOfSubArray(array)
{
    // write code here
    let l=0;
    let r=0;
    // 定义两个初始值 都取数组第一个数
    let sum=array[0];
    let max=array[0];
    // 做循环
    do{
        // 负数情况
        if(sum<array[r]){
            max=Math.max(sum,max);
            sum-=array[l++];
            // 正数 
        }else{
            max=Math.max(sum,max);
            sum+=array[++r];
        }
    }while(l<array.length&&r<array.length)
    //返回结果
    return max;
}
```
  2、不使用 加减乘除 做加法 
  
  写一个函数，求两个整数之和，要求在函数体内不得使用+、-、*、/四则运算符号。
  
  算法解决：
  
  ```
  function Add(num1, num2)
{
// 当num2存在时 num2不存在则直接返回num1
    while(num2){
        var t = num1 ^ num2    // 转成 2进制 相加
        num2 = (num1 & num2) << 1   // num1 & num2 如果两个都是正数 结果为1  << 1 转为2进制后向左移动一位
        num1 = t
    }
    return num1
}
  ```
  3、判断链表 有没有环形 
  
  如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

如果链表中存在环，则返回 true 。 否则，返回 false 。

```
时间复杂度 O(n) 空间复杂度 O(1) 因为没有额外的线性增长的数据结构  数组 矩阵
var hasCycle = function(head) {
    // 需要一快一慢两个指针
    let p1 = head;
    let p2 = head;
    // 需要满足判断值
    while(p1&&p1.next&&p2&&p2.next){
    // 一快一满两个指针
        p1 = p1.next;
        p2 = p2.next.next;
    // 当两个值相同时表示有链表
        if(p1 === p2){
            return true
        }
    }
    return false
};

```
  4、数组去重
  ```
  //方法一：数组去重常规方法   很重要的 
    var arr = [1, 1, 2, 3, 3, 6];

    function unique() {
        var hash = [];
        for (var i = 0; i < arr.length; i++) {
        // hash.indexOf(arr[i])      == -1 注意前一部分写法
            if (hash.indexOf(arr[i]) == -1) {
                hash.push(arr[i]);
            }
        }
        return hash;
    }
    console.log(unique(arr))
  ```
  ```
  // 方法二： es6 Set方法  数组去重
const arr = [1, 2, 1, 2];
    const arr1 = new Set(arr)
    console.log([...arr1]) // [1,2]  需要加一个[]不加得到的是一个集合内容为 1 2 
  ```
  5、算法 js原型链（链表）    https://juejin.cn/post/6914257079477731336
  
  6、 js算法之集合      https://juejin.cn/post/6914639899098529805/
  
  7、 求两个数组的交集部分   leetcode 349
  
  ```
      // 时间复杂度 O(M * N ) 空间 复杂度O(M) M表示num1长度 N表示num2长度
  // 求数组交集 字典解法
    var intersection = function (num1, num2) {
        // 新建一个字典
        var map = new Map();
        // 遍历第一个数组 并把值放进去 值为true表示放进字典内
        num1.forEach(n => {
            map.set(n, true)
        });
        // 初始化结果 数组
        const res = [];
        // 遍历第二个数组
        num2.forEach(n => {
            // 判断 也出现的值
            if (map.get(n)) {
                //  放进新数组就是交集部分
                res.push(n);
                // 需要立即从字典删除避免得到的结果重复
                map.delete(n);
            }
        })
        return res
    }
    var test = intersection([1, 2, 3, 4], [1, 2]);
    console.log(test)
  ```
  
  8、leetcode 20 有效的括号
  
  给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。
  
  ```
  // 方法一 使用 栈 操作
  var isValid = function (s) {
    if (s.length % 2 === 1) {
        return false
    }
    // 定义栈
    const stack = []
    // 遍历
    for (var i = 0; i < s.length; i++) {
        const c = s[i]
        if (c === '(' || c === '{' || c === '[') {
            stack.push(c)
        } else {
            const top = stack[stack.length - 1]
            if (top === '(' && c === ')' || top === '{' && c === '}' || top === '[' && c === ']') {
                stack.pop()
            } else {
                return false
            }
        }
    }
    return stack.length === 0
}
  ```

  ```
  // 时间复杂度 O(n) 空间复杂度 O(n)
  //方法二  使用 字典 优化 
   var isValid = function (s) {
    if (s.length % 2 === 1) {
        return false
    }
    // 定义栈
    const stack = []
    const map = new Map()
    map.set('(',')')
    map.set('[',']')
    map.set('{','}')
    // 遍历
    for (var i = 0; i < s.length; i++) {
        const c = s[i]
        if (map.has(c)) {
            stack.push(c)
        } else {
            const top = stack[stack.length - 1]
            if (map.get(top) === c) {
                stack.pop()
            } else {
                return false
            }
        }
    }
    return stack.length === 0
} 
  ```
## 算法 系列之 medium部分



## 算法 系列之 hard部分




## 专题-JS学透 系列
  1、学透原型和原型链一篇就好 https://juejin.cn/post/6907783000906268685
  
  2、学透 词法（静态）作用域和动态作用域  https://juejin.cn/post/6907798346459512839
  
  3、学透JS执行上下文  https://juejin.cn/post/6907801557543157773/
  
  4、学透执行上下文变量对象    https://juejin.cn/post/6907804959694782477/
  
  5、学透作用域链     https://juejin.cn/post/6907811400320548871/
  
  6、学透 闭包 一篇就够了    https://juejin.cn/post/6907953627223539726/
  
  7、一篇学透 类型转化（上）  https://juejin.cn/post/6908239708514418702
  
  


## 专题-vue 精简教程系列
  1、vue 精简教程（一） dev tools mvvm spa单页面 数据定义和渲染 https://juejin.cn/post/6909604250699956232/
  
  2、vue 精简教程（二 ）常用指令用法  更新超长版本   一次看个过瘾好吧  https://juejin.cn/post/6909599367410221070/
  
  3、vue 精简教程（三)大 组件它真的来了 组件通信方式 浅谈 过滤和 自定义组件  https://juejin.cn/post/6909604540731883528/
  
  4、vue 精简教程（四) vuerouter 路由  https://juejin.cn/post/6909605853205266446/#comment
  
  5、vue 精简教程（五)   vue-cli脚手架  https://juejin.cn/post/6909605467459321864/

## 专题-webpack 系列
  1、React 学习12-2 -- webpack必会内容（一） https://juejin.cn/post/6907575758068121607
  
  2、React 学习12-6 -- React 入门到熟练必会内容（二） 必出精品！！！ https://juejin.cn/post/6907575693970767879
  
## 专题-浏览器调试工具 系列
  1、浏览器开发工具使用技巧篇（一）html +css调试   https://juejin.cn/user/1741228277763278
  
  2、浏览器开发工具使用技巧篇（二）js调试+ 与后台对接的错误调试  https://juejin.cn/post/6907478521199722509
  
  
  

## 深入浅出的vue.js 系列
  1、解读vuejs源码教程（一）    https://juejin.cn/post/6913908311146397703/
