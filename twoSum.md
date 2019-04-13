## 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

    示例

    给定 nums = [2, 7, 11, 15], target = 9
    因为 nums[0] + nums[1] = 2 + 7 = 9
    所以返回 [0, 1]

```js
var twoSum = function(nums, target) {
    let res = []
    nums.some((item, index) => {
        let athIndex = nums.indexOf(target - item, index + 1)
        if (athIndex > -1 && athIndex !== index) {
            res = [index, athIndex]
            return true
        }
    })
    return res
}
twoSum([2, 7, 11, 15], 9)
```

* 小问题也犯错误，主要还是基础不牢固

* `Array.prototype.forEach()`回调的返回值是不会终止forEach的运行的
* `Array.prototype.some()`返回true终止some的执行，空数组始终返回false；`Array.prototype.every()`返回false终止every的执行
* 注意indexOf的第二个参数要加1,

从别的文章看到的解法，大致如下

* 1

```js
  var twoSum = function(nums, target) {
    let numobj = {}
    for (let i = 0; i < nums.length; i++) {
        let diff = target - nums[i]
        if (numobj[diff] === undefined) {
            numobj[nums[i]] = i
        } else {
            return [numobj[diff], i]
        }
    }
  }
  思路: 其实是在对象里找diff值的diff值的位置。意思就是将每次遍历的值a1先存到对象里，然后接着遍历，找啊找啊，突然找到了a2，这个a2等于target-a1，然后取下标完事。
```

    https://rohan-paul.github.io/javascript/2018/04/29/2-sum/