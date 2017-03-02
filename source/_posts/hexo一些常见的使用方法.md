---
title: hexo一些常见的使用方法
date: 2017-03-02 10:03:06
categories:
    - 写作
tags:
    - hexo
description: 关于hexo的使用可以参考hexo的官方文档。但官方文档过于细致，对于个人来说重点不够突出，在使用时查找也不是很方便。现在将一些常用的，重要的，易忘的集中起来，方便后续使用的查找。
---

以下的内容大都引用自hexo的官方文档，只是按自己的习惯作了一些摘取和整理。

# 常用配置

## 网站
| 参数 | 描述 |
|:-----|:-----|
| title | 网站标题 |
| subtitle | 网站副标题 |
| description | 网站描述 |
| author | 名字 |
| language | 网站使用的语言 |
| timezone | 网站时区。Hexo默认使用电脑的时区。具体时区列表可以参考[时区列表](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) |

## 网址
| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| url | 网址 |   |
| root | 网站根目录 |   |
| permalink | 文章的永久链接格式 | :year/:month/:day/:title/ |
| permalink_defaults | 永久链接中各部分的默认值 | &nbsp; |
{% blockquote %}
<span style="font-size:20px;">网站存放在子目录</span>
如果网站存放在子目录中，例如 http://yoursite.com/blog，则 url 设为 http://yoursite.com/blog 并把 root 设为 /blog/。
{% endblockquote %}

## 目录
| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| source_dir | 资源文件夹，这个文件夹用来存放内容。 | source |
| public_dir | 公共文件夹，这个文件夹用于存放生成的站点文件。 | public |
| tag_dir | 标签文件夹 | tags |
| archive_dir | 归档文件夹 | archives |
| category_dir | 分类文件夹 | categories |
| code_dir | Include code 文件夹 | downloads/code |
| i18n_dir | 国际化（i18n）文件夹 | :lang |
| skip_render | 跳过指定文件的渲染，您可使用 glob 表达式来匹配路径。 | &nbsp; |

## 文章
| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| new_post_name | 新文章的文件名称 | :title.md |
| default_layout | 预设布局 | post |
| auto_spacing | 在中文和英文之间加入空格 | false |
| titlecase | 把标题转换为 title case | false |
| external_link | 在新标签中打开链接 | true |
| filename_case | 把文件名称转换为 (1) 小写或 (2) 大写 | 0 |
| render_drafts | 显示草稿 | false |
| post_asset_folder | 启动 Asset 文件夹 | false |
| relative_link | 把链接改为与根目录的相对位址 | false |
| future | 显示未来的文章 | true |
| highlight | 代码块的设置 | &nbsp; |

## 分类 & 标签
| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| default_category | 默认分类 | uncategorized |
| category_map | 分类别名 | &nbsp; |
| tag_map | 标签别名 | &nbsp; |

