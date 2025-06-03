# Sass

## 参考资料

- https://www.sass.hk/docs/
- https://sass-lang.com/documentation/syntax/

1. 减少重复代码，节省开发时间

![image-20250318下午54844497](images/image-20250318下午54844497.png)

## Syntax

Sass:

1. 缩进敏感
2. 不使用花括号、分号

Scss保留原始的css外观，可读性更好



## @rules

### @forward



## 变量

定义变量

```scss
$color-text: #eee;
$primary-color: #000
```

使用变量

```scss
body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

### !default

 *仅当*变量未定义或其值为 [`null`](https://sass-lang.com/documentation/values/null) 时，才会为该变量赋值。否则，将使用现有值



## 嵌套

```scss
.navigation {
  li {
    display:inline-block;
    margin-left: 30px;
    &:first-child {
      margin: 0;
  	}
  }
  
  a {
    text-decoration: none;
  }
  
}
```

> 对应css
>
> ```css
> .navigation li {
>   
> }
> ```
>

## 运算符

```scss
+ - * / %
== !=
< <= > >=
and or not
```





## 函数

```scss
@funciton func($list) {
  $new-list: ();
  // 循环
  @each $item in $list {
    // 判断
    @if not meta.call($condition, $item) {
      $new
    }
   	@return $new-list
  }
}
```



## mixin

创建一组重复使用的css声明

```scss
// 定义mixin
// 配合参数传递
@mixin theme($theme: DarkGray) {
  background: $theme;
  box-shadow: 0 0 1px rgba($theme, .25);
  color: #fff;
}

// 使用mixin
.info {
  @include theme;
}
.alert {
  @include theme($theme: DarkRed);
}
.success {
  @include theme($theme: DarkGreen);
}
```



## 嵌套规则

在一个选择器中嵌套另一个选择器：解析为后代选择器

> 避免了重复输入父选择器



### 属性嵌套





## @use

从其他sass样式加载mixins/函数/变量

```scss
@use 'xxx'
```

