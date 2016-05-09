### 16/5/7 字符串复制 ###
	题目：
		（1）总结C语言字符串复制的源码
		（2）递归方法进行字符串复制
**(1)**

	#include <iostream>
	using namespace std;

	char dest[100] = {};
	char *strcpy_1(char *dest , const char *src)
	{
	    char *to = dest;
	    while( (*dest++ = *src++)!='\0')
	    {
	        NULL;
	    }
	    return to;
	}
	int main()
	{
	    cout << "dest:" << strcpy_1(dest,"ABCD")<< endl;
	    return 0;
	}
**(2)**

	#include <iostream>
	using namespace std;
	
	char dest[100] = {};
	int i = 0;
	void copy(char *src)
	{
	
	    if(*src == '\0')
	    {
	        return;
	    }
	    dest[i++] = *src;
	    copy(src+1);
	    dest[i++] = '\0';
	}
	int main()
	{
	    char *src = "ABCD";
	    cout << "dest:" <<dest << endl;
	    copy(src);
	    cout << "dest:" <<dest << endl;
	    return 0;
	}

**递归**

	char* c_copy(char* dst,const char* src)
	{
	if (*(src) =='\0')
	{
		*dst = '\0';
		return dst;
	}
	*dst = *src;
	dst++;
	src++;
	c_copy(dst,src);
	return dst;
	}
	
