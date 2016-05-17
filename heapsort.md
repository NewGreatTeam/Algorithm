### 16/5/9 堆排序 ###

	题目：
		- 理解堆排序的原理
		- 实现堆排序的算法
		- 熟练的写出
**【Java】**

	public class HeapSort {
		/**
		 * 构成堆
		 * @param a 数据
		 * @param r 需要构成堆的根结点序号
		 */
		public static void heapAdjust(int[] a, int r, int n) {
			while ((2 * r + 1) < n) {	 	//第r个结点有右子树
				int j = 2 * r + 1;
				if ((j + 1) < n) {
					if (a[j] < a[j + 1])	//左子树小于右子树，则需要比较右子树
						j++;				//序号增加1，指向右子树 
				}
				if (a[r] < a[j]) {	//比较s与j为序号的数据
					int temp = a[r];
					a[r] = a[j];
					a[j] = temp;
					r = j;			//堆被破坏，需要重新调整
				} else {			//比较左右孩子均大则堆未破坏，不再需要调整
					break;
				}
			}
		}
	
		/**
		 * 堆排序
		 * @param a
		 * @param n
		 */
		public static void heapSort(int a[], int n) {
			for (int i = n / 2 - 1; i >= 0; i--) {
				heapAdjust(a, i, n);
			}
			for (int i = n - 1; i > 0; i--) {
				int temp = a[0];
				a[0] = a[i];
				a[i] = temp;
				heapAdjust(a, 0, i); //将a[0]至a[i]重新调整为堆
			}
		}
	
		public static void main(String[] args) {
			int a[] = { 23, 15, 73, 70, 100, 99, 44, 1, 49, 12 };
			System.out.println("原数据：");
			for (int i = 0; i < a.length; i++) {
				System.out.print(a[i] + " ");
			}
			heapSort(a, a.length);
			System.out.println();
			System.out.println("堆排序数据：");
			for (int i = 0; i < a.length; i++) {
				System.out.print(a[i] + " ");
			}
		}
	}


**C++**
	
	#include<iostream>
	using namespace std;
	//构建大顶堆的调整算法
	void sift(int r[],int k,int m)
	{
		int i = k;
		int j = 2*k;
		while (j<=m)
		{
			if (j<m && r[j]<r[j+1])
			{
				//j指向较大的孩子结点
				j = j + 1;
			}
			if (r[i]<=r[j])
			{
				int temp = r[i];
				r[i] = r[j];
				r[j] = temp;
				//根节点的调整会影响孩子结点，所以一直调整到m
				i = j;
			j = 2*i;
			}
			else
			{
				break;
			}
		
		}
	}
	//堆排序
	void HeapSort(int r[ ], int n)
	{
		int i;
		for (i=n/2; i>=1; i--)       //初始建堆，从最后一个非终端结点至根结点
		{
		sift(r, i, n) ;     
		}
		for (i=1; i<n; i++)        //重复执行移走堆顶及重建堆的操作
		{
			int temp = r[1];
			r[1] = r[n-i+1];
			r[n-i+1] = temp;
			sift(r, 1, n-i);
		}
	}
	
	int main()
	{
		int a[] = {0,36,30,18,40,32,45,22,50};
		int i ;
		for (i = 1;i<9;i++)
		{
			cout<<a[i]<<" ";
		}
		cout<<endl;
	
		HeapSort(a,8);
		
		for (i = 1;i<9;i++)
		{
			cout<<a[i]<<" ";
		}
		cout<<endl;
		return 0;
	}
