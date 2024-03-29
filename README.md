# 第2周 2019.09.01 - 2019.09.08

### 1.一篇算法
  数组：
  > 题目：给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。你可以假设数组中无重复元素。

  解法一：普通遍历解法
  
  ```
    function searchInsert(nums, target) {
      if (nums.length === 0) return 0;
      if (target > nums[nums.length - 1]) return nums.length;

      const index = nums.indexOf(target);

      if (index > -1) return index;
      if (index === -1) {
        const len = nums.length;
        let i = 0;
        while (i < len) {
          const num = nums[i];
          if (num > target) {
            nums.splice(i, 0, target);
            break;
          }
          i++;
        }
        return nums.indexOf(target);
      }
    }
  ```
  复杂度分析：

  时间复杂度：最大 O(n)

  空间复杂度：O(n)

  解法二：二分法查找
  [二分法查找的详细题解](https://leetcode-cn.com/problems/search-insert-position/solution/te-bie-hao-yong-de-er-fen-cha-fa-fa-mo-ban-python-/)
  ```
    function searchInsert(nums, target) {
      let left = 0;
      let right = nums.length;

      if (right === 0) return 0;
      if (target > nums[right - 1]) return right;

      while (left < right) {
        const mid = (left + right) >>> 1;
        if (nums[mid] < target) {
          left = mid + 1;
        } else {
          right = mid;
        }
      }
      return left;
    }
  ```

### 2.学到的小技巧 / 知识

### 3.看一篇外语文章

### 4.分享一篇文章

  深拷贝与浅拷贝是老生常谈的一个东西，浅拷贝很容易，深拷贝却不简单，此篇文章就介绍了什么是深浅拷贝，如何使用原生的方法进行深拷贝。

  连接地址：
  [掘金-ConardLi：《如何写出一个惊艳面试官的深拷贝?》](https://juejin.im/post/5d6aa4f96fb9a06b112ad5b1)

# 第1周 2019.08.26 - 2019.09.01

### 1.一篇算法
  数组：
 > 题目：给定一个数组 nums 和一个值 val，你需要原地移除所有数值等于 val 的元素，返回移除后数组的新长度。
不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

解：
采用指针法：
定义2个指针： i慢指针，j快指针
当nums[j] !== val ，复制nums[j]到nums[i] 并同时递增2个指针，重复这一过程，直到 j 到达数组的末尾，该数组的新长度为 i。

```
  var nums = [0,1,2,2,3,0,4,2];
    function removeEl(nums, val) {
      var i = 0;
      for (let j = 0; j < nums.length; j++) {
        if (nums[j] !== val) {
          nums[i] = nums[j];
          i++;
        }
      }
      return i;
    }
```
复杂度分析：

时间复杂度：O(n)

空间复杂度：O(1)

### 2.学到的小技巧 / 知识

### 3.看一篇外语文章

### 4.分享一篇文章

#####  ------------------------------ 偷懒分割线  --------------------

# 第0周 2019.07.22 - 2019.07.28

### 1.一篇算法

### 2.学到的小技巧 / 知识

  使用sort自定义排序，在ie环境下遇到排序不成功的问题

  原来的方法：

  ```
  // 默认倒序排序
  var list = [
    {time: '2019-12-12 23:34:02'},
    {time: '2019-12-2 0:34:02'}
  ];

  // 转成正序排序
  list.sort(function(a, b) {
    const aTime = new Date(a.time).getTime();
    const bTime = new Date(b.time).getTime();
    return aTime - bTime;
  });

  ```

  解决方案：
  ```

  发现在ie下 必须返回1或者-1才会正常排序

  list.sort(function(a, b) {
    const aTime = new Date(a.time).getTime();
    const bTime = new Date(b.time).getTime();
    return aTime > bTime ? 1 : -1;
  });

  ```
### 3.看一篇外语文章

### 4.分享一篇文章
