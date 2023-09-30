# 标点符号的使用

2015 年 W3C 的国际化工作组发布了[中文排版需求（Requirements for Chinese Text Layout）](https://www.w3.org/International/clreq/)一文并持续完善，虽然目前仍处于 Editors's Draft 阶段，但现有的内容也足够进行排版的参考了。我也整理了一份其中常接触到的部分，放在了[我的 note](https://note.tonycrane.cc/web/typesetting/clreq/)里，也可以参考。

当然这里我不会逐条来写 CLReq 中的内容，对于一些比较熟知（比如中文排版中的一般标点符号的含义与选用）或者在实际网页排版中不需要考虑的（比如行首行尾禁则、行尾点号悬挂等）这里就不多赘述。整理了一下，发现其实网页排版中的很多问题是出在标点符号的使用上，所以本文就针对几种常见的情况进行探讨。

当然，在开始之前，我们首先需要清楚一点，就是一切的目的都是**为了视觉效果更好**，而不是一味地追求服从某些严格规范，只要是看起来舒服，那就应该是一个好的排版方式。

## 段落到底怎么安排

一般来讲，中文出版物的段落开头都会有两个字宽的段首缩排。但是在网页排版中一般不采用这种方式，也就是段落开头直接顶在行首，区分段落的方式就是在段落间增加间距，当然这个间距也是 material 为我们设置好了的样式。

所以其实要注意的就是**在段落开头不要加空格**。

## 句尾到底加不加标点

这个问题也是很多人都会遇到的。本来汉语一个句子结束加标点是很正常的事情，但在日常生活打字聊天的时候一般都不会带标点，所以有些人可能就会将这个思路顺带下来，将网页排版的句尾标点省略掉。

### 段尾的情况

!!! tip "TLDR"
    对于这个问题，我的观点还是“目的是为了观感更好”，所以无论你习惯在段尾加不加标点都没问题，但你需要保证**同一份文档中的风格统一**，也就是不要出现有的段落结尾有句号，有的没有的情况。

不过话虽如此，我还是更推荐在段尾加上标点。其中一个原因是，如果在一个段落里有两句话，那前一句话的结尾为了和下一句断开肯定要有句号，但如果段尾没有标点的话，那整个段落就只有中间部分出现了一个句号，我觉得这种效果是看起来很奇怪的。

???+ example "示例"
    === "不加标点"
        这是一句话。这是同一段的另一句话
    === "加标点"
        这是一句话。这是同一段的另一句话。

### 列表项的情况

这算是一个比较特殊的情况，因为推荐的做法是根据列表项内容来决定是否加标点：

- 如果列表项内容都是词组、短语、简短的句子，那就不加标点
- 如果列表项内容都比较长，且一项里面可能会出现多句话，那就加标点
- 如果列表项内容有长有短，那应该首先更改一些表达方式让其尽量统一

比如上面这个列表，因为每项都只有一个句子而且不太长，所以就没有加标点。除此之外需要加标点的情况也需要注意，不要每句后面都加句号，应该只有最后一项是句号，前面的其他项末尾加分号。

## 各种空格到底怎么用

空格算是一个老生常谈的问题了，主要有几种情况，我们分开来看。

### 纯英文内

这是一个比较没有争议的情况，英文单词间用一个半角空格分隔，英文标点前不加空格，后面加一个空格。

对于后面这个要求，有些人可能不太了解，但看一个效果对比就一目了然、不言而喻了：

- ⭕️ To be, or not to be, that is the question.
- ❌ To be,or not to be,that is the question.
- ❌ To be , or not to be , that is the question.
- ❌ To be ,or not to be ,that is the question.

标点要贴着前一个单词肯定是没问题的，所以后两个不行。一个英文标点后面没有空白，所以不加空格的话前后两个单词就会贴在一起，标点的功能就没有了，而且看起来也是非常难受，所以第二个也不行。所以应该只有第一种看起来顺眼吧。

### 纯中文内

!!! tip "TLDR: 纯中文内几乎不应该出现空格"

先来看标点的情况，以逗号为例，和英文逗号相区分，中文逗号是占一个字宽的，而且后面有一块空白，所以视觉效果上和英文逗号加一个空格的效果差不多，不需要也不应该额外加空格：

- To be, or not to be, that is the question.
- ⭕️ 生存，还是毁灭，这是个问题。
- ❌ 生存， 还是毁灭， 这是个问题。（多加空格，看起来空白过大）
- ❌ 生存 ，还是毁灭 ，这是个问题。（前面加空格不行）

其次是一句话内，如果出现加粗强调或者插入链接的情况，有些人会在这些内容的两侧加空格来“突出”。但实际上这种做法是不好的，因为这“打断”了整个句子的连贯性，看起来比较不舒服。行内的标记应该只改变原有一句话内某些内容的样式，而不应该在其中插入额外的空格导致句子破碎。

- ⭕️ 这句话里面包含**强调**内容
- ❌ 这句话里面包含 **强调** 内容
    - 有些时候可能为了专门特意强调某个词，这样效果可能更好一点，但**不推荐**
    - 特别是 **一句话** 里面出现 **多个** 需要 **强调** 的词的时候看着就会 **非常奇怪**
- ⭕️ 详见[官方网站](https://example.com)中的文档
- ❌ 详见 [官方网站](https://example.com) 中的文档

### 中英混排间

这个情况就稍微有点复杂了，而且也没有统一的处理标准（后续的 CSS 中可能会增加一些属性来处理这个问题），所以这里只是常用的推荐处理方式。

#### 中文字符和英文字符间

首先来看一下 CLReq 和更标准完善的日文排版需求 [JLReq](https://www.w3.org/TR/jlreq/) 中的描述：

!!! abstract "CLReq（中文排版需求）"
    原则上，汉字与西文字母、数字间使用不多于四分之一个汉字宽的字距或空白。
    
    !!! note "注：可使用西文词间空格（U+0020 SPACE [ ]，其宽度随不同字体有所变化）。"

!!! abstract "JLReq（日文排版需求）"
    Inter-character space, between hiragana, katakana or ideographic characters and Western characters or European numerals, is a quarter em space.（在平假名、片假名、汉字和西文字母、欧洲数字间的字符间距为四分之一字宽。）

    The reason a quarter em space is needed between Western characters or European numerals and hiragana, katakana or ideographic characters, is that the design concept of Latin fonts and Japanese fonts are different from each other, so it looks too tight without the spaces.（加四分宽空格的原因是，拉丁字体和日文字体的设计理念不同，如果不加空格看起来会太紧凑。）

日文的标准更严格一点，直接规定了使用四分宽空格，而中文的标准则是“不多于四分之一汉字宽”，而且说明了用西文空格也可以（因为西文比例字体的情况下西文空格宽度和四分宽差不太多）。

需要注意的一点是，Unicode 中有四分宽空格的码位 U+2005 FOUR-PER-EM SPACE [ ]，但有些字体并没有这个字形，可能会导致显示错误，所以不推荐使用这个字符除非字体固定且有这个字形。

接下来还是看一些效果对比：

=== "比例英文字体下效果"
    <div class="heti-skip">

    - 中文句子中包含English单词（不加）
    - 中文句子中包含 English 单词（加一个半角空格）
    - 中文句子中包含 English 单词（加一个 U+2005）
    - 中文句子中包含<span style="font-size: 0.25em">　</span>English<span style="font-size: 0.25em">　</span>单词（加一个 0.25em 的全角空格）
    - 中文句子中包含<span style="font-size: 0.5em"> </span>English<span style="font-size: 0.5em"> </span>单词（加一个 0.5em 的半角空格）

    </div>

    可以看出后四个的效果明显好于第一个；中间三个的差别不太大，基本都是四分宽；最后一个稍微紧凑一点，小于四分宽，但视觉效果也不错。
=== "等宽英文字体下效果"
    <div class="heti-skip" style="font-family: monospace">

    - 中文句子中包含English单词（不加）
    - 中文句子中包含 English 单词（加一个半角空格）
    - 中文句子中包含 English 单词（加一个 U+2005）
    - 中文句子中包含<span style="font-size: 0.25em">　</span>English<span style="font-size: 0.25em">　</span>单词（加一个 0.25em 的全角空格）
    - 中文句子中包含<span style="font-size: 0.5em"> </span>English<span style="font-size: 0.5em"> </span>单词（加一个 0.5em 的半角空格）

    </div>

    可以看出后三个的效果差不多，第二个半角空格的宽了点。
=== "源码"
    ```markdown
    - 中文句子中包含English单词（不加）
    - 中文句子中包含 English 单词（加一个半角空格）
    - 中文句子中包含 English 单词（加一个 U+2005）
    - 中文句子中包含<span style="font-size: 0.25em">　</span>English<span style="font-size: 0.25em">　</span>单词（加一个 0.25em 的全角空格）
    - 中文句子中包含<span style="font-size: 0.5em"> </span>English<span style="font-size: 0.5em"> </span>单词（加一个 0.5em 的半角空格）
    ```

因为等宽英文的空格大概半个字宽，所以只用一个西文空格还是有点宽了点，再考虑到 U+2005 可能有字体不支持，还是后两种为更好的选择。当然这种空格需要配合 css 调整空格的字体大小，手动替换空格又太费劲，所以可以考虑使用一些额外插件，比如载入 [heti.js](https://github.com/sivan/heti)、[pangu.js](https://github.com/vinta/pangu.js)，或使用 [mkdocs-heti-plugin](https://github.com/TonyCrane/mkdocs-heti-plugin)。

#### 有标点的情况

当然也不是所有的英文两侧都要加空格，比如以下情况：

- 英文出现在句首，前面不需要加空格
- 英文贴在全角标点上，和标点间不需要有空格
    - 逻辑就是，全角标点当作英文标点外加一个空格
        - 英文排版中英文和其后标点间不需要有空格，所以英文接全角标点也不需要有空格
        - 英文排版中标点后需要有一个空格再接英文，但全角标点内已经有空白了，所以全角标点接英文也不需要有空格
    - ⭕️ 这是一句话，This is a sentence，这是另一句话。
    - ❌ 这是一句话， This is a sentence ，这是另一句话。

???+ question "到底为什么要加空格"
    > 漢學家稱這個空白字元為「盤古之白」，因為它劈開了全形字和半形字之間的混沌。另有研究顯示，打字的時候不喜歡在中文和英文之間加空格的人，感情路都走得很辛苦，有七成的比例會在 34 歲的時候跟自己不愛的人結婚，而其餘三成的人最後只能把遺產留給自己的貓。畢竟愛情跟書寫都需要適時地留白。
    > 
    > 與大家共勉之。
    > <div style="text-align: right">——pangu.js</div>

    简单来说就是为了视觉效果更好，看起来更舒服。前面的效果还不太明显，那我们用等宽英文来进行一个极端的对比：

    <div class="heti-skip" style="font-family: monospace">

    - 中文中插入some English单词
    - 中文中插入 some English 单词
    - 中文中插入<span style="font-size: 0.5em"> </span>some English<span style="font-size: 0.5em"> </span>单词

    </div>

    也就是这种不止一个单词的情况，第一种写法整个句子的视觉效果就是内部只有一个空格，整个句子被切为了两段“中文中插入some”和“English单词”，这样的效果是非常糟糕的，视觉上英文被拆开了，而贴着的中文和英文却连到了一起。后两个就一目了然，英文更凸显出来，整个句子也更连贯。

    另一种理解方式是，即然英文单词之间都要有空格，那基本也就是再说英文每个单词左右都要有空格。所以既然如此，中文句子中的英文也不应例外，需要在英文两侧加上空格。而缩减空格至四分宽是为了让整个句子看起来更连贯而已。

    就连几乎人人都说难用的 Microsoft Word，以及人人喊打的微信都会在中西文连接部分加上一点空白，那我们也没理由不这么做吧。

## 到底用全角还是半角

“角”这个概念是从日语中来的，意思就是方块，也就是一个汉字字符的宽度。全角标点就是占一个汉字宽的标点，一般指中文标点，而半角标点一般指英文标点，即使其可能并不到半个汉字宽。

那可能遇到的一个问题就是，在经常中西文混排的情况下，到底该用全角标点还是半角标点呢？

当然答案也是，用视觉效果最好的一个，而且要统一用法。比较常见的处理方法是：

- 中文为主导的句子中，尽可能都使用全角标点
    - ⭕️ 这是一句话，This is a sentence，这是另一句话。
    - ❌ 这是一句话, This is a sentence, 这是另一句话.
    - 例外：一些学术类文章、书籍等可能会全篇统一使用半角标点
- 两侧连接都是英文的标点使用半角标点
- 两侧连接英文和中文的标点使用全角标点
    - ⭕️ To be, or not to be，这是一句名言
    - ❌ To be，or not to be，这是一句名言（英文间用了全角）
    - ❌ To be, or not to be, 这是一句名言（中英间用了全角）

对于括号：

- 如果括号内都是英文，则**可以**使用半角括号，但要注意括号两侧要加半角空格
    - ⭕️ <span class="heti-skip">中文排版需求 (CLReq) 中写道</span>
    - ⭕️ 中文排版需求（CLReq）中写道（也可以统一用全角括号）
    - ❌ <span class="heti-skip">中文排版需求(CLReq)中写道</span>
- 一旦括号内出现中文，则**需要**使用全角括号，且括号两侧不要加空格
    - ⭕️ CLReq（Requirements of Chinese Text Layout，中文排版需求）中写道
    - ❌ CLReq <span class="heti-skip">(Requirements of Chinese Text Layout，中文排版需求) </span>中写道
    - ❌ CLReq（Requirements of Chinese Text Layout，中文排版需求） 中写道（多加空格了）

## 标点调整是什么

!!! abstract "CLReq：连续标点符号的宽度调整"
    无论文本整体采用何种风格，当夹注符号与其他符号连续排列时，或者夹注符号重复出现（如开始+开始，结束+结束，或者结束+开始）时，都应该进行原则上的调整，以使文字体裁更加紧凑、易读。

    原则上的调整度应为：如果任意两个相邻标点符号占用2个字宽，应当缩减成1.5个字宽。在此原则上，允许排版风格进一步调整让两个符号只占1个字宽。

    注：夹注符号就是各种括号「『（《〈【〖〔［｛」』）》〉】〗〕］｝

这个也是一种视觉效果的优化，可以了解一下。

<style>
.show-border {
    outline: dotted 1px;
}
</style>

很多全角标点都有可以压缩的空间，比如 <span class="show-border heti-skip">。</span><span class="show-border heti-skip">，</span><span class="show-border heti-skip">、</span><span class="show-border heti-skip">：</span><span class="show-border heti-skip">；</span><span class="show-border heti-skip">！</span><span class="show-border heti-skip">（</span><span class="show-border heti-skip">「</span><span class="show-border heti-skip">【</span> 等。

根据 CLReq 的说法，有以下几种调整情况：

- 夹注符号与其他符号连续排列
    - <span class="show-border heti-skip">。</span><span class="show-border heti-skip">（</span> 比如这里共计产生了一个全宽的空白，可以压缩掉半个，变成 <span class="show-border">。</span><span class="show-border">（</span>
    - 同样 <span class="heti-skip">）。</span> 变为 ）。
- 夹注符号重复出现
    - <span class="show-border heti-skip">（</span><span class="show-border heti-skip">《</span> 可以变成 <span class="show-border heti-skip">（</span><span class="show-border heti-skip" style="margin-inline-start: -0.5em">《</span>，<span class="show-border heti-skip">）</span><span class="show-border heti-skip">（</span> 可以变成 <span class="show-border">）</span><span class="show-border">（</span>

同样这个也可以通过载入 [heti.js](https://github.com/sivan/heti) 或使用 [mkdocs-heti-plugin](https://github.com/TonyCrane/mkdocs-heti-plugin) 来自动处理，原理就是正则识别后为一方加入 margin-inline-end: -0.5em 的样式。