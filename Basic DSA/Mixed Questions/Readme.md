## [Check Permuation](https://www.codingninjas.com/studio/problems/check-permutation_1172164)

### Solution - Python
```python
def areAnagram(str1, str2):
    n = len(str1)
    if(n != len(str2)):
        return False
    mp = {}
    for c1,c2 in zip(str1,str2):
        if c1 in mp:
            mp[c1] = 0
        else:
            mp[c1] = 1
        
        if c2 in mp:
            mp[c2] = 0
        else:
            mp[c2] = 1
    
    return sum(mp.values()) == 0
```

## [Intersection Of Two Sorted Arrays](https://www.codingninjas.com/studio/problems/intersection-of-2-arrays_1082149)

### Solution - Python
```python
def findArrayIntersection(arr: list, n: int, brr: list, m: int):
    i,j=0,0
    ans = []

    while i<n and j<m:
        if arr[i] == brr[j]:
            ans.append(arr[i])
            i+=1
            j+=1
        elif arr[i] > brr[j]:
            j+=1
        else:
            i+=1
    
    return ans
```

## [N/3 repeated number in array](https://www.codingninjas.com/studio/problems/893027)

### Solution - Python
```python
def majorityElementII(arr):
    e1 = e2 = 0
    c1 = c2 = 0

    for num in arr:
        if num == e1:
            c1+=1
        elif num == e2:
            c2+=1
        elif c1==0:
            e1=num
            c1+=1
        elif c2==0:
            e2 = num
            c2+=1
        else:
            c1-=1
            c2-=1

    ans = []
    if sum(1 for num in arr if num == e1) > len(arr)//3:
        ans.append(e1)
    if sum(1 for num in arr if num == e2) > len(arr)//3:
        ans.append(e2)
    
    return ans
```

## [ Counting Sort](https://www.codingninjas.com/studio/problems/counting-sort_2663351)

### Solution - Python
```python
def sort(n: int, arr: List[int]) -> List[int]:
    maxEle = max(arr)
    minEle = min(arr)
    freqMap = {}
    for num in arr:
        if num in freqMap:
            freqMap[num] += 1
        else:
            freqMap[num] = 1
    
    i = 0
    for num in range(minEle, maxEle+1):
        while num in freqMap and freqMap[num] > 0:
            arr[i] = num
            i+=1
            freqMap[num]-=1
    return arr
```

## [  Rotate matrix to the right](https://www.codingninjas.com/studio/problems/rotate-matrix-by-k_840699)

### Solution - Python
```python
def rotateMatRight(mat, n, m, k):
	res = []
	k %= m
	for arr in mat:
		arr = arr[::-1]
		arr[:k] = arr[:k][::-1]
		arr[k:] = arr[k:][::-1] 
		for ele in arr:
			res.append(ele)
	
	return res
```


## [Find K’th Character of Decrypted String](https://www.codingninjas.com/studio/problems/find-k-th-character-of-decrypted-string_630508)

### Solution - Python
```python
def kThCharaterOfDecryptedString(s, k) :
    i = j = 0
    freq = 0
    subStringLen = decodeStringLen = 0

    n = len(s)
    while i < n:
        subStringLen = freq = 0
        j=i
        while j<n and s[j].isalpha():
            subStringLen+=1
            j+=1
        
        while j<n and s[j].isnumeric():
            freq = freq*10 + int(s[j])
            j+=1

        decodeStringLen = subStringLen * freq
        if(decodeStringLen>=k):
            k-=1
            k%=subStringLen
            return s[i+k]
        else:
            i = j
            k-= decodeStringLen

    return ""
```

## [ Move Zeroes To End](https://www.codingninjas.com/studio/problems/interview-shuriken-41-move-zeroes-to-end_240143)

### Solution - Python
```python
def pushZerosAtEnd(arr):
    n = len(arr)
    if n==1:
        return arr
    i,j = 0,1
    
    while i<n and j<n:
        if arr[i] == 0 and arr[j]!=0:
            arr[i],arr[j] = arr[j],0
        if arr[i] == 0 and arr[j] == 0:
            j+=1
        else:
            i+=1
            j+=1
    
    return arr

```

## [ Sum of Two Elements Equals the Third.](https://www.codingninjas.com/studio/problems/sum-of-two-elements-equals-the-third_992850)

### Solution - Python
```python
def findTriplet(arr,n):
	res = []
	freqDict = {}
	for num in arr:
		if num not in freqDict:
			freqDict[num] = 1
		else:
			freqDict[num] +=1
	
	getOutOfLoop = False
	for i in range(len(arr)):
		for j in range(i+1,len(arr)):
			if arr[i]+arr[j] in freqDict:
				res.append(arr[i])
				res.append(arr[j])
				res.append(arr[i]+arr[j])
				getOutOfLoop = True
				break
		if getOutOfLoop:
			break
	
	return res
```

## [Minimum operations to make strings equal](https://www.codingninjas.com/studio/problems/minimum-operations-to-make-strings-equal_840703)

### Solution - Python
```python

```

## [Maximum Sum Circular Subarray](https://www.codingninjas.com/studio/problems/maximum-sum-circular-subarray_1264302)

