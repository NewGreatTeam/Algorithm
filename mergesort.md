### 16/5/11 归并排序 ###

	题目：
		理解归并排序，并写出归并排序的代码。
**【JAVA】**

	public class Solution {
		public void sort(int[] A) {
			int[] temp = new int[A.length];
			mergeSort(A ,0 ,A.length - 1,temp);
		}
	
		private void mergeSort(int[] A, int start, int end, int[] temp) {
			if(start >= end)
				return ;
			int mid = (start + end) / 2;
			mergeSort(A, start, mid, temp);
			mergeSort(A, mid + 1, end, temp);
			merge(A,start,mid,end,temp);
		}
	
		private void merge(int[] A, int start, int mid, int end, int[] temp) {
			int left = start;
			int right = mid + 1;
			int index = start;
			
			while(left <= mid && right <= end) {
				if(A[left] < A[right]) {
					temp[index++] = A[left++];
				} else {
					temp[index++] = A[right++];
				}
			}
			
			while(left <= mid) {
				temp[index++] = A[left++];
			}
			
			while(right <= end) {
				temp[index++] = A[right++];
			}
			
			for(index = start;index <= end;index++) {
				A[index] = temp[index];
			}
		}
		
		public static void main(String[] args) {
			int A[] = new int[]{2,9,4,22,3,7,8};
			new Solution().sort(A);
			for(int i = 0;i < A.length;i++) {
				System.out.print(A[i] + " ");
			}
		}
	}