## 日期 / 时间格式
Hexo 使用 [Moment.js](http://momentjs.com/) 来解析和显示时间。

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| date_format | 日期格式 | YYYY-MM-DD |
| time_format | 时间格式 | HH:mm:ss |

## 分页
| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| per_page | 每页显示的文章量 (0 = 关闭分页功能) | 10 |
| pagination_dir | 分页目录 | page |

## 扩展
| 参数 | 描述 |
|:-----|:-----|
| theme | 当前主题名称。值为false时禁用主题 |
| deploy | 部署部分的设置 |

# 指令

## init
{% codeblock %}
$ hexo init [fold]
{% endcodeblock %}
新建一个网站。如果没有设置`folder`，Hexo 默认在目前的文件夹建立网站。

## new
{% codeblock %}
$ hexo new [layout] <title>
{% endcodeblock %}
新建一篇文章。如果没有设置`layout`的话，默认使用`_config.yml`中的`default_layout`参数代替。如果标题包含空格的话，请使用引号括起来。

## generate
{% codeblock %}
$ hexo generate
$ hexo g
{% endcodeblock %}
生成静态文件。
* -d, --deploy 文件生成后立即部署网站
* -w, --watch 监视文件变动

## publish
{% codeblock %}
$ hexo publish [layout] <filename>
{% endcodeblock %}
发表草稿。

## server
{% codeblock %}
$ hexo server
{% endcodeblock %}
启动服务器。默认情况下，访问网址为：{% raw %} http://localhost:4000/。 {% endraw %}
* -p, --port 重设端口
* -i, --ip 重设ip
* -s, --static 只使用静态文件
* -l, --log 启动日记记录，使用覆盖记录格式

## deploy
{% codeblock %}
$ hexo deploy
$ hexo d
{% endcodeblock %}
部署网站。
* -g, --generate 部署之前预先生成静态文件

## render
{% codeblock %}
$ hexo render <file1> [file2] ...
{% endcodeblock %}
渲染文件。
* -o, --output 设置输出路径

## migrate
{% codeblock %}
$ hexo migrate <type>
{% endcodeblock %}
从其他博客系统迁移内容。

## clean
{% codeblock %}
$ hexo clean
{% endcodeblock %}
清除缓存文件`(db.json)`和已生成的静态文件`(public)`。
在某些情况（尤其是更换主题后），如果发现对站点的更改无论如何也不生效，可能需要运行该命令。

# 写作
{% codeblock %}
$ hexo new [layout] <title>
{% endcodeblock %}
可以在命令中指定文章的布局`（layout）`，默认为`post`，可以通过修改`_config.yml`中的`default_layout`参数来指定默认布局。

## 布局（Layout）
Hexo 有三种默认布局：post、page 和 draft，它们分别对应不同的路径，而您自定义的其他布局和 post 相同，都将储存到 source/_posts 文件夹。

| 布局 | 路径 |
|:-----|:-----|
| post | source/_posts |
| page | source |
| draft | source/_drafts |
***如果不想文章被处理，可以将 Front-Matter 中的layout: 设为 false 。

## 文件名称
Hexo 默认以标题做为文件名称，但可以编辑 new_post_name 参数来改变默认的文件名称，举例来说，设为 :year-:month-:day-:title.md 可以更方便的通过日期来管理文章。

| 变量 | 描述 |
|:-----|:-----|
| :title | 标题（小写，空格将会被替换为短杠） |
| :year | 建立的年份，比如， 2015 |
| :month | 建立的月份（有前导零），比如， 04 |
| :i_month | 建立的月份（无前导零），比如， 4 |
| :day | 建立的日期（有前导零），比如， 07 |
| :i_day | 建立的日期（无前导零），比如， 7 |

## 草稿
草稿(draft)是 Hexo 的一种特殊部局。这种布局在建立时会被保存到 $source_dir/_drafts 文件夹，可以通过 `publish` 命令将草稿移动到 $source_dir/_posts 文件夹，该命令的使用方式与 `new` 十分类似，也可以在命令中指定 layout 来指定布局。
{% codeblock %}
$ hexo publish [layout] <title>
{% endcodeblock %}
草稿默认不会显示在页面中，可以在执行时加上 --draft 参数，或是把 render_drafts 参数设为 true 来预览草稿。

## 模版（Scaffold）
在新建文章时，Hexo 会根据 scaffolds 文件夹内相对应的文件来建立文件，例如：
{% codeblock %}
$ hexo new photo "My Gallery"
{% endcodeblock %}
在执行这行指令时，Hexo 会尝试在 scaffolds 文件夹中寻找 photo.md，并根据其内容建立文章，以下是可以在模版中使用的变量：
* layout 布局
* title 标题
* date 文件建立日期

## Front-Matter
Front-matter 是文件最上方以 --- 分隔的区域，用于指定个别文件的变量
以下是预先定义的参数，可在模板中使用这些参数值并加以利用。

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| layout | 布局 | &nbsp; |
| title | 标题 | &nbsp; |
| date | 建立日期 | 文件建立日期 |
| updated | 更新日期 | 文件更新日期 |
| comments | 开启文章的评论功能 | true |
| tags | 标签（不适用于分页） | &nbsp; |
| categories | 分类（不适用于分页） | &nbsp; |
| permalink | 覆盖文章网址 | &nbsp; |

# 标签插件

## 引用块
说明：在文章中插入引言，可包含作者、来源和标题。
别号：quote
语法：
```
{% blockquote [author[, source]]  [link] [source_link_title] %}
content
{% endblockquote %}
```

### 普通的 blockquote
没有提供参数
```
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
```
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}

### 引用书上的句子
```
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
```
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}

