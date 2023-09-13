# markdown 常见错误用法集锦

!!! abstract "这一部分是一些比较常犯且一定需要改的 markdown 错误用法"

在整理写这篇的时候发现，其实 markdown 会导致渲染出现“严重”错误的情况并不是很多。而且对于 python-markdown 渲染器，它的要求更是很低，比如 `#header` 这样井号和文字之间没有空格的情况也可以正常渲染为标题。所以这一页中的内容会相对较少。

## 到底要不要空行

空行可以说是影响 markdown 渲染的一个最大的问题了。对于空格、空行这种，有些人的习惯就是能省则省，大部分情况下影响不大，但对于 markdown 这种语法有依赖于空行的来说就不行了。

另一种情况来说，所见即所得的 markdown 编辑器一般都会遵从按一次<span class="heti-skip"> <kbd>Enter</kbd> </span>换行就是新起一段的使用逻辑（而带有附加按键比如<span class="heti-skip"> <kbd>Shift+Enter</kbd> </span>则是换行不新起一段），所以在转为直接编辑 markdown 源码的时候就会有人忽略空行的作用以及“新起一段”和“换行”的区别。

### 段落和换行到底什么区别

这个熟悉 HTML 的同学可能会分辨的更清楚，下面我通过两个 tab 来呈现它们之间的区别：

=== "新起一段"
    **markdown 源码：**

    ```markdown
    这是第一段

    这是第二段
    ```

    **渲染为 HTML：**

    ```html
    <p>这是第一段</p>
    <p>这是第二段</p>
    ```

    **效果：**

    这是第一段

    这是第二段
=== "换行"
    **markdown 源码：**

    ```python
    这是第一段   # (1)!
    这是第二段
    ```

    1. 注意这里第一行行尾有两个空格

    **渲染为 HTML：**

    ```html
    <p>这是第一段<br>这是第二段</p>
    ```

    **效果：**

    这是第一段  
    这是第二段
=== "连接内容"
    **markdown 源码：**

    ```python
    这是第一段# (1)!
    这是第二段
    ```

    1. 注意这里第一行行尾没有空格

    **渲染为 HTML：**

    ```html
    <p>这是第一段 这是第二段</p>
    ```

    **效果：**

    这是第一段
    这是第二段

可以看出来，在渲染出来的结果中，最直观的效果就是新起一段段落之间的间距比较大（因为这里有 p 标签带的 margin 属性），而换行则间距比较小（因为是同一个段落内的换行，间距就是行距）。

但同时需要注意的一点是如果想要使用第二种，即只换行，则**需要在行尾加上两个或以上的空格**（这个空格会转换为 `<br>`），否则就会出现源码里两行内容连接到一起的情况，即第三个 tab 中所示。

???+ note "关于多行连接"
    这里说点“题外话”，就是关于这个连接内容，到底该不该使用的问题。

    我的结论是，在中文语境内不应该使用，同一个段落在 markdown 源码内就应该是同一行内写完。
    
    原因是这个功能很明显是为西文语境设计的，关键在于连接后中间加的一个空格。不管你在前一行结尾是否有空格，这个连接后的空格都一定会存在。它的逻辑是，英文里词与词之间需要加空格，标点符号后与下一个单词之间也要加空格，所以既然要连接两个英文段落，那就肯定要在中间加 一个空格。

    我举个例子：

    === "markdown"
        ```markdown
        This is line 1 in the source code.
        And this is line 2, but this sentence is ended
        in line 3.
        ```
    === "渲染结果"
        This is line 1 in the source code.
        And this is line 2, but this sentence is ended
        in line 3.

    注意到这里源码的结尾都没有空格，但是渲染的结果中连接后都加上了空格，显示的非常完美，包括句子与句子、单词与单词。

    不过换到中文语境就不一样了，中文下的排版规范是中文之间**几乎任何情况下**都不应该出现间断，且全角标点后面也不需要额外的空格。这样来看连接后加的那个空格就是非常影响排版效果的了：

    === "markdown"
        ```markdown
        这是源码中的第一行。
        这是第二行，但是这个句子会在
        第三行结束。
        ```
    === "渲染结果"
        这是源码中的第一行。
        这是第二行，但是这个句子会在
        第三行结束。
    
    上面这个例子就可以看出来，第一行的句号后面多了一个空格，句子间间距大了；第二句中出现了一个空格，句子被打断了。在中文排版下这种情况都不应该出现。所以我的建议是不要使用这种连接功能，而是直接在源码中一行写完整个段落。

### 所以我该什么时候空行

根据上面介绍的区别来看，简单来说就是只要你希望源码里新的一行在渲染后也是自己新的一段，那就应该在源码中在它之前添加空行。

更细致一点说，这个所谓的“段落”也并非一定是文本段落。它包括标题、列表、代码块、分割线、表格、引用、HTML 块等等。换句话说，只要是不同“排版元素”之间就应该添加空行，以及多空行总没有错（多个连续空行就相当于一个空行）。

下面是一些常见错误情况的例子和修正：

=== "段落接列表"
    !!! failure "错误用法"
        ```markdown
        paragraph
        - list content
        ```

        paragraph
        - list content

        !!! note "这里是渲染器理解的就是多行连接到一段"
    !!! success "正确用法"
        ```markdown
        paragraph

        - list content
        ```

        paragraph

        - list content
