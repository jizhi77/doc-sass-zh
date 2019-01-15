@while 指令重复输出格式直到表达式返回结果为 false。这样可以实现比 @for 更复杂的循环。

```scss
$i: 1;
@while($i<10){
 $current: $i*10;
 
  .padding-#{$current}{
    top: $current;
    bottom: $current;
    left: $current;
    right: $current;
  }
  $i: $i+1;
}
```
