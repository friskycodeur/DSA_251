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

```

