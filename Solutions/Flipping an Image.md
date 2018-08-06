# Flipping an Image
题目传送门[Flipping an Image](https://leetcode.com/problems/flipping-an-image/description/)
## the first solution
```Java
/**
* @author:kaka2y
* @param 	The array to be manipulated.
* @return 	The array has fliped and reversed.
*/
class Solution {
    public int[][] flipAndInvertImage(int[][] A) {
    	if(A == null)
    		return A;
    	for(int i = 0; i<A.length;i++){
    		int len2 = A[i].length;
    		for(int k = 0;k < len2/2; k++){
        		int temp = A[i][k];
            	A[i][k] = A[i][len2-1-k];
            	A[i][len2-1-k] = temp;
        	}
    		for(int j = 0;j < len2;j++){
            	//和1做异或
            	A[i][j] ^= 1;
            }
    	}
    	return A;
    }
}
```
第一次的做法虽然可以运行，不过有三次循环，时间复杂度为O(n^3)，所以改进了以下，使用了下面的`if`语句代替
## improve 1
第二次的做法是在数组的第二次遍历里，采用判断语句，对当前数组做反转，可以减少一个O(n)
```Java
/**
* @author:kaka2y
* @param 	The array to be manipulated.
* @return 	The array has fliped and reversed.
*/
class Solution {
    public int[][] flipAndInvertImage(int[][] A) {
    	if(A == null)
    		return A;
    	for(int[] arr : A){
    		int len2 = arr.length;
    		for(int j = 0;j < len2;j++){
            	//只需要截取一半的长度做交换即可
            	if(j <= len2/2){
            		int temp = arr[j];
                	arr[j] = arr[len2-1-j];
                	arr[len2-1-j] = temp;
            	}
            	//和1做异或
                arr[j] ^= 1;
            }
    	}
    	return A;
    }
}
```
## improve 2
这一次是将第二层的遍历整合起来，仅对一半的数组进行遍历，减少了O(n/2)
```Java
/**
* @author:kaka2y
* @param 	The array to be manipulated.
* @return 	The array has fliped and reversed.
*/
class Solution {
    public int[][] flipAndInvertImage(int[][] A) {
    	if(A == null)
    		return A;
        for(int i = 0;i < A.length;i++){
        	int len2 = A[i].length;
        	for(int j = 0;j <= len2/2;j++){
            	int temp = A[i][j] ^ 1;
                A[i][j] = A[i][len2-1-j] ^ 1;
                A[i][len2-1-j] = temp;
            }
        }
        return A;
    }
}
```
