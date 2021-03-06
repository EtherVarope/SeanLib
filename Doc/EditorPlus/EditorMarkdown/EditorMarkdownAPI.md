﻿# EditorMarkdownAPI

## 简介
unityEditor表现和页面css等表现有所不同。因此EditorMD并没有完整的支持所有Markdown语法规则，而是基于md规则实现更严格的结构。
这样保证在unity中的文档能直接在网站中显示，而不需要额外的修改。
## 基本约束
	1.不允许语法的嵌套而且每一个语法必须在每一行第一个字符，例如嵌套的字体等将不被支持。
	2.支持的语法有所缩减，例如分隔符md规则中支持***、---等在EditorMD中只有一种实现***
	3.增加特殊的语法只在UnityEditor中支持。因此在发布到网页中时需要手动修改。例如跳转页面
## 语法
### 标签
 #1级标题#
 ##2级标题##
 ###3级标题###
效果如下:只支持1-3级标题
# 1级标题
## 2级标题
### 3级标题
***
### 字体
 *斜体*
 **粗体**
 ***斜体+粗体***
效果如下:只能一整行使用 不能嵌套。
*斜体*
**粗体**
***斜体+粗体***
***
### 贴图
 ![](Img/Img.jpg)
效果如下:会自缩放到最大不超过1024尺寸
!(Img/Img.jpg)
***
### 外部链接
 (https://www.baidu.com/)
效果如下:用默认浏览器打开。
**注意：可能会受到部分360等安全软件影响无法正常打开浏览器，会自动copy地址，手动打开浏览器粘贴在地址栏就可以。**
(https://www.baidu.com/)
***
### 跳转页面
 >EditorMarkdownAPI
<color="red">效果如下:EditorMD特有功能，只在Seanlibwindow有效。用来跳转到其他同目录下文档(相对当前目录)。</color>
>EditorMarkdownAPI
***
### 跳转页面(doc)
 >>EditorMarkdownAPI
<color="red">同上 唯一不同是这个跳转按照文档绝对目录</color>
>>EditorMarkdownAPI
### 分割线
 ***
效果如下
***
### 表格
 |姓名|技能|排行
 |--:|--:|--:
 |刘备|哭|大哥
 |关羽|打|二哥
 |张飞|骂|三弟
 效果如下:显示为列表 ,其中第二行中<color="cyan">|--:</color>是为了适配网页MD解析必须加。

|姓名|技能|排行
|--:|--:|--:
|刘备|哭|大哥
|关羽|打|二哥
|张飞|骂|三弟

<color="red">在EditorMD中 也可以用来横向布局</color>
 |!(Img/Img.jpg)|<color="red">表格文字</color>|!(Img/Img.jpg)|(https://www.baidu.com/)|>EditorMarkdownAPI
|!(Img/Img.jpg)|<color="red">表格文字不支持换行</color>|!(Img/Img.jpg)|(https://www.baidu.com/)|>EditorMarkdownAPI
|<color="red">表格文字不支持换行</color>|!(Img/Img.jpg)|                                              
***
### 代码块
 ``` 演示代码
int a()
{
	return 1;
}
 ```
效果如下：将2个区块表示中间的文字，单独显示在一个TextArea中。 其中第一个标签后可以添加标识
```演示代码
int a()
{
	return 1;
}
```
***
### QA 问答块
 QA 如何使用QA语法？
与代码块相似，用QA作为关键字 分别在QA块的 上下行。
其中Qustion问题，添加在 第一个标签之后。
问答块，在Seanlibwindow中可以搜索相关问题。需要通过脚本开启搜索功能。
 QA
效果如下：<color="red">EditorMD特有功能，只在Seanlibwindow有效</color>
QA 如何使用QA语法？
与代码块相似，用QA作为关键字 分别在QA块的 上下行。
其中Qustion问题，添加在 第一个标签之后。
问答块，在Seanlibwindow中可以搜索相关问题。需要通过脚本开启搜索功能。
QA

### 折叠页
 /{ 折叠页演示
<color="red">效果如下:EditorMD特有功能，只在UnityEditor中有效用部分内容折叠。</color>
 /}

/{ 折叠名称
<color="red">效果如下:EditorMD特有功能，只在UnityEditor有效用部分内容折叠。</color>
/}
  
 