### 引用Twitter
```
{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}
```
{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}

### 引用网络上的文章
```
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}
```
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

## 代码块
说明：在文章中插入代码。
别名： code
语法：
```
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}
```

### 普通代码块
```
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
```
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}

### 指定语言
```
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}
```
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}

### 附加说明
```
{% codeblock Array.map lang:javascript %}
array.map(callback[, thisArg])
{% endcodeblock %}
```
{% codeblock Array.map lang:javascript %}
array.map(callback[, thisArg])
{% endcodeblock %}

### 附加网址和说明
```
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js lang:javascript %}
_.compact([0, 1, false, 2, '', 3]);
//=> [1, 2, 3]
{% endcodeblock %}
```
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js lang:javascript %}
_.compact([0, 1, false, 2, '', 3]);
//=> [1, 2, 3]
{% endcodeblock %}

### 反引号代码块
另一种形式的代码块，不同的是它使用三个反引号来包裹。
~~~
```[language] [title] [url] [link text]
code snippet
```
~~~

## jsFiddle
在文章中嵌入 jsFiddle。
```
{% jsfiddle shorttag [tabs] [skin] [width] [height] %}
```

## Gist
在文章中嵌入 Gist。
```
{% gist gist_id [filename] %}
```

## iframe
在文章中插入 iframe。
```
{% iframe url [width] [height] %}
```

## Image
在文章中插入指定大小的图片。
```
{% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
```

## Link
在文章中插入链接，并自动给外部链接添加 target="_blank" 属性。
```
{% link text url [external] [title] %}
```

## Include Code
插入 source 文件夹内的代码文件。
```
{% include_code [title] [lang:language] path/to/file %}
```

## Youtube
在文章中插入 Youtube 视频。
```
{% youtube video_id %}
```

## Vimeo
在文章中插入 Vimeo 视频。
```
{% vimeo video_id %}
```

## 引用文章
引用其他文章的链接。
```
{% post_path slug %}
{% post_link slug [title] %}
```

## 引用资源
引用文章的资源。
```
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}
```

## Raw
如果您想在文章中插入 Swig 标签，可以尝试使用 Raw 标签，以免发生解析异常。
```
{% raw %}
content
{% endraw %}
```

# 变量

## 全局变量

| 变量 | 描述 |
|:-----|:-----|
| site | 网站变量 |
| page | 针对该页面的内容以及 front-matter 所设定的变量。 |
| config | 网站配置 |
| theme | 主题配置。继承自网站配置。 |
| _ (单下划线) | Lodash 函数库 |
| path | 当前页面的路径（不含根路径） |
| url | 当前页面的完整网址 |
| env | 环境变量 |

##  网站变量

| 变量 | 描述 |
|:-----|:-----|
| site.posts | 所有文章 |
| site.pages | 所有分页 |
| site.categories | 所有分类 |
| site.tags | 所有标签 |

## 页面(page)

| 变量 | 描述 |
|:-----|:-----|
| page.title | 页面标题 |
| page.date | 页面建立日期（Moment.js 对象） |
| page.updated | 页面更新日期（Moment.js 对象） |
| page.comments | 留言是否开启 |
| page.layout | 布局名称 |
| page.content | 页面的完整内容 |
| page.excerpt | 页面摘要 |
| page.more | 除了页面摘要的其余内容 |
| page.source | 页面原始路径 |
| page.full_source | 页面的完整原始路径 |
| page.path | 页面网址（不含根路径）。我们通常在主题中使用 url_for(page.path)。 |
| page.permalink | 页面的完整网址 |
| page.prev | 上一个页面。如果此为第一个页面则为 null。 |
| page.next | 下一个页面。如果此为最后一个页面则为 null。 |
| page.raw | 文章的原始内容 |
| page.photos | 文章的照片（用于相簿） |
| page.link | 文章的外部链接（用于链接文章） |

## 文章 (post)
和 page 布局类似，但是添加了下列变量。

| 变量 | 描述 |
|:-----|:-----|
| page.published | 如果该文章已发布则为True |
| page.categories | 该文章的所有分类 |
| page.tags | 该文章的所有标签 |

## 首页（index）

