# [278. 第一个错误的版本](https://leetcode-cn.com/problems/first-bad-version)

[English Version](/solution/0200-0299/0278.First%20Bad%20Version/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>你是产品经理，目前正在带领一个团队开发新的产品。不幸的是，你的产品的最新版本没有通过质量检测。由于每个版本都是基于之前的版本开发的，所以错误的版本之后的所有版本都是错的。</p>

<p>假设你有 <code>n</code> 个版本 <code>[1, 2, ..., n]</code>，你想找出导致之后所有版本出错的第一个错误的版本。</p>

<p>你可以通过调用&nbsp;<code>bool isBadVersion(version)</code>&nbsp;接口来判断版本号 <code>version</code> 是否在单元测试中出错。实现一个函数来查找第一个错误的版本。你应该尽量减少对调用 API 的次数。</p>

<p><strong>示例:</strong></p>

<pre>给定 n = 5，并且 version = 4 是第一个错误的版本。

<code>调用 isBadVersion(3) -&gt; false
调用 isBadVersion(5)&nbsp;-&gt; true
调用 isBadVersion(4)&nbsp;-&gt; true

所以，4 是第一个错误的版本。&nbsp;</code></pre>


## 解法

<!-- 这里可写通用的实现逻辑 -->

二分查找。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
# The isBadVersion API is already defined for you.
# @param version, an integer
# @return an integer
# def isBadVersion(version):

class Solution:
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        low, high = 1, n
        while low < high:
            mid = (low + high) >> 1
            if isBadVersion(mid):
                high = mid
            else:
                low = mid + 1
        return low
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int low = 1, high = n;
        while (low < high) {
            int mid = (low + high) >>> 1;
            if (isBadVersion(mid)) high = mid;
            else low = mid + 1;
        }
        return low;
    }
}
```

### **C++**

```cpp
// The API isBadVersion is defined for you.
// bool isBadVersion(int version);

class Solution {
public:
    int firstBadVersion(int n) {
        int low = 1, high = n;
        while (low < high) {
            int mid = low + (high - low) / 2;
            if (isBadVersion(mid)) {
                high = mid;
            } else {
                low = mid + 1;
            }
        }
        return low;
    }
};
```

### **JavaScript**

```js
/**
 * Definition for isBadVersion()
 *
 * @param {integer} version number
 * @return {boolean} whether the version is bad
 * isBadVersion = function(version) {
 *     ...
 * };
 */

/**
 * @param {function} isBadVersion()
 * @return {function}
 */
var solution = function (isBadVersion) {
  /**
   * @param {integer} n Total versions
   * @return {integer} The first bad version
   */
  return function (n) {
    let low = 1,
      high = n;
    while (low < high) {
      const mid = (low + high) >>> 1;
      if (isBadVersion(mid)) {
        high = mid;
      } else {
        low = mid + 1;
      }
    }
    return low;
  };
};
```

### **Go**

```go
/** 
 * Forward declaration of isBadVersion API.
 * @param   version   your guess about first bad version
 * @return 	 	      true if current version is bad 
 *			          false if current version is good
 * func isBadVersion(version int) bool;
 */

func firstBadVersion(n int) int {
    low, high := 1, n
    for low < high {
        mid := (low + high) >> 1
        if isBadVersion(mid) {
            high = mid
        } else {
            low = mid + 1
        }
    }
    return low
}
```

### **...**

```

```

<!-- tabs:end -->
