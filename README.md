# Relatives

Relatives

Description

Given n, a positive integer, how many positive integers less than n are relatively prime to n? Two integers a and b are relatively prime if there are no integers x > 1, y > 0, z > 0 such that a = xy and b = xz.

Input

There are several test cases. For each test case, standard input contains a line with n <= 1,000,000,000. A line containing 0 follows the last case.

Output

For each test case there should be single line of output answering the question posed above.

Sample Input

7

12

0

Sample Output

6

4



这题从题意可以看出就是求比从1~n - 1从有几个数和n没有公共因子， 通常的算法很简单就能够想到， 我开始也是按通常的做法写了一个， 觉得


可能会TLE, 果不其然， 后来上网查了一下， 知道了欧拉函数， 这个就是求比n小的数中与n互质（也就是没有公共因子）的算法， 看来还是那些经典的算法效率比较高， 比纯用暴力试探高多了...


欧拉函数描述如下：

　　利用欧拉函数和它本身不同质因数的关系，用筛法计算出某个范围内所有数的欧拉函数值。

　　欧拉函数和它本身不同质因数的关系：欧拉函数ψ（Ｎ）＝Ｎ｛∏ｐ｜Ｎ｝（１－１/ｐ）。（Ｐ是数Ｎ的质因数）

　　如：

　　ψ（１０）＝１０×（１－１/２）×（１－１/５）＝４；
  

　　ψ（３０）＝３０×（１－１/２）×（１－１/３）×（１－１/５）＝８；
  

　　ψ（４９）＝４９×（１－１/７）＝４２。
  

注意的是P是N的质因子， 这里求质因子还是不能够用常规的判断这个数是不是质数， 这样的话可能还会TLE, 网上学到他们用的一个while() 循环，感觉还挺巧的， 学习了...


#include <stdio.h>   

#include <math.h>   

int enlerFun(int n)   

{   

    int count = n;  
    
    
    int i = 2;  
    
    for(; i<=n; i++)   
    
        if(n % i == 0)   
        
        { 
        
            count -= count / i;  
            
            while(n % i == 0) 
            
                n /= i;   
                
        }   
        
    return count;   
    
}      

int main()   

{   

    int inputVal = 0;   
    
    int count = 0;   
    
    while(scanf("%d", &inputVal) && inputVal != 0)  
    
    {   
    
    
        count = enlerFun(inputVal);   
        
        printf("%d\n", count);   
        
    }    
    
    return 0;   
    
}  

