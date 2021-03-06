title: CTeX 2.0 发布 · 新功能简介
date: 2015-05-16 23:04:52
categories: LaTeX
tags: [CTeX]
---

CTeX 2.0 的代码主要是 李清 用 LaTeX 3 的语法书写的。之后 刘海洋 对代码做了一些调整，并构建了第一个版本的宏集手册。再之后，在测试版本发布之后，我重构了宏集手册，成为你们现在看到的这个样子。

现在，新版宏集已经上传，CTAN 地址是：<http://www.ctan.org/pkg/ctex>

<!-- more -->

首先说一下关于 CTeX 这个名字。
CTeX 的 C 是 China 或者 Chinese 的意思，在纯文本环境下，应该写作 CTeX。
CTeX 宏集是由 CTeX社区 发起并维护的 LaTeX 宏包和文档类集合。社区另有发布名为 CTeX 套装 的 TeX 发行版。
ctex 是本宏集中 `ctex.sty` 的名字。这一小写的名字过去被用来代指整个 CTeX 宏集，不过现在则专指 `ctex.sty` 这一宏包。不过，在一些特殊的情况下，由于历史原因，为了与 CTeX 套装做区分，也会用 ctex 来代指整个 CTeX 宏集。

本次更新的是 CTeX 宏集，版本号从 1.02d 升级到 2.0 （当前修复了一些问题，版本号是 2.0.2）。CTeX 套装的最新版本是 2.9.2.164，已有若干年未更新，将来可能也不会再更新，也不推荐使用。

CTeX 2.0 里比较重大的改变有四个：

* 对底层引擎的支持，放弃了 CCT，新增了 LuaLaTeX（基于 `LuaTeX-ja`）；
* 增强了字库选择，新增了华文、Fandol、方正等字库，并提供了基于操作系统自动选择字库的功能；
* 增强了 `ctex.sty` 的功能，用键值列表的方式提供选项支持，并提供全新的 \ctexset 接口；
* 关于字号的部分，在 `ctexsize.sty` 中单独列出，可独立于 CTeX 宏包或文档类使用。

除此之外，特别有意义的一点是，新版宏集可以做到「只提供中文支持，不改变版式风格」。只需要这样：

    \usepackage[scheme = plain]{ctex}

特别适用于在英文文档中需要添加少许汉字的情况。

除此之外，用户可能会比较关心新版宏集对旧版宏包的兼容性问题。CTeX 2.0 对使用时间较长的稳定版本 1.02c 和 1.02d 做了尽可能的兼容。基于这两个旧版本的宏包书写的文档，在新版本下可以不作任何修改地编译，并且效果几乎一致，但有一些过时选项需要注意。这些选项在新版宏集中基于兼容性考虑被保留，但在将来可能被移除。完整的兼容性可参看宏集手册 12.2 节，这里列出部分比较重要的：

* `cs4size` 和 `c5size`：旧版宏包用于选择文档全局字号的选项，已过时，相当于新版宏集 `zihao = -4` 和 `zihao = 5` 的功能。
* `cap` 和 `nocap`：旧版宏包用于选择排版风格的选项，已过时，相当于新版宏集 `scheme = chinese` 和 `scheme = plain` 的功能。
* `fancyhdr`, `hyperref` 和 `fntef`：旧版宏包的兼容性选项，均已过时。新版宏集默认打开兼容性，不过需要用户手工载入相关宏包（`fancyhdr` 和 `hyperref`）。出于兼容性考虑，选项保留，功能是载入相关宏包。
* `ctexcap.sty`：过时宏包，相当于 `\usepackage[heading = true]{ctex}`，不推荐使用。

具体的内容，烦请参看新版宏集手册。关于 `\ctexset`，有不少「很犀利」的用法哦~
