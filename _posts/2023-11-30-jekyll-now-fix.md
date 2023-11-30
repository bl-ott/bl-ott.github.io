---
layout: post
title: jekyll-now博客的一些修复

---

<img src="../images/124388790_0_final.png" alt="124388790_0_final" style="zoom:33%;" />

使用jekyll-now就是主打一个块，专注于内容，不浪费时间折腾花里胡哨的主题

搭建一个博客网站只需要不到5分钟时间，且不需要写一行代码

> 搭建过程如下：
>
> 1. 访问[jekyll-now仓库](https://github.com/barryclark/jekyll-now)
> 2. 点击fork，仓库名填写`xxx.github.io`
> 3. 打开你刚才fork到自己github的仓库，打开_posts文件夹，创建一个`.md`文件并填写内容
> 4. 等待不到一分钟的时间，github会将md文件构建成html静态文件
> 5. 访问你的博客网站`xxx.github.io`



不过这个开源项目作者已经不维护了，有一些严重影响使用的问题，需要我们自己修复一下

### 修复代码块渲染

存在的问题：1)不支持高亮 2)渲染了重复的代码块外框

修复方法：

修改`_sass/_highlights.scss`文件

- `highlight`标签前加`pre`
- `overflow`从`auto`改为`hidden`
- `code`标签新增一行`white-space:pre-wrap; `

```scss
pre.highlight { // 2023.11.30 add pre
  background-color: #efefef;
  padding: 7px 7px 7px 10px;
  border: 1px solid #ddd;
  -moz-box-shadow: 3px 3px rgba(0,0,0,0.1);
  -webkit-box-shadow: 3px 3px rgba(0,0,0,0.1);
  box-shadow: 0px 0px rgba(0,0,0,0.1);
  margin: 20px 0 20px 0;
  overflow: hidden; // 2023.11.30 change from scroll to hidden
}

code {
  font-family:'Bitstream Vera Sans Mono','Courier', monospace;
  white-space: pre;
  white-space:pre-wrap; //  2023.11.30 add
}
```



### 修复表格渲染

存在的问题：未渲染出表格，表格数据未对齐

修改`style.scss`文件，添加一下代码

```scss
// Rules for displaying TABLES
table {
  padding: 0; }
  table tr {
    border-top: 1px solid #cccccc;
    background-color: white;
    margin: 0;
    padding: 0; }
    table tr:nth-child(2n) {
      background-color: #f8f8f8; }
    table tr th {
      font-weight: bold;
      border: 1px solid #cccccc;
      text-align: left;
      margin: 0;
      padding: 6px 13px; }
    table tr td {
      border: 1px solid #cccccc;
      text-align: left;
      margin: 0;
      padding: 6px 13px; }
    table tr th :first-child, table tr td :first-child {
      margin-top: 0; }
    table tr th :last-child, table tr td :last-child {
      margin-bottom: 0; }
```

