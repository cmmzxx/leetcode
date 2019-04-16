## 给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水

    示例

    给定 nums = [2, 7, 11, 15], target = 9
    因为 nums[0] + nums[1] = 2 + 7 = 9
    所以返回 [0, 1]

绝对容器大小的因素：1，宽度，即两点的index的差；2，两点较小的那个的值，所以初始为第一个和最后一个，然后向中间移动较小的那个，直到相遇，返回在此之间最大的area

```js
  var maxArea = function(height) {
      let maxArea = 0
      let i = 0
      let j = height.length - 1
      
      while(i < j) {
          let width = j - i
          let min = Math.min(height[i], height[j])
          let area = min * width
          if (maxArea < area) {
              maxArea = min * width
          }
          if (height[i] > height[j]) {
              j--
          } else {
              i++
          }
      }
      return maxArea
  }
```