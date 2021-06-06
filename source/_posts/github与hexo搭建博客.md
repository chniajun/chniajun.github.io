---
title: github与hexo搭建博客
top: false
cover: false
toc: true
mathjax: true
date: 2021-05-30 21:10:55
password:
summary:
tags: hexo
categories: 教程
---
**本文内容源自网络和个人修改**
# 1、git
## 1、安装git
&emsp;由于git官网下载速度很慢，可以选择通过淘宝的镜像下载<https://npm.taobao.org/mirrors/git-for-windows/>，最新版在网页的最下面，，，
基本上全部默认安装
输入`git --version`,出现版本号则安装成功

## 2、github
&emsp;登录注册自己的github，创建仓库repository，仓库名称必须为用户名加上.github.io;格式：`xxxxx.github.io`。
这个时候就可以进行git的本地配置用于表明是谁提交的

```c++
git config --global user.name "zsj"
git config --global user.email "2570314352@qq.com"
```
使用`git config -l`可以查看全部配置信息
提交代码时，有两种方式，一种是http每次都输入账号密码，另一种是使用ssh提交不需要输入账号密码；推荐使用ssh。

# 2、安装node.js
&emsp;[Node.js下载](https://nodejs.org/en/download/),下载msi文件后双击运行，输入`node -v`出现版本号则nodejs安装成功，输入`npm -v`出现版本号则表明npm安装成功。
# 3、新建blog
&emsp;创建一个文件夹用于存放博客文件。如`D:\Blog`然后可以右键`git bash here`打开终端。
使用npm命令安装Hexo

```
npm install -g hexo-cli 
```
如果出现`npm ERR! code ENOTFOUND npm ERR! `,是因为国内无法访问外网，使用国内npm官方镜像
```
npm config set registry http://registry.cnpmjs.org/
```
重新安装后输入`hexo -v`出现版本号则安装hexo成功。
初始化博客输入：
```
hexo init
```
安装必备的组件，输入:
```
npm install
```
生成网页，输入
```
hexo g
```
本地服务器预览，输入
```
hexo s
```
打开浏览器输入
```
localhost:4000
```
则会显示hexo的默认博客文章
# 4、博客的配置
## 4.1 博客的基本配置
根目录里的_config.yml文件称为**站点**配置文件
themes文件里的_config.yml文件称为**主题**配置文件

为了部署在github上，用于网页访问，将站点配置文件的deploy修改
```
deploy:
  type: git
  repository: https://github.com/xxxx/xxxx.github.io.git
  branch: main
```
其中，xxxx为自己的github名称
部署到github，输入
```
hexo d
```
此时打开浏览器输入`xxxx.github.io`,即可看到hexo的博客文章

修改一些基本信息 ：
1. 修改#Site的信息，包含网站的名字等
2. 修改#URL
3. 修改#Directory
4. 修改theme: matery
以下为我自己的站点配置文件：

```
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: 张仕君的博客
subtitle: 技术与思考
description: 与世界联系并输出自己的价值
keywords: “技术 思考”
author: 张仕君
language: zh-CN
timezone: ''

# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: https://www.chniajun.com
permalink: :year/:month/:day/:title/
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link:
  enable: true # Open external links in new tab
  field: site # Apply to the whole site
  exclude: ''
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true

highlight:
  enable: false
  line_number: false
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:
  enable: false
  preprocess: true
  line_number: true
  tab_replace: ''

# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Metadata elements
## https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
meta_generator: true

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss
## updated_option supports 'mtime', 'date', 'empty'
updated_option: 'mtime'

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Include / Exclude file(s)
## include:/exclude: options only apply to the 'source/' folder
include:
exclude:
ignore:

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: matery

# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git
  repository: https://github.com/chniajun/chniajun.github.io.git
  branch: main
live2d:
  enable: false
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  log: false
  model:
    use: live2d-widget-model-shizuku
  display:
    position: left
    width: 200
    height: 400
  mobile:
    show: false
  react:
    opacity: 0.7

prism_plugin:
  mode: 'preprocess'    # realtime/preprocess
  theme: 'tomorrow'
  line_number: true    # default false
  custom_css:
```

为了以后新建文章时方便，可以修改scaffolds框架文件下的post.md文件
```
title: {{ title }}
date: {{ date }}
top: false
cover: false
password:
toc: true
mathjax: true
summary:
tags:
categories:
```
现在点击网页头部的目录是不会正常显示的，需要在source下新建文件夹about, categoris, contact, tags，并在每个文件夹下新建文件index.md
内容依次为：
about下的index.md：

```
---
title: about
date: 2021-05-23 16:06:56
type: "about"
layout: "about"
---
```
categories下:
```
---
title: categories
date: 2021-05-23 16:04:55
type: "categories"
layout: "categories"
---
```
contact下:
```
---
title: contact
date: 2021-05-23 16:44:47
type: "contact"
layout: "contact"
---

# 欢迎留言
大家有任何问题，都可以在评论区给我留言。

我很忙啦，如果不是很麻烦的问题就直接在评论区留言啦。
```
tags下:
```
---
title: tags
date: 2021-05-23 16:06:20
type: "tags"
layout: "tags"
---
```


## 4.2 博客的主题配置
**添加建站时间**
修改/themes/matery/layout/_partial/footer.ejs文件，在最后加上
```
<script language=javascript>
    function siteTime() {
        window.setTimeout("siteTime()", 1000);
        var seconds = 1000;
        var minutes = seconds * 60;
        var hours = minutes * 60;
        var days = hours * 24;
        var years = days * 365;
        var today = new Date();
        var todayYear = today.getFullYear();
        var todayMonth = today.getMonth() + 1;
        var todayDate = today.getDate();
        var todayHour = today.getHours();
        var todayMinute = today.getMinutes();
        var todaySecond = today.getSeconds();

        var t1 = Date.UTC(2021, 05, 22, 12, 00, 00); 
        var t2 = Date.UTC(todayYear, todayMonth, todayDate, todayHour, todayMinute, todaySecond);
        var diff = t2 - t1;
        var diffYears = Math.floor(diff / years);
        var diffDays = Math.floor((diff / days) - diffYears * 365);
        var diffHours = Math.floor((diff - (diffYears * 365 + diffDays) * days) / hours);
        var diffMinutes = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours) / minutes);
        var diffSeconds = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours - diffMinutes * minutes) / seconds);
        document.getElementById("sitetime").innerHTML = "本站已运行 " +diffYears+" 年 "+diffDays + " 天 " + diffHours + " 小时 " + diffMinutes + " 分钟 " + diffSeconds + " 秒";
    }
    siteTime();
</script>
```
然后在footer.ejs的开头Copyright下添加：
`<span id="sitetime"></span>`
**添加卜蒜子**
在footer.ejs末尾添加
```
<script>
    $(document).ready(function () {

        var int = setInterval(fixCount, 50);  // 50ms周期检测函数
        var pvcountOffset = 80000;  // 初始化首次数据
        var uvcountOffset = 20000;

        function fixCount() {
            if (document.getElementById("busuanzi_container_site_pv").style.display != "none") {
                $("#busuanzi_value_site_pv").html(parseInt($("#busuanzi_value_site_pv").html()) + pvcountOffset);
                clearInterval(int);
            }
            if ($("#busuanzi_container_site_pv").css("display") != "none") {
                $("#busuanzi_value_site_uv").html(parseInt($("#busuanzi_value_site_uv").html()) + uvcountOffset); // 加上初始数据 
                clearInterval(int); // 停止检测
            }
        }
    });
</script>
```
然后将footer.ejs开始处附近修改
```
<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalTraffic) { %> <span id="busuanzi_container_site_pv"
        style='display:none'> <i class="fa fa-heart-o"></i> 本站总访问量 <span id="busuanzi_value_site_pv"
            class="white-color"></span> </span>
    <% } %>
<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalNumberOfvisitors) { %> <span
                id="busuanzi_container_site_uv" style='display:none'> 人次,&nbsp;访客数 <span id="busuanzi_value_site_uv"
                    class="white-color"></span> 人. </span>
    <% } %>
```
**取消蒙版特效**
在主题文件的 theme/matery /source/css/matery.css 文件中，搜索 .bg-cover:after 注释它
```
/*.bg-cover:after {
    -webkit-animation: rainbow 60s infinite;
    animation: rainbow 60s infinite;
}*/
```

# 5、域名绑定
先去阿里云买一个域名，实名认证后解析域名

添加两个解析，如图

www：指向一个域名，eg www.baidu.com
A :指向一个地址

**添加百度和google统计**
[百度](https://ziyuan.baidu.com/site/index#/)

打开themes/matery/layout/_partial/head.ejs
```
<meta name="baidu-site-verification" content="xxxxxxxxxx" />
<meta name="google-site-verification" content="xxxxxxxxxxx" />
```
# 6、一般使用
清空缓存
```
hexo clean
```
新建文章
```
hexo new "My New Post"
```
生成网页
```
hexo g
```
本地预览
```
hexo s
```
部署到github
```
hexo d
```
**可以新建hexo分支保存文档**



