# pow(x,n)

实现 pow(x,n) ，即计算 x 的 n 次幂函数。

# 思路1: 暴力法
x * x ... * x (n个x相乘)

复杂度: O(N)
# 思路2: 递归法
减而治之：递归相乘，即pow(x,n) = x * pow(x,n-1) ，时间复杂度比较高，高达n

复杂度: O(N)

# 思路3: 分治法

分而治之：将pow(x,n)分为pow(x,n/2) * pow(x,n/2)（n为偶数）或者pow(x,n/2) * pow(x,n/2) * x（n为奇数），时间复杂度为(log n)
如果n小于0，将x变为其倒数，n = -n，再开始递归即可

复杂度: O(log n)

```
public class Solution {
    public double myPow(double x, int n) {
        int sign=1;
        if(n<0){
            sign=-1;
            n=-n;
        }
        return sign<0? 1/pow(x,n) : pow(x,n) ;
    }
     public double pow(double x,int n){
        if(n==0) return 1;
        if(n==1) return x;
        if(n%2==0) {
            double tmp=pow(x*x,n/2);
            return tmp;
        }else{
            double tmp=pow(x*x,n/2);
            return tmp*x;
        }
    }
```