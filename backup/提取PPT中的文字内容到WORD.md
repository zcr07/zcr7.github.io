## 提取PPT中的文字内容到WORD

1、打开PPT文件，按 `Alt + F11`  键打开[VBA编辑器

2、点击【工具】-【引用】，找到 `Microsoft Word 16.0 Object Library ` `勾选添加。

3、点击【插入】-【模块】，复制以下代码进编辑器。


```
Sub Main()
On Error Resume Next
Dim temp As New Word.Document, tmpShape As Shape, tmpSlide As Slide
For Each tmpSlide In ActivePresentation.Slides
For Each tmpShape In tmpSlide.Shapes
temp.Range().Text = temp.Range() + tmpShape.TextFrame.TextRange.Text
Next tmpShape
Next tmpSlide
temp.Application.Visible = True
End Sub
```

4、最后点击【运行】代码，或者按【F5】键，PPT就成功转换成Word了。


<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/07.13:13:02:20.png" style="width:400px;"></p><br>

按 `Alt + F11`  

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/07.13:13:03:15.png" style="width:400px;"></p><br>

点击【工具】-【引用】

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/07.13:13:05:23.png" style="width:400px;"></p><br>

点击【插入】-【模块】

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/07.13:13:08:11.png" style="width:400px;"></p><br>

点击 运行图标

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/07.13:13:09:28.png" style="width:400px;"></p><br>

转换成功

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/07.13:13:11:05.png" style="width:400px;"></p><br>