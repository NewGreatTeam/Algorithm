### 16/5/8 判断两个字符串是否互为变形词 ###

	题目：
		给定两个字符串str1和str2，如果str1和str2中出现的字符种类一样
		且每种字符出现的次数也一样，那么str1与str2互为变形词。请实现
		函数判断两个字符串是否互为变形词。
	例：
		str1 = "123" ,str2 = "231" ,返回true
		str1 = "123" ,str2 = "2331" ,返回false
**C++不使用数组和STL**
	
	#include<iostream>
	using namespace std;
	int c_time(char *str,char c);
	bool f(char *str1,char *str2);
	int main()
	{
		char *str1 = "123";
		char *str2 = "";
	
		cout<<f(str2,str1);
		return 0;
	}


	bool f(char *str1,char *str2)//判断str1和str2是否为变形
	{
		
	if (strlen(str1)!=strlen(str2))
	{
		return 0;
	}



	if (*str1=='\0'||*str2=='\0')
	{
		return 0;
	}
	while(*str1 != '\0')
	{
		if (c_time(str1,*str1)!=c_time(str2,*str1))
		{
			return 0;
		}
		str1++;
	}
	return 1;}
	int c_time(char *str,char c)//字符c在str中的出现的次数
	{
		int sum = 0;
		if (!str)
		{
			return sum;
		}
		while(*str != '\0')
		{
			if (*str == c)
			{
				sum++;
			}
			str++;
		}
		
		return sum;
	}
