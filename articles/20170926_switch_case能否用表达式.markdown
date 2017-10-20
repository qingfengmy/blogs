### 第一段代码
```
const a = 33;
const c1 = a>30 && a;// 33 所以可以进入case，进而显示`大于`
console.log(c1);
switch(a){
  case c1:
    console.log('大于');
    break;
  case a<30 && a:
    console.log('小于')
    break;
  default:
    console.log('等于')
}

```
输出`大于`
### 第二段代码
```
const b = 33;
const c2 = b>30;// true 和33不等，所以不显示`大于`，都不匹配，只能是default的`等于`
console.log(c2);
switch(b){
  case c2:
    console.log('大于');
    break;
  case b<30:
    console.log('小于')
    break;
  default:
    console.log('等于')
}
```
输出`等于`
### 其他
```
console.log(true && 44);// 44
console.log(true && 'hello');// hello
console.log(false && 44);// false
console.log(false && 'world');// false
console.log(11 && 44);// 44
console.log(true & 44);// 0
console.log(false & 44);// 0
console.log(11 & 44)// 8
```
### switch case 的不长注意问题
```
switch (10) {
    case 10:
        console.log(10);
    case 11:
        console.log(11);
        break;
    case 12:
        console.log(12);
        break;
}
```
输出 10 11

有人会有疑问说10不符合第二个条件为什么11也会输出，答案是switch case就是这么设计的。一旦开始执行case中的代码，如果不写break，代码会忽略其他case继续执行，直到遇到下一个break。不仅js如此，java和其他语言也是如此。
