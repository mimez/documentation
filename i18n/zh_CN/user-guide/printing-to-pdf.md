# 打印成PDF文档

注：这项功能始于EspoCRM 5.0.5版。

“打印成PDF”是生成一份包含记录数据的PDF文档。文档的内容由“模板”定义。


1. 对于你想打印的记录，它的实体类型必须至少要有一个“模板”。
2. “打印成PDF”这项功能在细节视图上邻近“编辑”按钮的下拉菜单中。

## 模板

“模板”选项卡在默认情况下是隐藏着的。管理员可以在“管理”>“用户界面”中添加模板。

如果你要进行更精确的编辑工作，推荐采用“代码视图”模式。

在模板中使用占位符，可以打印记录字段与相关记录字段。

如：

* `{{name}}`——记录名；
* `{{assignedUserName}}`——指派的用户；
* `{{account.name}}`——相关账户的名称。

可以打印图片字段：
```
<img src="{{file imageId}}">
```

其中的`imageId`是自定义图像字段的名称，它带有后缀`Id`。

要显示没有小数部分的浮点数字（如整数），使用下列的表达式：
```
{{numberFormat quantity_RAW decimals=0}}
```

对货币数值的格式进行自定义：
```
{{numberFormat unitPrice_RAW decimals=2 decimalPoint=',' thousandsSeparator=' '}}
```

值`10000.5`会被打印为`10 000,50`（千分位后有空格，小数点用英文逗号表示）。

显示多行的文本字段，要使用三层大括号包围它：`{{{description}}}`。

