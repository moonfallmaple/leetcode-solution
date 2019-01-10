---
title: Leetcode-1-Reverse Integer
date: 2019-01-09 10:39:12
tags:
---
# 7.Reverse Integer

Given a 32-bit signed integer, reverse digits of an integer.

Example 1:
```
Input: 123
Output: 321
```
Example 2:
```
Input: -123
Output: -321
```
Example 3:
```
Input: 120
Output: 21
```
Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

### 题解一：数字转为string
Code:
```
let reverse = function(x) {
    let stringX=x+'';
    let arrayX=stringX.split('');
    let i
    let newArray=[];
    let reversed
      
    if(x>=0){
            for(i=arrayX.length;i>0;i--){
                newArray.push(arrayX[i-1]);       
            }
            reversed=Number(newArray.slice(0,newArray.length).join(''))
            if(reversed>2**31-1){
                return 0  
            }
        
            return reversed

    }
    
     if(x<0){
            for(i=arrayX.length;i>0;i--){
                newArray.push(arrayX[i-1]);       
            }
            reversed=Number('-'+newArray.slice(0,newArray.length-1).join(''))
            if(reversed<-(2**31)){
                return 0
            }
            return reversed
    }    
};
```


### 题解二：

Code:
```
let reverse = function(a) {
    let x=a
    let y=a
    let z=0
    let c=0
    let i=1
  
    while(x!==0){   
        x=Math.floor(x/10)
        c++
    }  
    if(x>=0){
        while(y!==0){ 
            r=y%10        
            y=Math.floor(y/10)        
            z=z+r*10**(c-i)  
            i++             
        }
        
        if(z>2**31-1){
            return 0  
        }
    }    
    if(x<0){    
        while(y!==0){ 
            r=y%10        
            y=parseInt(y/10)        
            z=z+r*10**(c-i)  
            i++     
        }
        if(z<-(2**31)){
            return 0
        }  
        console.log(z)
    } 
    return z      
};
```


