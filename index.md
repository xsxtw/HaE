## About

**HaE**是基于 `BurpSuite Java插件API` 开发的请求高亮标记与信息提取的辅助型框架式插件，该插件可以通过自定义正则的方式匹配响应报文或请求报文，并对满足正则匹配的报文进行信息高亮与提取。

现代化Web应用走上前后端分离开发模式，这就导致在日常测试时候会有许多的流量，如果你想要尽可能全面的对一个Web应用进行测试评估，将花费大量精力浪费在无用的报文上；**HaE的出现正是为了解决这一类似场景**，借助HaE你可以**有效的减少**测试的时间，将更多的精力放在**有价值、有意义**的报文上，**提高漏洞挖掘效率**。

**注**: 要想灵活的使用`HaE`，你需要掌握正则表达式阅读、编写、修改能力；由于`Java`正则表达式的库并没有`Python`的优雅或方便，所以HaE要求使用者必须用`()`将所需提取的表达式内容包含；例如你要匹配一个**Shiro应用**的响应报文，正常匹配规则为`rememberMe=delete`，如果你要提取这段内容的话就需要变成`(rememberMe=delete)`。

## Download Public Rules

[gh0stkey/HaE/gh-pages/Config.yml](https://raw.githubusercontent.com/gh0stkey/HaE/gh-pages/Rules.yml)
