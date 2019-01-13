
# 9.Palindrome Number

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Example 1:
```
Input: 121
Output: true
```
Example 2:
```
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```
Example 3:
```
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```
Follow up:

Coud you solve it without converting the integer to a string?


### 题解一：
每取原数字的最后1位，都储存到变量r中，以便调用为回文的第1位。
去掉原数字的最后1位，形成新的数字。

小技巧
> x%10:得到数字的最后1位

> parseInt(x/10):得去掉最后1位的新整数

Code:
```
let isPalindrome = function(x) {
    let l=x
    let y=x
    let z=0
    let c=0
    let r=0 
    let i=1


    //计算数字的长度
    while(l!==0){   
        l=Math.floor(l/10)
        c++
    }

    //r:除10后得到的余数
    //y:除10后得到的少1位的新整数
    //z：原数倒序后的新数
    while(y!==0){ 
        r=y%10        
        y=parseInt(y/10)        
        z=z+r*10**(c-i)  
        i++             
    }
    if(x<0){
        return false;
    }
    
    return x==z    
};
```
### 题解二：
```
let isPalindrome = function(x) {
   
    let y=x;
    let z=0;

    if(x<0){
        return false     
    }

    while(y !==0){
        z=z*10+y%10
        y=parseInt(y/10);  
    }
    return x==z    
};

```


date: 2019-01-09
