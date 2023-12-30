## [Insertion Sort](https://www.codingninjas.com/studio/problems/insertion-sort_3155179)

### Solution - Python
```python
def insertionSort(n: int, arr: List[int]) -> None:
    if n<=1:
        return

    for i in range(1,n):
        j = i-1
        while j>=0 and arr[j] > arr[j+1]:
            arr[j],arr[j+1] = arr[j+1],arr[j]
            j-=1
```

Also Try this one -> [Insertion Sort with Objects](https://neetcode.io/problems/insertionSort)



## [Selection Sort](https://www.codingninjas.com/studio/problems/selection-sort_981162)

### Solution - Python
```python
def selectionSort(arr,n):
    for i in range(n):
        mn = float('inf')
        mnIdx = i
        for j in range(i,n):
            if mn > arr[j]:
                mn = arr[j]
                mnIdx = j
        arr[i],arr[mnIdx] = arr[mnIdx],arr[i]
```

## [Bubble Sort](https://www.codingninjas.com/studio/problems/bubble-sort_980524)

### Solution - Python

```python
def bubbleSort(arr,n):
    sortedIdx = n
    while sortedIdx>0:
        for i in range(0,sortedIdx-1):
            if arr[i] > arr[i+1]:
                arr[i],arr[i+1] = arr[i+1],arr[i]
        sortedIdx -= 1
```

## [Maximum Subarray Sum(Kadane's Algorithm)](https://www.codingninjas.com/studio/problems/630526)

### Solution - Python

```python
def maxSubarraySum(arr, n) :
    mx_sum = float('-inf')
    s = 0
    for i in range(n):
        s += arr[i]
        if mx_sum < s:
            mx_sum = s
        if s<0:
            s = 0
    return 0 if mx_sum<0 else mx_sum
```

Follow up Question - Print Subarrays in above question.

## [Sort 0 1 2 (Dutch National Flag Algorithm)](https://www.codingninjas.com/studio/problems/631055)

### Solution - Python

```python
def sort012(arr, n) :
    left,mid,right = 0,0,n-1
    while mid<=right:
        if arr[mid] == 0:
            arr[left],arr[mid] = arr[mid],arr[left]
            left+=1
            mid+=1
        elif arr[mid] == 2:
            arr[right],arr[mid] = arr[mid],arr[right]
            right-=1
        else:
            mid+=1
```

## [Majority element (Moore's Voting Algorithm)](https://www.codingninjas.com/studio/problems/842495)

### Solution - Python

```python
def findMajorityElement(arr, n):
	count,ele = 0,0
	for num in arr:
		if count ==0:
			ele = num
			count +=1
		elif ele == num:
			count+=1
		else:
			count-=1
	
    # Only if question says that majority element might not exist at all
	count = 0
	for num in arr:
		if num == ele:
			count +=1
	
	return ele if count > n//2 else -1
```