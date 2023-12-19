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

