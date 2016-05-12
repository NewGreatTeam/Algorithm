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
