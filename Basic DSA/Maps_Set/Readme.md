### [Make Unique Array](https://www.codingninjas.com/studio/problems/make-unique-array_920329?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube)


```java
import java.util.* ;
import java.io.*; 
public class Solution {

	public static int minElementsToRemove(ArrayList<Integer> arr) {
		HashSet<Integer> uniq_arr = new HashSet<Integer>();
		for(int i=0;i<arr.size();i++){
			uniq_arr.add(arr.get(i));
		}
		return arr.size() - uniq_arr.size();
	}
}
```


### [ First non repeating character](https://www.codingninjas.com/studio/problems/first-non-repeating-character_920324?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)


```java
import java.util.* ;
import java.io.*; 
public class Solution {

	public static char firstNonRepeatingCharacter(String str) {
		HashMap<Character,Integer> freq_map =new HashMap<Character,Integer>();
		for(int i=0;i<str.length();i++){
			Character curr_char = str.charAt(i);
			if(freq_map.get(curr_char) != null ){
				freq_map.put(curr_char, freq_map.get(curr_char)+1);
			} else {
				freq_map.put(curr_char, 1);
			}
		}

		for(int i=0;i<str.length();i++){
			if(freq_map.get(str.charAt(i)) < 2) return str.charAt(i);
		}

		return str.charAt(0);
	}
}
```


### [Longest Subarray Zero Sum](https://www.codingninjas.com/studio/problems/longest-subset-zero-sum_920321?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)

```java
import java.io.*;
import java.util.* ;

import java.util.ArrayList;

public class Solution {

	public static int LongestSubsetWithZeroSum(ArrayList<Integer> arr) {
		int n = arr.size(),sum=0,mx_len=0;
		HashMap<Integer,Integer> mp = new HashMap<Integer,Integer>();
		for(int i=0;i<n;i++){
			sum+=arr.get(i);

			if(sum==0){
				mx_len = mx_len > i+1? mx_len : i+1;
			}

			if(mp.containsKey(sum)){
				int ln = i- mp.get(sum);
				mx_len = ln > mx_len ? ln : mx_len; 
			}

			if(!mp.containsKey(sum)){
				mp.put(sum, i);
			}
		}
		return mx_len;
	}
}

```

### [Count all sub-arrays having sum divisible by k](https://www.codingninjas.com/studio/problems/count-all-sub-arrays-having-sum-divisible-by-k_973254?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)

```java
import java.util.* ;
import java.io.*; 
import java.util.ArrayList;

public class Solution {

    public static int subArrayCount(ArrayList < Integer > arr, int k) {
        int cnt = 0, rem = 0;
        HashMap<Integer,Integer> prefix_map = new HashMap<Integer,Integer>();
        prefix_map.put(0,1);        
        // Bruteforce method, Time -> O(n^2)
        /*
        for(int i=0;i<arr.size();i++){
            int sum = 0;
            for(int j=i;j<arr.size();j++){
                sum+= arr.get(j);
                if(sum%k == 0) cnt++;
            }
        }
        */


        // Optimal Soln, Time -> O(n)
        for(int i=0;i<arr.size();i++){
            rem = (rem + arr.get(i)) % k;
            if(rem < 0) rem += k;
            cnt += prefix_map.getOrDefault(rem, 0);
            prefix_map.put(rem,prefix_map.getOrDefault(rem, 0) + 1);
        }

        return cnt;
    }
    
}
```

### [Group Anagrams](https://www.codingninjas.com/studio/problems/group-anagrams_800285?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)

```java
import java.util.* ;
import java.io.*; 
public class Solution {

	public static ArrayList<ArrayList<String>> getGroupedAnagrams(ArrayList<String> inputStr, int n) {
		// Write your code here.
		HashMap<HashMap<Character,Integer>,ArrayList<String>> mp = new HashMap<>();
		for(String str: inputStr){
			HashMap<Character,Integer> freq_map = new HashMap<>();
			for(int i=0;i<str.length();i++){
				char curr_char = str.charAt(i);
				freq_map.put(curr_char,freq_map.getOrDefault(curr_char, 0) + 1);
			}
			if(mp.containsKey(freq_map)){
				ArrayList<String> arr = mp.get(freq_map);
				arr.add(str);
				mp.put(freq_map,arr);
			} else {
				ArrayList<String> arr = new ArrayList<>();
				arr.add(str);
				mp.put(freq_map,arr);
			}
		}
		ArrayList<ArrayList<String>> ans = new ArrayList<>(mp.values());
		return ans;
	}
}

```