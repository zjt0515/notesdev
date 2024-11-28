> 模板命名空间
>
> 虽然我们现在可以将模板文件直接放在 `polls/templates` 文件夹中（而不是再建立一个 `polls` 子文件夹），但是这样做不太好。Django 将会选择第一个匹配的模板文件，如果你有一个模板文件正好和另一个应用中的某个模板文件重名，Django 没有办法 *区分* 它们。我们需要帮助 Django 选择正确的模板，最好的方法就是把他们放入各自的 *命名空间* 中，也就是把这些模板放入一个和 *自身* 应用重名的子文件夹里。





## 去除模板中的硬编码 URL

```html
{# 硬编码 #}
<a href="/polls/{{ question.id }}/">{{ question.question_text }}</a>
```

问题在于，硬编码和强耦合的链接，对于一个包含很多应用的项目来说，修改起来是十分困难的。然而，因为你在 `polls.urls` 的 `url()` 函数中通过 name 参数为 URL 定义了名字，你可以使用 `{% url %}` 标签代替它：

```html
<a href="{% url 'detail' question.id %}">{{ question.question_text }}</a>
```

工作方式：在 `polls.urls` 模块的 URL 定义中寻具有指定名字的条目。即寻找到name=detail的url，并传入question.id的参数

方便：如果想修改url名称，只要修改path的第一个参数即可，因为name已经对应，无需修改

## 为 URL 名称添加命名空间







## 

成功处理 POST 数据后，你应该总是返回一个 `HttpResponseRedirect`





- [`request.POST`](https://docs.djangoproject.com/zh-hans/4.2/ref/request-response/#django.http.HttpRequest.POST) 是一个类字典对象，让你可以通过关键字的名字获取提交的数据。 这个例子中， `request.POST['choice']` 以字符串形式返回选择的 Choice 的 ID。 [`request.POST`](https://docs.djangoproject.com/zh-hans/4.2/ref/request-response/#django.http.HttpRequest.POST) 的值永远是字符串。

  注意，Django 还以同样的方式提供 [`request.GET`](https://docs.djangoproject.com/zh-hans/4.2/ref/request-response/#django.http.HttpRequest.GET) 用于访问 GET 数据 —— 但我们在代码中显式地使用 [`request.POST`](https://docs.djangoproject.com/zh-hans/4.2/ref/request-response/#django.http.HttpRequest.POST) ，以保证数据只能通过 POST 调用改动。

- 如果在 `request.POST['choice']` 数据中没有提供 `choice` ， POST 将引发一个 [`KeyError`](https://docs.python.org/3/library/exceptions.html#KeyError) 。上面的代码检查 [`KeyError`](https://docs.python.org/3/library/exceptions.html#KeyError) ，如果没有给出 `choice` 将重新显示 Question 表单和一个错误信息。