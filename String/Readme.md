### [Reverse String Word Wise](https://www.codingninjas.com/studio/problems/reverse-string-word-wise_1262348?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=SUBMISSION)

```java
import java.util.Scanner;

class Solution {

    static String reverseStringWordWise(String input) {
        // Write your code here
        int i=input.length()-1;
        String ans = "";
        while(i>=0){
            // To skip trailing spaces
            while(i>=0 && input.charAt(i) == ' ') i--;
            int j=i;
            // Takes care of starting spaces if any 
            if(i<0) break;
            // To point i to the next space, i.e start of the current word
            while(i>=0 && input.charAt(i) != ' ') i--;
            if(!ans.isEmpty()) ans = ans.concat(" ");
            ans = ans.concat(input.substring(i+1,j+1));
        }
        return ans;
    }

    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();
        String ans = reverseStringWordWise(input);
        System.out.println(ans);
    }
}
```


### [Encode the Message](https://www.codingninjas.com/studio/problems/encode-the-message_699836?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=SUBMISSION)



Sol-1 : 
``` java
import java.util.* ;
import java.io.*; 
public class Solution {
	public static String encode(String message) {
		int n = message.length();
		if(n == 0) return message;
		StringBuilder ans = new StringBuilder();
		Character prev_char = message.charAt(0);
		int cnt = 1;
		for(int i=1;i<n;i++){
			if(message.charAt(i) == prev_char){
				cnt++;
			} else{
				String char_message = prev_char + Integer.toString(cnt);
				ans.append(char_message);
				prev_char = message.charAt(i);
				cnt=1;
			}
		}
		String char_message = prev_char + Integer.toString(cnt);
		ans.append(char_message);
		return ans.toString();
	}
}
```

Sol-2:

``` java
import java.util.* ;
import java.io.*; 
public class Solution {
	public static String encode(String message) {
		int n = message.length();
		if(n == 0) return message;
		StringBuilder ans = new StringBuilder();
		for(int i=0;i<n;i++){
			char prev_char = message.charAt(i);
			int cnt = 1;
			while(i+1<n && message.charAt(i+1)==prev_char){
				i++;
				cnt++;
			}
			String encoded_char = prev_char + Integer.toString(cnt);
			ans.append(encoded_char);
		}
		return ans.toString();
	}
}
```


### [Minimum Parentheses](https://www.codingninjas.com/studio/problems/mnfrj_1075018?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=PROBLEM)

``` Java
import java.util.* ;
import java.io.*; 
public class Solution {
	public static int minimumParentheses(String pattern) {
		// Write your code here.
		int open_pr = 0, close_pr = 0, n = pattern.length();
		char close_pattern = ')', open_pattern = '(';
		for(int i=0;i<n;i++){
			if(pattern.charAt(i) == close_pattern){
				if(open_pr > 0 ) open_pr--;
				else close_pr++;
			} else {
				open_pr++;
			}
		}
		return open_pr+close_pr;
	}
}
```

### [Beautiful String](https://www.codingninjas.com/studio/problems/beautiful-string_1115625?utm_source=youtube&utm_medium=affiliate&utm_campaign=parikh_youtube&leftPanelTabValue=SUBMISSION)

``` Java
public class Solution {
    public static int makeBeautiful(String str) {
        int n = str.length();
        int diff_zero = get_diff_size(generate_ans_str(n, 0), str);
        int diff_one = get_diff_size(generate_ans_str(n, 1), str);
        return diff_one>diff_zero?diff_zero:diff_one;
    }

    public static String generate_ans_str(int size, int start_number){
        StringBuilder ans = new StringBuilder();
        if(size==0) return ans.toString();
        ans.append(start_number);
        for(int i=1;i<size;i++){
            int curr_bin_num = (ans.charAt(i-1) == '1')? 0 : 1;
            ans.append(curr_bin_num);
        }
        return ans.toString();
    }

    public static int get_diff_size(String s1, String s2){
        int diff_size = 0, n= s1.length();
        for(int i=0;i<n;i++){
            if(s1.charAt(i) != s2.charAt(i)) diff_size++;
        }
        return diff_size;
    }
}
```