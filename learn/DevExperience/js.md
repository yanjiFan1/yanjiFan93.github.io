1. 数字换成数组数字 eg:  1->[1]
eg:  (1 + '').split(',').map(Number)
example2:if(!Array.isArray(req.params.applyIdList)) {req.params.applyIdList = (req.params.applyIdList+'').split(',').map(Number)} 

2.防重复提交
通过在请求的时候加个flag；
eg : 
let flag = false;
handleOk = () => {
	flag = true;
	if(ajax) {
		ajax.success{
			flag = false;
		}
	}
} 

3.获取一个数组中最后一个不为undefined的值；
eg let departmentId = [depList1,depList2,depList3].filter(item => item !== undefined).pop(); //处理部门id，获取选取的最后一个id
！！！ depList1, depList2, depList3为变量

4.请问for循环5000次--- unshift 的push的效率谁高（参考：https://mrluo.life/article/detail/78）
答案  push的效率高   
push  12ms
unshift 1120ms
那问题来了   for循环在数组第一位添加数？
answer:
首先push  然后 reserve   
push reserve  12ms   reserve几乎没有性能消耗
eg:
for (var i = 0; i < 50000; i++) {
　　arr.push(i);
}
arr.reverse(); //可见，reverse性能极高，甚至于没有额外的消耗，可以放心使用。