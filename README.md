#include<stdlib.h>
#include<time.h>
#include<stdlib.h>
/*人机互猜游戏 
例如：计算机产生一个四位整数“1234”请人猜，可能的提示如下。
人猜的整数计算机判断有几个数字正确，有几个位置正确：
1111 1R1S
1222 2R2S*/
int numRiddle();
int Star();
int main()
{ 
      numRiddle();
      printf("\n"); 
      printf("星星图形\n");
	  Star();
	  printf("谢谢使用\n");
	  getchar();
	  return 0; 
}s
int numRiddle()
{
    int a,z,i,y,s,x,b,c,j,k,q[4]; // j:数字正确的位数 k:位置正确的位数//
    srand((unsigned int)time(NULL)); //重新播种，以防生成伪随机数 
    z=rand()%1000+1000; //计算机生成一个四位数的随机数 
    printf("机器输入四位数\n"); 
    for(c=1; ;c++) //c:猜数次数计算器//
    {
        printf("请输入你猜的四位数:");
        scanf("%d",&x); /*输入人猜的数*/
        a=z; //获取计算机生成的随机数 
        j=0; 
        k=0;
        q[0]=q[1]=q[2]=q[3]=0;
        for(i=1;i<5;i++) 
        {
            s=x; //获取人猜的随机数 
            b=1;
            for(y=1;y<5;y++)   //遍历人猜的数 
            {
                if(a%10 == s%10) //人猜的数与计算机生成的数逐个比较 
                {
                    if(b && y!=q[0] && y!=q[1] && y!=q[2] && y!=q[3]) //防止记下相同数字 
                    {
                        j++;//记下正确数字 
                        b=0;
                        q[j-1]=y;  //用q[j-1]数组记住正确的位置 
                    }  
                    if(i==y) //判断位置是否一样，一样就用k记下正确位置次数 
                        k++;
                }
                s/=10;  //避免与上一次比较的数字相同
            }
            a/=10; 
        }
        printf("你猜的结果是");
        printf("%dR%dS\n",j,k);
        if(k == 4)
        {
            printf("O(∩_∩)O哈哈~，你赢了\n");
            break;  //结束 
        }
    }
    printf("你总共猜了%d次\n",c);
    return 0;
}
int Star()
 { 
 int a,b,c;
 printf("请输入星星的行数\n");  
 scanf("%d",&c);    //输入行数 
 //嵌套循环，最外面的循环控制行数，第二个循环控制星星的位置，第三个循环打印星星个数 
 for(a=1;a<=c;a++)//输出c行 
 {
  for(b=c-a;b>0;b--) // 输出c-a>0个空格 
  {
   printf(" ");
  }
  for(b=1;b<2*a;b++) //输出b<2*a个星星 
  {
   printf("*");
  }
  printf("\n");
  }
 //嵌套循环
  for(a=1;a<=c-1;a++)  //避免重复，输出c-1行 
 {
 for(b=1;b<a+1;b++){ //输出b<a+1个空格 
  printf(" "); 
 }
 for(b=(2*c)-(2*a+1);b>0;b--) //偶数-奇数=奇数，所以会输出奇数个星星 
 {
  printf("*"); 
  } 
printf("\n");
}
  return 0;  
 }

