---
layout: default
title: "Horizon Summary: 2026-11-28 (EN)"
date: 2026-11-28
lang: en
---

> From 30 items, 11 important content pieces were selected

---

**Technology News**
1. [OpenSec discloses CVSS 9.8 Linux nfsd CVE-2026-99362 root flaw](#item-tech-news-1) ⭐️ 8.0/10
2. [Google Research claims DeepCrossAttention yields up to 3x speedup](#item-tech-news-2) ⭐️ 7.0/10
3. [Report: WebRTC-based card skimming scripts found on shopping sites](#item-tech-news-3) ⭐️ 7.0/10
4. [Convex coding skill accused of uploading app ideas without disclosure](#item-tech-news-4) ⭐️ 7.0/10
5. [False computer-checked proofs and the soundness-bug debate](#item-tech-news-5) ⭐️ 7.0/10
6. [States sue SpaceX over Grok generating child sexual abuse, non-consensual images](#item-tech-news-6) ⭐️ 7.0/10
7. [Minecraft Bedrock resource-pack flaw affects 26.52–26.63, fixed in 26.65](#item-tech-news-7) ⭐️ 7.0/10
8. [Microsoft expands Windows in-box drivers, starting with printers](#item-tech-news-8) ⭐️ 7.0/10

**Financial News**
1. [China&\#x27;s State Council Executive Meeting Calls for Bigger &quot;National Team&quot; Role in Stabilizing Markets](#item-finance-news-1) ⭐️ 8.0/10
2. [央行下调大额存单认购门槛：个人降至10万元](#item-finance-news-2) ⭐️ 7.0/10
3. [China market regulator summons 15 electric-bicycle makers over quality failures](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenSec discloses CVSS 9.8 Linux nfsd CVE-2026-99362 root flaw](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

OpenSec reported CVE-2026-99362, a CVSS 9.8 pre-authentication heap overflow in the Linux kernel&\#x27;s nfsd server that can be triggered by a single connection to tcp/2049 and may yield a root shell. It says the flaw has existed since Linux 3.16 \(2014\) and affects hosts with NFSv4.1 or 4.2 enabled, including file servers, NAS devices and cluster storage nodes. Fixes are listed in kernels 6.12.117, 6.18.61, 7.3.2 and 7.4-rc1 and require a reboot; if an immediate upgrade is not possible, the report recommends restricting tcp/2049 at the firewall. The CVE was published on Nov 20, 2026, but the item provides no exploitation evidence or independent corroboration.

telegram · zaihuapd · Nov 27, 12:57

**「Background」** nfsd is the kernel&\#x27;s built-in NFS server, and NFSv4.1/4.2 is the version served by default on most current distributions, so any host with tcp/2049 reachable is exposed. OpenSec&\#x27;s write-up describes the primitive as a 61-byte out-of-bounds write past a kernel heap object from a single TCP connection, which can be chained into a root shell. The defect is not new: BleepingComputer describes it as a 12-year-old flaw, consistent with the source&\#x27;s statement that it has existed since Linux 3.16 in 2014.

**「Mitigation and action」** Administrators of hosts serving NFSv4.1 or 4.2 should upgrade to a fixed kernel — 6.12.117, 6.18.61, 7.3.2, or 7.4-rc1 — and reboot, since installing the patched kernel alone does not remove the flaw from the running kernel. Where upgrading is not immediately possible, including long-lived 3.16-and-later deployments such as CentOS 7, restricting TCP port 2049 to trusted clients is the interim control, because any host able to reach that port can trigger the overflow without authenticating.

<details><summary>References</summary>
<ul>
<li><a href="https://opensec.in/blog/nfs2root-cve-2026-99362">NFS 2ROOT ( CVE - 2026 - 99362 ): pre-auth root in Linux nfsd | OpenSec</a></li>
<li><a href="https://www.bleepingcomputer.com/news/security/new-nfs2root-linux-flaw-can-let-attackers-gain-root-privileges/">New NFS 2ROOT Linux flaw can let attackers gain root privileges</a></li>
<li><a href="https://opensec.in/blog/nfs2root-cve-2026-99362">NFS2 ROOT ( CVE - 2026 - 99362 ): pre - auth root in Linux nfsd | OpenSec</a></li>
<li><a href="https://www.getpagespeed.com/server-setup/security/nfs2root-cve-2026-99362-centos-7">NFS2 ROOT ( CVE - 2026 - 99362 ) on CentOS 7: Fixed Kernel</a></li>

</ul>
</details>

**Tags**: `#Linux kernel`, `#NFS`, `#security vulnerability`, `#CVE-2026-99362`, `#patching`

---

<a id="item-tech-news-2"></a>
### [Google Research claims DeepCrossAttention yields up to 3x speedup](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research published a post describing DeepCrossAttention, a transformer residual-connection technique it claims can deliver model quality comparable to baseline while running up to 3x faster. The post, &quot;Supercharging Transformer Residual Connections,&quot; presents the result as an efficiency improvement for transformer model developers, but the supplied material provides no independent benchmark, implementation details, or availability and compatibility information, so the 3x figure remains a vendor claim.

hackernews · ComputedCamp995 · Nov 27, 23:06 · [Discussion](https://news.ycombinator.com/item?id=50672565)

**「Background」** Transformer residual connections normally add each layer’s output to the running representation; Google’s post notes that this simple summation can dilute crucial information. The underlying paper, arXiv:2502.06785, describes DeepCrossAttention \(DCA\) as an input-dependent, depth-wise cross-attention mechanism for the query, key, and value components, and the post contrasts that learnable routing with standard sequential residual connections.

**「Impact」** For AI systems practitioners, the immediate consequence is that any adoption decision should wait for reproducible benchmarks and implementation details; the supplied evidence does not show which transformer workloads, hardware, or training-versus-inference settings the claimed speedup applies to.

**「Community discussion」** Commenters focused on presentation and practical upside: one objected that the results were plotted as line graphs despite no temporal relationship, and another asked whether DeepCrossAttention could compound with MTP plus Dflash derivatives to reach 30x, saying those had already delivered 10x tokens/sec over two years. A separate commenter speculated that Gemini Neon&\#x27;s low cost and speed might be connected, but offered no evidence.

<details><summary>References</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections</a></li>
<li><a href="https://arxiv.org/html/2502.06785">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>
<li><a href="https://www.alphaxiv.org/overview/2502.06785v1">DeepCrossAttention : Supercharging Transformer Residual ...</a></li>

</ul>
</details>

**Tags**: `#transformers`, `#model efficiency`, `#Google Research`, `#attention mechanisms`

---

<a id="item-tech-news-3"></a>
### [Report: WebRTC-based card skimming scripts found on shopping sites](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

A report published by InfoHawk on 27 November 2026 describes credit card skimming scripts that use WebRTC to exfiltrate stolen payment data from popular shopping sites. The technique matters because the data leaves the browser over a channel that defenders and monitoring tools watch less closely than ordinary HTTP requests, according to the report. The supplied material does not name the affected retailers, the script families involved, or how many sites were compromised, so the scope of the campaign is unverified. The finding is a vendor report rather than an independently confirmed measurement.

hackernews · scanr · Nov 27, 15:40 · [Discussion](https://news.ycombinator.com/item?id=50668145)

**「Background」** Web skimming campaigns, often grouped under the MageCart label, inject JavaScript into e-commerce checkout flows so customer payment data is captured and sent to an attacker-controlled server. Attackers have also industrialized the tooling: services such as Caramel supply skimming scripts plus obfuscation intended to keep them from being detected. The WebRTC detail in the current report concerns the exfiltration channel used after that injection, not a new way to compromise a site.

**「CSP and HTTP monitoring miss this path」** Merchants relying on Content Security Policy and HTTP-request monitoring as their main checkout defenses should not assume those controls cover this path: the skimmer exfiltrates card data over WebRTC DataChannels, a transport separate from the HTTP requests CSP restricts, so filtering tuned for HTTP endpoints can be bypassed. The reported entry point is a small payload injected into an already-trusted third-party dependency or CDN resource, and one account ties injection to the PolyShell flaw in Magento and Adobe Commerce, making patching those platforms and auditing scripts loaded on checkout pages the concrete remediation steps. Published detection guidance focuses on flagging unexpected RTCPeerConnection creation on payment pages rather than on blocking HTTP destinations alone.

**「Community discussion」** Hacker News commenters treated the incident as a third-party script problem rather than a WebRTC bug: afavour argued the same exfiltration could be done with plain HTTP requests and that any site embedding third-party scripts remains exposed, while jszymborski cited the episode as justification for ad blocking. Others pushed on structural fixes, with snickerer objecting that the web lets strangers run arbitrary code in the browser and s\_u\_d\_o asking why ad networks and browsers do not sandbox ads with JavaScript execution disabled.

<details><summary>References</summary>
<ul>
<li><a href="https://www.bleepingcomputer.com/news/security/caramel-credit-card-stealing-service-is-growing-in-popularity/">Caramel credit card stealing service is growing in popularity</a></li>
<li><a href="https://cybersecuritynews.com/magecart-hackers/">MageCart Hackers Steal Customer Credit Card Data from Camera...</a></li>
<li><a href="https://informatecdigital.com/en/A-skimmer-using-WebRTC-that-evades-controls-and-steals-data-in-e-commerce./">WebRTC skimmer that bypasses security controls in e - commerce</a></li>
<li><a href="https://vibewshield.com/news/webrtc-skimmer-bypasses-csp-steal-payment-data">WebRTC Skimmer Bypasses CSP to Steal Payment... | VibeWShield</a></li>
<li><a href="https://cyberreplay.com/blog/webrtc-skimmer-detection-detect-block-csp-bypassing-payment-skimmers/">WebRTC Skimmer Detection: How to Detect and Block... | CyberReplay</a></li>

</ul>
</details>

**Tags**: `#web security`, `#credit card skimming`, `#WebRTC`, `#third-party scripts`, `#e-commerce`

---

<a id="item-tech-news-4"></a>
### [Convex coding skill accused of uploading app ideas without disclosure](https://github.com/convex/convex-backend-skill/issues/64) ⭐️ 7.0/10

A GitHub issue alleges that Convex&\#x27;s coding skill sends users&\#x27; app ideas to a remote server without clearly telling them. Convex CEO Jamie responded in the thread that the plugin&\#x27;s prompt upload powers Convex&\#x27;s &quot;quickstart&quot; feature, the successor to the recently shut-down Convex Chef vibe-coding product. The supplied material does not independently verify the original allegation or establish the full scope of what is transmitted.

hackernews · MickyTheMouse · Nov 27, 18:02 · [Discussion](https://news.ycombinator.com/item?id=50669765)

**「Background」** Convex is a hosted backend platform for building and running applications, and its AI app builder, Convex Chef, was developed by the Convex team as a fork of the open-source bolt.diy project that generates full-stack apps against that platform. The item concerns a &quot;skill&quot; — a packaged bundle of agent instructions — which an AI coding assistant loads and executes locally, so following the skill can involve network requests sent from the developer&\#x27;s machine.

**「Impact」** Developers using the Convex skill should check what the quickstart flow sends before entering proprietary app ideas or sensitive implementation details, since the CEO&\#x27;s response confirms that prompt upload is part of that feature.

**「Community Discussion」** Commenters treated the dispute as a trust problem for hosted AI developer tools; one argued that self-hosted open-weight models are the long-term answer, while another said prompt injection is more common than models making malicious tool calls on their own.

<details><summary>References</summary>
<ul>
<li><a href="https://chef.convex.dev/">chef . convex .dev</a></li>
<li><a href="https://github.com/convex/chef">GitHub - convex / chef : The only AI app builder that knows backend</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#AI coding tools`, `#developer tooling`, `#prompt injection`, `#vendor trust`

---

<a id="item-tech-news-5"></a>
### [False computer-checked proofs and the soundness-bug debate](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

An essay at cr.yp.to argues that a computer-checked proof can still be false when the proof checker itself has a soundness bug, so acceptance by a checker is not by itself a guarantee of truth. It examines how such false proofs can arise and why defenses matter for formal verification systems such as Lean and Metamath. The item is an analysis of the risk, not a report of a new checker failure.

hackernews · \_tk\_ · Nov 27, 15:26 · [Discussion](https://news.ycombinator.com/item?id=50667989)

**「Why the checker&\#x27;s kernel matters」** Proof assistants such as Lean and Metamath are built around a small trusted kernel that replays each inference step; if that kernel contains a soundness bug, the checker can accept a derivation that does not actually establish the claimed theorem. Earlier work in this area includes a 2022 computer-checked proof that a standalone HOL proof checker in OpenTheory format is correct, cited in the source page itself. Community discussion also points to a forged Lean proof that reportedly passed the independent nanoda checker as well, which is why multiple independently written checkers feature in the debate.

**「Practical risk」** Projects that rely on a single proof checker cannot treat its acceptance as definitive: a kernel-level soundness bug can allow an invalid proof, including a proof of False, to pass until the checker is patched. Lean kernel issue \#14576 is a concrete case in which such a proof was reported and then fixed.

**「Community discussion」** Commenters disputed the practical severity rather than the existence of soundness bugs: twotwotwo noted that Lean has had such bugs and that misleading mathematicians would require failures in multiple independent checkers plus input that survives informal review. dwheeler said Metamath&\#x27;s main databases require proofs to pass five independently created verifiers in five languages, while gr\_norm argued that the few known bugs are acceptable for most software because an attacker would still need to exploit one in a way that hides another defect.

<details><summary>References</summary>
<ul>
<li><a href="https://cr.yp.to/proofs/falseccp.html">False computer - checked proofs (djb)</a></li>
<li><a href="https://www.nacionale.com/en/articles/can-lean-proof-be-wrong-riemann-hypothesis-claude-checkers-collatz-kernel-bug">A forged Lean proof in July explains the Riemann checks</a></li>
<li><a href="https://news.ycombinator.com/item?id=49137060">Postmortem for Kernel Soundness Bug #14576 | Hacker News</a></li>

</ul>
</details>

**Tags**: `#formal verification`, `#proof checkers`, `#soundness`, `#Lean`, `#Metamath`

---

<a id="item-tech-news-6"></a>
### [States sue SpaceX over Grok generating child sexual abuse, non-consensual images](https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform) ⭐️ 7.0/10

State attorneys general have sued SpaceX, identified as the parent company of X and xAI, over allegations that xAI&\#x27;s Grok generates child sexual abuse material and non-consensual intimate images, including revenge porn. The Virginia Attorney General&\#x27;s office announced the filing and named Attorneys General Jones and Rayfield; the action seeks to stop the platform from creating and promoting that imagery. The available account gives no Grok model version, prompt conditions, court ruling, or technical remediation commitment, so this is an early-stage legal action rather than a demonstrated fix.

hackernews · DeepLogin · Nov 27, 19:42 · [Discussion](https://news.ycombinator.com/item?id=50670855)

**「Background」** Grok is xAI&\#x27;s chatbot on X, and the suit names SpaceX as its parent company. The action follows a September 2026 lawsuit by a survivor of child sexual abuse, who alleged that Grok used images of her abuse to generate new pornographic images. A coalition of state attorneys general had also demanded that xAI stop producing nonconsensual intimate images and child sexual abuse material.

**「Where liability lands」** The states&\#x27; suit targets generation and promotion rather than private possession — a distinction that matters because a federal appeals court has already held that privately possessing AI-generated child sexual abuse imagery is constitutionally protected, as summarized in the supplied results. That shifts the practical compliance burden onto model-level safeguards at generation and distribution time for xAI and other image-model providers, since user-side possession is the harder legal target. The suit is early-stage, so no court has yet ruled on whether SpaceX as parent company bears liability for Grok&\#x27;s outputs.

**「Community discussion」** Commenters questioned whether Grok required deliberate trickery to produce the prohibited images and asked why enforcement targets the platform rather than the people using it. One commenter asserted, without substantiation in the thread, that U.S. Supreme Court precedent protects AI-generated child sexual abuse material made for personal consumption but not images depicting real people; that claim is not established by the supplied material.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2026/sep/03/elon-musk-ai-grok-child-porn-lawsuit">Child sexual abuse survivor alleges Elon Musk’s AI... | The Guardian</a></li>
<li><a href="https://www.tapinto.net/towns/phillipsburg/sections/around-new-jersey/articles/acting-ag-davenport-demands-immediate-action-from-xai-to-stop-production-of-nonconsensual-intimate-images-and-child-sexual-abuse-material">Acting AG Davenport Demands Immediate Action from xAI to... | TAPinto</a></li>
<li><a href="https://factually.co/fact-checks/justice/landmark-us-cases-ai-generated-child-sexual-abuse-images-aae3c7">What Landmark Legal Cases Addressed AI - Generated Child ...</a></li>
<li><a href="https://getcoai.com/news/court-ruling-ai-generated-child-sexual-abuse-images-protected-for-private-possession-not-distribution/">Court ruling : AI - generated child sexual abuse images protected for...</a></li>

</ul>
</details>

**Tags**: `#AI safety`, `#generative AI`, `#content moderation`, `#AI regulation`, `#xAI/Grok`

---

<a id="item-tech-news-7"></a>
### [Minecraft Bedrock resource-pack flaw affects 26.52–26.63, fixed in 26.65](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

A flaw in Minecraft Bedrock Edition let a resource pack carrying a \`content.zipe\` file modify the game&\#x27;s Ore UI interface framework and run hidden scripts, according to add-on developer 8Crafter, who disclosed it on Reddit on November 15. The reported affected versions are 26.52 through 26.63, with earlier builds possibly affected too, spanning PC, mobile, and console; Java Edition is not affected, and Mojang fixed the issue in version 26.65. Because players who join a server or Realm with automatic resource-pack downloads enabled can receive the file without installing anything, 8Crafter listed possible abuses including deleting all saves, obtaining the player&\#x27;s IP address, and, on Windows under specific conditions, silently opening arbitrary URIs or launching a batch file from the pack to download malware. The disclosure is a community report with no CVE, root-cause detail, or independent confirmation supplied, and the version numbers are given as stated by the source.

telegram · zaihuapd · Nov 27, 18:04

**「Background」** Bedrock Edition resource packs are client-side content bundles, and the game&\#x27;s interface is rendered through the Ore UI framework. That meant a pack able to alter Ore UI files could affect interface behavior rather than only textures or sounds; with auto-download enabled when joining a server or Realm, the malicious content.zipe could arrive without a manual install.

**「Impact」** Server and Realm operators should treat auto-downloaded resource packs as able to reach clients without manual approval, and either vet packs or disable automatic downloads; players should update to 26.65. AxmBro&\#x27;s read-only Windows detection tool scans for \`content.zipe\` files but cannot determine whether a pack is malicious, so a clean scan is not evidence of safety.

**Tags**: `#security vulnerability`, `#Minecraft Bedrock`, `#game security`, `#exploit`, `#patching`

---

<a id="item-tech-news-8"></a>
### [Microsoft expands Windows in-box drivers, starting with printers](https://www.techspot.com/news/114721-microsoft-wants-replace-most-third-party-device-drivers.html) ⭐️ 7.0/10

At Ignite 2026, Microsoft confirmed it is developing new drivers for entire hardware classes and relying more on Windows in-box drivers, with some third-party code potentially replaced to keep more third-party code out of the kernel. Printers are the first focus: the recently introduced Windows Ready Print mode is intended to replace legacy third-party print drivers. Windows product manager Mehmet Kucukgoz said SoundWire and SDCA audio drivers will soon become built-in, and I3C bus, USB Ethernet, and MIPI camera class drivers are also in development. Microsoft also introduced a Driver Quality Initiative at its Windows Hardware Engineering Conference to raise driver reliability, quality, and security standards and to encourage third-party developers and OEMs to use in-box drivers; the non-printer classes are described as planned or in development, not shipped.

telegram · zaihuapd · Nov 28, 02:09

**「Background」** Microsoft&\#x27;s stated motivation is driver fragmentation: 3DNews reports that Windows carries hundreds of driver variants for the same hardware classes, and Microsoft wants to reduce that duplication with its own drivers. At an Ignite 2026 event on the Driver Quality Initiative, Windows product manager Mehmet Kucukgoz said WLAN support is &quot;currently in progress and will be released in 2027,&quot; according to Notebookcheck.

**「Impact」** Driver developers and OEMs should expect some printer, audio, I3C, USB Ethernet, and MIPI camera functionality to move into Windows itself, reducing the need for custom kernel drivers in those classes and pushing remaining drivers toward Microsoft&\#x27;s DQI reliability, quality, and security standards. The source does not specify which vendor-specific features will remain outside in-box coverage or give a timeline beyond &quot;soon&quot; for the audio drivers.

<details><summary>References</summary>
<ul>
<li><a href="https://3dnews.ru/1151918/microsoft-reshila-izbavit-windows-11-ot-zooparka-drayverov-radi-stabilnosti-i-bezopasnosti">Microsoft решила избавить Windows 11 от зоопарка драйверов...</a></li>
<li><a href="https://www.notebookcheck.com/Windows-11-WLAN-Treiber-laufen-ab-2027-ausserhalb-des-Kernels.1457992.0.html">Windows 11: WLAN-Treiber laufen ab 2027... - Notebookcheck News</a></li>

</ul>
</details>

**Tags**: `#Windows`, `#device drivers`, `#Microsoft`, `#kernel security`, `#hardware compatibility`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China&\#x27;s State Council Executive Meeting Calls for Bigger &quot;National Team&quot; Role in Stabilizing Markets](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

At a State Council executive meeting chaired by Premier Li Qiang on Nov 27, China&\#x27;s cabinet called for &quot;greater effort&quot; in the &quot;national team&\#x27;s&quot; role in steadying the capital market and for further optimizing the quasi-&quot;stabilization fund&quot; function of sovereign fund Central Huijin, alongside ample liquidity guarantees. The meeting also urged listed companies to raise dividend payouts and buybacks, backed policies to channel long-term money — insurance funds, enterprise annuities and social security funds — into the market, and pledged full-chain supervision to punish financial fraud and irregular share sales; no financial figures, tool details or timetable were disclosed.

telegram · zaihuapd · Nov 27, 05:35

**「Background」** Central Huijin is a state-owned investment company that has previously described itself as the capital market&\#x27;s &quot;national team,&quot; playing a quasi &quot;stabilization fund&quot; role, so the meeting&\#x27;s call seeks to strengthen an existing mechanism rather than create a new fund.

**「Impact」** If implemented, the measures would push insurers, enterprise annuities and the social security fund — long-term institutional investors — to become larger buyers of mainland-listed stocks, while widening state-owned Central Huijin&\#x27;s role as a backstop buyer during market selloffs.

<details><summary>References</summary>
<ul>
<li><a href="https://36kr.com/p/3242170090487424">A股 史 上最强“ 稳 市 组合拳”，脉络清晰了-36氪</a></li>
<li><a href="https://www.cls.cn/detail/2546318">cls.cn/detail/2546318</a></li>
<li><a href="https://finance.eastmoney.com/a/202611273941564045.html">finance.eastmoney.com/a/202611273941564045.html</a></li>

</ul>
</details>

**Tags**: `#资本市场政策`, `#中央汇金`, `#平准基金`, `#中长期资金入市`, `#国务院常务会议`

---

<a id="item-finance-news-2"></a>
### [央行下调大额存单认购门槛：个人降至10万元](https://www.news.cn/fortune/20261127/70789d77822242cc82216f51a416f872/c.html) ⭐️ 7.0/10

中国人民银行11月27日公布《大额存单管理办法》，将个人投资人认购起点由不低于20万元下调至不低于10万元、机构由1000万元下调至500万元，新规自2027年3月21日起施行。

telegram · zaihuapd · Nov 27, 11:36

**「背景」** 现行门槛出自2015年《大额存单管理暂行办法》；同日公布并同日施行的《人民币存贷款利率管理规定》要求金融机构自主确定存贷款利率，不得通过高息揽储等不正当手段吸收存款。

**「影响」** 门槛减半后，存款在10万元至20万元之间的个人也可认购大额存单，而银行在吸收存款时须遵守更明确的自主定价约束。

**Tags**: `#大额存单`, `#央行监管`, `#存款利率`, `#个人投资`, `#银行负债`

---

<a id="item-finance-news-3"></a>
### [China market regulator summons 15 electric-bicycle makers over quality failures](https://www.news.cn/20261127/0c8c665ce70c417b9263b39fa8a519f0/c.html?hl=zh-CN) ⭐️ 7.0/10

China&\#x27;s market regulator on Nov. 27, 2026, summoned 15 electric-bicycle companies, including Yadea, Tailg, Aima, Ninebot and Niu, demanding that they correct quality-control and mandatory-standard violations and immediately recall confirmed defective products. It also told them not to shift responsibility to consumers, mislead buyers into riding unregistered vehicles, or refuse returns by claiming certificates will soon be restored.

telegram · zaihuapd · Nov 27, 12:06

**「Background」** Electric bicycles sold in China must carry China Compulsory Certification \(CCC\) — the mandatory safety mark required for both sale and registration of a vehicle — and the regulator said its recent unannounced spot checks covering CCC certification found the problems that triggered the summons \[tool-1-2\].

**「Impact」** Owners of affected models could see their bicycles recalled or return handling change, while the 15 manufacturers face added compliance and product-traceability obligations.

<details><summary>References</summary>
<ul>
<li><a href="https://m.hz.bendibao.com/live/117726.shtm">杭州 电 动 自 行 车 新 车 上牌办理指南（条件+材料+流程）- 杭州本地宝</a></li>

</ul>
</details>

**Tags**: `#市场监管`, `#电动自行车`, `#产品质量`, `#召回`, `#行业监管`

---