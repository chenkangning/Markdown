[TOC]  
 <!-- [TOC]：将标题显示在文章开头当目录索引-->
# 语法说明
1. ## 标题
    #号后要加空格，  
    如果你想要给你的标题添加**id**或者**class**,要在标题最后添加{#id .calss1 .calss2}

# 这个标题拥有1个id {#my_id}
# 这个标题拥有1个class{.class1}
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
---


## 段落/字体

  段落的前后要有空行，所谓的空行指没有文字内容。若想在段內强制换行的方式是使用**两个以上**空格加上回车。   

  *这会是 斜体 的文字*  
  _这会是 斜体 的文字_

  **这会是 粗体 的文字**
  __这会是 粗体 的文字__

  _你也 **组合** 这些字符_
  
  ~~这个文字将会被横线删除~~
***

## 块引用

在段落的毎行或者只在第一行使用符号>，还可使用多个嵌套引用，如:
>区块引用
>>嵌套引用
***

## 代码
 ### 行內代码(加反斜号点)
`<adder>`
      
### 代码块
你可以在你的代码上面和下面添加 **```** 来表示代码块:
```
import shutile
shutile.make_archive()  
```  

### 语法高亮
你可以给你的代码块添加任何一种语言的语法高亮
例如，给python代码添加语法高亮:
```python
import shutile
p = shutile.make_archive()
print(p)  
```
### 代码块class（MPE扩展的特性）
你可以给你的代码块设置 **class** 。
```
javascript {.class1 .class}
function add(x, y) {
return x + y
}
```

### 代码行数   
如果你想要你的代码块显示代码行数，只要添加 **line-numbers** class就可以了。  
例如:  
```javascript{.line-numbers}
function add(x,y){

    return x + y

}

```

***

## 列表

      (符号后要记得加上空格)
    ### 无序列表
    * Item 1
    * Item 2
        * Item 2a
        * Item 2b

    ### 有序列表
    1. Item 1
    2. Item 2
    3. Item 3
        1. Item 3a
        2. Item 3b
***

## 添加图片
![海贼王](～/vs_codde/kangning.jpg)
***

## 链接
[github](http://github.com)
***

## 分割线
    如下，三个或者更多的
    
    ---
    连字符

    ***
    星号

    ___
    下划线
***
## 任务列表
    当 **[]** 不为x时要为空，否则出错  

- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required （any unodered or ordered list supported）
- [x] this is a complete item
- [x] this a complete item
***
## 表格
‘**|**’:分隔表格
‘**---|---**’:分隔标题与內容
‘**--**’：必须要有，数量不限

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
***
---


# 扩展的语法

1. ## 表格  
(    markdown-it parser是本教程所使用的VS Code扩展，不支持表格合并，如要合并可使用HTML代码)
colspan `>` or `empty call`：
| a | b |
| --| --|
| > | 1 |
| 2 |   |
***

## 上标
30^th^
***

## 下标
H~2~0
***

## 脚注（**_未理解_**）
Content [^1]

[^1]: Hi! This is a footnote
***

## 缩略  
(多注意符号的中/英输入法的区别)  

*[HTML]: Hyper Text Markup Language
*[W3C]: World Wide Web Consortium
The HTML specification
is maintained by the W3C.
***

## 标记
==marked==
  

## 流程图
```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
```

