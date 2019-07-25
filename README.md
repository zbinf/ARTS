# 第一周 2019.07.22 - 2019.07.28

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
