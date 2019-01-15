SassScript 支持 8 种主要的数据类型：

- numbers (e.g. 1.2, 13, 10px)
- strings of text, with and without quotes (e.g. "foo", 'bar', baz)
- colors (e.g. blue, #04a3f9, rgba(255, 0, 0, 0.5))
- booleans (e.g. true, false)
- nulls (e.g. null)
- lists of values, separated by spaces or commas (e.g. 1.5em 1em 0 2em, Helvetica, Arial, sans-serif)
- maps from one value to another (e.g. (key1: value1, key2: value2))
- function references

SassScript还支持所有其他类型的CSS属性值，例如Unicode字符集和！重要声明。然而Sass 不会特殊对待这些属性值，一律视为无引号字符串。

## 字符串

- 有引号字符串 (quoted strings)，如 "Lucida Grande";
- 与无引号字符串 (unquoted strings)，如 sans-serif bold

Sass在编译 CSS 文件时不会改变其类型。只有一种情况例外，使用 `#{} (interpolation)` 时，有引号字符串将被编译为无引号字符串，这样便于在 mixin 中引用选择器名：

```scss
//  SCSS
@mixin message($selector) {
    body #{$selector}::before {
        content: 'Hello world!';
    }
}
@include message('.header');

// 输出
body .header::before {
  content: "Hello world!";
}
```

## 列表

列表是Sass如何表示CSS声明的值，如`margin：10px 15px 0 0`或`font-face：Helvetica，Arial，sans-serif`。列表只是一系列其他值，用空格或逗号分隔。实际上，个别值也算作列表：它们只是一个项目的列表。

列表本身并没什么用，但SassScript列表函数使它们变得有用。`nth`函数可以访问列表中的项目，`join`函数可以将多个列表连接在一起，`append`函数可以将项目添加到列表中。`@each`指令还可以为列表中的每个项添加样式。

列表中可以包含子列表，比如 `1px 2px, 5px 6px` 是包含 `1px 2px` 与 `5px 6px` 两个列表的列表。如果内外两层列表使用相同的分隔方式，则需要用圆括号包裹内层，所以也可以写成 `(1px 2px) (5px 6px)`。变化是，之前的 `1px 2px, 5px 6px` 使用逗号分割了两个子列表 (comma-separated)，而 `(1px 2px) (5px 6px)` 则使用空格分割(space-separated)。

```scss
$common-padding: 5px 10px;
```
## Map

```scss
$map: (key1: value1, key2: value2, key3: value3);
```

- 不像列表（List），Map必须以`,`分割，以括号包围；
- Map中，key是唯一的，而value不是唯一的；
- 与列表一样，Map主要使用SassScript函数进行操作。`map-get`函数在Map中查找值，`map-merge`函数将值添加到Map中。`@each`指令可用于为Map中的每个键/值对添加样式。Map中键值对的顺序始终与创建Map时的顺序相同。
- Map可以用在任何List可以使用的地方，使用时被读作： `(key1: value1, key2: value2)` => `key1 value1, key2 value2` 或者 `(key1, value1) (key2, value2)`

## Color

在压缩输出模式下，Sass将输出颜色的最小CSS表示。例如，＃FF0000将在压缩模式下输出为红色，但blanchedalmond将输出为#FFEBCD。

## First Class Functions

`get-function（$ function-name）`返回一个函数引用，该函数可以传递给`call（$ function，$ args ...）`，并且将调用它引用的函数。第一类函数不能直接用作CSS输出，不然会报错。





