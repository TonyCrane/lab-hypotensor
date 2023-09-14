# 其他 markdown 编写建议

除了前一篇中写的会严重影响渲染结果的必须修改的错误写法，还有一些对于渲染结果影响不大，但为了追求完美还是建议修改的写法。同时这篇中更注重于 markdown 本身的语法，关于内容的组织、合理 markdown 元素的选择会写在[更多排版建议](../typesetting/suggestions/)中，可以配合阅读。

一些简易的规则会参考于 [markdownlint](https://github.com/markdownlint/markdownlint) 的实现，虽然其有一些规则有点“激进”，但大部分笔者认为还是比较必要的，这些规则可以详见[其 repo 中的 RULES.md](https://github.com/markdownlint/markdownlint/blob/main/docs/RULES.md#md018---no-space-after-hash-on-atx-style-header)。

## 标题怎么写好看
### 格式注意

!!! note "格式注意目的是将 markdown 源文本写的更加规范"

参考于 markdownlint，其和标题（header）相关的规则有以下几个（划掉是我认为不常见/意义不大的）：

- MD001 - Header levels should only increment by one level at a time
- MD002 - First header should be a top level header
- ~~MD003 - Header style~~
- MD018 - No space after hash on atx style header
- MD019 - Multiple spaces after hash on atx style header
- ~~MD020 - No space inside hashes on closed atx style header~~
- ~~MD021 - Multiple spaces inside hashes on closed atx style header~~
- MD022 - Headers should be surrounded by blank lines
- MD023 - Headers must start at the beginning of the line
- MD024 - Multiple headers with the same content
- MD025 - Multiple top level headers in the same document
- MD026 - Trailing punctuation in header
- ~~MD041 - First line in file should be a top level header~~

??? note "关于 ATX style 和 Setext style 的补充"
    这里简单解释一下上面提到的 "atx style header" 是什么。

    实际上 markdown 有两种标题的语法：
    
    - 一种是我们熟知的井号，它叫做 ATX style
        - `# header` 就是一种 ATX style header
    - 另一种是从另一门 markup 语言 "Setext" 继承来的，就叫做 Setext style
        - 只有一级标题和二级标题
        - 在文本下一行加任意多 = 表示一级标题，加任意多 - 表示二级标题

    另外，ATX style header 在标题的后面也可以加等量的井号用来“闭合”，即类似 `# header #` `## header ##` 这样，这就是所谓的 "closed atx style header"。

    上面的 MD003 的意思便是同一个文档内最好不要混用 ATX style 和 Setext style，因为 Setext style 真的不是很常用，所以我划掉了。

那我们逐条来看：

- MD001：强调了标题层级只能一级一级增加，不能跳过某一级
- MD002 MD025：强调了一份文档必须要由一级标题开头，且只能有一个一级标题
- MD018 MD019：强调了井号和标题内容中间必须有且仅有一个空格
- MD023：标题的井号必须从行首开始（井号前不能有空格）
- MD024：同一份文档中不同标题的内容不能重复
- MD026：标题内容结尾最好不要加标点符号
- ~~MD022：标题上下必须有空行~~
    - 但是没有空行一般不会影响渲染结果，连续的标题之间没空行个人认为甚至更合适一点

所以对于源文件中标题写法的建议也就是这些，还是很明确的。

### 样式注意

!!! note "样式注意目的是让渲染结果变得更加易读"

这种文档中最需要注意的标题样式便是字号、字重、编号。其中字号从层次高到低逐次减小没什么问题，material 也是这样做的，但后两者就需要注意了。

首先是字重（即字体粗细），或许是因为注重面向英文排版的缘故，material 设置的更高层级的标题字重反而更小（粗细更细），而使用中文标题的话看起来效果就非常不佳。所以为了改到更高层级更粗的样式，需要手动加入 css 来覆盖 material 的配置（建议写一个 css 文件然后在 mkdocs.yml 中 extra_css 添加载入），效果就是本文档的样式：

```css
.md-typeset h1, .md-typeset h2 {
  font-weight: 600;
}
.md-typeset h3 {
  font-weight: 500;
}
```

其次是编号，即使有了互相区分的字号、字重，分辩层级和标题之间的关系仍然不是那么清晰，解决方法也很简单，就是在标题前面添加一个编号，例如本文。为了这个效果，很多人会选择直接在源标题中就把编号带上，但是这样在后续更新的时候都需要手动进行，不太方便，而且多人协作的话也需要提前明确写法（避免有人写阿拉伯数字有人写汉字数字的情况）。

这里我推荐一个方法就是使用 css 自带的 counter 系统记录编号，再用 h*n* 标签的 :before 的 content 来添加编号内容。当然使用这一方法的前提是要遵循前面格式建议中的 MD001 MD002 MD025 即不跨层级、有且仅有一个一级标题。设置也是添加 css 即可：

??? success "自动编号 css"
    ```css
    h1 {
      counter-reset: h2;
    }
    h2 {
      counter-reset: h3;
    }
    h3 {
      counter-reset: h4;
    }
    h4 {
      counter-reset: h5;
    }
    h5 {
      counter-reset: h6;
    }
    h2:before {
      counter-increment: h2;
      content: counter(h2);
      margin-right: 0.8rem;
    }
    h3:before {
      counter-increment: h3;
      content: counter(h2) "." counter(h3);
      margin-right: 0.8rem;
    }
    h4:before {
      counter-increment: h4;
      content: counter(h2) "." counter(h3) "." counter(h4);
      margin-right: 0.8rem;
    }
    h5:before {
      counter-increment: h5;
      content: counter(h2) "." counter(h3) "." counter(h4) "." counter(h5);
      margin-right: 0.8rem;
    }
    h6:before {
      counter-increment: h6;
      content: counter(h2) "." counter(h3) "." counter(h4) "." counter(h5) "." counter(h6);
      margin-right: 0.8rem;
    }
    ```

## 列表各种写法有什么区别

列表的样式不用太担心，只要语法正确渲染起来效果都不会太差（或许需要微调的就是各种 margin、padding 之类的，不过 material 做的不错了）。

所以关于列表的这部分主要着重于一些写法规范，以及一些特殊用法下的写法。

### 列表相关规范

首先还是先来看 markdownlint 的有关 rules：

- MD004 - Unordered list style
- MD005 - Inconsistent indentation for list items at the same level
- MD006 - Consider starting bulleted lists at the beginning of the line
- MD007 - Unordered list indentation
- MD029 - Ordered list item prefix
- MD030 - Spaces after list markers
- MD032 - Lists should be surrounded by blank lines

这几个规则其实都还挺没有意思的，MD004 要求文档中所有列表的同一层级使用同一种标记，MD005 MD006 MD007 要求同一层级缩进相同且第一级前无缩进，MD029 规范的是有序列表的前缀写法（但没大必要），MD030 规范的是列表标记后面有且仅有一个空格，MD032 要求列表前后必须有空行（这个是一定要做的，在[常见错误用法集锦](syntax/)中也有讲到过这个空行不能省）。

### 两种实际情况

有两个比较常见的问题需要说一下，就是同一列表的列表项之间是否可以加空行，以及列表项下还想继续写内容该怎么办。

先站在 parser 的角度，决定一个列表该怎么渲染的因素肯定也就只有空行和空格了。那先说一个简单的结论：列表项里出现空行就会升级为 <p\> tag（列表项写法除了带缩进外和普通段落就没有区别了）。因此列表项内想要继续写内容可以选择换行来写，或者加空行变成段落来写。

接下来看一些对比：

=== "列表项间不加空行"
    为了方便对比先看效果：

    - item a
    - item b

    markdown 源码：

    ```markdown
    - item a
    - item b
    ```
    
    HTML 结果：
    ```html
    <ul>
        <li>item a</li>
        <li>item b</li>
    </ul>
    ```
=== "列表项间加空行"
    为了方便对比先看效果：

    - item a

    - item b

    markdown 源码：

    ```markdown
    - item a

    - item b
    ```
    
    HTML 结果：
    ```html
    <ul>
        <li><p>item a</p></li>
        <li><p>item b</p></li>
    </ul>
    ```

可以看出不加空行的明显要比加了空行的更紧凑一些，因为加了空行之后列表项中包了一层 <p\>，其带有上下的 margin 导致空白加大。所以更规范的写法是这种情况下不要加空行。

<style>
#fake-python .highlight .o {
    color: var(--md-code-hl-keyword-color);
}
</style>

