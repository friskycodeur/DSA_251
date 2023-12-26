## [Reverse String Word Wise](https://www.codingninjas.com/studio/problems/reverse-string-word-wise_1262348)


### Solution - Java
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

### Solution - Python
```python
def reverseStringWordWise(string):
    ans = []
    i = len(string) - 1 

    while(i>=0):
        while i>=0 and string[i] == " " :
            i-=1
        j = i
        if i<0:
            break
        while i>=0 and string[i] != " ":
            i-=1
        ans.append(string[i+1:j+1])
    
    return " ".join(ans)
```


## [Encode the Message](https://www.codingninjas.com/studio/problems/encode-the-message_699836)



### Solution - Java
``` java
// Approach #1
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

// Approach #2

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


### Solution - Python

```python
def encode(message):
    n,i = len(message),0
    ans = []
    while i < n:
        char = message[i]
        cnt = 1
        while i+1 < n and message[i+1] == char:
            i+=1
            cnt+=1
        ans.append(char+str(cnt))    
        i+=1
    return ''.join(ans)
```


## [Minimum Parentheses](https://www.codingninjas.com/studio/problems/mnfrj_1075018)

### Solution - Java
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

### Solution - Python
```python
def minimumParentheses(pattern):
    leftPar,rightPar = 0,0
    for s in pattern:
        if s == '(':
            leftPar += 1
        elif s == ')':
            if leftPar > 0:
                leftPar -= 1
            else:               
                rightPar += 1
    
    return (leftPar + rightPar)
```

## [Beautiful String](https://www.codingninjas.com/studio/problems/beautiful-string_1115625)

### Solution - Java

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

### Solution - Python

```python
def makeBeautiful(str):
	n = len(str)
	diffWithZero = generate_diff_size(generate_ans_str(n,0),str)
	diffWithOne = generate_diff_size(generate_ans_str(n,1),str)
	return min(diffWithZero,diffWithOne)


def generate_ans_str(size,startNumber):
	ans = [str(startNumber)]
	ans.extend(str(0 if ans[-1] == '1' else 1) for _ in range(1,size))
	return ''.join(ans)

def generate_diff_size(s1,s2):
	return sum(ch1!=ch2 for ch1,ch2 in zip(s1,s2))
```

### Solution 2 - Python

```python
def makeBeautiful(s):
	count = 0
	n = len(s)
	
	for i in range(n):
		if i%2==0:
			count += 1 if s[i] == '1' else 0
		else:
			count += 1 if s[i] == '0' else 0
	return min(count,n-count)
```

## [Given a string, find the next smallest palindrome](https://www.codingninjas.com/studio/problems/given-a-string-find-the-next-smallest-palindrome_874577)


### Solution - Java
``` Java
import java.util.* ;
import java.io.*; 
public class Solution {

	public static StringBuilder reverse_str(StringBuilder s1){
		StringBuilder s2 = new StringBuilder();
		for(int i=s1.length()-1;i>=0;i--){
			s2.append(s1.charAt(i));
		}
		return s2;
	}

	public static int compare_str(StringBuilder s1, StringBuilder s2){
		for(int i=0;i<s1.length();i++){
			if (Character.getNumericValue(s1.charAt(i))  > Character.getNumericValue(s2.charAt(i))) return 1;
			else if(Character.getNumericValue(s1.charAt(i))  < Character.getNumericValue(s2.charAt(i))) return 2;
			else continue;
		}
		return 0;
	}
	public static String handle_odd(String s, int n){
		StringBuilder ans = new StringBuilder();
		StringBuilder left = new StringBuilder(s.substring(0, n/2));
		char mid = s.charAt(n/2);
		StringBuilder right = new StringBuilder(s.substring(n/2+1, n));
		if(compare_str(reverse_str(left), right) == 1 ){
			ans.append(left);
			ans.append(mid);
			ans.append(reverse_str(left));
		} else {
			left = left.append(mid);
			left = new StringBuilder(add_one(left.toString()));
			ans.append(left);
			ans.append(reverse_str(left).substring(1));
		}
		return ans.toString();
	}

	public static String handle_even(String s, int n){
		StringBuilder ans = new StringBuilder();
		StringBuilder left = new StringBuilder(s.substring(0, n/2)); 
		StringBuilder right = new StringBuilder(s.substring(n/2, n));
		if(compare_str(reverse_str(left), right) == 1 ){
			ans.append(left);
			ans.append(reverse_str(left));
		} else {
			left = new StringBuilder(add_one(left.toString()));
			ans.append(left);
			ans.append(reverse_str(left));
		}
		return ans.toString();
	}
	public static String nextLargestPalindrome(String number, int sz) {
		// Write your code here.
        String ans = "";
		if(is_palindrome(number, sz)){
			number = add_one(number);
			sz = number.length();
		}
		if(sz==1) return number;
        if(sz%2==1){
			ans = handle_odd(number,sz);
		} else{
			ans = handle_even(number,sz);
		}
		return ans;
	}

	public static boolean is_palindrome(String s, int n){
		int i=0,j=n-1;
		while(j>=i){
			if(s.charAt(i) != s.charAt(j)) return false;
			i++;j--;
		}
		return true;
	}

	public static String add_one(String s){
		char[] digits = s.toCharArray();
        int carry = 1;

        for (int i = digits.length - 1; i >= 0; i--) {
            int sum = Character.getNumericValue(digits[i]) + carry;
            carry = sum / 10;
            digits[i] = (char) ((sum % 10) + '0');
        }

        StringBuilder result = new StringBuilder(s.length() + 1);

        if (carry > 0) {
            result.append((char) (carry + '0'));
        }

        result.append(digits);

        return result.toString();
	}
}
```

### Solution - Python

```python
def nextLargestPalindrome(s, length):
    if s == s[::-1]:
        s = addOneToString(s)
        length = len(s)
    if length == 1:
        return s
    
    if(length%2 == 0):
        s= evenCase(s,length)
    else:
        s= oddCase(s,length)

    return s

def addOneToString(s):
    digits = [int(digit) for digit in s]
    carry = 1
    for i in range(len(digits)-1,-1,-1):
        digits[i] += carry
        carry = digits[i] // 10
        digits[i] %=10
    
    if carry:
        digits.insert(0,carry)

    return ''.join(map(str,digits))

def oddCase(s,n):
    leftSide,midEle,rightSide = s[:int(n//2)], s[int(n//2)], s[int(n//2)+1:]
    ans = []

    if int(leftSide[::-1]) < int(rightSide):
        leftSide = addOneToString(leftSide+midEle)
        ans.append(leftSide+leftSide[::-1][1:])
    else:
        ans.append(leftSide + midEle + leftSide[::-1])

    return ''.join(ans)


def evenCase(s,n):
    leftSide,rightSide = s[:int(n/2)], s[int(n/2):]
    ans = []

    if int(leftSide[::-1]) < int(rightSide):
        leftSide = addOneToString(leftSide)
    
    ans.append(leftSide+leftSide[::-1])
    return ''.join(ans)
```