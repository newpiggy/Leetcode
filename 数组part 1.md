#代码随想录第一天
#05/10/23
## 数组part 1
###二分法 Leetcode 704
注意事项：

1. 区间分为左闭右开和左右都闭两种：
	* 两种定义情况需要在代码里保持一致
	* right定义；while里<和<=选择；mid移动时候需不需要+1/-1

Java Version

~~~java
/*左闭右闭*/
class Solution {
    public int search(int[] nums, int target) {
        if(nums.length==0) return -1;
        int left=0,right=nums.length-1;
        while(left<=right){
            int mid=left+(right-left)/2;
            if (nums[mid]==target) return mid;
            if (nums[mid]>target) right=mid-1;
            if (nums[mid]<target) left=mid+1;
        }
        return -1;
    }
}
~~~

Python Version

~~~python
#左闭右开
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left=0
        right=len(nums)
        while (left<right):
            mid=left+(right-left)//2
            if (nums[mid]==target):
                return mid
            elif(nums[mid]>target):
                right=mid
            else:
                left=mid+1
        
        return -1
}
~~~

###移除元素 Leetcode 27

快指针指向新数组所需要的元素；

慢指针指向新数组中需要更新的位置 O(n)。

Java Version:

~~~java
class Solution {
    public int removeElement(int[] nums, int val) {
        int slow=0;
        for (int fast=0;fast<nums.length;fast++){
            if (val!=nums[fast]) {
                nums[slow]=nums[fast];
                slow++;
            }
        }
        return slow;
    }
}
~~~
Python Version:

~~~python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        slow=0
        fast=0
        for fast in range(len(nums)):
            if (nums[fast]!=val):
                nums[slow]=nums[fast]
                slow+=1
        return slow
~~~

