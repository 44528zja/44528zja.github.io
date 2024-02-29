---
title: html以及css学习
date: 2024-02-10 21:35:11
tags: [html,css]
categories: 学习笔记
---

# html

## 容易忘的标签

```html
<!--删除线-->
<del>删除线</del>
<s>删除线</s>
<!--下划线-->
<ins>下划线</ins>
<u>下划线</u>
<!--倾斜线-->
<em>倾斜线</em>
<i>倾斜线</i>
```

## 图像标签

>图像标签为单标签

```html
<img src=./img.jpg alt='图片显示不出来的标签' title='鼠标放到图片上显示的文字'>
```

>图片标签 也有 width宽度 height 高度 borer边框属性

## 超链接标签

```html
<a href='跳转目标' target='有两种弹出方式'>链接1号</a>
```

>target='_self' target='_blank' 在新窗口跳转

### 链接分类

1. 外部链接

2. 内部链接

3. 空链接 

   ```html
   <a href='#'>空链接</a>
   ```

   

4. 下载链接 

```html
<a href='文件名字'>下载链接</a>
```

5. 网页元素链接

   ```html
   <a <href='xxx.com'><img src='img.jpg'></a>
   ```
   

  6.锚点链接

```html
a<href='#id'>直接跳转id的标签位置</href>
```

## hmtl注释标签

```html
<!-- 这是注释标签 -->
```

## 特殊标签

```html
小于号 &lt;
大于号 &gt;
空格 &nbsp;
和号& &amp;
```

## 表格标签

```html
表格属性 align 规定表格对其方式 center left right
border属性
cellpadding 设置文字与单元格之间的空白 现在被废弃 在css设置
cellspacing 设置单元格之间的距离 一般设为0 边框就变成一条线了
width属性 设置宽度
<table>
    <thead> <tr><th>目标</th></tr></thead>
    <tbody>
     <tr><td>学习html</td></tr>
    
    </tbody>
   
</table>
```

### 表头标签

>用于第一行 突出重要性
>
>th标签 代替td！！  
>
>里面的文字会居中加粗显示

### 表格区域标签

>让表格有更好的语义化

```html
thead标签 包裹表头 
tbody标签 包裹表body
```

### 合并单元格

```html
跨行合并 rowspan = '合并单元格数目'
跨列合并 colspan = '合并单元格数目'

写在目标单元格
跨行 以最上面的单元格为目标格
跨列 以最左边的单元格为目标格

最后删掉多余的单元格
```

## 列表标签

>用来布局的

### 无序列表

>无序列表各个列表项之间没有顺序级别之分 
>
>ul标签里 只能 嵌套li标签 而且里面也不能写文字
>
>li标签里可以放任何标签
>
>无序列表会带自己的属性样式 在实际使用当中自己设置css

```html
<ul>
    <li></li>
    <li></li>
</ul>
```

### 有序列表

>ol标签里 只能 嵌套li标签 而且里面也不能写文字
>
>ol标签里可以放任何标签
>
>有序列表会带自己的属性样式 在实际使用当中自己设置css

```html
<ol>
    <li></li>
    <li></li>
</ol>
```

### 自定义列表

>dl 只能包含dt 和 dd
>
>dt 和 dd没有个数限制 一般是dt 对应多个dd 
>
>但是dt 和 dd 是兄弟关系

```html
<dl>
    <dt>关注我们</dt>
    <dd>新浪微博</dd>
    <dd>官方微信</dd>
    <dd>联系我们</dd>
</dl>
```

## 表单标签

>用于收集用户信息

### 表单域

```html
<from method='post' action='/demo' name='name1'></from>
```

### input表单标签

>name 是表单元素的名字 一般用于后台拿数据
>
>value 是表单元素的值 也用于后台拿数据 也方便先预显示数据
>
>单选框和复选框必须写name才能确定为一组

```html
<input> 单标签
checked属性
在单选框或多选框添加 checked='checked' 则会预选

maxlength属性 maxlength='6'用户最大输入的数量为6

name属性
是表单元素的名字 一般用于后台拿数据

value 是表单元素的值
也用于后台拿数据 也方便先预显示数据
```

#### 账号以及密码框

```html
<input type='text'>
<input type='password'>
```

#### 单选框

