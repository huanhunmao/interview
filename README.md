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
  
  9、两数 之和  
  
  输入：nums = [2,7,11,15], target = 9
  输出：[0,1]
  解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。

  ```
  // leetcode 1 求两个数之和
  // 时间复杂度 O(n)  空间复杂度 O(n)
    var twoSum = function (nums, target) {
    //新建一个字典
        var map = new Map()
        for (var i = 0; i < nums.length; i++) {
            const n = nums[i]; // 拿到每个数组值
            const n2 = target - n; // 匹配值
            // 匹配到之后  拿到两个的下标
            if (map.has(n2)) {
                return [map.get(n2), i]
                //没有匹配上 则 先将值和下标存在map中
            } else {
                map.set(n, i)
            }
        }
    }

    var test = twoSum([1, 2, 3, 6], 9)
    console.log(test) // [2,3]
  ```
  
  10、javascript 算法之 树    必出精品 （递归版本简单 非递归版本面试很重要）（一）  https://juejin.cn/post/6916503216288956429
  
  11、leetcode 104 二叉树最大  深度
  
  ```
  /**
 * @param {TreeNode} root
 * @return {number}
 * 1、新建变量 存放层级 deep
 * 2、深度优先遍历  
 * 3、刷新 deep值  传入参数 l 先拿到每一层的deep 初始为1
 * 4、拿到层级最大值 Math.max(deep,l)
 */
var maxDepth = function(root) {
    // 新建变量记录层级
 var deep = 0;
 // 深度优先遍历 dfs函数
        var dfs = function (n,l) {
            if (!n) {
                return
            }
            // 先访问当前节点
            // console.log(n.val,l)
            // 拿到层级比较大的结果
            //判断一下 叶子节点才计算最大深度 节省性能
            if(!n.left && !n.right){
            deep = Math.max(deep,l)
        } 
            //访问左节点
            dfs(n.left,l+1)
            //访问右节点
            dfs(n.right,l+1)
        }
        // 1 表示传入的默认层级 初始化 层级是 1
       dfs(root,1) // 调用根节点
       return deep
    };
  ```
  
## 算法 系列之 medium部分

  1、leetcode   3. 无重复字符的最长子串
  
  给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
  ```
  输入: s = "abcabcbb"
  输出: 3 
  解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
  ```
  ```
  // 时间复杂度O(n) n表示s.length 空间复杂度 O(m)  m是字符串 不重复字符个数
  var lengthOfLongestSubstring = function (s) {
        // 新建两个移动指针 l r
        let l = 0;
        // 初始化结果
        let res = 0;
        // 新建字典 
        const map = new Map();
        for (var r = 0; r < s.length; r++) {
            // 如果字典中 再次出现右指针指向的东西
            if (map.has(s[r]) && map.get(s[r] >= l)) {
                // 左指针向右指针下一位移动
                l = map.get(s[r]) + 1;
            }
            res = Math.max(res, r - l + 1);
            map.set(s[r], r)
        }
        return res;
    }
  ```


## 算法 系列之 hard部分

  1、leetcode    76. 最小覆盖子串
  
  给你一个字符串 s 、一个字符串 t 。返回 s 中涵盖 t 所有字符的最小子串。如果 s 中不存在涵盖 t 所有字符的子串，则返回空字符串 "" 。

注意：如果 s 中存在这样的子串，我们保证它是唯一的答案。

```
    // leetcode 76  最小覆盖长度
    var minWindow = function (s, t) {
        // 新建两个移动指针
        var l = 0;
        var r = 0;
        // 新建一个字典
        var need = new Map();
        // 循环遍历 t 
        for (let c of t) {
            need.set(c, need.has(c) ? need.get(c) + 1 : 1)
        }
        // console.log(need)    //Map(3) {"A" => 1, "B" => 1, "C" => 1}

        // 字典长度 赋给t 中的需求类型 
        let needType = need.size;
        // 初始化结果
        let res = "";
        while (r < s.length) {
            // 找到 t中匹配的每个字符后 减一 找剩下的
            // 遍历右 指针
            const c = s[r];
            if (need.has(c)) {
                need.set(c, need.get(c) - 1);
                if (need.get(c) === 0) {
                    needType -= 1
                }
            }
            // 当 t中的都找到了 需要缩小范围
            while (needType === 0) {
                // console.log(s.substring(l, r + 1))
                const newRes = s.substring(l, r + 1);
                if (!res || newRes.length < res.length) {
                    res = newRes
                }
                const c2 = s[l];
                if (need.has[c2]) {
                    need.set(c2, need.get(c2) + 1)
                    if (need.get(c2) === 1) {
                        needType += 1
                    }
                }
                l += 1;
            }
            r = r + 1;
        }

        return res
    }
```



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
