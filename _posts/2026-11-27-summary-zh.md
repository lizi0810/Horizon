---
layout: default
title: "Horizon Summary: 2026-11-27 (ZH)"
date: 2026-11-27
lang: zh
---

> 从 37 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [为何需要可形式化验证的主流编程语言](#item-tech-news-1) ⭐️ 7.0/10
2. [面向 AMD GPU 的 llama.cpp 专用分支](#item-tech-news-2) ⭐️ 7.0/10
3. [阿斯麦 CEO：全面断供只会逼中国加速自研](#item-tech-news-3) ⭐️ 7.0/10
4. [荷兰大臣反对美国 MATCH Act 限制 ASML 对华销售](#item-tech-news-4) ⭐️ 7.0/10
5. [智谱、月之暗面新模型据报延期](#item-tech-news-5) ⭐️ 7.0/10
6. [谷歌 Play 将于 2027 年起公开商家开发者电话和地址](#item-tech-news-6) ⭐️ 7.0/10

**科技博客**
1. [谁有权判定文本由 AI 写成](#item-tech-blog-1) ⭐️ 5.0/10

**财经新闻**
1. [德银：半导体出口额首次超过石油和天然气](#item-finance-news-1) ⭐️ 8.0/10
2. [国常会部署稳市：加力发挥“国家队”作用，优化中央汇金类“平准基金”功能](#item-finance-news-2) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [为何需要可形式化验证的主流编程语言](https://blainehansen.me/post/mainstream-verifiable-language/) ⭐️ 7.0/10

这篇文章主张，应该有一门既面向主流采用、又支持形式化验证的编程语言；现有材料显示，它是设计与论证性文章，并非新语言或工具发布，也没有可独立核验的验证结果。Hacker News 的讨论集中在形式化正确性能否保证真实需求，以及已有验证语言为何没有成为主流；评论者提到多个现有工具和项目，但未形成共识。

hackernews · todsacerdoti · 11月27日 05:22 · [社区讨论](https://news.ycombinator.com/item?id=50663089)

**「背景」** 形式化验证本身已有成熟工具链，但通常依附于特定语言或领域：Why3 提供名为 WhyML 的规格与编程语言，并调用自动化与交互式外部定理证明器来消解验证条件，同时充当 Frama-C WP、SPARK Ada 的 GNATprove 等工具的证明管理层。也就是说，可验证性长期存在于这类专用或研究导向的生态中，而非主流通用语言的一等公民，这正是该文主张的出发点。

**「影响」** 对准备在项目中引入形式化验证的开发者，讨论中的具体提醒是：证明代码或规范正确，并不自动保证实现符合预期；还需要把规范、实现和真实需求对齐。

**「社区讨论」** 有评论者引用 Knuth 的话强调“证明正确”不等于“满足预期”，并称即便为软件写了 TLA+ 规范，也未必显著改善质量；另一位评论者则从状态空间爆炸的角度质疑简单系统的完全验证是否可行。也有评论者列举 Dafny、SPARK Ada、Why3、Verus、Frama-C、TLA+ 等已有方向，认为“主流”来自采用而非设定目标，并有人介绍自己正在开发面向 WebAssembly GC 的 Zena。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://why3.org/">Why3</a></li>
<li><a href="https://sota.io/blog/why3-eu-formal-verification-framework-inria-saclay">Why3: EU-Native Proof Framework — Frama-C, SPARK Ada ...</a></li>

</ul>
</details>

**标签**: `#formal verification`, `#programming languages`, `#software correctness`, `#language design`, `#TLA+`

---

<a id="item-tech-news-2"></a>
### [面向 AMD GPU 的 llama.cpp 专用分支](https://devnull.land/amd-specific-llama-cpp) ⭐️ 7.0/10

一个面向 AMD GPU 的 llama.cpp 专用分支已在开发者社区出现，目标是改善 AMD 显卡上的大语言模型推理。现有材料没有给出该分支的具体版本、改动列表、支持的 GPU 型号或独立性能数据，因此它目前应视为一个针对 AMD 硬件的社区分支，而不是已验证的通用加速方案。

hackernews · julianlam · 11月26日 17:11 · [社区讨论](https://news.ycombinator.com/item?id=50657265)

**「背景」** llama.cpp 是通用的本地大模型推理引擎，社区常针对特定 GPU 架构维护分支，以替换或调整底层计算内核。相关 AMD 专用分支 llama-cpp-rdna-boosts 采用补丁集形式：把最小改动应用到固定的 llama.cpp 提交上，并在上游更新后持续重放这些改动，而不是维护完全独立的代码树。此前已有面向 AMD gfx906（MI50/MI60/Vega7）等较老显卡的分支，在 ROCm 环境下加入 FlashAttention 等优化，显示按 GPU 代际定制推理后端已形成细分的实践路径。

**「影响」** 对仍在使用 MI50、MI60 或 Radeon VII（gfx906）的用户，实际可行路径是采用社区维护的 llama.cpp 分支；但相关分支的兼容性目前只明确覆盖 Qwen3 30B-A3B Thinking 2507 与 Qwen3 4B Instruct 2507 的 Q4\_0 量化，且 gfx906 仅进入 ROCm nightly 构建、未进入官方稳定版，因此部署前需验证目标模型并准备自行处理 ROCm 版本管理。

**「社区讨论」** 评论者重点讨论了较老的 gfx906 数据中心卡：有人称其 32GB HBM2 和约 1TB/s 带宽在二手市场价格很低，并已形成针对缺少张量核心、原生 bf16 等限制优化 llama.cpp 的小生态。也有用户报告在 R9700 上使用 radiance engine 或在 MI100 上把部分 NVIDIA 内核移植到 ROCm 后获得明显提速，但这些属于个人体验，尚未在材料中独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://devnull.land/amd-specific-llama-cpp">AMD - specific fork of llama . cpp | devnull . land</a></li>
<li><a href="https://github.com/CypherpunkSamurai/awesome-llama-cpp">GitHub - CypherpunkSamurai/awesome- llama - cpp : An Index of most...</a></li>
<li><a href="https://github.com/thickprogrammer/llama.cpp-gfx906">thickprogrammer/ llama . cpp - gfx 906 : llama . cpp optimized for AMD ...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50657265">AMD -specific fork of llama . cpp | Hacker News</a></li>

</ul>
</details>

**标签**: `#llama.cpp`, `#AMD`, `#GPU optimization`, `#LLM inference`, `#open source`

---

<a id="item-tech-news-3"></a>
### [阿斯麦 CEO：全面断供只会逼中国加速自研](https://www.semafor.com/article/11/25/2026/asml-makes-the-case-for-selling-chips-to-china) ⭐️ 7.0/10

阿斯麦 CEO 富凯在 Semafor 的《Future Proof》节目中表示，出口管制应只保护最先进技术，不能把中国完全排除在外；否则中国会在自研光刻设备上“加倍甚至三倍投入”。他称阿斯麦近 30 年在华光刻机市场份额接近 100%，对华销售设备比最先进制程落后十多年，维持这一代差反而能让中国继续依赖西方设备。美国方面正推动拟议中的 MATCH 法案，拟把管制从 EUV 扩大到浸没式 DUV 和维护服务；荷兰政府与阿斯麦均表示反对。

telegram · zaihuapd · 11月26日 12:19

**「背景」** 阿斯麦在光刻设备市场长期占据主导地位，在中国市场的份额近 30 年接近 100%。美国现有管制主要针对最先进的 EUV 光刻机，而拟议中的 MATCH 法案试图把限制范围扩大到浸没式 DUV 和维护服务，使管制从尖端制程延伸至更成熟的芯片生产环节。

**「已装机设备的维护或成下一个管制焦点」** 若 MATCH 法案按现有文本推进，受影响的将不只是新机出口，还包括已在中国装机的浸没式 DUV 的备件与维护服务。据 Tom&\#x27;s Hardware 报道，中国此前已囤积 343 台浸没式 DUV，其中 270 台阿斯麦扫描机可在不使用 EUV 的情况下用于 7nm 制程；一旦原厂服务被切断，这些设备的持续运行将更依赖厂商自行维护和备件储备。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://hwbusters.com/news/match-act-asml-could-lose-the-right-to-service-the-machines-it-already-sold-china/">MATCH Act : ASML Could Lose the Right to Service the Machines It...</a></li>
<li><a href="https://www.tomshardware.com/tech-industry/semiconductors/china-stockpiled-343-immersion-duv-tools-for-advanced-chipmaking-report-claims-270-asml-scanners-can-produce-7nm-processors-without-sanctioned-euv-tools">China stockpiled 343 immersion DUV tools for... | Tom&#x27;s Hardware</a></li>

</ul>
</details>

**标签**: `#semiconductors`, `#export controls`, `#ASML`, `#China`, `#technology policy`

---

<a id="item-tech-news-4"></a>
### [荷兰大臣反对美国 MATCH Act 限制 ASML 对华销售](https://www.bloomberg.com/news/articles/2026-11-26/netherlands-plans-to-fight-rollout-of-proposed-us-curbs-on-asml) ⭐️ 7.0/10

荷兰外贸与发展合作大臣 Sjoerd Sjoerdsma 11 月 26 日在议会表示，荷兰不会接受美国进一步限制 ASML 对华销售，并反对 MATCH Act 的域外管辖效力。荷兰正与欧盟委员会协调，同时联合德国、法国游说，争取将该法案从美国年度国防政策法案中剔除。MATCH Act 由两党共同提出，要求荷兰、日本等盟友收紧对华出口管制，否则美方将单方面限制其半导体设备；中国约占 ASML 今年销售额的 20%，外界预计国会 12 月中旬表决且通过可能性较大。

telegram · zaihuapd · 11月26日 14:56

**「背景」** 此前，美国和荷兰已禁止 ASML 向中国出口最先进的 EUV 光刻机；拟议中的 MATCH Act 则进一步收紧转售管制，并可能把限制扩大到部分较旧的 DUV 浸没式设备。该法案要求荷兰、日本在 150 天内将其出口管制与美国对齐，否则美方将单方面限制相关半导体设备。

**「影响」** 若法案按现文本通过，ASML 等荷兰设备商将面临更严对华出口限制，否则可能被美方单方面限制；荷兰政府在表决前联合德法游说，正是试图避免这种合规与市场压力落到本国企业身上。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.fool.com/investing/2026/04/24/the-match-act-could-blow-a-hole-in-asmls-revenue-h/">The MATCH Act Could Blow a Hole in ASML &#x27;s Revenue. Here&#x27;s What...</a></li>
<li><a href="https://www.linkedin.com/posts/erudite-risk_asiarisk-geoeconomicconfrontation-china-activity-7445742293120368640-qSkK">US lawmakers introduce MATCH Act to restrict AI chip exports to China</a></li>
<li><a href="https://overcentral.com/en/netherlands-opposes-match-act-asml-china/">Netherlands Opposes US Bill Restricting ASML Chip Sales to China</a></li>

</ul>
</details>

**标签**: `#ASML`, `#半导体出口管制`, `#MATCH Act`, `#美荷关系`, `#科技政策`

---

<a id="item-tech-news-5"></a>
### [智谱、月之暗面新模型据报延期](https://www.reuters.com/world/china/us-chip-curbs-distillation-crackdown-threaten-chinese-ai-model-development-2026-11-26/) ⭐️ 7.0/10

路透社 11 月 26 日报道，智谱原计划本月发布约 3 万亿参数的 GLM-5.5，但至今尚未推出，知情人士称发布可能推迟至 2027 年第一季度或更晚。报道还称，月之暗面内部预计，若完全失去海外算力，其重大版本发布间隔将从 6 个月拉长到一年以上，下一代旗舰 Kimi K4 或推迟至 2027 年年中。报道将原因归于反蒸馏防护措施日趋有效、海外算力受限，以及 Anthropic 和 OpenAI 的反蒸馏措施令训练数据获取变难；月之暗面已转向蒸馏谷歌和 Meta 的模型。智谱通过网传朋友圈截图否认相关说法，路透报道又依赖匿名消息，实际发布时间仍不确定。

telegram · zaihuapd · 11月26日 15:14

**「背景」** 知识蒸馏通常指用能力更强的模型生成输出，再以此训练新模型，从而降低数据与算力成本；反蒸馏措施则是上游模型厂商限制这类输出被用于训练竞品。对依赖海外高端算力和外部模型数据的团队来说，蒸馏渠道收紧与算力供给不确定会直接拉长训练和版本迭代周期。

**「影响」** 对依赖 GLM 或 Kimi 的开发者与企业而言，短期应把模型升级和供应商备份计划按延期风险处理，并以官方发布信息为准，而不宜把报道中的 2027 年时间点视为确定日程。

**标签**: `#AI industry`, `#China AI`, `#model releases`, `#export controls`, `#knowledge distillation`

---

<a id="item-tech-news-6"></a>
### [谷歌 Play 将于 2027 年起公开商家开发者电话和地址](https://www.androidpure.com/google-play-trader-developer-address/) ⭐️ 7.0/10

谷歌 Play 宣布，自 2027 年 3 月 1 日起在全球向用户展示自我声明为“商家”的开发者的联系方式，包括个人账户持有者的电话号码和地址。所有活跃开发者账户须在 2027 年 2 月 1 日前申报商家或非商家身份，逾期可能无法更新应用，并被从 Play 全球下架。该政策于 2026 年 10 月公布，本周因隐私担忧遭到开发者反弹。报道还称，欧盟相关法规并未要求向欧盟以外用户展示这些信息；谷歌不接受邮政信箱作为付款地址，苹果则仅在欧洲相关国家展示地址并允许使用邮政信箱。

telegram · zaihuapd · 11月27日 01:44

**「背景」** 所谓“商家”身份申报，原本与欧盟要求向消费者披露经营者联系方式的规则相关；苹果目前也只在欧洲相关国家展示地址。此次谷歌把申报义务扩大到全球所有活跃开发者账户，并把电话和地址的展示范围从欧盟扩展到全球用户，而欧盟法规本身并未要求向欧盟以外用户公开这些信息。

**「影响」** 对个人账户持有者的直接影响是：一旦自我声明为商家，其电话号码和地址将向全球 Play 用户公开，而不只限于欧盟用户；开发者需在 2027 年 2 月 1 日前确认商家身份和可公开的联系方式，逾期可能影响应用更新或上架状态。

**标签**: `#Google Play`, `#developer privacy`, `#platform policy`, `#Android development`, `#app ecosystem`

---

## 科技博客

<a id="item-tech-blog-1"></a>
### [谁有权判定文本由 AI 写成](https://seangoedecke.com/who-gets-to-decide-if-something-is-written-by-ai/) ⭐️ 5.0/10

rss · Sean Goedecke · 11月27日 00:00

**「背景」** 围绕作品、稿件或推文是否由 AI 生成的争议每天都在出现。作者认为，争论表面上是检测是否可靠，实质上是“谁有权作出判定”的权力问题。

**「方案」** Sean Goedecke 对 Pangram 等检测工具的怀疑者抱有同情：这类工具来自人们本就不信任的科技行业，而用工具化流程取代社区判断，也被许多人视为过去几十年社会变化的一部分。若把判定交给社区自律，作者认为结果更糟：不用 AI 的人往往不熟悉 AI 文本特征，可能漏掉明显的 AI 痕迹，也可能仅因一段文字较长、语气礼貌就误判为 AI。调查和草稿同样难以证明清白，因为熟练的 AI 写作也能伪造这些痕迹。因此，真想阻止 AI 进入文学和文化空间，就应使用现有最强检测工具，或推动开源方案、政府自建检测平台，而不是依赖社区共识。文章也提到误报是合理担忧，并承认检测可靠性仍有争议；其“人们不擅长判断 AI 文本”的论据主要来自观察和轶事。

**「启示」** 作者的结论是：AI 作者身份争议本质上是治理权归属之争；在缺乏可信制度或公共检测工具时，社区自律并不会更公正，反而可能让更多 AI 生成内容进入公共空间。

**标签**: `#AI detection`, `#power and governance`, `#community moderation`, `#writing authenticity`, `#tooling policy`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [德银：半导体出口额首次超过石油和天然气](https://www.cnbc.com/2026/11/26/semiconductor-chips-are-the-new-oil-heres-why.html) ⭐️ 8.0/10

德意志银行基于国际贸易中心数据的分析显示，受 AI 热潮推动，按最近四个季度的总额计算，2026 年第一季度全球半导体出口额约 1.61 万亿美元，首次超过石油和天然气的约 1.53 万亿美元。

rss · CNBC Finance · 11月26日 17:52

**「背景」** 德银称，过去数十年石油出口国把盈余投入美国国债等资产，形成“石油美元”，如今可能要考虑“芯片美元”；这一变化出现在投资者重新评估 AI 支出、半导体股大幅波动之际。

**「影响」** 德银认为，由于亚洲芯片出口国与美国科技企业联系更紧，部分芯片出口收入可能回流美国科技股、初创企业和数据中心，从而影响 AI 投资周期的资金来源。

**标签**: `#semiconductors`, `#AI`, `#global trade`, `#market volatility`, `#macro finance`

---

<a id="item-finance-news-2"></a>
### [国常会部署稳市：加力发挥“国家队”作用，优化中央汇金类“平准基金”功能](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

11 月 27 日召开的国务院常务会议提出，持续完善资本市场稳市机制，加力发挥“国家队”稳市作用，并进一步优化中央汇金公司的类“平准基金”（用于平抑市场异常波动的资金）功能、提供充足流动性保障。会议还要求推动上市公司加大分红回购，完善保险、企业年金、社保基金等中长期资金入市支持政策。

telegram · zaihuapd · 11月27日 05:35

**「背景」** 中央汇金是国有投资机构，被市场视为“国家队”入场买股的主要力量；所谓类“平准基金”功能，指在股市大幅下跌时买入股票以稳定市场。11 月 5 日发布的国务院相关报告已提出支持中央汇金发挥这一作用并完善相关机制，本次国常会属于进一步部署。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.globaltimes.cn/page/202611/1373716.shtml">China’s State Council report calls for supporting state-owned ...</a></li>

</ul>
</details>

**标签**: `#China capital markets`, `#State Council policy`, `#Central Huijin`, `#market stabilization`, `#long-term capital`

---