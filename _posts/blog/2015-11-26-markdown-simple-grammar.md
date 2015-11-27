---
layout: post
title: Markdown快速入门简要教程
category: blog
description: Markdown是当今最流行最简洁最高效的文本标记语言
---



### Markdown是什么？
* 一种轻量级标记语言
* 不想也不会取代HTML
* 易读易写的网络书写语言

总结起来就是：Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法使普通文本内容具有一定的格式。

### 谁发明了这个东西？
它由[**Aaron Swartz**](http://www.aaronsw.com/)和**John Gruber**共同设计，**Aaron Swartz**就是那位于前几年（_2013年1月11日_）自杀,有着**开挂**一般人生经历的程序员。维基百科对他的[介绍](https://zh.wikipedia.org/wiki/%E4%BA%9A%E4%BC%A6%C2%B7%E6%96%AF%E6%B2%83%E8%8C%A8)是：**软件工程师、作家、政治组织者、互联网活动家、维基百科人**。    

他有着本可以靠脸吃饭却足以让你跪拜的人生经历：    
+ **14岁**参与RSS 1.0规格标准的制订。     
+ **2004**年入读**斯坦福大学**，一年后退学。   
+ **2005**年创建[Infogami](http://infogami.org/)，之后与[Reddit](http://www.reddit.com/)合并成为其合伙人。   
+ **2010**年创立求进会（Demand Progress），积极参与禁止网络盗版法案（SOPA）活动，最终该提案**居然**被撤回。   
+ **2011**年7月19日，因被控从MIT和JSTOR下载480万篇学术论文并以免费形式上传于网络被捕。     
+ **2013**年1月自杀身亡（天妒英才）。    

### 怎么使用Markdown？
#### 一点点说明
* 由于这是入门级的简要教程，所以涉及到如有两种或多种方法可以达到同样效果的情况，本文只分享一种。
* 详细的语法说明：**Markdown 语法详细说明 ([简体中文版](http://www.appinn.com/markdown/)|[繁体中文版](http://markdown.tw/))**
* 本文按一下顺序分享Markdown常用功能 <br/>
**① 标题** <br/>
**② 段落** <br/>
**③ 区块引用** <br/>
**④ 代码区块** <br/>
**⑤ 强调** <br/>
**⑥ 列表** <br/>
**⑦ 分割线** <br/>
**⑧ 链接** <br/>
**⑨ 图片** <br/>
**⑩ 反斜杠和符号** <br/>
*****************************************************************
### ① 标题
* 标题的设置非常简单，直接使用'#'且'#'的个数直接可表示1-6级标题。

> \# 我爱Markdown  
> \## 我爱Markdown    
> \### 我爱Markdown    
> \#### 我爱Markdown    
> \##### 我爱Markdown    
> \###### 我爱Markdown     

* 效果如下：
   
> ## 我爱Markdown    
> ### 我爱Markdown   
> #### 我爱Markdown    
> ##### 我爱Markdown    
> ###### 我爱Markdown  

### ② 段落
* 一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行（空行的定义是显示上看起来像是空的，便会被视为空行。比方说，若某一行只包含空格和制表符，则该行也会被视为空行）。
* 普通段落不该用空格或制表符来缩进。Markdown 中Email式的**区块引用**和多段落的**列表**在使用换行来排版的时候，不但更好用，还更方便阅读。

### ③ 区块引用
* 在段落的每行或者只在第一行使用符号'>'还可使用多个嵌套引用，如：
> \> 区块引用  
> \>> 嵌套引用  
> \>>> 再嵌套引用 

* 效果如下：
> 区块引用  
>> 嵌套引用
>>> 再嵌套引用 

### ④ 代码区块
* 代码区块的建立是在每行加上4个空格。如：    

**普通段落：**

void main()    
{    
    printf("Hello, Markdown.");    
}    

**代码区块：**

    void main()
    {
        printf("Hello, Markdown.");
    }

* **注意**:代码区块的第一行之前和最后一行之后必须存在空行。

### ⑤ 强调
* 在强调内容两侧加上'\*'和'\**'分别表示斜体和加粗，以此用来强调。如：
> \*我是斜体\* <br/>
> \*\*我是粗体\*\*

* 效果如下：
> *我是斜体* <br/>
> **我是粗体** 

### ⑥ 列表
* Markdown 支持有序列表和无序列表。
* 使用'+'标记无序列表，如：

> \+ Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
> \+ Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.


* **注意**：标记后面最少有一个空格。若不在引用区块中，必须和前方段落之间存在空行。

效果如下：
> + Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
> + Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.

* 有序列表的标记方式是将上述的符号换成数字,并辅以`.`，如：
> 1.  Lorem ipsum dolor sit amet, consectetuer adipiscing elit.Aliquam 
hendrerit mi posuere lectus. Vestibulum enim wisi,viverra nec, fringilla in,
laoreet vitae, risus. 
> 2.  Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.    

效果如下：
> 1.  Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
> 2.  Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.

* 列表项目标记通常是放在最左边，但是其实也可以缩进，最多 3 个空格，项目标记后面则一定要接着至少一个空格。

### ⑦ 分割线
* 分割线最常使用就是三个或以上`*`即可。如：

> \*\*\* 

效果如下：
> *** <br/>
### ⑧ 链接
* 链接的语法非常简单格式是\[需要连接的文字\](URL) ，如：

> \[Markdown创始人](https://zh.wikipedia.org/wiki/%E4%BA%9A%E4%BC%A6%C2%B7%E6%96%AF%E6%B2%83%E8%8C%A8)
效果如下：
> [Markdown创始人](https://zh.wikipedia.org/wiki/%E4%BA%9A%E4%BC%A6%C2%B7%E6%96%AF%E6%B2%83%E8%8C%A8)

### ⑨ 图片
* 添加图片的形式和链接相似，只需在链接的基础上前方加一个`！`。如：
> \!\[Markdown创始人\](http://ww1.sinaimg.cn/mw690/9325ea4dgw1eyfvjpjyc2j20hs0oodhq.jpg)
效果如下：
> ![Markdown创始人](http://ww1.sinaimg.cn/mw690/9325ea4dgw1eyfvjpjyc2j20hs0oodhq.jpg)  <br/>

### ⑩ 反斜杠和符号
#### 反斜杠
* 相当于C语言里**反转义**作用，使符号成为普通符号。如：

> 想显示一个'\\'的效果，就必须使用反斜杠这样表示：\\\

效果如下：
> \\

#### 符号
* 符号起到标记作用。如：
>\`ctrl+a\`

效果如下：
>`ctrl+a`    

### 参考资料###


|资料源                              |链接                                |
|:------------------------------------:|------------------------------------|
|Markdown                              |[https://github.com/younghz/Markdown](https://github.com/younghz/Markdown "Github")|
|亚伦·斯沃茨                            |[https://zh.wikipedia.org/wiki/Aaron_Swartz](https://zh.wikipedia.org/wiki/Aaron_Swartz "维基百科")|
|Markdown繁体中文版                            |[https://markdown.tw/](http://markdown.tw/ "繁体")|
|Markdown简体中文版                            |[http://www.appinn.com/markdown/](http://www.appinn.com/markdown// "简体")|

* 水平有限，难免有错。收获颇多，特别感谢[伍燎](http://wuliao.in)。