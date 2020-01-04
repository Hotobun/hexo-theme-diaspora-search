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

 


<form style=" text-align:center">  
    <style >
        input {
            outline: none;
        }
        input[type=search] {
            -webkit-appearance: textfield;
            font-family: inherit;
            font-size: 100%;
        }
        input::-webkit-search-decoration,
        input::-webkit-search-cancel-button {
            display: none;
        }
        input[type=search] {
            border: solid 1px #ccc;
            padding: 9px 9px 9px 9px;
            width: 200px;
            -webkit-border-radius: 10em;
            -moz-border-radius: 10em;
            border-radius: 10em;
            -webkit-transition: all .5s;
            -moz-transition: all .5s;
            transition: all .5s;
        }
        input[type=search]:focus {
            width: 130px;
            background-color: #fff;
            border-color: #6dcff6;
            margin-left: -11px;
            margin-right: 11;
            width: 330px;
            -webkit-box-shadow: 0 0 5px rgba(109, 207, 246, .5);
            -moz-box-shadow: 0 0 5px rgba(109, 207, 246, .5);
            box-shadow: 0 0 5px rgba(109, 207, 246, .5);
        }
        input:-moz-placeholder {
            color: #999;
        }
        input::-webkit-input-placeholder {
            color: #999;
        }
    </style>
    <script>
    function button_search_onkeypress(){
        var text = document.getElementById("search").value.toLowerCase();
        var p = document.getElementById("search_test");
        p.innerHTML = text;
    }
    </script>
    <input id = "search" name= "search" type="search" placeholder="积极开发中" 
    autocomplete="off" style="text-align:center" onfocus="this.setAttribute('placeholder', ''); " 
    onblur="if (this.value == '') this.setAttribute('placeholder', '下次一定！');" 
    onkeyup="button_search_onkeypress(),this.value=this.value.replace(/(^\s*)/g,'')">
    <input id = "search-btn" style="display: none;">
</form>

<span>检测到的文本: </span><span id = "search_test"></span>

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