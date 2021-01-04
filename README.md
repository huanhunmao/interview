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
