圆括号可以用来影响运算的顺序：

```scss
p {
  width: 1em + (2em * 3);
}

// 编译输出为
p {
  width: 7em;
}
```
