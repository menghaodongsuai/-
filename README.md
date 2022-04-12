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







#include<stdio.h>
#include<stdlib.h>
char*getOperand(char* p,double* pnum);
int main()
{
	char exp[]="1-2.5*4+10.2/5.1";
	char * p=exp,op[20];
	int i=0,j=0,k=0;
	double temp,operand[20],result;
	while(*p != '\0')
	{
		if(*p >= '0' && *p <= '9')
		{
			p = getOperand(p,&temp);
			operand[j++] = temp;
			continue;
		}
		else if(*p =='+'||*p=='-')
		{
			op[k++]=*p;
		}
		else if(*p=='*')
		{
			p=getOperand(++p,&temp);
			operand[j-1]*=temp;
			continue;
		}
		else if(*p=='/')
		{
			p=getOperand(++p,&temp);
			operand[j-1]/=temp;
			continue;
		}
		p++;
	}
	result=operand[0];
	for(i=0;i<k;i++)
	{
		switch(op[i])
		{
			case '+': result +=operand[i+1];
						break;
			case '-': result -=operand[i+1];
						break;
		}
	}
	printf("result:%.2lf\n",result);
	return 0;
}
char* getOperand(char*p,double*pnum)
{
	char buffer[20];
	int i=0;
	while(*p>='0'&&*p<='9'||*p=='.')
	{
		buffer[i++]=*p++;
	}
	buffer[i]='\0';
	*pnum=atof(buffer);
	return p;
}

