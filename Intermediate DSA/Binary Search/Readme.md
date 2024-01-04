## [Square Root of a number](https://www.codingninjas.com/studio/problems/square-root-integral_893351)

### Solution - Python
```python
def floorSqrt(n):
   if(n==0):
      return 0
   start = 1
   end = n

   while start<=end:
      mid = start + (end-start)//2
      if mid> n/mid:
         end = mid-1
      else:
         if (mid+1) > n/(mid+1):
            return mid
         start = mid+1
```

## [Search In Rotated Sorted Array](https://www.codingninjas.com/studio/problems/630450)

### Solution - Python
```python
def search(nums, target) :
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[right]:
            if target > nums[mid] or target <= nums[right]:
                left = mid + 1
            else:
                right = mid
        else:
            if target > nums[mid] and target <= nums[right]:
                left = mid + 1
            else:
                right = mid

    return -1 if left == right and target != nums[left] else left
```

## [Single Element in a Sorted Array](https://www.codingninjas.com/studio/problems/1112654)

### Solution - Python
```python
def singleNonDuplicate(arr):
    left,right = 0,len(arr)-1

    while left<right:
        mid = (left+right)//2
        if (mid%2==0 and arr[mid] == arr[mid+1]) or (mid%2!=0 and arr[mid] == arr[mid-1]) :
            left = mid + 1
        else:
            right = mid

    return arr[left]
```

## [Matrix Median](https://www.codingninjas.com/studio/problems/873378)

### Solution - Python
```python
def getMedian(matrix):
    low = matrix[0][0]
    high = 0
    n,m = len(matrix), len(matrix[0])
    totalElements = (n*m)//2

    for i in range(n):
        high = max(high,matrix[i][m-1])
        low = min(low,matrix[i][0])
    
    while(low<=high):
        mid = (low+high)//2
        smallerEquals = blackBox(matrix,mid)
        if(smallerEquals <= totalElements):
            low = mid+1
        else:
            high = mid-1

    return low


def blackBox(matrix,number):
    smallerEquals = 0
    for i in range(len(matrix)):
        smallerEquals += upperBound(matrix[i],number)
    
    return smallerEquals


def upperBound(arr,number):
    ans = len(arr)
    low,high = 0,len(arr)-1
    while(low<=high):
        mid = (low+high)//2
        if(arr[mid]>number):
            ans = mid
            high = mid - 1
        else:
            low = mid + 1

    return ans;

```

## [Aggressive Cows](https://www.codingninjas.com/studio/problems/aggressive-cows_1082559)

### Solution - Python
```python
def aggressiveCows(stalls, k):
    n = len(stalls)
    stalls = sorted(stalls)
    low = ans = 0
    high =(stalls[n-1]-stalls[0])

    while(low<=high):
        mid = (low+high)//2
        canPlaceAtMid = canWeplaceCows(stalls,k,mid)
        if canPlaceAtMid:
            low = mid + 1
        else:
            high = mid - 1

    return high



def canWeplaceCows(stalls,cowsToPlace,minDist):
    cowsPlaced = 1
    lastStall = stalls[0]

    for i in range(1,len(stalls)):
        if (stalls[i]-lastStall) >= minDist:
            cowsPlaced+=1
            lastStall = stalls[i]

        if (cowsPlaced >= cowsToPlace):
            return True
    
    return False
```