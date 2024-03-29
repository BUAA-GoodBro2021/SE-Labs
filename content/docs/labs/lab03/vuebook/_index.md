---
title: 'Vue Guide Book'
weight: 2003
---

# Vue Guide Book

{{< hint info >}}
在学习 Vue 之前，同学们至少要对 HTML5、CSS3 和 JavaScript 有了一定的熟练度。除此之外，最好对于 ES6 之后的新的语法规范有一定了解，（尤其是<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let" target="_blank">let</a>、<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions" target="_blank">箭头函数</a>、<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_syntax" target="_blank">展开语法</a>等）并对 Promise 有初步的认识。在此基础上，再展开对 Vue 的学习。
{{< /hint >}}


本指导书将介绍 **在大多数的网络教程中鲜有提及，但是在学习过程中是尤为重要的部分**（比如说 Vue 的配置和项目搭建过程），以及在学习过程中大量相关的资料和助教的心得。我们会在给出的资料中尽可能简明地介绍 Vue 的一些基本语法，但是 **不能代替网络上已有的系统的、体系化的 Vue 教程**。作为一个功能强大、富有生命力的前端框架，Vue 不是靠读完篇幅极为有限的指导书就可以真正掌握的。想要摸见入门的“门槛”，需要跟随网络教程认真学习；想要真正入门，在学完教程后还需要多加练习，多做项目。

本指导书依然保留了对于 Vue2 的介绍。尽管 Vue2 将于 2023 年 12 月 31 日停止维护，但是这并不代表 Vue2 就将在十年内甚至二十年内退出市场。原因有二：其一是 Vue3 还是一个非常年轻的框架，立足未稳，很多公司的项目就如同他们钟爱的 windows XP 和 windows 7 一样，还是使用 Vue2 写的。原因无他——稳定，生态好；其二，Vue3 并不是完全摒弃了 Vue2 的语法特点。读过 Vue3 官网文档就会发现，Vue3 实际上是双管齐下、并驾齐驱，既安利了 Vue3 全新的核心组合式 API（Composition API），也保留了 Vue2 经典的选项式 API（Options API）。在只调用 Vue.js 的核心运行库的时候，Vue3 对于 Vue2 的兼容性是非常好的。当然，和 React 的严格保证非破坏性更新不同，Vue3 在很多方面已经和 Vue2 有了较大差异，尤其是在使用了较多第三方库的情况下，升级迭代并非易事。

上面的原因似乎都过于宏大。其实，仅从学习的角度来看，Vue2 对于新手来说也是不容忽视的一环。尽管在搭建项目骨架的过程中，方式、调用的 API、架构逻辑等都发生了变化，但是 Vue2 和 Vue3 的核心概念还是一脉相承的，其基本语法指令也几无变化。很多重要的概念，例如生命周期、数据和交互函数分离、父子组件利用 props 通信等，从 Vue2 去理解要比直接学 Vue3 清晰的多。而且学完 Vue2 之后，Vue3 的选项式 API 就不需要花更多功夫额外学习了。而只学会在 setup 语法糖下简化的组合式 API，在遇到需要维护 Vue2 项目的场景时，难免会犯怵。从诸多互联网公司的招聘要求可以看出，Vue2 仍然是同学们在学习时不能丢开的一环。即使在本学期“逃课”，在后面的项目经历中多半也会被迫“补票”。

不同于其他框架，Vue 是由国人开发者尤雨溪开发，因此 Vue 有着完备的中文文档，并且不需要担心翻译造成曲解的问题。因此大家在阅读中文文档时大可放心学习。

- Vue2 的中文文档：<a href="https://v2.cn.vuejs.org/" target="_blank">https://v2.cn.vuejs.org/</a>
- Vue3 的中文文档：<a href="https://cn.vuejs.org/" target="_blank">https://cn.vuejs.org/</a>
- Vue CLI （Vue 开发的标准工具）的中文文档：<a href="https://cli.vuejs.org/zh//" target="_blank">https://cli.vuejs.org/zh/</a>
- Vue Router （Vue.js 的官方路由）的中文文档：<a href="https://router.vuejs.org/zh/" target="_blank">https://router.vuejs.org/zh/</a>