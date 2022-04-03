# -
计算机
#include<stdio.h>
#include<string.h>
int main()
{
	char strExp[]="3+4";
	int a=strExp[0]-'0';
	int b=strExp[2]-'0';
	printf("%d",a+b);
	return 0;
}


#include<stdio.h>
#include<string.h>
int main()
{
	char strExp[]="1+2+2+1+2+5+4-1-3+4-8";
	int a=strExp[0]-'0';
	int i;
	for(i=1;i<strlen(strExp);i++)
	{
	    if(strExp[i]=='+')
		{
			int m=strExp[i+1]-'0';
			a=a+m;
			i++;
		}
		else if(strExp[i]=='-')
		{
			int n=strExp[i+1]-'0';
			a=a-n;
			i++;
		}	
	}
	printf("%d",a);
	return 0; 
}


#include<stdio.h>
#include<string.h>
int main()
{
	char strExp[]="2*2/4*1/1*2*3/2";
	int a=strExp[0]-'0';
	int i;
	for(i=1;i<strlen(strExp);i++)
	{
	    if(strExp[i]=='*')
		{
			int m=strExp[i+1]-'0';
			a=a*m;
			i++;
		}
		else if(strExp[i]=='/')
		{
			int n=strExp[i+1]-'0';
			a=a/n;
			i++;
		}	
	}
	printf("%d",a);
	return 0; 
}



#include<stdio.h>
#include<string.h>
int main()
{
	char s[]="2+2*3+2/2-1";
	int i;
	int ans=s[0]-'0';
	int sum,sub,mul,div; 
	//分别代表加减乘除 
	for(i=1;i<=sizeof(s);i++)
	{
		if(s[i] == '+')
		{
			if(s[i+2] == '*' || s[i+2] == '/')
				i++;
			//如果下一运算符为*/时，i+1 
			else
			{
				ans += s[i+1]-'0';
				i++;
			}		
		}
		//加法 
		else if(s[i] == '-')
		{
			if(s[i+2]=='*' || s[i+2]=='/')
				i++;
			//如果下一运算符为*/时，i+1 
			else
			{
				ans -= s[i+1]-'0';
				i++;
			}
		}
		//减法 
		else if(s[i] == '*')
		{
			mul=(s[i-1]-'0') * (s[i+1]-'0');
			ans+=mul;
			s[i+1]=mul;
			i++;
		}
		//乘法 
		else if(s[i] == '/')
		{
			div=(s[i-1]-'0' )/ (s[i+1]-'0');
			ans+=div;
			s[i+1]=div;
		
			i++;
		}
		//除法 
		
	} 
	printf("v3答案是：%d",ans);
	
	return 0;
	
	
}