| 变量 | 描述 |
|:-----|:-----|
| page.per_page | 每页显示的文章数量 |
| page.total | 总文章数 |
| page.current | 目前页数 |
| page.current_url | 目前分页的网址 |
| page.posts | 本页文章 |
| page.prev | 上一页的页数。如果此页是第一页的话则为 0。 |
| page.prev_link | 上一页的网址。如果此页是第一页的话则为 ''。 |
| page.next | 下一页的页数。如果此页是最后一页的话则为 0。 |
| page.next_link | 下一页的网址。如果此页是最后一页的话则为 ''。 |
| page.path | 当前页面的路径（不含根目录）。我们通常在主题中使用 url_for(page.path)。 |

## 归档 (archive)
与 index 布局相同，但新增以下变量。

| 变量 | 描述 |
|:-----|:-----|
| page.archive | 等于 true |
| page.year | 年份归档 (4位) |
| page.month | 月份归档 (没有前导零的2位数) |

## 分类 (category)
与 index 布局相同，但新增以下变量。

| 变量 | 描述 |
|:-----|:-----|
| page.category | 分类名称 |

## 标签 (tag)
与 index 布局相同，但新增以下变量。

| 变量 | 描述 |
|:-----|:-----|
| page.tag | 标签名称 |

# 辅助函数
辅助函数帮助在模版中快速插入内容。辅助函数不能在源文件中使用。

## 网址

### url_for
在路径前加上根路径，从 Hexo 2.7 开始您应该使用此函数而不是 config.root + path。
```javascript
<%- url_for(path) %>
```

### relative_url
取得与 from 相对的 to 路径。
```javascript
<%- relative_url(from, to) %>
```

### gravatar
插入 Gravatar 图片。
如果不指定 options 参数，将会应用默认参数。否则，你可以将其设置为一个数字，这个数字将会作为 Gravatar 的大小参数。最后，如果你设置它一个对象，它将会被转换为 Gravatar 的一个查询字符串参数。
```
<%- gravatar(email, [options]) %>;
```
示例：
```javascript
<%- gravatar('a@abc.com') %>
// http://www.gravatar.com/avatar/b9b00e66c6b8a70f88c73cb6bdb06787
<%- gravatar('a@abc.com', 40) %>
// http://www.gravatar.com/avatar/b9b00e66c6b8a70f88c73cb6bdb06787?s=40
<%- gravatar('a@abc.com' {s: 40, d: 'http://example.com/image.png'}) %>
// http://www.gravatar.com/avatar/b9b00e66c6b8a70f88c73cb6bdb06787?s=40&d=http%3A%2F%2Fexample.com%2Fimage.png
```

## HTML 标签

### css
载入 CSS 文件。path 可以是数组或字符串，如果 path 开头不是 / 或任何协议，则会自动加上根路径；如果后面没有加上 .css 扩展名的话，也会自动加上。
```javascript
<%- css(path, ...) %>
```
示例：
```javascript
<%- css('style.css') %>
// <link rel="stylesheet" href="/style.css" type="text/css">
<%- css(['style.css', 'screen.css']) %>
// <link rel="stylesheet" href="/style.css" type="text/css">
// <link rel="stylesheet" href="/screen.css" type="text/css">
```

### js
载入 JavaScript 文件。path 可以是数组或字符串，如果 path 开头不是 / 或任何协议，则会自动加上根路径；如果后面没有加上 .js 扩展名的话，也会自动加上。
```javascript
<%- js(path, ...) %>
```
示例：
```javascript
<%- js('script.js') %>
// <script type="text/javascript" src="/script.js"></script>
<%- js(['script.js', 'gallery.js']) %>
// <script type="text/javascript" src="/script.js"></script>
// <script type="text/javascript" src="/gallery.js"></script>
```

### link_to
插入链接。
```javascript
<%- link_to(path, [text], [options]) %>
```
| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| external | 在新视窗打开链接 | false |
| class | Class 名称 | &nbsp; |
| id | ID | &nbsp; |

示例：
```javascript
<%- link_to('http://www.google.com') %>
// <a href="http://www.google.com" title="http://www.google.com">http://www.google.com</a>
<%- link_to('http://www.google.com', 'Google') %>
// <a href="http://www.google.com" title="Google">Google</a>
<%- link_to('http://www.google.com', 'Google', {external: true}) %>
// <a href="http://www.google.com" title="Google" target="_blank" rel="external">Google</a>
```

