### 16/5/6 转圈打印矩阵 ###

	题目：给定一个N*N的矩阵matrix，请按照转圈的方式打印它。
	例：
		1   2   3   4
		5   6   7   8
		9   10  11  12
		13  14  15  16
	打印结果：1 2 3 4 8 12 16 15 14 13 9 5 6 7 11 10
	要求：额外空间复杂度为O(1)。

**JAVA**


	public class PrintMatrixSpiralOrder {

		public static void spiralOrderPrint(int[][] matrix) {
			int tR = 0;
			int tC = 0;                     
			int dR = matrix.length - 1;
			int dC = matrix[0].length - 1;
			while (tR <= dR && tC <= dC) {
				printEdge(matrix, tR++, tC++, dR--, dC--);
			}
		}
	
		public static void printEdge(int[][] m, int tR, int tC, int dR, int dC) {
			if (tR == dR) { // 子矩阵只有一行时
				for (int i = tC; i <= dC; i++) {
					System.out.print(m[tR][i] + " ");
				}
			} else if (tC == dC) { // 子矩阵只有一列时
				for (int i = tR; i <= dR; i++) {
					System.out.print(m[i][tC] + " ");
				}
			} else { // 一般情况
				int curC = tC;
				int curR = tR;
				while (curC != dC) {
					System.out.print(m[tR][curC] + " ");
					curC++;
				}
				while (curR != dR) {
					System.out.print(m[curR][dC] + " ");
					curR++;
				}
				while (curC != tC) {
					System.out.print(m[dR][curC] + " ");
					curC--;
				}
				while (curR != tR) {
					System.out.print(m[curR][tC] + " ");
					curR--;
				}
			}
		}

		public static void main(String[] args) {
			int[][] matrix = { { 1, 2, 3, 4 }, { 5, 6, 7, 8 }, { 9, 10, 11, 12 },
					{ 13, 14, 15, 16 } };
			spiralOrderPrint(matrix);
	
		}
	}

**C++**

	void printEdge(int * m, int tR, int tC, int dR, int dC,int row,int col) {
		if (tR == dR) {
			
			// 子矩阵只有一行时
			for (int i = tC; i <= dC; i++) {
				cout<<*(m+i)<<endl;
			}
	
	
		} 
		
		else if (tC == dC) { 
			
			// 子矩阵只有一列时
			for (int i = tR; i <= dR; i++) {
				cout<<*(m+col*i+tC)<<endl;
			}
	
	
		} 
		
		else { // 一般情况
			int curC = tC;
			int curR = tR;
			while (curC != dC) {
				cout<<*(m+tR*col+curC)<<endl;
				curC++;
			}
			while (curR != dR) {
				cout<<*(m+curR*col+dC)<<endl;
				curR++;
			}
			while (curC != tC) {
				cout<<*(m+col*dR+curC)<<endl;
				curC--;
			}
			while (curR != tR) {
				cout<<*(m+col*curR+tC)<<endl;
				curR--;
			}
		}
	}



	void spiralOrder(int* matrix,int row,int col)
	{
		int tR = 0;
		int tC = 0;
		int dR = row -1;
		int dC = col -1;
		while(tR<=dR&&tC<=dC)
		{
			printEdge(matrix, tR++, tC++, dR--, dC--,col,row);
		}
	}
