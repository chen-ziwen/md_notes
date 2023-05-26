> 总结一下学过的排序算法

### T3 级别
> 这三种排序方式的时间复杂度都是O(n^2)
1. 冒泡排序 ( 最慢)
```javascript
fucntion bubble (nums) {
	const len = nums.length-1;
	for(let i=0;i<len;i++) {
		for(let j=0;j<len-i;j++){
			if(nums[j]>nums[j+1]) {
				[nums[j],nums[j+1]]= [nums[j+1]=nums[j]];
			}
		}
	}
	return nums;
}

```
2. 选择排序 
```javascript
function choose (nums) {
	const len = nums.length;
	for(let i=0;i<len-1;i++) {
	let minIndex = i;
	for(let j=i+1;j<len;i++) {
		if(nums[j]<nums[minIndex]){
		minIndex=j;
		}
	}
	[nums[i],nums[minIndex]]= [nums[minIndex],nums[i]];
		}
	return nums;
}

```
3. 插入排序
```javascript

```