=== "段落接分割线"
    !!! failure "错误用法"
        ```markdown
        paragraph
        ---
        ```

        <p style="font-size: 1.5625em; font-weight: 600">paragraph</p>

        !!! note "这里是 Setext 式二级标题的语法"
    !!! success "正确用法"
        ```markdown
        paragraph

        ---
        ```

        paragraph

        ---
=== "段落接表格"
    !!! failure "错误用法"
        ```markdown
        paragraph
        | table |
        | ----- |
        |content|
        ```

        paragraph
        | table |
        | ----- |
        |content|

        !!! note "这里是渲染器理解的就是多行连接到一段"
    !!! success "正确用法"
        ```markdown
        paragraph

        | table |
        | ----- |
        |content|
        ```

        paragraph

        | table |
        | ----- |
        |content|
=== "引用接段落"
    !!! failure "错误用法"
        ```markdown
        > quote
        paragraph
        ```

        > quote
        paragraph

        !!! note "这里是渲染器理解的就是多行连接到一段，空行才会打破引用"
    !!! success "正确用法"
        ```markdown
        > quote

        paragraph
        ```

        > quote

        paragraph

这里只列举了一些常见且只通过源码不易发现的情况。其他比如标题接段落、标题接标题、段落接引用、段落接 HTML 块等情况其实都可以正常渲染，不过更好的习惯还是在它们之间都加上空行。

## 这个路径是正确的吗

这个问题或许并不该多说，这种非常严重的渲染问题在预览的时候应该都能一眼发现。

外部连接/外部图片的问题相对少一点，只要保证可以访问就可以。比较容易出问题的是网站内的相对路径，到底该怎么写。多说一点就是 mkdocs 的路径组织方式问题。关于这个问题，读源码是最有效的，下面我简单总结一下。

非常直观地讲，基于 docs 文件夹结构以及 mkdocs.yml 中的设置，mkdocs 会有两种路径组织的选择：

- 完全按照 docs 文件夹的结构来得到渲染后静态网站的目录结构
- 按照 mkdocs.yml 中设置的 nav 网站导航层级来重排目录结构

mkdocs 选择的是前者，这样更加自然。所以更明确的说就是以 docs/ 为网站根目录，将 index.md 渲染为 index.html，将其他名称的比如 file.md 渲染为 file/index.html（这样通过 .../file .../file/ 都可以访问），剩下的非 markdown 文件直接全部拷贝到对应目录下。

所以在引用其他页面/站内素材的时候，直接根据 docs/ 目录下的相对路径来引用就可以了。需要注意的点是：

- docs/ 就是网站根目录，所以和它同级或者往上的位置都是肯定无法访问到的
- 引用页面的时候记住引用的是渲染结果而非源文件
    - 比如引用源码相对位置 ../dir/file.md 的页面，需要写 `[](../dir/file/)`

## 行内标记真的渲染了吗

这也是一个比较常见的问题，也就是源码里使用了 `****` 这种行内标记，但是渲染的结果可能仍然保留了这个标记，而不是渲染为加粗的文字。

这个问题其实出现的比较少，因为 python-markdown 的渲染基本上只会“只多不少”地判断行内标记，不会出现漏渲染的情况。也因此，出现这个问题没有经验的人会比较难排查。

目前我遇到的造成这种问题的罪魁祸首是 python-markdown extensions (pymdownx) 的 BetterEm 扩展，即有些人会在 mkdocs.yml 里面加上：

```yaml
markdown_extensions:
  - pymdownx.betterem:
      smart_enable: all
```

这会让 `*_` 这种行内标记变得更“聪明”，即在它觉得应该是行内标签的地方应用，在它觉得不是的地方原样渲染。所以其实它是让这些行内标记的使用变得更加“严格”了。

对于 betterem 的行为，[pymdownx 的文档](https://facelessuser.github.io/pymdown-extensions/extensions/betterem/)中已经写的非常清晰了。这个效果看起来很诱人，但可惜，它的例子都是英文的。如果只是没有中文例子的话那当然不是大问题，可是和前面讲到过的段落连接一样，问题出在了它是只针对英文排版的。

我们来看一下它的要求，简单地集合到一起来看：

=== "markdown"
    ```markdown
    This *will emphasize*. This _ will not _.
    In-word em*phasi*s is also not allowed.
    ```
=== "开启 betterem 的渲染结果"
    This *will emphasize*. This _ will not _.
    In-word em\*phasi\*s is also not allowed.
=== "不开启 betterem 的渲染结果"
    This *will emphasize*. This _ will not _.
    In-word em*phasi*s is also not allowed.

可以发现 betterem 的要求就是行内标记需要需要紧紧围绕包裹的内容，而且在行内标记外两侧需要有空格。在英语语境下，这是非常自然的，毕竟单词与单词之间，句子与句子之间本就应该有空格。

但是对于中文语境来说，句子中间不应该出现空格间断，所以你需要写 `这是*强调*内容`，但是 betterem 认为 `*强调*` 两侧没有空格，它觉得这是单词中间的星号，不应该认为它是行内标记，所以就不会渲染。为了让它成功渲染，betterem 要求你写 `这是 *强调* 内容`，但这就导致了强调周围有了空格，打断了句子，是错误用法。

所以说结论是，在中文语境中，mkdocs 的设置里不要启用 `pymdownx.betterem`。