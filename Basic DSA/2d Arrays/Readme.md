## [Sum Of Zeroes](https://www.codingninjas.com/studio/problems/array-sum_893287)

### Solution - Java
```java
import java.util.* ;
import java.io.*; 
import java.util.ArrayList;

public class Solution {

	public static Integer coverageOfMatrix(ArrayList<ArrayList<Integer>> mat) {
		// Write your code here.
		int total_coverage = 0;
		for(int i=0;i<mat.size();i++){
			for(int j=0;j<mat.get(0).size();j++){
				if(mat.get(i).get(j) == 0){
					total_coverage += zero_coverage(mat, i , j);
				}
			}
		}
		return total_coverage;
	}

	public static int zero_coverage(ArrayList<ArrayList<Integer>> mat, int row_idx, int col_idx){
		int cnt = 0;
		if(row_idx + 1 >= 0 && row_idx + 1 < mat.size()) cnt += mat.get(row_idx+1).get(col_idx);
		if(row_idx - 1 >= 0 && row_idx - 1 < mat.size()) cnt += mat.get(row_idx-1).get(col_idx);


		if(col_idx + 1 >= 0 && col_idx + 1 < mat.get(0).size()) cnt += mat.get(row_idx).get(col_idx+1);
		if(col_idx - 1 >= 0 && col_idx - 1 < mat.get(0).size()) cnt += mat.get(row_idx).get(col_idx-1);
		 
		return cnt;
	}
}

```

### Solution - Python
```python
def coverageOfMatrix(mat):
    n,m = len(mat),len(mat[0])
    sum_zeroes = 0
    for i in range(n):
        for j in range(m):
            if mat[i][j] == 1:
                continue
            if (i-1) in range(n):
                sum_zeroes += mat[i-1][j]
            if (i+1) in range(n):
                sum_zeroes += mat[i+1][j]
            if (j-1) in range(m):
                sum_zeroes += mat[i][j-1]
            if (j+1) in range(m):
                sum_zeroes += mat[i][j+1]
    return sum_zeroes
```
### [Matrix Is Symmetric](https://www.codingninjas.com/studio/problems/matrix-is-symmetric_799361)

### Solution - Java
```java
import java.util.* ;
import java.io.*; 
public class Solution {
    public static boolean isMatrixSymmetric(int[][] matrix) {
        // Elegeant solution xd 
        int n = matrix.length;
        for(int i=0;i<n;i++){
            for(int j=i;j<n;j++){
                if(matrix[i][j] != matrix[j][i]) return false;
            }
        }
        return true;
    
    }
}
```

### Solution - Python
```python
def isMatrixSymmetric(matrix):
    n,m = len(matrix), len(matrix[0])
    for i in range(n):
        for j in range(i,m):
            if matrix[i][j] != matrix[j][i]:
                return False 
    return True 
```


### [Set Matrix Zeros](https://www.codingninjas.com/studio/problems/set-matrix-zeros_3846774)

### Solution - Java
```java
import java.io.*;
import java.util.* ;

public class Solution {
    public static void setZeros(int matrix[][]) {
        int n = matrix.length, m = matrix[0].length, flg = 0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(matrix[i][j] == 0){
                    matrix[i][0] = 0;
                    if(j!=0)matrix[0][j] = 0;
                    else flg++;
                } 
            }
        }

        for(int i=1;i<n;i++){
            for(int j=1;j<m;j++){
                if(matrix[i][j]!=0){
                    if(matrix[i][0] == 0 || matrix[0][j] ==0){
                        matrix[i][j] = 0;
                    }
                }
            }
        }
        if(matrix[0][0] == 0){
            for (int j = 0; j < m; j++) {
                matrix[0][j] = 0;
            }
        }
        if(flg!=0){
            for (int i = 0; i < n; i++) {
                matrix[i][0]= 0;
            }
        } 
    }
}
```
### Solution - Python

```python
def setZeros(matrix: List[List[int]]) -> None:
    n, m, colZero = len(matrix), len(matrix[0]), False

    for i in range(n):
        if matrix[i][0] == 0:
            colZero = True
    
    for j in range(m):
        if matrix[0][j] == 0:
            matrix[0][0] = 0

    for i in range(1, n):
        for j in range(1, m):
            if matrix[i][j] == 0:
                matrix[i][0] = 0
                matrix[0][j] = 0
    
    for i in range(1, n):
        for j in range(1, m):
            if matrix[0][j] == 0 or matrix[i][0] == 0:
                matrix[i][j] = 0

    if matrix[0][0] == 0:
        for j in range(m):
            matrix[0][j] = 0

    if colZero:
        for i in range(n):
            matrix[i][0] = 0
```

### [ Inplace rotate matrix 90 degree](https://www.codingninjas.com/studio/problems/inplace-rotate-matrix-90-degree_839734)


### Solution - Java
```java
import java.util.* ;
import java.io.*; 
public class Solution {
	
	public static void inplaceRotate(int[][] arr, int n) {
		
		// Reverse the rows
		for(int i=0;i<n;i++){
			for(int j=0;j<n/2;j++){
				int temp = arr[i][j];
				arr[i][j] = arr[i][n-j-1];
				arr[i][n-j-1] = temp;
			}
		}

		// Convert the rows to columns
		for(int i=0;i<n;i++){
			for(int j=i;j<n;j++){
				int temp = arr[i][j];
				arr[i][j] = arr[j][i];
				arr[j][i] = temp;
			}
		}
	}

}
```

### Solution - Python

```python
def inplaceRotate(inputArray, n):
    for i in range(n):
        inputArray[i] = inputArray[i][::-1]
    
    for i in range(n):
        for j in range(i,n):
            inputArray[i][j],inputArray[j][i] = inputArray[j][i],inputArray[i][j]

    return inputArray
```

### [Print Spiral](https://www.codingninjas.com/studio/problems/print-spiral_547)


### Solution - Java
```java


public class Solution {

	public static void spiralPrint(int matrix[][]){
		if(matrix.length ==0 ) return;
		int row_start = 0, row_end = matrix.length-1;
		int col_start = 0, col_end = matrix[0].length-1;

		while(row_end>=row_start && col_end >= col_start){
			// Traverse Right
			for(int j=col_start;j<=col_end;j++){
				System.out.print(matrix[row_start][j] + " ");
			}
			row_start++;

			// Traverse Down
			for(int i=row_start;i <= row_end; i++){
				System.out.print(matrix[i][col_end] + " ");
			}
			col_end--;

			if(row_start <= row_end){
				// Traverse Left
				for(int j=col_end;j>=col_start;j--){
					System.out.print(matrix[row_end][j] + " ");
				}
				row_end--;
			}

			if(col_start <= col_end){
				// Traverse Up
				for(int i=row_end;i >= row_start; i--){
					System.out.print(matrix[i][col_start] + " ");
				}
				col_start++;
			}
		}
	}
}
```

### Solution - Python