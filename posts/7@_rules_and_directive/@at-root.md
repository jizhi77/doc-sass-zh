- 未完成

```scss
.para {
    font: 14px;
    @at-root {
        p {
            color: red;
        }
    }
    div {
        color: black;
    }
}
// 输出
.para {
  font: 14px;
}
p {
  color: red;
}

.para div {
  color: black;
}
```