### mail_to
插入电子邮箱链接。
```javascript
<%- mail_to(path, [text], [options]) %>
```

| 参数 | 描述 |
|:-----|:-----|
| class | Class 名称 |
| id | ID |
| subject | 邮件主题 |
| cc | 抄送（CC） |
| bcc | 密送（BCC） |
| body | 邮件内容 |

示例：
```javascript
<%- mail_to('a@abc.com') %>
// <a href="mailto:a@abc.com" title="a@abc.com">a@abc.com</a>
<%- mail_to('a@abc.com', 'Email') %>
// <a href="mailto:a@abc.com" title="Email">Email</a>
```

### image_tag
插入图片。
```javascript
<%- image_tag(path, [options]) %>
```

| 参数 | 描述 |
|:-----|:-----|
| alt | 图片的替代文字 |
| class | Class 名称 |
| id | ID |
| width | 图片宽度 |
| height | 图片高度 |

### favicon_tag
插入 favicon。
```javascript
<%- favicon_tag(path) %>
```

### feed_tag
插入 feed 链接。
```javascript
<%- feed_tag(path, [options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| title | Feed 标题 |  |
| type | Feed 类型 | atom |

## 条件函数

### is_current
检查 path 是否符合目前页面的网址。开启 strict 选项启用严格比对。
```javascript
<%- is_current(path, [strict]) %>
```

### is_home
检查目前是否为首页。
```javascript
<%- is_home() %>
```

### is_post
检查目前是否为文章。
```javascript
<%- is_post() %>
```

### is_archive
检查目前是否为存档页面。
```javascript
<%- is_archive() %>
```

### is_year
检查目前是否为年度归档页面。
```javascript
<%- is_year() %>
```

### is_month
检查目前是否为月度归档页面。
```javascript
<%- is_month() %>
```

### is_category
检查目前是否为分类归档页面。
如果给定一个字符串作为参数，将会检查目前是否为指定分类。
```javascript
<%- is_category() %>
<%- is_category('hobby') %>
```

### is_tag
检查目前是否为标签归档页面。
如果给定一个字符串作为参数，将会检查目前是否为指定标签。
```javascript
<%- is_tag() %>
<%- is_tag('hobby') %>
```

## 字符串处理

### trim
清除字符串开头和结尾的空格。
```javascript
<%- trim(string) %>
```

### strip_html
清除字符串中的 HTML 标签。
```javascript
<%- strip_html(string) %>
```
示例：
```javascript
<%- strip_html('It's not <b>important</b> anymore!') %>
// It's not important anymore!
```

### titlecase
把字符串转换为正确的 Title case。
```javascript
<%- titlecase(string) %>
```
示例：
```javascript
<%- titlecase('this is an apple') %>
# This is an Apple
```

### markdown
使用 Markdown 解析字符串。
```javascript
<%- markdown(str) %>
```
示例：
```javascript
<%- markdown('make me **strong**') %>
// make me <strong>strong</strong>
```

### render
解析字符串。
```javascript
<%- render(str, engine, [options]) %>
```

### word_wrap
使每行的字符串长度不超过 length。length 预设为 80。
```javascript
<%- word_wrap(str, [length]) %>
```
示例：
```javascript
<%- word_wrap('Once upon a time', 8) %>
// Once upon\n a time
```

### truncate
移除超过 length 长度的字符串。
```javascript
<%- truncate(text, length) %>
```
示例：
```javascript
<%- truncate('Once upon a time in a world far far away', {length: 17}) %>
// Once upon a ti...
<%- truncate('Once upon a time in a world far far away', {length: 17, separator: ' '}) %>
// Once upon a...
<%- truncate('And they found that many people were sleeping better.', {length: 25, omission: '... (continued)'}) %>
// And they f... (continued)
```

## 模板

### partial
载入其他模板文件，可在 locals 设定区域变量。
```javascript
<%- partial(layout, [locals], [options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| cache | 缓存（使用 Fragment cache） | false |
| only | 限制局部变量。在模板中只能使用 locals 中设定的变量。 | false |

### fragment_cache
局部缓存。它储存局部内容，下次使用时就能直接使用缓存。
```javascript
<%- fragment_cache(id, fn);
```
示例：
```javascript
<%- fragment_cache('header', function(){
  return '<header></header>';
}) %>
```

## 日期与时间

### date
插入格式化的日期。date 可以是 UNIX 时间、ISO 字符串、Date 对象或 Moment.js 对象。format 默认为 date_format 配置信息。
```javascript
<%- date(date, [format]) %>
```
示例：
```javascript
<%- date(Date.now()) %>
// 2013-01-01
<%- date(Date.now(), 'YYYY/M/D') %>
// Jan 1 2013
```

### date_xml
插入 XML 格式的日期。date 可以是 UNIX 时间、ISO 字符串、Date 对象或 Moment.js 对象。
```javascript
<%- date_xml(date) %>
```
示例：
```javascript
<%- date_xml(Date.now()) %>
// 2013-01-01T00:00:00.000Z
```

### time
插入格式化的时间。date 可以是 UNIX 时间、ISO 字符串、Date 对象或 Moment.js 对象。format 默认为 time_format 配置信息。
```javascript
<%- time(date, [format]) %>
```
示例：
```javascript
<%- time(Date.now()) %>
// 13:05:12
<%- time(Date.now(), 'h:mm:ss a') %>
// 1:05:12 pm
```

### full_date
插入格式化的日期和时间。date 可以是 UNIX 时间、ISO 字符串、Date 对象或 Moment.js 对象。format 默认为 date_format + time_format。
```javascript
<%- full_date(date, [format]) %>
```
示例：
```javascript
<%- full_date(new Date()) %>
// Jan 1, 2013 0:00:00
<%- full_date(new Date(), 'dddd, MMMM Do YYYY, h:mm:ss a') %>
// Tuesday, January 1st 2013, 12:00:00 am
```

### moment
[Moment.js](http://momentjs.com/) 函数库。

## 列表

### list_categories
插入分类列表。
```javascript
<%- list_categories([options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| orderby | 分类排列方式 | name |
| order | 分类排列顺序。1, asc 升序；-1, desc 降序。 | 1 |
| show_count | 显示每个分类的文章总数 | true |
| style | 分类列表的显示方式。使用 list 以无序列表（unordered list）方式显示。 | list |
| separator | 分类间的分隔符号。只有在 style 不是 list 时有用。 | , |
| depth | 要显示的分类层级。0 显示所有层级的分类；-1 和 0 很类似，但是显示不分层级；1 只显示第一层的分类。 | 0 |
| class | 分类列表的 class 名称。 | category |
| transform | 改变分类名称显示方法的函数 | &nbsp; |

### list_tags
插入标签列表。
```javascript
<%- list_tags([options]) %>
```

| 选项 | 描述 | 预设值 |
|:-----|:-----|:-------|
| orderby | 标签排列方式 | name |
| order | 标签排列顺序。1, asc 升序；-1, desc 降序。 | 1 |
| show_count | 显示每个标签的文章总数 | true |
| style | 标签列表的显示方式。使用 list 以无序列表（unordered list）方式显示。 | list |
| separator | 标签间的分隔符号。只有在 style 不是 list 时有用。 | , |
| class | 标签列表的 class 名称。 | tag |
| transform | 改变标签名称显示方法的函数 | &nbsp; |
| amount | 要显示的标签数量（0 = 无限制） | 0 |

### list_archives
插入归档列表。
```javascript
<%- list_archives([options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| type | 类型。此设定可为 yearly 或 monthly。 | monthly |
| order | 排列顺序。1, asc 升序；-1, desc 降序。 | 1 |
| show_count | 显示每个归档的文章总数 | true |
| format | 日期格式 | MMMM YYYY |
| style | 归档列表的显示方式。使用 list 以无序列表（unordered list）方式显示。 | list |
| separator | 归档间的分隔符号。只有在 style 不是 list 时有用。 | , |
| class | 归档列表的 class 名称。 | archive |
| transform | 改变归档名称显示方法的函数 | &nbsp; |

### list_posts
插入文章列表。
```javascript
<%- list_posts([options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| orderby | 文章排列方式 | date |
| order | 文章排列顺序。1, asc 升序；-1, desc 降序。 | -1 |
| style | 文章列表的显示方式。使用 list 以无序列表（unordered list）方式显示。 | list |
| separator | 文章间的分隔符号。只有在 style 不是 list 时有用。 | , |
| class | 文章列表的 class 名称。 | post |
| amount | 要显示的文章数量（0 = 无限制） | 6 |
| transform | 改变文章名称显示方法的函数 | &nbsp; |

### tagcloud
插入标签云。
```javascript
<%- tagcloud([tags], [options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| min_font | 最小字体尺寸 | 10 |
| max_font | 最大字体尺寸 | 20 |
| unit | 字体尺寸的单位 | px |
| amount | 标签总量 | 40 |
| orderby | 标签排列方式 | name |
| order | 标签排列顺序。1, sac 升序；-1, desc 降序 | 1 |
| color | 使用颜色 | false |
| start_color | 开始的颜色。您可使用十六进位值（#b700ff），rgba（rgba(183, 0, 255, 1)），hsla（hsla(283, 100%, 50%, 1)）或 颜色关键字。此变量仅在 color 参数开启时才有用。 | &nbsp; |
| end_color | 结束的颜色。您可使用十六进位值（#b700ff），rgba（rgba(183, 0, 255, 1)），hsla（hsla(283, 100%, 50%, 1)）或 颜色关键字。此变量仅在 color 参数开启时才有用。 | &nbsp; |


## 其他

### paginator
插入分页链接。
```javascript
<%- paginator(options) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| base | 基础网址 | / |
| format | 网址格式 | page/%d/ |
| total | 分页总数 | 1 |
| current | 目前页数 | 0 |
| prev_text | 上一页链接的文字。仅在 prev_next 设定开启时才有用。 | Prev |
| next_text | 下一页链接的文字。仅在 prev_next 设定开启时才有用。 | Next |
| space | 空白文字 | … |
| prev_next | 显示上一页和下一页的链接 | true |
| end_size | 显示于两侧的页数 | 1 |
| mid_size | 显示于中间的页数 | 2 |
| show_all | 显示所有页数。如果开启此参数的话，end_size 和 mid_size 就没用了。 | false |

### search_form
插入 Google 搜索框。
```javascript
<%- search_form(options) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| class | 表单的 class name | search-form |
| text | 搜索提示文字 | Search |
| button | 显示搜索按钮。此参数可为布尔值（boolean）或字符串，当设定是字符串的时候，即为搜索按钮的文字。 | false |

### number_format
格式化数字。
```javascript
<%- number_format(number, [options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| precision | 数字精度。此选项可为 false 或非负整数。 | false |
| delimiter | 千位数分隔符号 | , |
| separator | 整数和小数之间的分隔符号 | . |
示例：
```javascript
<%- number_format(12345.67, {precision: 1}) %>
// 12,345.68
<%- number_format(12345.67, {precision: 4}) %>
// 12,345.6700
<%- number_format(12345.67, {precision: 0}) %>
// 12,345
<%- number_format(12345.67, {delimiter: ''}) %>
// 12345.67
<%- number_format(12345.67, {separator: '/'}) %>
// 12,345/67
```

### open_graph
插入 open graph 资源。
```javascript
<%- open_graph([options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| title | 页面标题 (og:title) | page.title |
| type | 页面类型 (og:type) | blog |
| url | 页面网址 (og:url) | url |
| image | 页面图片 (og:image) | 内容中的图片 |
| site_name | 网站名称 (og:site_name) | config.title |
| description | 页面描述 (og:desription) | 内容摘要或前 200 字 |
| twitter_card | Twitter 卡片类型 (twitter:card) | summary |
| twitter_id | Twitter ID (twitter:creator) |  |
| twitter_site | Twitter 网站 (twitter:site) |  |
| google_plus | Google+ 个人资料链接 |  |
| fb_admins | Facebook 管理者 ID |  |
| fb_app_id | Facebook 应用程序 ID | &nbsp; |

### toc
解析内容中的标题标签 (h1~h6) 并插入目录。
```javascript
<%- toc(str, [options]) %>
```

| 参数 | 描述 | 默认值 |
|:-----|:-----|:-------|
| class | Class 名称 | toc |
| list_number | 显示编号 | true |

示例：
```javascript
<%- toc(page.content) %>
```

# 参考
* [Hexo官方文档](https://hexo.io/zh-cn/docs/)
