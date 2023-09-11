# 重修 markdown！

!!! abstract "本部分着重于整理一些 markdown 易错易漏用法"

> 感觉是所见即所得的 markdown 编辑器用多了
> <div style="text-align: right">—— 笔者学长</div>

由于 markdown 语法简单，以及越来越多像 typora 一类的所见即所得的 markdown 编辑器大肆发展，很多人并不会注意 markdown 语法的细致规范。虽然日常使用中能用就行，但放在实验文档这种需要展示出去的场景下，就会暴露出相当多的问题。

markdown 的好处是它用法简单，坏处也是它用法简单，初代版本并没有细致规范，因此其危机四伏。所以也涌现出了很多种 markdown 规范来试图解决这个问题，最知名的便是 [CommonMark](https://commonmark.org/)，GitHub 使用的 markdown 规范也是从这个版本改编的。CommonMark 对于 markdown 的具体语法细节进行了规定，你去自己看一眼就会发现原来 markdown 也需要这么多的规范限制。

不过遗憾的是 mkdocs 默认使用 python-markdown 作为渲染器，但其并不是根据 CommonMark 编写的，不过大部分常见的细节上还是基本一致的。

## Table of Contents

- [常见错误用法集锦](syntax/)：即“must”，一定需要修改的
- [其他编写建议](suggestions/)：即“should”，建议修改，改了会更好

## 更多参考

- 笔者的[实用工具拾遗课程第三讲：Markdown 语法及应用](https://slides.tonycrane.cc/PracticalSkillsTutorial/lec3/)
- [CommonMark 规范](https://spec.commonmark.org/current/)可参考