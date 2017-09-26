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
