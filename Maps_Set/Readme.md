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


