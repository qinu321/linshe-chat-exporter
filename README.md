# 邻舍 · 聊天记录导出器

[English](./README_EN.md)

配合[邻舍](https://github.com/icecranberry/galgame-with-comfyUI)使用的聊天记录导出器，能把私聊/群聊的聊天记录导出成Obsidian用的md格式。

能自动将文本转化为[Chatbox](https://github.com/qinu321/Chatbox-for-Obsidian)所用的对话体代码，让聊天记录在Obsidian上也能展现出跟邻舍里一样的气泡聊天框！感受最原汁原味的邻舍风味！


## 安装方法

下载releases里的zip包，解压后：

1. 把`chatbox.css`复制粘贴到你的Obsidian的`CSS 样式代码片段` 文件夹内（可以点设置-外观-CSS 样式代码片段，点击那个文件夹按钮）

   一般就是你库的`.obsidian/snippets`

   然后在设置-外观-CSS 样式代码片段里把`chatbox`启用。

2. 把`linshe-chat-exporter.html`放在你想放的任意固定的位置，用Chrome/Edge浏览器打开它，将它收藏进书签，下次想用直接打开书签就行。


## 关于聊天记录隐私的安全性

**完全安全可靠！** 你的聊天记录不会被泄露任何隐私！

1. 此工具所有操作均在本地完成，只会在本地保存你的设置和批量导出后最后消息的ID值。
2. 仅在导出时对聊天记录的文本进行格式化处理，不会涉及具体内容。
3. 此工具为单个html文件，仅由CSS（样式）和JS（程序）组成，代码功能清晰可查。您完全可以自己查看代码确定安全性。
4. 如果懒得查看代码又担心安全性，可以将此工具（单html文件）保存到本地硬盘上，断网后用Chrome/Edge浏览器打开使用。

本工具所有操作无需联网，只连接本地的邻舍服务API而已。


## 功能介绍

先确保开启了邻舍，然后用Chrome/Edge浏览器打开`linshe-chat-exporter.html`

正常连接上邻舍的话，侧边栏会显示你的私聊角色们

点击想导出聊天记录的角色，可以手动勾选想导出的对话，也能自动批量导出全部记录。

![侧边栏显示私聊角色列表及对话勾选界面](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/sidebar-contacts-selection.jpg)

复制选中是最轻量的，它只会下载选中的图片，把文本格式化处理后复制到你的剪贴板，方便编辑

![复制选中功能：下载图片并格式化文本到剪贴板](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/copy-selected-messages.jpg)

聊天记录可以轻松按页数查看，也能**搜索过滤**，匹配内容/ID/日期/角色名

```
AND（空格）：关键词1 关键词2
OR：+关键词1  +关键词2
排除：-关键词1
```

点击`上下文`就能直接跳转到原聊天记录

![搜索过滤与上下文跳转至原聊天记录](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/search-filter-context-jump.jpg)

批量导出是按日期进行分割的，且能设置md文档的最大KB数，超出限制会自动再进行分割。

`已导出到 ID：XXXX`是记住这批导出后最后一个对话的ID，方便下次能直接导出后续更新的内容。你也可以手动修改ID来重新导出，点击ID前面的说明文本能直接自动跳转到原聊天对话，方便查看该ID的具体内容。


## 设置

### 导出文件夹

我强烈建议导出前**先去设置**看一遍

把导出的3个文件夹（md、图片、表情包）给设置好

![设置页面：配置md、图片、表情包三个导出文件夹路径](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-export-folders.jpg)

这样导出器的**查重功能**就能正常运作，增量导出时能防止重复下载。

导出大批量的聊天记录时也会更快速和稳定！

### 图片链接前缀

如果你的Obsidian使用的是图库外链

在设置里也能设置图片链接的前缀

![设置页面：图片链接前缀配置项](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-image-url-prefix.jpg)

使用本地图片的话强烈建议留空

### 导出样式

可以轻松选择7种气泡框样式，默认为邻舍本体样式

（尽量还原到9成了，还算原汁原味）

![七种气泡框样式选择预览，默认为邻舍本体样式](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-bubble-styles.jpg)

### md模板设置

支持变量替换，你可以设置出很复杂的模板

批量导出时支持上一个文件名，

比如：在模板里写上 `上一篇:: [[{{previousFileName}}]]`

就能自动将整批导出的md文档都链接起来，方便面包屑插件或是dv代码的导航。

![md模板设置：支持变量替换与上一篇文件名链接](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-md-template.jpg)

### 导出头像

考虑到头像只有第一次需要导出，所以放在设置的最后面了

![设置页面：导出头像功能选项](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-export-avatar.jpg)


## 在Obsidian里的展示效果

是用我家的[Chatbox](https://github.com/qinu321/Chatbox-for-Obsidian)CSS来展示的聊天对话体样式。

普通用户无需在意它的代码格式，导出器会自动把所有的格式转换都做好。

### 浅色样式

例图为使用默认模板自动生成的效果

![浅色样式下聊天记录在Obsidian中的展示效果](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/light-theme-preview.jpg)

### 深色样式

![深色样式下聊天记录在Obsidian中的展示效果](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/dark-theme-preview.jpg)

### 群聊名字和表情包

![群聊名称显示与表情包在Obsidian中的展示效果](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/group-chat-stickers.jpg)

### 补充斜体和粗体

带`（）`的动作描写会加上斜体，`！`或`？`的数量超过2个就会加上粗体，一点小润色

![动作描写的括号斜体润色效果示例](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/italic-formatting-example-1.jpg)

![感叹号问号超过2个时加粗的润色效果示例](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/italic-formatting-example-2.jpg)

### 更详细的说明

若您很感兴趣，欢迎去[Chatbox](https://github.com/qinu321/Chatbox-for-Obsidian)查看更详细的说明。里面还带有它的生成器，能很方便地帮助您修改对话体代码！


## 导出时注意事项

我自己测试14000+对话，1000+图片（已压缩成avif）的批量导出在2分钟左右，应该是挺快的。

注意图片的查重只有名字，即使你在邻舍重新生图，因为名字一样，重新导出时并不会替换老图片。如有必要请手动替换。

md的查重会看名字和大小，都相同会跳过，名字一样但大小不一的话，新md会加序号后导出。


---

## 致谢

十分感谢邻舍的作者冰乐大佬开发出如此有趣的AI聊天软件！

让我沉迷邻舍才会衍生出搞导出器的念头。

也十分感谢大D老师的代码开发！虽然烧了好多token，改了好多bug，但它也是真做出来了啊！

注：只有聊天记录导出器是由deepseek写的，chatbox.css及它的生成器都是我个人手搓的