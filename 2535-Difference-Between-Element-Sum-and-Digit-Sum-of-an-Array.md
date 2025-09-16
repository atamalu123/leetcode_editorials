# [2535. Difference Between Element Sum and Digit Sum of an Array](https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/description/)

* [Python Soluton](https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/solutions/7194440/optimal-solution-in-python-java-c-by-ata-zrky/)
* [Java Solution](https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/solutions/7194440/optimal-solution-in-python-java-c-by-ata-zrky/)
* [C# Solution](https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/solutions/7194440/optimal-solution-in-python-java-c-by-ata-zrky/)

# Problem

```
Approach
Loop across each number in nums and for each number

Add to the element sum
Extract the digits of each number and add to the digit sum. This is done by using modulo 10 to extract the digit, then dividing by 10 to reduce the size of the number by 1 and repeating until the number becomes 0.
Complexity
Time complexity: O(n log m) where
n = length of nums
m = number of digits of largest number in nums
The dominant process is the digit extraction + addition process, which takes O(log m) time and is done n times

Space complexity: O(1)
```

# Solution

## Python

```python
class Solution:
    def differenceOfSum(self, nums: List[int]) -> int:
        
        element_sum = 0
        digit_sum = 0

        for num in nums:
            element_sum += num
            while num != 0:
                digit = num % 10
                digit_sum += digit
                num //= 10

        return abs(element_sum - digit_sum)
```

## Java

```java
class Solution {
    public int differenceOfSum(int[] nums) {
        int ele_sum = 0;
        int dig_sum = 0;
        for(int i:nums){
            ele_sum += i;
            dig_sum += sumDigits(i);
        }
        return Math.abs(ele_sum-dig_sum);
    }
    private int sumDigits(int x){
        int sum = 0;
        while(x>0){
            sum += x%10;
            x /= 10;
        }
        return sum;
    }
}
```

## C#
```csharp
public class Solution {
    public int DifferenceOfSum(int[] nums) {
        int sumE = nums.Sum();  
        int sumD = 0;           

        foreach (int num in nums) {
            int n = num;
            while (n > 0) {
                sumD += n % 10; 
                n /= 10; 
            }
        }

        return Math.Abs(sumE - sumD);
    }
}
```

