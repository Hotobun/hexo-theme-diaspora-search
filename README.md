#### 在线预览|[demo](https://hotococoa.com/search)

### 原理  
搜索页面先把所有文章标题都列举出来   
div标签设置隐藏 看上去就跟空标签一样  
JavaScript捕捉搜索框输入的文本   
有了用户搜索的字符串 有了文章标题列表   
只要文章标题含有搜索文本的div 全部取消隐藏  
这样 文章就显示出来了   
最后加个计数器 搜索完成  
  
*** 
### 弊端  
不适用太多数据 因为页面其实一开始就已经把所有文章列举出来的  
我写的少 不慌 目测300篇内不出大问题  
  
***   
### 输入框  
用了站长之家找的样式 稍作改动 还不错     
每按下一个按键 都能捕捉到 不需要按回车 取消了放大镜小图标    
[可扩展css3圆形搜索框](http://sc.chinaz.com/jiaoben/130222276600.htm)    

***
### 食用方法
`gitbash` 下运行的  

``` bash
$ hexo new page search      #这行只是创建文件夹和index.md  
```
 
  
编辑Hexo的`source/search/`文件夹下的`index.md` 写入`type`   
 
```
---
title: search
type: "search"  
---
```

`themes/diaspora/layout/`文件夹下创建`search.ejs`

代码整合到一个页面了 也不多 就没有做分开模块做css、js (懒)

最后主题的_config.yml文件修改 menu

```
# 头部菜单，title: link
menu:
  主页: ''
  标签: /tags 
  归档: /archives 
  搜索: /search
```