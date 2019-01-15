Sass扩展了CSS的`@import`规则，允许它导入SCSS和Sass文件。被导入的文件将合并编译到同一个 CSS 文件中，另外，被导入的文件中所包含的变量或者混合指令 (mixin) 都可以在导入的文件中使用

通常，@import 寻找 Sass 文件并将其导入，但在以下情况下，@import 仅作为普通的 CSS 语句，不会导入任何 Sass 文件:

- 文件扩展名为`.css`；
- 文件名以'http://`开头；
- 文件名形式为`url()`；
- 有media query形式；

```scss
@import "foo.css";
```

## Partials

如果需要导入 SCSS 或者 Sass 文件，但又不希望将其编译为 CSS，只需要在文件名前添加下划线，这样会告诉 Sass 不要编译这些文件，但导入语句中却不需要添加下划线。

例如，将文件命名为 `_colors.scss`，便不会编译 `_colours.css` 文件。

```scss
@import "colors";
```

上面的例子，导入的其实是`_colors.scss` 文件

> 注意，不可以同时存在添加下划线与未添加下划线的同名文件，添加下划线的文件将会被忽略。

## Index

如果您使用特殊名称`_index.scss`或`_index.sass`编写文件，则在导入包含该文件的目录时将加载该文件。例如，如果你有`dir/_index.scss`，你可以写`@import“dir”;`它会加载你的文件。但是，如果您有一个名为`_dir.scss`的文件和一个名为`dir/_index.scss`的文件，则`_dir.scss`将优先。

## 嵌套

大多数情况下，一般在文件的最外层（不在嵌套规则内）使用 @import，其实，也可以将 @import 嵌套进 CSS 样式或者 @media 中，与平时的用法效果相同，只是这样导入的样式只能出现在嵌套的层中。

假设 example.scss 文件包含以下样式：

```scss
.example {
  color: red;
}
```

然后导入到 #main 样式内

```scss
#main {
  @import "example";
}
```

将会被编译为

```scss
#main .example {
  color: red;
}
```

> 不可以在混合指令 (mixin) 或控制指令 (control directives) 中嵌套 @import。
