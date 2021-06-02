- [JavaScript的诞生](#javascript的诞生)
  - [JavaScript名字的由来](#javascript名字的由来)
  - [JavaScript的缺陷](#javascript的缺陷)
- [JavaScript的历史](#javascript的历史)
  - [浏览器大战](#浏览器大战)
  - [黑暗时代——IE 6 如日中天](#黑暗时代ie-6-如日中天)
  - [Chrome 横空出世](#chrome-横空出世)
  - [移动互联网的兴起](#移动互联网的兴起)
  - [JavaScript的兴起--Gmail的诞生](#javascript的兴起--gmail的诞生)
  - [JS的爆发--V8引擎](#js的爆发--v8引擎)



# JavaScript的诞生
　　1994 年，网景公司（Netscape）发布了 Navigator 浏览器0.9版。这是历史上第一个比较成熟的网络浏览器，轰动一时。但是，这个版本的浏览器只能用来浏览，不具备与访问者互动的能力。网景公司急需一种网页脚本语言，使得浏览器可以与网页互动。

　　当时的形势就是，网景公司的整个管理层，都是 Java 语言的信徒，Sun 公司完全介入网页脚本语言的决策。

　　此时，34 岁的系统程序员 Brendan Eich 登场了。1995 年 4 月，网景公司录用了他。

　　Brendan Eich 的主要方向和兴趣是函数式编程，网景公司招聘他的目的，是研究将 Scheme 语言作为网页脚本语言的可能性。Brendan Eich 本人也是这样想的，以为进入新公司后，会主要与 Scheme 语言打交道。

　　仅仅一个月之后，1995年5月，网景公司做出决策，未来的网页脚本语言必须"看上去与 Java 足够相似"，但是比 Java 简单，使得非专业的网页作者也能很快上手。这个决策实际上将 Perl、Python、Tcl、Scheme 等非面向对象编程的语言都排除在外了。

　　Brendan Eich 被指定为这种"简化版Java语言"的设计师。

　　但是，他对 Java 一点兴趣也没有。为了应付公司安排的任务，他只用 10 天时间就把 Javascript 设计出来了。
>"与其说我爱 Javascript，不如说我恨它。它是 C 语言和 Self 语言一夜情的产物。十八世纪英国文学家约翰逊博士说得好：'它的优秀之处并非原创，它的原创之处并不优秀。'" ——Brendan Eich

　　就是这样一个连发明这门语言的人都不待见，只用了 10 天时间草草完工的语言竟然成了世界上使用最广泛的语言之一，实在是充满了传奇色彩。

## JavaScript名字的由来
　　
　　最初为了紧贴Java（有一种咖啡也叫Java），这门“新语言”被命名为Mocha（有一种咖啡也叫Mocha）。
　　但由于商标的问题，以及网景公司很多产品已经使用了“Live”作为产品名前缀，Mocha更名为LiveScript。
　　由于网景公司与Sun公司有一些合作（网景公司允许Java程序以applet（小程序）的形式，直接在浏览器中运行；甚至还考虑直接将Java作为脚本语言嵌入网页），Sun把Java这个商标授权给了网景公司，于是LiveScript更名为JavaScript。

## JavaScript的缺陷
　　JavaScript被Brenden仅仅花了10天就开发了出来，可想而知JavaScript是如此的粗糙 [阮一峰--Javascript的10个设计缺陷](http://www.ruanyifeng.com/blog/2011/06/10_design_defects_in_javascript.html)
   


# JavaScript的历史
 ## 浏览器大战
　　JavaScript 发明之后微软进行跟进发明了 JScript，而网景公司进行反击，将 JavaScript 向 ECMA 提交标准，制定了 ECMAScript。

　　微软公司由于在 Windows 系统中捆绑了 IE 浏览器，导致网景公司的浏览器份额大幅下跌最后被收购。

　　临死之前网景公司将 FireFox 开源试图最后一搏，结果失败。

　　Brendan 一直协助维护 FireFox。
 ## 黑暗时代——IE 6 如日中天
　　2001年，IE6和Windows XP系统一起发布。至2004年，IE6已经占据了市场的80%以上。然而这款浏览器却不兼容W3C标准（主要是CSS）。
　　看见IE6独霸一方，无人可敌，微软直接把IE6开发团队给解雇了一大部分，导致IE6不断爆出安全漏洞。这种情况下，FireFox重新出山，希望打败IE。
　　看到FireFox的东山再起，微软重新组建的团队开发IE7。2005年，IE7发布，但是由于开发团队能力不如IE6的团队，IE7也干不过自家兄弟IE6。
　　2006年，主流浏览器除了IE6还有一个FireFox。但由于盗版XP系统在中国横行，直至2010年中国浏览器市场仍然被IE6占据。这也成为了中国前端开发的噩梦（需要不断兼容IE），大大阻碍了中国前端的发展。

## Chrome 横空出世
　　2004年，谷歌雇用了一些FireFox和IE的开发者进行自己浏览器Chrome的开发。
　　2008年，Chrome浏览器发布，并迅速拿下1%的市场份额。由于Chrome浏览器非常快，越来越受到市场的欢迎。
　　2011年，Chrome浏览器的市场份额超越FireFox。
　　2016年，Chrome浏览器的市场份额达到62%。Chrome的腾飞结束了中国前端开发者被IE折磨的日子。2016年，淘宝天猫宣布不再支持IE6、7；同年年底，宣布不再支持IE8。

## 移动互联网的兴起
　　2010年iPhone4发布，宣告智能手机时代来临。但是无论是IOS系统（Safari），还是Android系统（chrome）都不支持IE浏览器。
　　微软见此情况和Nokia联合起来，但最终还是Nokia在手机行业宣告失败，手机业务被微软收购。可以认为，手机上基本见不到IE了。
　　至此，前端开发者可以不再需要考虑IE用户的需求，摆脱了被IE支配的日子，前端从此极速发展。

## JavaScript的兴起--Gmail的诞生
　　2004年愚人节，谷歌发布Gmail。Gmail是谷歌开发的一款具有发送接收邮件功能的在线网页。在Gmail出现以前，所有人都认为浏览器只能用于浏览阅读。但是Gmail让用户重新认识了浏览器的功能。
　　2005年，Jesse将谷歌实现Gmail的技术命名为AJAX。从此前端技术正式出现。
　　2006年，JQuery发布，JQuery是最长寿的JS库，其主要是兼容IE，但随着IE的落寞，JQuery也逐渐淡出前端开发者的视野。

## JS的爆发--V8引擎
　　Chrome的JS引擎是V8（V1~V7是不同语言的引擎），V8引擎超快的速度让chrome成为了最主流的浏览器。
　　2009年，Ryan基于V8，创建了Node.js；2010年Issac基于Node.js写出了npm。有了node.js，前端工程师实现了在浏览器之外执行JS。
　　2010年，TJ受Sinatra的启发，发布了Express.js。Node.js与Express.js让前端工程师可以完成后端的内容。虽然还比不上Java，但是至少也具备了手段。
　　借助Chrome的风，期间也爆发除了很多前端的技术：gulp、grunt、yeoman、require.js、webpack、Angular、React、Vue等。当然其中一些技术也已经过时了。


  
