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