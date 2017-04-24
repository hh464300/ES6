1.  变量
		let  b = 10;
	特性
		1. 使用let 不能重复声明 也不能使用var重复声明
				let b = 10;
				let b = 100;//报错  --可以改值 但是不能重新声明
				var b = 100;//报错
		2. 没有预解析过程
				console.log(b);
				let b = 10;
		3. 块级作用域
				{
					let b = 10;
					console.log(b); //可以访问
				}
					console.log(b); //不能访问
				--暂存死区 
					声明之前无法访问
2. 常量
		--定义固定不变的量 如：配置文件(用户名 密码 数据的库名 密码 表等)
		不能被修改
		不能重新声明

		如果常量保存的值是一个对象，那么对象的属性值是可以被修改的。

3. 变量的解构赋值
		ES6允许按照一定模式，从数组和对象中取值，对变量进行复制，被称为解构。
		var [a,b,c] = [1,2,3];  顺序一一对应
		只要结构相同也可以解析
			var [a,b,c] = [1,[1,2,3],[4,5,6]];
		数组的解构
			var [a,b,c] = arr;
		对象的解构
			var {a,show,arr} = obj;
		作用： 
			函数return对象    接受的时候可以不用一个一个的赋值。
			值的交换
				var x = 1;var y = 2;
				1. 使用中间变量
				2. var [x,y] = [y,x];
4. 字符串
		1. 'abc'.repeat(3);  字符串重复
		2. 'abc'.codePointAt(0);获取码号
		3. 超级字符串`姓名：${obj.name}`
	扩展方法
		1. str.includes()  --存在返回true 不存在返回false
			参数一： 要查找的字符
			参数二： 起始位置   --查找重哪个位置开始
		2. startsWith(); 是不是首位
				 --返回true | false
		3. endsWith();   是不是尾部
				-- 返回true | false
5. 数值
	   ECMA6提供了二进制和八进制数值的新的写法，分别用前缀0b  和 0o表示

6. Math对象扩展
	Math.trunc()      将小数点去掉
	Math.sign()  判断是正数，负数， 0   -0
	Math.hypot() 勾股定理     (平方和的平方根)
7. 数组的扩展
		1.Array.from();  类数组转换成数组 
			原来的方法
				1. 使用循环
					for(var i = 0; i<list.length; i++){
						eles[i] = list[i];
					}
				2. slice().call()方法
					var list = document.getElementsByTagName('li');
					var eles = [].slice.call(list);
					console.log(eles);	
			新方法
				Array.from(); 
					var list = document.getElementsByTagName('li');
				var eles = Array.from(list);
		2. Array.of();   将一组参数转换成数组
			console.log(Array.of(5));  区别于 new Array(5)
			console.log(Array.of(1,2,4));
		3. arr.find(); 找出第一个符合条件的数组元素
			参数：
				回调函数
			遍历整个数组，遍历过程中调用回调函数，如果回调函数的返回值为true，则返回当前正在遍历的元素
			如果所有元素都不符合条件则返回undefined
		4. arr.findIndex();  找出第一个符合条件的数组的元素索引
			参数：
				回调函数
			查找成功返回索引，否则返回-1
		5. arr.fill()  填充
				@param1   value 填充的内容
				@param2   start 起始点(可选)
				@param3   end   介绍点(可选)

		6. for  of 语句
				--类似for in   （遍历key值）
				for of (遍历value值)
				可以遍历数组 字符串 不能遍历对象  需要一个遍历接口
				遍历对象报错  undefined is not  a function

		7. arr.keys()  获取所有的索引组成一个新的数组
				var iterator = arr.keys();
				console.log(iterator.next().value);   
				console.log(iterator.next().value);   
				console.log(iterator.next().value);   
				console.log(iterator.next().value);
		8. arr.values() 获取所有值组成的数组
				--暂不支持
				var iterator = arr.keys();
		9. arr.entries()  用于对数组键值对的遍历
				for(var [key,value] of arr.entries()){
					console.log(key,value);
				}
		10. 数组的推导
				--通过现有数组生成新的数组
				--非标准 不推荐使用   火狐
				var arr = [1,2,3,4,5];
				var newArr = [for(value of arr) value*2];
8. 对象的扩展
		1.对象中属性的新的表示方法
			var x = 1;
			var y = 2;
			function showObj = function(){
				/*return {
					x:x,
					y:y
				}*/
				return {x,y}
			}
			console.log(showObj());
		2.对象中函数的新的表示方法	
			var obj1 = {
				name:'三毛',
				getName(){
					console.log(this.name);
				},
				age:12
			}
			obj1.getName();
		3. 变量名表示式
				var goods = 'iphone';
				var index = 10;
				var myphone = {
					[goods+index]:'商品ID',
					[goods+'price']:'商品价格',
					['get'+'name'](){
						console.log(this.iphone10,this.iphoneprice);
					}
				}
				myphone.getname();
		4. Object.is() 判断  不会自动转换数据类型
			Object.is(NaN,NaN)  true
			Object.is([],[])    false
			Object.is(0,-1)     false
			Object.is(NaN,0/-0)     true
		5. Object.assign(obj1,obj2,obj3,...); 合并对象
				--如果多个属性的属性名相同，后面的属性会覆盖前面的属性
				--第一个obj1将具有后面所有对象的属性
				  obj2 obj3依然是原来的属性
		6.  obj.__proto__  ECMA6是一个新标准属性  获取设置原型
		当对象的原型 __proto__ 属性已被大多数浏览器厂商所支持的今天，它的存在和使用行为，只是为了ECMAScript 6标准规范作为遗产特征而确保Web浏览器的兼容性。为了更好的支持，仅建议使用 Object.getPrototypeOf() 来代替。
		7.  设置对象的代理
			var obj = {};
			var p = new Proxy(obj,{
				get(obj,attr){
					return obj[attr];
				},
				set(obj,attr,value){
					obj[attr] = value;
				}
			})
		8. Object.observe() -- 检测对象属性的更改 类似于对象
				--此功能已过时。虽然它可能仍然在某些浏览器中工作，但是它的使用是不鼓励的，因为它可以随时被删除。尽量避免使用它。
		9. Object.unobserve() -- 解除检测 此功能已过时

		10. Object.keys() 
				--获取索引的属性组成数组 

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
		
		 