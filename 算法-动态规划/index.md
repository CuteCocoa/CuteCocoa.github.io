# 动态规划


# 动态规划

## ***动态规划***

1. *动态规划 跟 “分治、递归、回溯”没有太大的区别，我们来看看动态规划的具体定义*
   
   - ***simplifying a complicated problem by breaking it down into simpler sub-problems***
     
     *这个是 wiki百科 对动态规划的解释，同时我感觉这是最好的解释*
     
     *动态规划，个人觉得翻译成 “动态递推/动态推导” 是最好的，动态规划其实有点不直白*
     
     *然后上述英文的意思则是 “把一个复杂的问题分解为更简单的子问题”*
     
     *其实就是分治的思想，但是分治和动态规划只有小小的不一样，那就是第二点*
   
   - ***动态规划 = 分治 + 最优子结构***
     
     *一般来说 动态规划 会让你求 最优解 最大值 最小值，这也就是动态规划的应用场景*
     
     *正因为，他有所谓的最优子结构，所以，你就不需要，将中间所有的状态都保存下来，只需要存最优的状态*

2. *重点总结*
   
   - *动态规划和 递归 分治 没有根本上的区别（关键是看有无最优子结构）*
   - *他们之间的共性就是 找到重复子问题*
   - *他们之间的差别就在于 动态规划有最优子结构，中途可以淘汰最优解*

## ***斐波那契数列***

[![image-20220628222611743](https://raw.githubusercontent.com/vlicecream/cloudImage/main/data/imagesimage-20220628222611743.png)](https://raw.githubusercontent.com/vlicecream/cloudImage/main/data/imagesimage-20220628222611743.png)

*斐波那契额数列 我们都知道是可以用递归去解决，但是面试的时候，千万不能说用递归，傻递归的效率是极慢的 时间复杂度为指数级，也就是 O(2^n)*

*所以我们就得想办法来优化啦，我们可以加一个缓存，这个缓存可以用数组，这种叫做 “记忆化搜索”*

```go
func fib(n int, memo []int) {
  // resursion terminator(递归终止条件)
  if (n <= 1) {
    return 0
  } 

  if (memo[n] == 0) {
    memo[n] = fib(n - 1) + fib(n - 2)
  }
  return memo[n]
}
```

*在上述代码中我们通过增加数组实现的缓存，使得只要在数组出现的值就直接return，不让他参与遍历，把重复的节点直接砍掉，所以O(2^n) 变成了 O(n) 是不是贼棒，其实这个也是分治的思想，只不过加了个记忆化搜索*

## ***思想 - 自顶向下***

*我们在面对斐波那契时，当然可以用上述讲的 分治 + 记忆化搜索 来实现，其实这个思想就是 “自顶向下” 的思想*

*什么叫自顶向下呢？就是上述图片，我们一直从上面也就是fib(6)找到最下面的叶子结点*

- *我要算 fib(6) 就得算fib(5) 和 fib(4)*
- *我要算fib(5) 就得算fib(4) 和 fib(3)*
- *...*

*就如上述一直下去，中间算过的结果，我们可以用记忆化搜索，这种符合人脑的习惯，也是分治的思想*

## ***思想 - 自底向上***

*我们学习了自顶向下的方法，emmm，是不是感觉很不错，但是后来当我们遇到更难得dp也就是动态规划时，高手一般会直接用“自底向上”的思想*

*那么什么是自底向上呢*

- *我们想算fib(6) 从fib(0) fib(1) 开始 然后一直用循环去递推*

*所以我们只需要了解自底向下思想即可，所以动态规划翻译成动态递推是不是很有道理*

## ***状态转移方程***

*状态转移方程也叫 dp方程*

*这个其实是要在例题1 例题2 后来讲的 这里为了工整性 提前说了*

*大家可以先看一下例题1 和例题2 的分析再来看 dp方程 和 关键点 思考步骤*

*两道例题 其实都有一个核心的关键方程*

- *例题1 是 `v[i] = v[i-1] + v[i-2]`*
- *例题2 是 `v[i][j] = v[i-1][j] + v[i][j-1]`*

*这类方程 我们叫状态转移方程 也叫dp方程 但是又回到 咬文嚼字上 这其实就是一个递推方程*

## ***dp 思考点***

1. *化繁为简，将复杂的问题 变成子问题，其实就是 找重复性（分治思想）*
2. *定义好状态空间*
   - *定义dp数组 && 初始化dp数组*
   - *注意这里定义和初始化数组的长度一定要注意 有时候会是 “>=” 或者其他的，如果定义错误，则会数组越界，或者答案错误*
3. *写好dp方程*

---

## ***例题1 - 爬楼梯***

### ***方法1 - 动态规划***

1. *URL*
   
   - *[70. 爬楼梯 - 力扣（LeetCode）](https://leetcode.cn/problems/climbing-stairs/)*

2. *代码示例*
   
   ```c
   class Solution {
   public:
       int climbStairs(int n) {
           /* 定义dp数组 */
           vector<int> dp(n+1);
           /* 初始化dp数组 */
           dp[0] = 1;
           dp[1] = 1;
           /* dp方程 自底向上 */
           for (int i = 2; i < dp.size(); i++) {
               dp[i] = dp[i-1] + dp[i-2];
           }
           return dp[n];
       }
   };
   ```