=== "使用换行附加内容"
    还是先看效果：

    - item a  
        content
    - item b

    markdown 源码：


    <div id="fake-python">

    ```python
    - item a  # (1)!
        content
    - item b
    ```

    1. 这里后面有两个空格

    </div>

    HTML 结果：
    ```html
    <ul>
        <li>item a<br>content</li>
        <li>item b</li>
    </ul>
    ```
=== "使用段落附加内容"
    还是先看效果：

    - item a

        content
    - item b

    markdown 源码：

    ```markdown
    - item a

        content
    - item b
    ```

    ??? note "另一种等效且某种情况下更清晰的写法"
        ```markdown
        -   item a
        
            content

        -   item b
        ```

    HTML 结果：
    ```html
    <ul>
        <li>
            <p>item a</p>
            <p>content</p>
        </li>
        <li><p>item b</p></li>
    </ul>
    ```

可以看出换行的这种同一列表项内贴的更紧密，而段落的这种由于三个都是 <p\> 所以等距分布，这里不具体推荐哪一种，根据情况看着舒服来就好。但需要注意的一点还是如果第一种情况下没有加行尾的两个空格，就会出现段落连接的情况，可能会导致列表项里出现超长一大段话，这是不合适的。

## 行内标记该如何选择

### 强调标记

