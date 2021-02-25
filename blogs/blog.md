---
title: 本博客的搭建
date: 2021-01-19
sidebar: 'auto'
categories:
 - 博客搭建
tags:
 - 博客
sticky: 2
---

::: tip
希望能对你有所帮助
:::
<!-- more -->
## <font color=#008000>前言</font>
首先我是一名大四准毕业生，因为大学前几年都一直在happy虽然我是软件工程专业的学生但是我真是一点不会，马上要毕业了我就在图书馆自己学习，偶然发现了一个博客用的就是vuepress做的我当时特别喜欢  就一直想写一个博客写点自己喜欢的东西所以就有了这个博客。最开始上小破站上找视频看学会了vuepress后来又了解到了有[<font color=#008000>vuepress-theme-reco</font>](https://vuepress-theme-reco.recoluan.com/)这个主题。真是挺好的

## <font color=#008000>博客三部曲</font>

vuepress官网：[<font color=#008000>vuepress</font>](https://vuepress.vuejs.org/zh/ ) 

vuepress自定义开发主题：[<font color=#008000>vuepress-theme</font>](https://vuepress.vuejs.org/zh/theme/writing-a-theme.html) 

vuepress-theme-reco官网：[<font color=#008000>vuepress-theme-reco</font>](https://vuepress-theme-reco.recoluan.com/)
        
## <font color=#008000>音乐播放器</font>
><font color=red>这是我在别人的博客上**学习**过来的 哈哈哈！</font>

这个插件叫meting会自动在页面上生成一个播放器

先安装好依赖然后配置config.js配置如下

```
  module.exports = {
    themeConfig: {
      ...
      plugins: [
        ...
        [
          "meting",
          {
            meting: {
              server: "netease", // netease:网易云，tencent:qq音乐，xiami:虾米音乐
              type: "playlist",
              mid: "歌单或音乐id",
            },
            aplayer: {
              autoplay: true,
              mini: true,
              theme: '#282c34'
            },
            mobile: {
              cover: false,
              lrc: false
            }
          }
        ]
      ]
    }
  }

```
## <font color=#008000>看板娘插件</font>

同样先安装好依赖，然后在config.js配置文件如下

```
 module.exports = {
    themeConfig: {
      plugins: [
        [
          "@vuepress-reco/vuepress-plugin-kan-ban-niang",
          {
              theme: ["miku"],
              clean: true,
              modelStyle: {
                position: "fixed",
                right: "65px",
                bottom: "0px",
                zIndex: 99999,
                pointerEvents: 'none'
              }
          }
        ],
      ]
    }
  }

```
## <font color=#008000>鼠标点击动画</font>

1. 在public文件下创建一个js文件夹人后在里面创建一个MouseClickEffect.js文件文件内容如下
```
var a_idx = 0;

function getRandom(max, min) {
    return Math.floor(Math.random() * (max - min + 1) + min);
}
function css(el,styles) {
  for (style in styles) {
    el.style.setProperty(style, styles[style]);
  }
};

window.onload = function(){
    document.querySelector("body").onclick = (e)=>{
        var a = new Array("富强", "民主", "文明", "和谐", "自由", "平等", "公正", "法治", "爱国", "敬业", "诚信", "友善");
        var span = document.createElement("span");  
        span.innerText = '❤' + a[a_idx] + '❤';
        a_idx = (a_idx + 1) % a.length;
        var x = e.clientX,
            y = e.clientY;
        css(span,{
            "z-index": 999999,
            "top": y - 20 + "px",
            "left": x + "px",
            "position": "fixed",
            "font-weight": "bold",
            "color": `rgb(${getRandom(255,0)},${getRandom(255,0)},${getRandom(255,0)})`,
            "user-select": "none",
            "cursor": "default",
            "opacity": 1,
            "transition": "all 1s"
        });
        document.querySelector("body").appendChild(span);
        setTimeout(()=>{
          css(span,{
            "opacity": 0,
            "top": y - 100 + "px",
          })
        },0)
        setTimeout(()=>{
          span.parentNode.removeChild(span)
        },1500)
    };
};

```
2. 在config.js文件里配置  
```
// 引入鼠标点击脚本
    ["script", {
    "language": "javascript",
    "type": "text/javascript",
    "src": "/js/MouseClickEffect.js"
    }
    ],

```
## <font color=#008000>总结</font>

其实博客不是很难写，相反还很有意思，在写博客的同时会有很多知识，可以复习一下，然后你每做完一点心里还会有点小激动，只要你想你就可以不要害怕，我写了一些插件的使用还有一些细节简单的东西自己看看官方文档就ok了网址我都放在上面了，最后，山高水长，有缘再见。

------------------------
<Vssue />