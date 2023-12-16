### [Pair Sum](https://www.codingninjas.com/studio/problems/pair-sum_1171154?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)


```java
import java.util.* ;
import java.io.*; 
public class Solution {
    public static int pairSum(int arr[], int n, int target) {
        // Write your code here.
        int left=0, right = n-1, count = 0;
        while(left < right){
            int curr_sum = arr[left] + arr[right];
            if( curr_sum == target){
                count++;
                left++;
            } else if(curr_sum > target){
                right--;
            } else {
                left++;
            }
        }
        if(count == 0 ) return -1;
        return count;
    }
}
```

### [Move All Negative Numbers To Beginning And Positive To End](https://www.codingninjas.com/studio/problems/move-all-negative-numbers-to-beginning-and-positive-to-end_1112620?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)


```java
public class Solution {
    public static int[] separateNegativeAndPositive(int a[]) {
        int n = a.length;
        if(n==1) return a;
        int left=0, right=1;
        while(left<n && a[left]<0 ){
           left++;right++;
        }
        while(right<n && left<n){
            if(a[right] < 0){
                int temp = a[left];
                a[left] = a[right];
                a[right] = temp;
                left++;
            } else {
                right++;
            }
        }
        return a;
    }
}
```


### [Container With Most Water](https://www.codingninjas.com/studio/problems/container-with-most-water_873860?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=SUBMISSION)

```java
public class Solution {

	public static int maxArea(int[] height) {
	    int n = height.length;
		int left=0,right=n-1,max_area = 0,curr_area = 0;
		while(left < right){
			if(height[left] <= height[right]){
				curr_area = height[left] * (right-left);
				left++;
			} else {
				curr_area = height[right] * (right-left);
				right--; 
			}
			max_area = max_area < curr_area ? curr_area : max_area;
		}
		return max_area;
	}
}

```


### [Is SubSequence](https://www.codingninjas.com/studio/problems/is-subsequence_892991?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)


```java
import java.util.* ;
import java.io.*; 
public class Solution {

	public static String isSubsequence(String str1, String str2) {    
    	int n1 = str1.length(), n2= str2.length();
		int c1 = 0, c2 = 0, count = 0;
		while(c1 < n1 && c2 < n2){
			if(str1.charAt(c1) == str2.charAt(c2)){
				c1++;c2++;
				count++;
			}else{
				c2++;
			}
		}
		if(count == n1) return "True";
		return "False";
	}

}
```