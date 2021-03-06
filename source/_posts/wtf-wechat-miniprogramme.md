---
title: 微信小程序开发踩坑总结
date: 2018-08-30 00:08:00
tags: 
    - 微信
    - 微信小程序
    - wechat
    - 随手
categories: 随笔
---
从开始写微信小程序，到现在第三次提交审核，大概过了有一个星期多吧。

我的微信小程序是基于守望轩开源的 Wordpress 微信小程序进行开发的，主要的底层都没有进行改动，只是进行了一些精简。我对其进行开发的部分主要是在 UI 上的改动。

微信小程序在刚刚诞生的时候，我还是很不屑的。觉得所谓的“小程序”就是一个用阉割版的 HTML 和阉割版的 CSS 以及阉割版的 JavaScript 封装在微信里的 PWA。简单来说，就是 PWA 的“拙劣的模仿者”。但是随着小程序的不断进化以及微信的大力推广，目前来看，小程序似乎也在移动应用市场中占有了一席之地。以至于阿里和百度都相继推出了小程序来与微信小程序竞争。

微信小程序和 PWA，从功能上来看，PWA 依然更胜一筹。我认为，PWA 应该属于原有的 Web 的父级，而小程序则是属于 Web 的子集。PWA 的发展是属于整个互联网标准的进步，而小程序的发展只能说是中心化平台大力推广的结果。

毕竟是“子集”，那么微信小程序的功能也并没有完整 Web 那么完善，虽然功能简陋，但依托于强大的微信，微信小程序在载入时间上丝毫不比原生 APP 要短。并且，微信小程序继承了微信公众平台系统的封闭性，一切在小程序中展示的内容，也必须通过在后台设置的若干个“合法域名”传输。也就是说，在博客上发文章，如果想在微信小程序之中展示，那么使用广为人知的 sm.ms 图床是不可能的事情了，必须自建图床来托管自己博客文章中的插图。

在微信小程序中，JavaScript 是不被允许用来操作 DOM 的，那么这就直接影响到博客评论的展示。在守望轩原有的微信小程序中，其直接写死了五级评论和子评论，在有评论产生是直接填入，而无需再操作 DOM，但是这样的操作看起来十分繁杂，并且理论上微信并没有允许个人小程序带有评论的功能，于是我便将 WXML 中的所有评论的框架删除了。

还有一个不得不吐槽的就是，微信小程序官方对个人开发者带有的与生俱来的“歧视”。首先在发布初期，微信小程序直接不允许任何个人开发者开发和发布小程序，后期允许个人开发小程序后，又在发布审核上作出种种摸不清道不明的限制，不少开发了微信小程序的站长都说，在提交审核的时候，微信总是用“文娱咨询”来 ban 掉小程序，并且按照腾讯一贯以来的尿性，他说是啥就是啥，你既不能反驳也不能申诉，你只能接受腾讯告诉你的一切。并且腾讯可是并没有人工客服的哦，除非你充了足够多的钱，不然除非到他的大楼里，你能找到活着的腾讯客服，那几乎是不可能的事情。

曾经尝试找了几次腾讯客服之后差点被气死的我，决定把网站的内容全部删掉再提交小程序的审核，但愿这次能过把。

微信小程序的审核这种事情，也并没有一个统一的标准，纵然你对着腾讯开发者文档中一条条的来自查自己的小程序，觉得没什么问题了，你依然可能会被因为小程序中含有“文娱资讯”而被打回来。然而再腾讯的文档中，可并没有提到哪怕一丝一毫关于“文娱资讯“的内容。甚至，连”资讯“两个字都没有在文档中出现过。

说白了，微信小程序公开的标准和内部的标准完全是两码事，公开的标准中尽可能的体现腾讯所谓”开放“的一面，而腾讯并不会去执行他自己所制定的公开的这部标准，他只会再自己的小本本中写下各种乱七八糟的条条框框，然后拿来卡着用户和开发者。并且微信小程序的审核，也是完全看审核员的”心情“的，他觉得你有文娱资讯，你就是有文娱资讯，他觉得你的功能不完整，你就是功能不完整。~~引申到微信支付上，你的微信钱包内的资金被盗，你因为被诈骗而转账，微信都可以以你没有保管你的账户为由而拒绝赔偿，拒绝提供行骗者的个人信息，哪怕是提供给警方。（题文无关，划掉）~~

一位 WXG 的员工的博客和小程序中提到

> 小程序用个人类型的上线的小程序，后来发现要扩展功能却因为这“个人类型”而遇到种种限制，比如说个人类型是不准出现评论内容的。

> 基于以上考虑，为了“微信小程序版”能安稳活下去，必须转成企业类型的小程序。

总而言之，还是基于对开发者的不信任和歧视，而制定了那么多摸不清道不明的审核规范，以及并没有提供任何审核申诉的入口。

中心化的所谓互联网，发展到这个阶段，个人开发者总会处处碰壁的。