有些时候可能会需要强调部分文本，所以这时候就会选择使用行内标记。markdown 提供了 \* 和 \_ 用于标记，一个标记包裹是*斜体*，两个标记包裹是**粗体**，三个标记包裹是***粗斜体***。关于这两个标记的选择并没有什么规定，尽量文档内统一即可。

markdownlint 也没有什么针对行内标记的规则，只有 MD036 标题不要使用加粗的段落文本代替以及 MD037 标记内两侧不能出现空格需要注意。

那剩下的就简单来讨论一下这种标记什么时候该用，怎么用、用哪个更好。我的建议是只有必要突出强调的地方再使用（比如突出关键词、突出要求等），不建议高频率使用，也不建议一次强调过长的内容。

同时其实斜体、粗体、粗斜体的显示效果都不怎么样，粗体字重并非很明显；斜体严格意义上来讲在中文排版中是不存在的，不推荐使用，不过它的突出效果还是有的。

那如果真为了更突出的话，我建议可以进行一些 css 样式上的调整，比如说为 strong 标签（粗体）添加突出颜色，为 em 标签（斜体）修改字体（例如楷体一类），这样就能达到更好的效果。

```css
.md-typeset strong {
  color: red;
}
.md-typeset em {
  font-family: "STKaiti";
  font-style: normal;
}
```

### 内联 HTML 标记

markdown 提供的行内标记很有限，所以有些时候使用 HTML 的行内标签也不失为一种好的选择，两个常用的：

- <del\> 标签：~~删除线~~

    这个其实是有扩展 markdown 语法的，即波浪线包裹，但是 python-markdown 的实现不太好，其要求波浪线左右没有汉字，在句子内使用 `~` 的情况显示就会如下出现问题，所以这种时候还是直接使用 <del\> 标签更方便。

    === "markdown 代码"
        ```markdown
        这段文本中插入了~~波浪号包围的~~删除线。  
        这段文本中插入了<del>标签包围的</del>删除线。
        ```
    === "渲染结果"
        这段文本中插入了~~波浪号包围的~~删除线。  
        这段文本中插入了<del>标签包围的</del>删除线。

- <u\> 标签：<u>下划线</u>

    这个的强调效果也蛮不错的，可以使用。

### 行内代码

这个为什么要单独拿出来说呢，因为笔者见过滥用行内代码块的情况。所以这里强调一下行内代码块只应该用于包裹和代码有关的文本，换句话说就是你无论如何都想让它呈现为等宽字体的文本。而不要只要出现了英文就使用行内代码块，也不要用行内代码块来强调文本内容，这样的渲染效果是很难看的。

顺带一提，markdownlint 有一条规则 MD038 规定了和强调标记一样，行内代码内左右也不要有多余空格。

## 怎么更好地插入图片

markdown 里插入图片也是一个老生常谈的问题了。其主要问题在于 markdown 提供的插入图片的语法非常有限，非常不自由。material 中的默认的情况就是左对齐，显示图片原大小，超过文本宽度了就进行缩放。但是想要进行居中对齐、图片大小的设置就没办法搞了了。

所以建议是直接通过 HTML 语法来插入图片。这里提供一个简单的模板：

```html
<div style="text-align: center;">
<img src="img.png" width="50%" style="margin: 0 auto;">
</div>
```

src 后面的就是普通的图片路径，width 后面的是宽度（这里百分数表示占文本宽度的百分比），样式是图片居中。如果对图片上下和段落的距离不满意的话可以在外层的 div style 中加入 margin-top 或 margin-bottom 来额外设置。