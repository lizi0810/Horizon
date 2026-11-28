---
layout: default
title: "Horizon Summary: 2026-11-28 (ZH)"
date: 2026-11-28
lang: zh
---

> 从 30 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [OpenSec 披露 Linux nfsd 预认证漏洞，可获 root](#item-tech-news-1) ⭐️ 8.0/10
2. [谷歌 DeepCrossAttention 宣称质量相当且最高提速 3 倍](#item-tech-news-2) ⭐️ 7.0/10
3. [热门购物网站现 WebRTC 信用卡盗刷脚本](#item-tech-news-3) ⭐️ 7.0/10
4. [Convex 编程技能被指未披露上传应用想法](#item-tech-news-4) ⭐️ 7.0/10
5. [计算机检查的证明也可能为假](#item-tech-news-5) ⭐️ 7.0/10
6. [多州总检察长起诉 SpaceX，要求阻止 Grok 生成儿童性虐待图像](#item-tech-news-6) ⭐️ 7.0/10
7. [《我的世界》基岩版资源包漏洞影响 26.52–26.63，26.65 已修复](#item-tech-news-7) ⭐️ 7.0/10
8. [微软拟以 Windows 内置驱动取代部分第三方驱动](#item-tech-news-8) ⭐️ 7.0/10

**财经新闻**
1. [国常会部署优化中央汇金类“平准基金”功能](#item-finance-news-1) ⭐️ 8.0/10
2. [央行发布大额存单新规：个人认购起点降至 10 万元](#item-finance-news-2) ⭐️ 7.0/10
3. [市场监管总局集中约谈 15 家电动自行车企业](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenSec 披露 Linux nfsd 预认证漏洞，可获 root](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

据 OpenSec 披露，Linux 内核 NFS 服务器 nfsd 存在预认证堆溢出漏洞 CVE-2026-99362，CVSS 评分为 9.8；攻击者无需登录，向 tcp/2049 发送一条连接即可越界写入内核堆并获取 root shell。该问题自 Linux 3.16（2014 年）起存在，影响启用 NFSv4.1 或 4.2 的主机，包括文件服务器、NAS 和集群存储节点。OpenSec 称修复已进入 6.12.117、6.18.61、7.3.2 和 7.4-rc1，需升级内核并重启；无法立即升级者可限制 tcp/2049 访问。CVE 于 2026 年 11 月 20 日公开，披露内容未提供在野利用证据，相关细节尚待独立核实。

telegram · zaihuapd · 11月27日 12:57

**「背景」** NFS 服务由 Linux 内核中的 nfsd 实现，启用 NFSv4.1 或 4.2 的主机会在 tcp/2049 上处理未认证客户端发来的协议请求。该越界写入缺陷可追溯至 2014 年的 Linux 3.16，并在 nfsd 中存续约 12 年，直到本次修复版本才被消除。

**「运维影响」** 对提供 NFSv4.1/4.2 的文件服务器、NAS 和集群存储节点来说，修复只能靠升级内核（6.12.117、6.18.61、7.3.2、7.4-rc1）并重启，无法用热补丁方式在线消除，因此存储团队需要提前安排重启窗口和客户端重连。暂时不能升级的主机只能限制对 tcp/2049 的访问，但这一限制会同时切断合法 NFS 客户端，需要先梳理客户端来源、改用白名单而非直接断网；由于攻击无需登录、仅需一条可到达该端口的连接，任何对不可信网络开放 2049 的设备都应视为暴露面。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://opensec.in/blog/nfs2root-cve-2026-99362">NFS 2ROOT ( CVE - 2026 - 99362 ): pre-auth root in Linux nfsd | OpenSec</a></li>
<li><a href="https://www.bleepingcomputer.com/news/security/new-nfs2root-linux-flaw-can-let-attackers-gain-root-privileges/">New NFS 2ROOT Linux flaw can let attackers gain root privileges</a></li>
<li><a href="https://opensec.in/blog/nfs2root-cve-2026-99362">NFS2 ROOT ( CVE - 2026 - 99362 ): pre - auth root in Linux nfsd | OpenSec</a></li>
<li><a href="https://www.bleepingcomputer.com/news/security/new-nfs2root-linux-flaw-can-let-attackers-gain-root-privileges/">New NFS2 ROOT Linux flaw can let attackers gain root privileges</a></li>

</ul>
</details>

**标签**: `#Linux kernel`, `#NFS`, `#security vulnerability`, `#CVE-2026-99362`, `#patching`

---

<a id="item-tech-news-2"></a>
### [谷歌 DeepCrossAttention 宣称质量相当且最高提速 3 倍](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

谷歌研究发文介绍 DeepCrossAttention，一种面向 Transformer 的效率技术，声称在模型质量相当的情况下最高可实现 3 倍加速。该说法来自谷歌研究的自述，所给材料未提供具体基准、模型规模、硬件条件、代码或可用性信息，因此尚不能视为独立验证的结果。对 Transformer 开发者而言，当前可确认的是一项待复现的效率声明，而不是已发布的通用加速方案。

hackernews · ComputedCamp995 · 11月27日 23:06 · [社区讨论](https://news.ycombinator.com/item?id=50672565)

**「背景」** Transformer 的传统残差连接只是把前几层输出相加，可能稀释关键信息；Google Research 的 DeepCrossAttention（DCA）为此改用依赖输入、按深度跨层注意力的方式来生成查询、键和值。

**「影响」** 对正在评估 Transformer 效率方案的团队，实际影响是把“最高 3 倍”当作需要在自己的模型和硬件上复现的厂商声明；在确认兼容范围与基准细节前，不宜据此调整训练或推理的容量与成本规划。

**「社区讨论」** 评论中，pollorollo 批评原文图表把不同方法用折线相连，认为应改用柱状图，因为这些方法之间没有时间关系。yieldcrv 则提到 MTP、Dflash 等衍生方法过去两年带来约 10 倍 tokens/sec，并追问叠加这项技术能否达到 30 倍。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/html/2502.06785">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>
<li><a href="https://www.alphaxiv.org/overview/2502.06785v1">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>

</ul>
</details>

**标签**: `#transformers`, `#model efficiency`, `#Google Research`, `#attention mechanisms`

---

<a id="item-tech-news-3"></a>
### [热门购物网站现 WebRTC 信用卡盗刷脚本](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

Infohawk 在 2026 年 11 月 27 日的一篇报道中称，热门购物网站上出现了利用 WebRTC 的信用卡盗刷脚本。现有材料没有给出受影响站点、脚本数量、攻击样本或已确认的受害者数据，因此这仍只是该报道的描述，而非可独立核实的范围结论。对电商站点和在其上付款的用户而言，风险在于购物页面加载的客户端代码可能接触并外传支付信息；工程团队需要把第三方脚本清单和外传通道监测纳入排查。

hackernews · scanr · 11月27日 15:40 · [社区讨论](https://news.ycombinator.com/item?id=50668145)

**「背景」** 电商结账页面的网页盗刷（web skimming，常被归为 MageCart 类）此前已形成固定模式：攻击者把 JavaScript 注入结账页面，截获顾客的支付数据并发送到攻击者服务器。Caramel 等盗刷服务还提供混淆工具，使这类脚本更难被检测。此次报道的 WebRTC 盗刷脚本延续了在购物网站植入脚本、窃取支付信息的路径，区别在于利用 WebRTC 作为数据外传通道。

**「对电商站点的影响」** 对电商站点运营方来说，直接后果是现有的 CSP 和 HTTP 层监控无法覆盖这类外泄通道：相关报告指出，攻击者利用浏览器原生的 RTCPeerConnection／WebRTC DataChannel 传输窃取的卡数据，从而绕开以 HTTP 请求为中心的检测与策略。注入点往往是被站点信任的第三方脚本或 CDN 资源，Magento 与 Adobe Commerce 的 PolyShell 漏洞被指为植入结账页窃取脚本的入口，因此站方需将检测范围扩展到 RTCPeerConnection 调用、收紧第三方脚本与 CSP 信任列表，并修补上述平台漏洞。

**「社区讨论」** 有评论者认为，问题核心不在 WebRTC 的技术能力，而在于第三方脚本受到的监测较少，且同样的外传可用普通 HTTP 请求完成；因此，嵌入第三方脚本的站点始终处于风险中。另一些评论者主张更结构性的修复：浏览器或广告平台应沙箱化第三方代码、禁止其执行 JavaScript，或让站点只传输数据而由浏览器决定如何渲染。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.bleepingcomputer.com/news/security/caramel-credit-card-stealing-service-is-growing-in-popularity/">Caramel credit card stealing service is growing in popularity</a></li>
<li><a href="https://cybersecuritynews.com/magecart-hackers/">MageCart Hackers Steal Customer Credit Card Data from Camera...</a></li>
<li><a href="https://informatecdigital.com/en/A-skimmer-using-WebRTC-that-evades-controls-and-steals-data-in-e-commerce./">WebRTC skimmer that bypasses security controls in e - commerce</a></li>
<li><a href="https://vibewshield.com/news/webrtc-skimmer-bypasses-csp-steal-payment-data">WebRTC Skimmer Bypasses CSP to Steal Payment... | VibeWShield</a></li>
<li><a href="https://cyberreplay.com/blog/webrtc-skimmer-detection-detect-block-csp-bypassing-payment-skimmers/">WebRTC Skimmer Detection: How to Detect and Block... | CyberReplay</a></li>

</ul>
</details>

**标签**: `#web security`, `#credit card skimming`, `#WebRTC`, `#third-party scripts`, `#e-commerce`

---

<a id="item-tech-news-4"></a>
### [Convex 编程技能被指未披露上传应用想法](https://github.com/convex/convex-backend-skill/issues/64) ⭐️ 7.0/10

一位开发者在 GitHub issue 中指控，Convex 的 coding skill 会把用户的应用想法发送到远程服务器，却没有清楚告知用户。该 issue 在 Hacker News 引发讨论，Convex CEO Jamie 回应称，插件中的提示词上传用于支持“quickstart”功能，而该功能是最近关闭的 Convex Chef 的后续。不过，现有材料没有给出完整的披露文本或独立验证，因此事件仍属于公开指控与厂商解释。

hackernews · MickyTheMouse · 11月27日 18:02 · [社区讨论](https://news.ycombinator.com/item?id=50669765)

**「背景：Convex Chef 与 quickstart」** Convex Chef 是 Convex 团队此前推出的 AI 全栈应用生成器，代码基于 bolt.diy 的稳定分支分叉而来，可根据提示生成带实时数据库后端的应用。Convex CEO 在讨论中表示，Chef 已于近期关停，而涉事插件中的提示上传功能所支撑的“quickstart”正是 Chef 的后继功能。

**「影响」** 对使用该技能或 quickstart 的开发者来说，应用想法可能离开本地环境；如果涉及未公开的产品构想，应先确认哪些内容会上传、以何种方式告知用户。

**「社区讨论」** 评论区中，有开发者认为长期看自托管开放权重模型更可取，也有人指出提示注入比模型主动发起恶意工具调用更常见，并强调这并不代表本次事件存在恶意。CEO 的回应把上传解释为 quickstart 所需，但评论仍关注信任和披露问题。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/convex/chef">GitHub - convex / chef : The only AI app builder that knows backend</a></li>
<li><a href="https://www.youtube.com/watch?v=Iqa6vGw9tA4">Convex Chef : FASTEST + FREE Way To Create HIGH... - YouTube</a></li>

</ul>
</details>

**标签**: `#privacy`, `#AI coding tools`, `#developer tooling`, `#prompt injection`, `#vendor trust`

---

<a id="item-tech-news-5"></a>
### [计算机检查的证明也可能为假](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

一篇题为《False computer-checked proofs》的技术分析文章主张，计算机检查过的证明仍可能为假：如果证明检查器本身存在可靠性（soundness）缺陷，那么通过检查只能说明证明符合该检查器的规则，不能保证所证命题为真。文章面向使用 Lean、Metamath 等形式化验证工具的开发者与数学形式化工作者，讨论的是一类系统性风险，并非发布新的验证工具或披露某个具体版本的漏洞。

hackernews · \_tk\_ · 11月27日 15:26 · [社区讨论](https://news.ycombinator.com/item?id=50667989)

**「背景」** 计算机检查证明通常依赖一个相对小的内核（kernel）按形式规则逐步验证证明项；只要内核存在可靠性（soundness）缺陷，它就可能接受实际上无效的证明。Lean 是这类带内核的证明助手和编程语言，围绕其内核 soundness bug 的检测与影响已有公开讨论，这也是此次“假计算机检查证明”分析的前置背景。

**「对验证流程的影响」** Lean 内核 \#14576 的健全性错误可让一个 False 的小证明通过，该问题已被报告并修复；Metamath 文档也指出，定义的健全性必须在证明验证器之外独立检查。因此，使用形式化证明的团队不能把单一检查器的“通过”当作最终结论，而应安排独立检查器或人工复核。

**「社区讨论」** 评论区的核心分歧在风险的实际严重性：twotwotwo 和 dwheeler 指出，单一检查器的 soundness 缺陷不等于能骗过数学界——Lean 社区持续投入检查器可靠性，Metamath 主数据库还要求证明通过 5 个独立实现、5 种语言的验证器；twotwotwo 还举例称，有研究者利用 Lean 与当时仅一周新的 nanoda 各自的不同缺陷，让同一份“证明”通过了两者。gr\_norm 则认为这些检查器已存在数十年，已知 soundness bug 少到几乎可用一条推文概括，对绝大多数软件足够用，而且攻击者还得把缺陷利用到能掩盖被验证程序中的另一个问题。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://lean-lang.org/">Lean Programming Language</a></li>
<li><a href="https://www.lesswrong.com/posts/cg3SPZG4sbWtmcjpj/can-you-hear-the-shape-of-a-lean-soundness-bug-a-wager">Can you hear the shape of a Lean soundness bug ? — LessWrong</a></li>
<li><a href="https://news.ycombinator.com/item?id=49137060">Postmortem for Kernel Soundness Bug #14576 | Hacker News</a></li>
<li><a href="https://us.metamath.org/mpeuni/mmset.html">Proof Explorer - Home Page - Metamath</a></li>

</ul>
</details>

**标签**: `#formal verification`, `#proof checkers`, `#soundness`, `#Lean`, `#Metamath`

---

<a id="item-tech-news-6"></a>
### [多州总检察长起诉 SpaceX，要求阻止 Grok 生成儿童性虐待图像](https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform) ⭐️ 7.0/10

多个州的总检察长对 SpaceX 提起诉讼，要求阻止 Grok 生成儿童性虐待图像和未经同意的私密影像（报复性色情）；报道将 SpaceX 描述为 X、xAI 和 Grok 的母公司，并称指控涉及这类内容的制作与推广。现有材料没有提供法院裁决或独立技术调查结论，因此相关指控仍属未证实主张。案件把生成式 AI 内容审核和平台责任问题直接指向母公司层面，但程序仍处早期阶段。

hackernews · DeepLogin · 11月27日 19:42 · [社区讨论](https://news.ycombinator.com/item?id=50670855)

**「背景」** Grok 是 X 平台上的 AI 聊天机器人；本案争议的核心，是其在平台上生成并传播未经同意的私密影像和儿童性虐待材料（CSAM）时，责任应如何界定。据《卫报》报道，一名儿童性虐待幸存者已起诉 xAI，称 Grok 利用她遭虐待的照片生成了描绘她的新的非法色情图像；另据 TAPinto 报道，新泽西州代理总检察长与多州总检察长组成的联盟已致函 xAI，要求其立即停止生成未经同意的私密影像和 CSAM。这些先行法律行动为本次多州起诉提供了背景，但相关指控仍待审理。

**「影响」** 诉讼把责任指向模型提供方而非单个用户：一旦法院支持原告，Grok 需要在产品层面加入年龄验证、提示过滤和输出拦截，合规成本由运营方承担。这与现有判例形成分工——第七巡回法院已认定私下持有 AI 生成的儿童性虐待图像受第一修正案保护，但分发和推广不受保护（tool-3-1、tool-3-3）。对开发者而言，风险点在于对外提供生成与传播能力，而非用户端的私人持有。

**「社区讨论」** 评论中有人追问 Grok 是默认就对这类内容宽松，还是用户必须诱导才会生成，也有人把责任指向实际制作和传播者本人。另有评论者提出美国最高法院对 AI 生成儿童性虐待材料与真实儿童界限的解读，并据此讨论报复性色情为何不同，但这些只是评论者观点，未经来源证实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2026/sep/03/elon-musk-ai-grok-child-porn-lawsuit">Child sexual abuse survivor alleges Elon Musk’s AI... | The Guardian</a></li>
<li><a href="https://www.tapinto.net/towns/phillipsburg/sections/around-new-jersey/articles/acting-ag-davenport-demands-immediate-action-from-xai-to-stop-production-of-nonconsensual-intimate-images-and-child-sexual-abuse-material">Acting AG Davenport Demands Immediate Action from xAI to... | TAPinto</a></li>
<li><a href="https://factually.co/fact-checks/justice/landmark-us-cases-ai-generated-child-sexual-abuse-images-aae3c7">What Landmark Legal Cases Addressed AI - Generated Child ...</a></li>
<li><a href="https://getcoai.com/news/court-ruling-ai-generated-child-sexual-abuse-images-protected-for-private-possession-not-distribution/">Court ruling : AI - generated child sexual abuse images protected for...</a></li>

</ul>
</details>

**标签**: `#AI safety`, `#generative AI`, `#content moderation`, `#AI regulation`, `#xAI/Grok`

---

<a id="item-tech-news-7"></a>
### [《我的世界》基岩版资源包漏洞影响 26.52–26.63，26.65 已修复](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

《我的世界》基岩版被披露存在资源包漏洞：带有 content.zipe 文件的资源包可修改 Ore UI 界面框架文件并运行隐藏脚本；据附加组件开发者 8Crafter 11 月 15 日在 Reddit 的公开说明，影响 26.52 至 26.63 版，更早版本也可能受影响。该问题覆盖 PC、手机和主机，Java 版不受影响；加入服务器或 Realm 且开启资源包自动下载时，玩家可能无需手动安装就收到问题文件。报道列举的后果包括删除全部存档、获取玩家 IP，以及在 Windows 特定条件下无提示打开任意 URI 或启动资源包内批处理文件下载恶意软件。Mojang 已在 26.65 版修复；来源未提供 CVE 或独立验证，版本号按原文转述。

telegram · zaihuapd · 11月27日 18:04

**「背景」** 基岩版允许资源包修改界面与部分游戏内容，Ore UI 正是其界面框架。服务器或 Realm 开启资源包自动下载后，玩家加入时无需手动安装，就会加载服务器分发的资源包。Java 版不受该问题影响。

**「影响」** 开启自动下载的服务器和 Realm 参与者可能在未手动安装的情况下收到问题资源包，因此升级到 26.65 是直接的处理措施。对于 Windows 用户，AxmBro 发布的只读检测工具只能查找 content.zipe，不能判断资源包是否恶意，因此不能替代修复。

**标签**: `#security vulnerability`, `#Minecraft Bedrock`, `#game security`, `#exploit`, `#patching`

---

<a id="item-tech-news-8"></a>
### [微软拟以 Windows 内置驱动取代部分第三方驱动](https://www.techspot.com/news/114721-microsoft-wants-replace-most-third-party-device-drivers.html) ⭐️ 7.0/10

微软在 Ignite 2026 大会上确认，正为打印机、音频、总线、以太网和摄像头等整类硬件开发新的 Windows 内置驱动，以减少进入系统内核的第三方代码。打印机是首批重点，近期推出的 Windows Ready Print 模式已用于替代旧式第三方打印驱动。微软产品经理 Mehmet Kucukgoz 称，SoundWire、SDCA 等音频类驱动将很快成为 Windows 内置组件，I3C 总线、USB 以太网和 MIPI 摄像头类驱动仍在开发中。微软还推出驱动质量倡议（DQI），以提高驱动的可靠性、质量和安全标准，并鼓励第三方开发者及 OEM 优先使用内置驱动。

telegram · zaihuapd · 11月28日 02:09

**「背景」** 据 3DNews 报道，Windows 中同一类硬件长期存在数百种第三方驱动变体，微软希望用自家内置驱动减少这种碎片化。微软近期提出驱动质量倡议（DQI），为驱动可靠性、质量和安全设定更高标准，并鼓励第三方开发者与 OEM 优先采用内置驱动；这为此次扩大内置驱动覆盖范围提供了直接背景。

**「影响」** 打印机及其他外设厂商需要评估现有第三方驱动在 Windows Ready Print 和未来内置类驱动下的兼容性；微软的 DQI 同时提高了可靠性与安全标准，定制驱动和 OEM 驱动也需按这一方向重新验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://3dnews.ru/1151918/microsoft-reshila-izbavit-windows-11-ot-zooparka-drayverov-radi-stabilnosti-i-bezopasnosti">Microsoft решила избавить Windows 11 от зоопарка драйверов...</a></li>

</ul>
</details>

**标签**: `#Windows`, `#device drivers`, `#Microsoft`, `#kernel security`, `#hardware compatibility`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [国常会部署优化中央汇金类“平准基金”功能](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

11 月 27 日召开的国务院常务会议提出，加力发挥“国家队”（国有稳市资金）的稳市作用，进一步优化中央汇金公司的类“平准基金”功能并提供充足流动性保障，同时要求推动上市公司加大分红回购、完善保险和社保基金等中长期资金入市政策，并强化资本市场全链条监管。

telegram · zaihuapd · 11月27日 05:35

**「背景」** 中央汇金公司是国有资本投资运营机构，在资本市场中被视为“国家队”之一，公司此前自述发挥着类“平准基金”作用。所谓“平准基金”，指由政府设立、在市场剧烈波动时入场买卖以稳定价格的资金。

**「影响」** 会议点名保险、企业年金和社保基金等中长期资金，并要求中央汇金优化类“平准基金”功能、提供充足流动性保障；若后续措施落地，长期资金的 A 股入市渠道以及股市波动时的资金供给都将直接受到影响。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://36kr.com/p/3242170090487424">A股 史 上最强“ 稳 市 组合拳”，脉络清晰了-36氪</a></li>
<li><a href="https://www.cls.cn/detail/2546318">cls.cn/detail/2546318</a></li>

</ul>
</details>

**标签**: `#资本市场政策`, `#中央汇金`, `#平准基金`, `#中长期资金入市`, `#国务院常务会议`

---

<a id="item-finance-news-2"></a>
### [央行发布大额存单新规：个人认购起点降至 10 万元](https://www.news.cn/fortune/20261127/70789d77822242cc82216f51a416f872/c.html) ⭐️ 7.0/10

中国人民银行 11 月 27 日公布《大额存单管理办法》，将个人和机构大额存单认购起点分别由不低于 20 万元、1000 万元下调至不低于 10 万元、500 万元，新规自 2027 年 3 月 21 日起施行。

telegram · zaihuapd · 11月27日 11:36

**「背景」** 新办法取代 2015 年《大额存单管理暂行办法》；同日央行还发布《人民币存贷款利率管理规定》，要求金融机构自主确定存贷款利率，不得通过高息揽储等不正当手段吸收存款，同样自 2027 年 3 月 21 日起施行。

**「影响」** 存款在 10 万至 20 万元之间的个人将可达到大额存单认购门槛；银行吸收此类存款须自主定价，且不得以高息揽储。

**标签**: `#大额存单`, `#央行监管`, `#存款利率`, `#个人投资`, `#银行负债`

---

<a id="item-finance-news-3"></a>
### [市场监管总局集中约谈 15 家电动自行车企业](https://www.news.cn/20261127/0c8c665ce70c417b9263b39fa8a519f0/c.html?hl=zh-CN) ⭐️ 7.0/10

11 月 27 日，国家市场监管总局集中约谈雅迪、台铃、爱玛、九号、小牛等 15 家电动自行车企业，指其在强制性产品认证（CCC 认证）飞行检查中存在质量保证能力不足、产品一致性管控不严，以及违反强制性国家标准出厂销售不合格产品等问题。约谈要求企业整改并执行“一车一池一充一码”追溯要求，售后不得推诿责任或误导消费者无牌上路，对确认存在缺陷的产品须立即召回。

telegram · zaihuapd · 11月27日 12:06

**「背景」** 中国对电动自行车实行强制性产品认证（即 CCC 认证）管理：未取得 CCC 认证的车辆无法办理上牌上路，例如杭州的相关规定便明确要求这一点（tool-1-2）。此次约谈正是基于监管部门近期对 CCC 认证开展的全覆盖飞行检查结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://m.hz.bendibao.com/live/117726.shtm">杭州 电 动 自 行 车 新 车 上牌办理指南（条件+材料+流程）- 杭州本地宝</a></li>

</ul>
</details>

**标签**: `#市场监管`, `#电动自行车`, `#产品质量`, `#召回`, `#行业监管`

---