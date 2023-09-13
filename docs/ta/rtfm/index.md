# 去读各个文档！

!!! abstract "本部分着重于整理一些关于网站本身设置的建议"

> RTFM, Read The Fucking Manual.

一般来讲实验指导手册网站都会采用比较简约的设置，即 mkdocs 配合 material 主题。在这个过程中涉及到四份文档，都建议来读一读。

[mkdocs 的文档](https://www.mkdocs.org/)介绍了一些 mkdocs 框架基础的用法和基本设置，相信使用 mkdocs 的人都基本了解这个文档里的内容。

[material](https://github.com/squidfunk/mkdocs-material) 是一个 mkdocs 的主题，也可以说基本是目前唯一好用/常用的主题，提供了超多高级用法。[它的文档](https://squidfunk.github.io/mkdocs-material/)本身也是用 mkdocs+material 编写的，非常美观，而且内容非常丰富全面。不过据我了解，很多人都是简单看一看 mkdocs 用法，然后配置里把主题改为 material 就结束了，这样虽然能用能看，但很多 material 的优势都没有发挥出来。

[python-markdown 文档](https://python-markdown.github.io/)，主要需要看的是[官方提供的扩展](https://python-markdown.github.io/extensions/)部分，除此之外没什么其他有意义内容。

[pymdown extensions 文档](https://facelessuser.github.io/pymdown-extensions/)，即 python-markdown 的额外扩展的文档，也就是 mkdocs.yml 设置里以 `pymdownx.` 开头的扩展。

## Table of Contents

- [mkdocs 配置拾遗](mkdocs/)
- [material 主题使用拾遗](material/)
- [markdown 扩展配置拾遗](markdown/)