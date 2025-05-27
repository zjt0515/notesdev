# Sass

![image-20250318下午54844497](images/image-20250318下午54844497.png)

Sass:

1. 缩进敏感
2. 不使用花括号、分号

Scss保留原始的css外观，可读性更好

## 变量

```scss
$color-text: #eee;
$color-theme: #000
```



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
> 

## 参考资料

- https://www.sass.hk/docs/

1. 减少重复代码，节省开发时间

## 嵌套规则

在一个选择器中嵌套另一个选择器：解析为后代选择器

> 避免了重复输入父选择器



### 属性嵌套

## 变量

```scss
$name_1: #787878;

.h1 {
  color: $name_1;
}
```

## @
