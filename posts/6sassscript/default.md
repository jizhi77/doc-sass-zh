可以在变量的结尾添加`!default`给一个未通过`!default`声明赋值的变量赋值.

- 如果变量已经被赋值，不会再被重新赋值;
- 但如果变量还没有被赋值，则会被赋予新的值；

```scss
$content: "First content";
$content: "Second content?" !default;
$new_content: "First time reference" !default;

#main {
  content: $content;
  new-content: $new_content;
}
// 输出CSS
#main {
  content: "First content";
  new-content: "First time reference";
}
```
