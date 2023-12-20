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