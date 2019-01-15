## 基础语法

- `@for $var from <start> through <end>`
- `for $var from <start> to <end>`

```scss
@for $count from 1 through/to 10 {
    .padding-#{$count*10} {
        padding: {
            top: $count * 10px;
            bottom: $count * 10px;
            left: $count * 10px;
            right: $count * 10px;
        }
    }
}
```

> - through与包含<start>和<to>，to只包含<start>不包含<to>;
> - $var可以是任何变量，但<start>和<to>只能是整数；
