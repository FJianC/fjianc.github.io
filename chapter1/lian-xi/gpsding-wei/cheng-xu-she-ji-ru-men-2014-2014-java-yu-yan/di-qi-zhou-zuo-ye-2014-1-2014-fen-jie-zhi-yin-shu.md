### 1    分解质因数

**题目内容：**

每个非素数（合数）都可以写成几个素数（也可称为质数）相乘的形式，这几个素数就都叫做这个合数的质因数。比如，6可以被分解为2x3，而24可以被分解为2x2x2x3。

现在，你的程序要读入一个\[2,100000\]范围内的整数，然后输出它的质因数分解式；当读到的就是素数时，输出它本身。

**输入格式:**

一个整数，范围在\[2,100000\]内。

**输出格式：**

形如：

n=axbxcxd

或

n=n

所有的符号之间都没有空格，x是小写字母x。

**输入样例：**

18

**输出样例：**

18=2x3x3

时间限制：500ms                内存限制：32000kb

```java
import java.util.Scanner;
public class Main
{
    public static void main(String[] args)
    {
        Scanner in=new Scanner(System.in);
        int num=in.nextInt(),i=2;
        if(num>=2&&num<=100000)
        {
            for(;i<=Math.sqrt(num);i++)
            {
                if(num%i==0)
                {
                    break;
                }
            }
            if(i>Math.sqrt(num))//num是素数
                {
                    System.out.println(num+"="+num);
                }
            else//num不是素数
                {
                System.out.print(num+"=");
                for(int j=2;j<num;)
                {
                    if(num%j==0)
                    {
                        System.out.print(j+"x");
                        num/=j;
                        j=1;
                    }
                    else if(j>=num-1)
                    {
                        System.out.print(num);
                        break;
                    }
                    j++;
                    if(j==num)//当num是偶数时
                    {
                        System.out.print(num);
                    }
                }
            }
        }
    }
}
```

### 2    完数

**题目内容：**

一个正整数的因子是所有可以整除它的正整数。而一个数如果恰好等于除它本身外的因子之和，这个数就称为完数。例如6=1＋2＋3\(6的因子是1,2,3\)。

现在，你要写一个程序，读入两个正整数n和m（1&lt;=n&lt;m&lt;1000），输出\[n,m\]范围内所有的完数。

提示：可以写一个函数来判断某个数是否是完数。

**输入格式:**

两个正整数，以空格分隔。

**输出格式：**

其间所有的完数，以空格分隔，最后一个数字后面没有空格。如果没有，则输出一个空行。

**输入样例：**

1 10

**输出样例：**

6

时间限制：500ms                内存限制：32000kb

```java
import java.util.Scanner;
public class Main
{
	public static boolean wangshu(int n)
	{
		int sum=0;
		for(int i=1;i<n;i++)
		{
			if(n%i==0)
			{
				sum+=i;
			}
		}
		if(sum==n)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
	public static void main(String[] args)
	{
		Scanner in=new Scanner(System.in);
		int n=in.nextInt();
		int m=in.nextInt();
		int count=0;
		boolean frist=true;		
		for(;n<=m;n++)
		{
			if(wangshu(n))
			{
				if(frist)
				{
					System.out.print(n);
					frist=false;
					count++;
				}
				else
				{
					System.out.print(" "+n);
					count++;
				}
			}
		}
		if(count==0)
		{
			System.out.println("");
		}		
	}
}
```



