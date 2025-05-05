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
