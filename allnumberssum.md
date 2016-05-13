### 16/5/10 字符串中数字子串的求和 ###

	题目：
		给定一个字符串str，求其中全部数字串所代表的数字之和。
	要求：
		1.忽略小数点字符，例如“A1.3”，其中包含两个数字1和3。
		2.如果紧贴数字子串的左侧出现字符‘-’，当连续出现次数为奇数时，
		  则数字视为负，连续出现的数量为偶数时，则数字视为正。
		  例如：“A-1BC--12”,其中包含数字为-1和12。
	例：
		str = "A1CD2E33" , 返回36
		str = "A-1B--2C--D6E" , 返回7
**【JAVA】**

	public class AllNumbersSum {
		public static int numSum(String str) {
			if (str == null)
				return 0;
			char[] cha = str.toCharArray();
			int res = 0;
			int cur = 0;
			int num = 0;
			boolean flag = true; // true 正
	
			for (int i = 0; i < cha.length; i++) {
				cur = cha[i] - '0';
				if (cur < 0 || cur > 9) { // 处理字符
					res += num;
					num = 0;
					if (cha[i] == '-') {
						if (i - 1 > -1 && cha[i - 1] == '-') {
							flag = !flag;
						} else {
							flag = false;
						}
					} else {
						flag = true;
					}
				} else { // 数字部分
					num = num * 10 + (flag ? cur : -cur);
				}
			}
			res += num;
			return res;
		}
	
		public static void main(String[] args) {
			String test = "1K-100ABC500D-T--100F200G!!100H---300";
			System.out.println(numSum(test));
		}
	}		
**测试用例**
<pre>
* 字符串无数字
* 字符串为空
* 字符串中数字子串都为单个数字 1a2b3c
* 数字子串有连续数字
* 数字子串中含有-、--等
* 待补充
</pre>
**C++**
<pre>
#include<iostream>
#include<string>
using namespace std;

bool is_number(char c)
{
	if (c>='0'&&c<='9')
	{
		return true;
	}
	return false;
}
int sum(string str)
{
	int sum = 0;
	int flag1 = -1;
	int flag2 = 0;
	if(str.empty())
		return 0;

	for (int i = 0;i<str.length();i++)
	{

		if (is_number(str[i])&&flag1<0)
		{
			flag1 = i;
		} 

	   if(is_number(str[i])&&flag1>=0&&!is_number(str[i+1]))
		{
			flag2 = i;
			string tem = str.substr(flag1,flag2-flag1+1);
			if (str[flag1-1]=='-'&&str[flag1-2]!='-')
			{
			
					sum = sum-atoi(tem.data());
				
			}
			else
			{
				sum = sum+atoi(tem.data());
			}
		
			flag1 = -1;
		}
	
	}

	return sum;
}
int main()
{
	string str = "A-1BC--12";
	cout<<sum(str);
	return 0;
}
</pre>
