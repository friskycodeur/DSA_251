## [Merge Sort](https://www.codingninjas.com/studio/problems/merge-sort_920442)

### Solution - Python

```python
def mergeSort(arr, n):
    mergeSortRec(arr,0,n-1)
    return arr

def mergeSortRec(arr,low,high):
    if (low >= high):
        return
    mid = (low+high)//2
    mergeSortRec(arr,low,mid)
    mergeSortRec(arr,mid+1,high)
    merge(arr,low,mid,high)

def merge(arr,low,mid,high):
    ans = []
    left = low
    right = mid+1

    while left <= mid and right <= high:
        if arr[left] <= arr[right]:
            ans.append(arr[left])
            left+=1
        else:
            ans.append(arr[right])
            right+=1
    
    while left<=mid:
        ans.append(arr[left])
        left+=1
    
    while right<=high:
        ans.append(arr[right])
        right+=1
    
    for i in range(low,high+1):
        arr[i] = ans[i-low]
```

## [Quick Sort](https://www.codingninjas.com/studio/problems/quick-sort_983625)

### Solution - Python
```python
def quickSort(arr):
    qs(arr,0,len(arr)-1)
    return arr

def qs(arr,low,high):
    if low<high :
        parIdx = placeParitionIndex(arr,low,high)
        qs(arr,low,parIdx-1)
        qs(arr,parIdx+1,high)
    
def placeParitionIndex(arr,low,high):
    pivot = arr[low]
    i,j = low,high
    while i<j:
        while i<= high and arr[i]<=pivot:
            i+=1
        
        while j>=low and arr[j]>pivot:
            j-=1
        
        if j>i:
            arr[i],arr[j] = arr[j],arr[i]
    arr[j],arr[low] = arr[low],arr[j]

    return j
```

### Quick Sort - Descending

```python
def quickSort(arr):
    qs(arr,0,len(arr)-1)
    return arr

def qs(arr,low,high):
    if low<high :
        parIdx = placeParitionIndex(arr,low,high)
        qs(arr,low,parIdx-1)
        qs(arr,parIdx+1,high)
    
def placeParitionIndex(arr,low,high):
    pivot = arr[low]
    i,j = low,high
    while i<j:
        while i<= high and arr[i]>=pivot:
            i+=1
        
        while j>=low and arr[j]<pivot:
            j-=1
        
        if j>i:
            arr[i],arr[j] = arr[j],arr[i]
    arr[j],arr[low] = arr[low],arr[j]

    return j
```


## [Find K-th Element](https://www.codingninjas.com/studio/problems/find-k-th-element_1214963)


### Solution - Python
```python
def findKthElement(a, b, k):
	n,m =len(a),len(b)
	if n>m:
		findKthElement(b,a,k)
	low = max(0,k-m)
	high = min(k,n)
	while low<=high:
		m1 = (low+high)//2
		m2 = k - m1
		l1 = float('-inf') if m1==0 else a[m1-1]
		l2 = float("-inf") if m2==0 else b[m2-1]
		r1 = float("inf") if m1 == n else a[m1] 
		r2 = float("inf") if m2 == m else b[m2]
		if l1<=r2 and l2<= r1:
			return max(l1,l2)
		elif l1>r2:
			high = m1-1
		else:
			low = m1+1
	return 1
```

