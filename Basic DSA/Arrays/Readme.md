### [Second largest element in the array](https://www.codingninjas.com/studio/problems/second-largest-element-in-the-array_873375)

```
import java.util.* ;
import java.io.*; 
public class Solution {
	public static int findSecondLargest(int n, int[] arr) {
		if(n<2) return -1;
		int max = Integer.MIN_VALUE, sec_max = Integer.MIN_VALUE;
		for(int i=0;i<n;i++){
			if(arr[i] > max){
				sec_max = max;
				max = arr[i];
			} else if(arr[i] > sec_max && arr[i] != max){
				sec_max = arr[i];
			}
		}
		if(sec_max == Integer.MIN_VALUE) return -1;
		return sec_max;
	}
}
```

```python
def findSecondLargest(sequenceOfNumbers):
    maxNum = float('-inf')
    secMax = float('-inf')
    for num in sequenceOfNumbers:
        if num > maxNum:
            secMax = maxNum
            maxNum = num
        elif num > secMax and num!=maxNum:
            secMax = num
    

    return -1 if secMax == float('-inf') else secMax
```

### [Rotate array](https://www.codingninjas.com/studio/problems/rotate-array_1230543)

```
import java.util.ArrayList;
import java.util.List;

public class Solution {
	public static ArrayList<Integer> rotateArray(ArrayList<Integer> arr, int k) {
        // Write your code here.
        ArrayList<Integer> res = new ArrayList<Integer>();
        int n = arr.size();
         /*
        First Approach -> Time O(n); Space O(n)

        for(int i=k;i<n;i++){
            res.add(arr.get(i));
        }
        for(int i=0;i<k;i++){
            res.add(arr.get(i));
        }
        return res;
        
        */

        /* 
        Second Approach -> Time O(n); Space O(1)
        */

        k %= n;
        reverseArray(arr,0,k-1);
        reverseArray(arr, k, n-1);
        reverseArray(arr, 0, n-1);
        return arr;
    }

    public static void reverseArray(ArrayList<Integer> arr, int start, int end){
        while(start<=end){
            int temp = arr.get(start);
            arr.set(start, arr.get(end));
            arr.set(end,temp);
            start++; end--;
        }
    }
}
```

```python
def rotateArray(arr: list, k: int) -> list:
    k = k%len(arr)
    arr[:k] = arr[:k][::-1]
    arr[k:] = arr[k:][::-1]
    arr[:] = arr[::-1]
    return arr
```


### [ Non-Decreasing Array](https://www.codingninjas.com/studio/problems/non-decreasing-array_699920)

```
import java.util.* ;
import java.io.*; 
public class Solution {
	public static boolean isPossible(int[] arr, int n) {
		// Write your code here.
		int cnt = 0;
		for(int i=1;i<n && cnt<= 1;i++){
			if(arr[i-1] > arr[i]){
				cnt++;
				if(i-2<0 || arr[i-2] <= arr[i])arr[i-1] = arr[i];
                else arr[i] = arr[i-1]; 
			} 
		}
		return cnt<=1;
	}
}
```

```python
def isPossible(arr, n):
    cnt = 0
    for i in range(1,n):
        if cnt <= 1 and arr[i-1] > arr[i]:
            cnt += 1
            if i-2<0 or arr[i-2] <= arr[i]:
                arr[i-1] = arr[i]
            else:
                arr[i] = arr[i-1]
    
    return cnt<=1
```

### [ Equilibrium Index](https://www.codingninjas.com/studio/problems/equilibrium-index_893014)

```
import java.util.* ;
import java.io.*; 
public class Solution {

	public static int arrayEquilibriumIndex(int[] arr){  
		int n = arr.length, right_sum=0, left_sum = 0;
		for(int i=0;i<n;i++){
			right_sum+=arr[i];
		}
		for(int i=0;i<n;i++){
			right_sum -= arr[i];
			if (left_sum == right_sum) return i; 
			left_sum += arr[i];
		}
		return -1;
	}
}
```

```python
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        rightSum = sum(nums)
        leftSum=0
        for i,num in enumerate(nums):
            rightSum -= num
            if leftSum == rightSum:
                return i
            leftSum += num
            
        return -1
```
### [First Missing Positive](https://www.codingninjas.com/studio/problems/first-missing-positive_699946)

```
import java.util.* ;
import java.io.*; 
public class Solution {
	public static int firstMissing(int[] arr, int n) {
		for(int i=0;i<n;i++){
			if(arr[i]<=0 || arr[i]>n) arr[i] = n+1;
		}
		for(int i=0;i<n;i++){
			int curr_num = Math.abs(arr[i]);
			if(curr_num > n){
				continue;
			}
			curr_num--;
			if(arr[curr_num] > 0) arr[curr_num] *= -1;
		}

        for(int i=0;i<n;i++){
			if(arr[i] >= 0) return i+1;
		}
		return n+1;
    
	}
}
```


```python
def firstMissing(arr, n):
    for i in range(n):
        if arr[i] <= 0 or arr[i] > n:
            arr[i] = n+1

    for num in arr:
        currPos = abs(num)
        if currPos in range(1,n+1) and arr[currPos-1] > 0:
            arr[currPos - 1] = -1*arr[currPos - 1]
         
    for i,num in enumerate(arr):
        if num >= 0:
            return i+1

    return n+1
```