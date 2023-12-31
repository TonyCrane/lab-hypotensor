# 实验文档降压宝典

> 一位助教写出了一份十分不规范的实验指导手册，这是做他实验的学生身体发生的变化。
>
> Hypo meaning low, tensor meaning blood pressure.   
> lab-hypotensor is aimed to help lower the blood pressure of the students who are doing the expriments.

## 这份文档是什么？

一句话概括：是针对计算机类实验指导网站的规范化编写指南，旨在从文档层面提升学生们做实验的体验。

## 为什么要有这份文档？

目前越来越多的课程实验部分设计交给了课程助教来完成，也有越来越多的助教选择了使用 mkdocs 搭建在线网站的方式呈现实验指导。但由于大部分助教缺乏对 markdown 规范的阅读、缺乏对于 mkdocs/material 文档的阅读、缺乏一些基础的文字排版知识，导致制作出来的实验文档虽然能用，但对于“完美主义者”来讲体验极其糟糕。

在我参与助教或者我朋友参与助教的课程中，我都尽可能将实验文档整理得更加规范，但这样后期调整不仅是个极费劲的苦力活也更是对于修改者身心的摧残。所以我编写了这份文档，希望能够从根源上解决这个问题，即希望各位使用 mkdocs 编写实验文档的助教们可以在编写文档的时候就尽量做到规范、清晰、美观。

我不清楚这样一份文档的效果能有多少，但总归比没有更强，相信各位以学生为中心的助教们一定会认真阅读这份文档并用于实践，将文档编写至更好的。

同时实验也是两方面的工作，助教向学生呈现实验指导文档，学生最终还会向助教呈现完成后的实验报告。换位思考，助教们也希望同学们写出更简介明了的实验报告，所以这份文档的“学生版”中会提供一些关于实验报告的写作建议。（这部分会晚些完成）

## 关于贡献

本文档正在编写中，支持一切贡献，有任何问题可以提出 Issue 或者在页面下方评论，有内容贡献可以提出 Pull Request。

### 本地构建

```shell
$ git clone https://github.com/TonyCrane/lab-hypotensor.git
$ cd lab-hypotensor
$ pip install -r requirements.txt
$ mkdocs serve
```

## 致谢

- 感谢 [mkdocs](https://www.mkdocs.org/) 和 [material 主题](https://squidfunk.github.io/mkdocs-material/)提供了易用、美观的网站框架和主题
- 本文档有参考于[中文技术文档写作风格指南](https://github.com/yikeke/zh-style-guide/)，这也是一份非常推荐阅读的文档

## License

本文档采用 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) 协议进行许可，转载请注明出处。