```html
男<input type='radio'> 
女 <input type='radio'> 
```

#### 多选框

```html
吃饭<input type='checkbox'>
睡觉<input type='checkbox'> 
打豆豆<input type='checkbox'> 
```

#### 提交按钮

```html
<input type='submit' value='这里设按钮显示的字'>
```

#### 重置按钮

```html
<input type='reset' value='重复填写'>
```

#### 普通按钮 button

>后期搭配js使用

```html
<input tpye='button' value='获取短信验证码'>
```

#### 文件域按钮

>用于上传文件

```html
<input type='file'>
```

#### label标签

```html
点标签旁边的文字也可以定位到这个表单元素
<label for='usernaeme'>用户名：</label>
<input type='text' id='username'>
```

### select表单元素

>select标签 至少包一对option标签
>
>在option标签 用selected=’selected‘可以预选

```html
<select>
    <option selected='selected'>选项1</option>
    <option>选项2</option>
</select>
```

### textarea文本域标签

>常见于留言板 评论

```html
<textarea cols='50' rows='5'>
cols='一行可以显示多少个字'
    row是显示几行
    实际开发当中用css控制
</textarea>
```

# css

```css
分三种书写风格
紧凑格式
h1{color: deeppink;font-size:20px;}
展开格式
h3 {
    color: pink;
    font-size: 12px;
}
选择器和大括号中间保留空格 属性值冒号后面 保留空格
```

## 选择器

### 基础选择器

#### 标签选择器

```css
p {
    color: green;
}
div {
    color : pink;
}
```

#### 类选择器

```css
.red {
  color: red;
}
类命名规则 
头 header
内容 container
尾  footer
导航 nav
侧栏 sidebar
栏目 column
页面外围控制整体布局宽度 wrapper
左右中 left right center
登陆条 loginbar
标志 logi
广告 banner
页面主体 main
热点 hot
新闻 news
下载 download
子导航 subnav
菜单 menu
子菜单 submenu
```

#### id选择题

```css
#pink {
    color: pink;
}
```

#### 通配符选择器

```css
* {
    color: red'
}
```

### 复合选择器

#### 后代选择器

```css
fu元素 zi元素 {
    color: red;
}
父元素和子元素中间用空格隔开
而且父元素所有子代字体都会变红
```

#### 子选择器

>亲儿子选择器

```css
fu>zi {
    color: yellow;
}
```

#### 并集选择器

```css
div,
p {
    color: pink;
}
div,
p,
.pig li{
    color:red;
}
```

#### 伪类选择器

##### 链接伪类选择器

```css
a:link 未被访问的连接
a:visited 已被访问的连接
a:hover 鼠标指针位于其上的连接
a:active 选择活动连接(鼠标按下未弹起的连接)

lvha 按这个
```



## 字体

### 设置字体系列

```css
body {
    font-family: 'Microsoft Yahei';
}
如果有空格的多个单词组成的字体加引号
字体间用英语逗号隔开
```

### 设置字体字号

```css
body {
    font-size: 16px;
}
```

### 设置字体粗细

```css
.bold {
    font-weight: 700;等价于bold
}
```

### 设置文字样式

```css
p {
    font-style: italic;
}
p {
    font-style: normal;
}
```

### 字体复合属性

```css
body {
    font: font-style font-weight font-size/line=height font-family;
}
复合属性其他可以省略 必须保留font-size 和font-weiht
h1 {
   font: 20px '黑体';
}
```

## 文本

### color

```css
div {
    color: #cc00ff;
    color: rgb(255,0,0);
    color:rgb(100%,0,0)
}
```

### 文本对齐

```css
div {
    text-align: center;
}
```

### 装饰文本

```css
div {
    text-decoration: underline;
    text-decoration: line-through;
    text-decoration: overline;
}
```

### 文本缩进

```css
p {
    em是相对当前元素一个字体大小
    text-indent: 2em;
}
```

### 行间距

>行间距是文字高度+文字上下的那段距离

```css
p {
    line-height: 26px;
}
```

	## 样式表引入

>行内样式

```html
<div style='font-size: 12px;font-weight: 700;'></div>
```

>内部样式

```html
<style>
    *{
        margin: 0;
        padding: 0;
    }
</style>
```

>外部样式

```html
<link rel='stylesheet' href='style.css'>
```

