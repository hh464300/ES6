函数的默认参数
		--IE不支持
		function demo(a=100,b=200){
			console.log(a,b);
		}
		demo();
		demo(1,2);

	扩展运算符...
		1. function demo(a,b,c,...res){
			console.log(res); 
			//返回[4,5,6,7,8,9]
			//res后面不能写其他的形参
		}
		demo(1,2,3,4,5,6,7,8,9);
		2.  拆包 需要有遍历接口的 
			var arr = [1,2,7,5,3];
			Math.max(...arr);
		
			var str = 'lamp';
			console.log(...str);
	apply参数中的null
		1. window
		2. 不改变this指向

	箭头函数

		例如： var fn = a => a+1;
				fn是函数名
				a 是参数
				a+1是return值
		注意： 如果没有参数
				var fn = ()=>1000;
			   如果多个参数
			   	var fn = (a,b)=>a+b
			   如果需要更多的操作
			   	var fn = (a,b,c)=>{
			   		return Math.max(a,b,c);
			   	}
		特点：
			1. 函数体内的this对象
				绑定定义时所在的对象，而不是使用时所在的对象
			2. 不可以当作构造函数  不能使用new
			3. 该函数体内不存在arguments
数据结构  
	set
		类似于数组，但是成员的值都是唯一的，没有重复的值
		set是一个构造函数，可以传入一个数组(类数组)的初始化默认值
		相关方法 属性
			1. set.size  		成员个数
			2. set.add(value)  	添加值
			3. set.delete(value)删除值
			4. set.has(value)	判断值
			5. set.clear() 		清空值


	weakset
		--使用的地方较少
		类似于set,只有add()   delete()  has() 方法