### Solution - Python
```python
def maxSubarraySum(arr, n):
	currMax = currMin = totalSum = 0
	maxSum = minSum = arr[0]

	for num in arr:
		totalSum+=num
		currMax = max(currMax+num,num)
		maxSum = max(maxSum,currMax)
		currMin = min(currMin+num,num)
		minSum = min(currMin,minSum)
	return max(maxSum,totalSum-minSum) if maxSum>0 else maxSum
```

## [Longest Consecutive Sequence](https://www.codingninjas.com/studio/problems/longest-consecutive-sequence_759408)

### Solution - Python
```python
def lengthOfLongestConsecutiveSequence(nums, n):
    seqSet = set(nums)
    maxLen = currLen = 0
    for num in seqSet:
        if num-1 not in seqSet:
            currLen = 0
            while num+currLen in seqSet:
                currLen +=1
            maxLen = max(maxLen,currLen)
    
    return maxLen
```

## [Maximum subarray sum after K concatenation](https://www.codingninjas.com/studio/problems/maximum-subarray-sum-after-k-concatenation_874513)

### Solution - Python
```python
def maxSubSumKConcat(arr, n, k):
	arrSum = sum(arr)
	if k == 1:
		return kadanes(arr)
	if k>1:
		if arrSum > 0:
			return (kadanes(arr+arr) + (k-2)*arrSum)
		else:
			return (kadanes(arr+arr))
	
	return 0

def kadanes(arr):
    currSum = 0
    maxSum = float('-inf')
    
    for num in arr:
        currSum +=num
        maxSum = max(currSum,maxSum)
        if currSum < 0:
            currSum = 0

    return maxSum 
```

## [Max Product Count](https://www.codingninjas.com/studio/problems/max-product-count_763416)

### Solution - Python
```python

```

## [Multiply Strings](https://www.codingninjas.com/studio/problems/multiply-strings_982763)

### Solution - Python
```python
def multiplyStrings(a, b):
    if "0" in [a,b]:
        return "0"
    
    res = [0]*(len(a)+len(b))

    a,b = a[::-1],b[::-1]

    for n1 in range(len(a)):
        for n2 in range(len(b)):
            digit = int(a[n1]) * int(b[n2])
            res[n1+n2] += digit
            res[n1+n2+1] += (res[n1+n2]//10)
            res[n1+n2] %=10

    res,beg = res[::-1],0

    while beg<len(res) and res[beg] == 0:
        beg+=1


    res = map(str,res[beg:])
    return "".join(res)
```

## [Find All Sub-Square Of Size K](https://www.codingninjas.com/studio/problems/print-all-kxk_893291)

### Solution - Python
```python

```

## [Missing and repeating numbers](https://www.codingninjas.com/studio/problems/missing-and-repeating-numbers_873366)

### Solution - Python
```python
def missingAndRepeating(arr, n):
    repNum = 0
    misNum = 0

    for num in arr:
        num = abs(num)
        if(arr[num-1] > 0):
            arr[num-1] *=-1
        else:
            repNum = num
    
    for i in range(n):
        if arr[i] > 0:
            misNum = i + 1
            break
    
    return [misNum,repNum]
```

## [Find Four Elements That Sums To A Given Value](https://www.codingninjas.com/studio/problems/983605)

### Solution - Python
```python

```

## [Count All Subarrays With Given Sum](https://www.codingninjas.com/studio/problems/subarray-sums-i_1467103)

### Solution - Python
```python
def findAllSubarraysWithGivenSum(arr, s):
    mp = {}
    cnt = 0
    currSum = 0

    for num in arr:
        currSum += num
        requiredNum = currSum - s
        if requiredNum in mp or requiredNum == 0:
            cnt+=1
        mp[currSum] = 1
    
    return cnt
```

## [Maximum Sum Rectangle](https://www.codingninjas.com/studio/problems/maximum-sum-rectangle_1082564)

### Solution - Python
```python
def maxSumRectangle(arr, n, m):
    sumarr = []
    maxSum = float('-inf')
    for colStart in range(m):
        sumarr = [0 for i in range(n)]
        for colEnd in range(colStart,m):
            for row in range(n):
                sumarr[row]+= arr[row][colEnd]
            currMaxSum = kadanes(sumarr)
            maxSum = max(currMaxSum,maxSum)
    return maxSum

def kadanes(arr):
    currSum = 0
    maxSum = float('-inf')
    
    for num in arr:
        currSum +=num
        maxSum = max(currSum,maxSum)
        if currSum < 0:
            currSum = 0

    return maxSum 
```

## [Find nth elements of spiral matrix](https://www.codingninjas.com/studio/problems/find-nth-elements-of-spiral-matrix_981305)

### Solution - Python
```python
def findKthElement(matrix, k):
    col_it = row_it = 0
    eleCount = 0
    rowSize, colSize = len(matrix), len(matrix[0])

    while rowSize > 0 and colSize > 0:
        eleCount += colSize
        if eleCount >= k:
            return matrix[row_it][eleCount-k]
        else:
            col_it +=1
            rowSize -= 1
        
        eleCount += rowSize
        if eleCount >= k:
            return matrix[eleCount-k][col_it]
        else:
            row_it +=1
            colSize -= 1

    return matrix[0][0]
```
