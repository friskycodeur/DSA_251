### [Second largest element in the array](https://www.codingninjas.com/studio/problems/second-largest-element-in-the-array_873375?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube)

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

### [Rotate array](https://www.codingninjas.com/studio/problems/rotate-array_1230543?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)

```
import java.util.ArrayList;
import java.util.List;

public class Solution {
	public static ArrayList<Integer> rotateArray(ArrayList<Integer> arr, int k) {
        // Write your code here.
        ArrayList<Integer> res = new ArrayList<Integer>();
        int n = arr.size();
        for(int i=k;i<n;i++){
            res.add(arr.get(i));
        }
        for(int i=0;i<k;i++){
            res.add(arr.get(i));
        }
        return res;
    }
}
```


### [ Non-Decreasing Array](https://www.codingninjas.com/studio/problems/non-decreasing-array_699920?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=SUBMISSION)

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

### [ Equilibrium Index](https://www.codingninjas.com/studio/problems/equilibrium-index_893014?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)

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
### [First Missing Positive](https://www.codingninjas.com/studio/problems/first-missing-positive_699946?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=SUBMISSION)

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