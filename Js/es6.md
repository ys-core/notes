
Array Destructure

1. 事实上,只要某种数据结构具有Iterator接口,都可以采用数组形式的解构赋值

2. 默认值可以引用解构赋值的其他变量，但该变量必须已经声明。
	let [x = 1, y = x] = [];     // x=1; y=1
	let [x = 1, y = x] = [2];    // x=2; y=2
	let [x = 1, y = x] = [1, 2]; // x=1; y=2
	let [x = y, y = 1] = [];     // ReferenceError: y is not defined
	
Object Destructure

1.  let { foo: baz } = { foo: 'aaa', bar: 'bbb' };
	baz // "aaa"
	foo // error: foo is not defined
	上面代码中，foo是匹配的模式，baz才是变量。真正被赋值的是变量baz，而不是模式foo。
	
String Destructure




解构赋值的规则是，只要等号右边的值不是对象或数组，就先将其转为对象。由于undefined和null无法转为对象，所以对它们进行解构赋值，都会报错。
let { prop: x } = undefined; // TypeError
let { prop: y } = null; // TypeError