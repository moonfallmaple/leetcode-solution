# 1.Two Sum

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
```
Given nums = [2, 7, 4, 5], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

### 题解一：穷举
Code:
```
let twoSum = function(nums, target) {
    for(let i=0;i<nums.length;i++){
        for(let j=0;j<nums.length;j++){
            if(nums[i]+nums[j]===target && i!==j){
                return [i,j]                      
            }
        } 
    }   
};
```


### 题解二：搜索全字典

 **步骤1**：新建一个字典dic，将nums[i]和i更新到字典的key和value中

| key   | value     | 
| :---  | :----:    | 
|  2 	|         0	| 
|  7	|         1	| 
|  4  	|         2	| 
|  5  	|         3	| 

 **步骤2**：对nums中的每一项，在字典的key中，搜索相加为9所需的数
例：nums中的第一项为2，若要相加为9，则另一项是7。lookUp=9-2=7
在字典的key中搜索7，如果有就返回这两个数的index

Code:
```
twoSum = function(nums, target) {
    let i
    let len = nums.length;
    let dic={}
    
    for (i=0; i<len; i++) {
        dic[nums[i]]=i  
    }
    
    for (i=0; i<len; i++) {
        let lookUp;
        look=target-nums[i];
        if(dic.hasOwnProperty(lookUp) && dic[lookUp] !== i){
            return [i,dic[lookUp]]
        }        
    }
};
```



### 题解三：边搜索边更新字典

新建一个空字典。对nums中的每一项，先在字典的key中，搜索相加为9所需的数，如果没有这样的key，则将nums[i]和i更新到字典的key和value中，如果有这样的key，则不用继续搜索而是返回它们对应的index就可以

例：序列nums的第0项是2，若要相加为9，则另一项是7。lookUp=9-2=7
在dic中找key为7的项。

| key   | value     | 
| :---  | :----:    | 
|    	|   	    | |
	     
若无此项，则将第0项更新到字典后,i++

| key   | value     | 
| :---  | :----:    | 
|   2 	|   0	    |  

序列nums的第1项是7，若要相加为9，则另一项是2。lookUp=9-7=2
由于在dic有key为2的项，则不用继续搜索返回它们对应的index就可以

Code:
```
let twoSum = function(nums, target) {
    let i
    let lookUp
    let len = nums.length;
    let dic = {};
    
    for (i=0; i<len; i++) {
        lookUp = target-nums[i];
        if (dic[lookUp] !== undefined){
           return [dic[lookUp],i];   
        }
        dic[nums[i]] = i;
    }
};

```



date: 2019-01-09 





 





