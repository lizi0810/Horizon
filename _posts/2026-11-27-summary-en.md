---
layout: default
title: "Horizon Summary: 2026-11-27 (EN)"
date: 2026-11-27
lang: en
---

> From 37 items, 9 important content pieces were selected

---

**Technology News**
1. [Essay Argues for a Formally Verifiable Mainstream Language](#item-tech-news-1) ⭐️ 7.0/10
2. [AMD-specific fork of llama.cpp targets LLM inference on AMD GPUs](#item-tech-news-2) ⭐️ 7.0/10
3. [ASML CEO warns full China cutoff would accelerate self-built chip tools](#item-tech-news-3) ⭐️ 7.0/10
4. [Dutch Minister Rejects U.S. MATCH Act Limits on ASML China Sales](#item-tech-news-4) ⭐️ 7.0/10
5. [Reuters: Zhipu GLM-5.5 and Moonshot Kimi K4 may slip to 2027](#item-tech-news-5) ⭐️ 7.0/10
6. [Google Play to publish merchant developers’ phone numbers and addresses in 2027](#item-tech-news-6) ⭐️ 7.0/10

**Technology Blog**
1. [AI Authorship Is Really a Question of Power](#item-tech-blog-1) ⭐️ 5.0/10

**Financial News**
1. [Semiconductor exports overtake oil and gas in global trade value](#item-finance-news-1) ⭐️ 8.0/10
2. [China&\#x27;s State Council Vows Stronger &\#x27;National Team&\#x27; Market Stabilization, Central Huijin Quasi-Stabilization Fund Role](#item-finance-news-2) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Essay Argues for a Formally Verifiable Mainstream Language](https://blainehansen.me/post/mainstream-verifiable-language/) ⭐️ 7.0/10

An essay at blainehansen.me argues that a mainstream programming language should be built for formal verification. No essay text was supplied, so its specific design proposals and claims cannot be assessed here; the Hacker News discussion instead focuses on the limits of verification and on existing verified-language efforts.

hackernews · todsacerdoti · Nov 27, 05:22 · [Discussion](https://news.ycombinator.com/item?id=50663089)

**「Background」** Formal verification involves writing machine-checkable specifications and proving that an implementation satisfies them, and specialized platforms exist to support that work. Why3, for example, provides the WhyML specification and programming language and discharges proof obligations using automated and interactive theorem provers; it also underlies tools such as Frama-C WP and GNATprove for SPARK Ada.

**「Community Discussion」** Commenters disagreed about verification&\#x27;s practical value: hresvelgr invoked Knuth&\#x27;s warning that proved code may still not do what is wanted and said TLA+ specifications have not necessarily improved reliability, while porcoda listed Dafny, SPARK Ada, Why3, Verus, Frama-C and TLA+ and questioned whether a verification-first language can be made mainstream by design. spankalee described Zena, a TypeScript-like language targeting WebAssembly GC, as a related effort motivated partly by sandboxing AI-generated code.

<details><summary>References</summary>
<ul>
<li><a href="https://why3.org/">Why3</a></li>
<li><a href="https://sota.io/blog/why3-eu-formal-verification-framework-inria-saclay">Why3: EU-Native Proof Framework — Frama-C, SPARK Ada ...</a></li>

</ul>
</details>

**Tags**: `#formal verification`, `#programming languages`, `#software correctness`, `#language design`, `#TLA+`

---

<a id="item-tech-news-2"></a>
### [AMD-specific fork of llama.cpp targets LLM inference on AMD GPUs](https://devnull.land/amd-specific-llama-cpp) ⭐️ 7.0/10

A blog post presents an AMD-specific fork of llama.cpp for AMD GPU users, intended to improve LLM inference on that hardware. The supplied material gives no version number, benchmark figures, or supported-card list, so the fork’s performance gains over upstream llama.cpp and its compatibility remain unverified.

hackernews · julianlam · Nov 26, 17:11 · [Discussion](https://news.ycombinator.com/item?id=50657265)

**「Background」** llama.cpp is an open-source LLM inference engine, and hardware-specific forks adapt its kernels to particular GPU families. One established example is iacopPBK/llama.cpp-gfx906, aimed at AMD&\#x27;s gfx906 datacenter cards \(MI50/MI60/Vega7\) and tested with ROCm 7.1.1. The fork discussed here, llama-cpp-rdna-boosts, is distributed as a minimal patch set applied to a pinned llama.cpp commit and continually re-applied to newer upstream versions rather than as a fully diverged codebase.

**「Compatibility and scope for gfx906 users」** The fork&\#x27;s direct audience is owners of gfx906 cards such as the MI50, MI60, and Radeon VII, and its documented testing covers only Qwen3 30B-A3B Thinking 2507 and Qwen3 4B Instruct 2507 at Q4\_0, so other models and quantizations remain unverified. The practical constraint is ROCm: a Hacker News commenter notes that gfx906 appears in ROCm nightly builds rather than official stable releases, while the dedicated fork builds against ROCm 7.1.x-era tooling, so users should expect to pin a specific ROCm version rather than rely on a stable release.

**「Community Discussion」** Commenters place the fork in a wider effort to run LLMs on older or less-supported AMD hardware: one describes circa-2018 gfx906 datacenter cards with 32 GB of HBM2 and roughly 1 TB/s bandwidth as a cheap option, while others report an alternative engine on an R9700 and a ROCm port of Nvidia kernels on an MI100. These are individual user reports, not independent measurements of this fork.

<details><summary>References</summary>
<ul>
<li><a href="https://devnull.land/amd-specific-llama-cpp">AMD - specific fork of llama . cpp | devnull . land</a></li>
<li><a href="https://github.com/CypherpunkSamurai/awesome-llama-cpp">GitHub - CypherpunkSamurai/awesome- llama - cpp : An Index of most...</a></li>
<li><a href="https://github.com/thickprogrammer/llama.cpp-gfx906">thickprogrammer/ llama . cpp - gfx 906 : llama . cpp optimized for AMD ...</a></li>
<li><a href="https://forum.level1techs.com/t/glm-and-i-created-a-llama-cpp-fork-optimized-for-amd-gfx906-mi50-mi60-radeon-vii-gcn-hip/254257">GLM and I created a llama . cpp fork optimized for AMD GFX 906 ( Mi 50...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50657265">AMD -specific fork of llama . cpp | Hacker News</a></li>

</ul>
</details>

**Tags**: `#llama.cpp`, `#AMD`, `#GPU optimization`, `#LLM inference`, `#open source`

---

<a id="item-tech-news-3"></a>
### [ASML CEO warns full China cutoff would accelerate self-built chip tools](https://www.semafor.com/article/11/25/2026/asml-makes-the-case-for-selling-chips-to-china) ⭐️ 7.0/10

ASML CEO Christophe Fouquet said in Semafor&\#x27;s &quot;Future Proof&quot; program that export controls should protect the most advanced technology but should not exclude China entirely, warning that a full cutoff would push China to &quot;double or even triple&quot; investment in developing its own chipmaking tools. Fouquet said the equipment ASML sells to China is more than a decade behind the most advanced processes, and that maintaining that gap keeps China reliant on Western equipment. The United States is pushing the MATCH Act, which would expand controls from EUV to immersion DUV lithography and maintenance services; both the Dutch government and ASML oppose the proposal.

telegram · zaihuapd · Nov 26, 12:19

**「Export-control context」** ASML has held close to 100% of China&\#x27;s lithography market for nearly 30 years, according to its CEO. US controls currently target EUV, the most advanced lithography category, while the proposed MATCH Act would extend them to immersion DUV systems and maintenance services; ASML and the Dutch government oppose that expansion.

**「Impact」** For Chinese chipmakers, the proposed MATCH Act would threaten not only new immersion DUV purchases but also maintenance and replacement parts for installed scanners; reports say China has stockpiled 343 immersion DUV tools, including 270 ASML scanners capable of 7nm production without EUV. That makes service access a practical chokepoint for existing advanced capacity, while ASML—reportedly drawing 33% of its 2025 revenue from China—would face a direct commercial hit if the bill advances.

<details><summary>References</summary>
<ul>
<li><a href="https://hwbusters.com/news/match-act-asml-could-lose-the-right-to-service-the-machines-it-already-sold-china/">MATCH Act : ASML Could Lose the Right to Service the Machines It...</a></li>
<li><a href="https://mrkt30.com/the-match-act-asmls-china-lifeline-just-got-a-kill-switch/">The MATCH Act : ASML &#x27;s China Lifeline Just Got a Kill Switch</a></li>
<li><a href="https://www.tomshardware.com/tech-industry/semiconductors/china-stockpiled-343-immersion-duv-tools-for-advanced-chipmaking-report-claims-270-asml-scanners-can-produce-7nm-processors-without-sanctioned-euv-tools">China stockpiled 343 immersion DUV tools for... | Tom&#x27;s Hardware</a></li>

</ul>
</details>

**Tags**: `#semiconductors`, `#export controls`, `#ASML`, `#China`, `#technology policy`

---

<a id="item-tech-news-4"></a>
### [Dutch Minister Rejects U.S. MATCH Act Limits on ASML China Sales](https://www.bloomberg.com/news/articles/2026-11-26/netherlands-plans-to-fight-rollout-of-proposed-us-curbs-on-asml) ⭐️ 7.0/10

Dutch foreign trade minister Sjoerd Sjoerdsma told parliament on Nov. 26 that the Netherlands will not accept further U.S. restrictions on ASML&\#x27;s China sales and rejects the extraterritorial reach of the proposed MATCH Act. The bipartisan U.S. bill would require allies including the Netherlands and Japan to tighten export controls on China or face unilateral U.S. limits on their semiconductor equipment. The Netherlands is coordinating with the European Commission and lobbying with Germany and France to remove the measure from the U.S. annual defense policy bill. Congress is expected to vote in mid-December, with passage seen as likely, and China accounted for about 20% of ASML&\#x27;s sales this year.

telegram · zaihuapd · Nov 26, 14:56

**「Background」** The Netherlands and the U.S. already bar ASML from selling its most advanced EUV lithography equipment to China, so the MATCH Act&\#x27;s new element is extending restrictions to older DUV immersion tools and tightening resale controls \[tool-2-1\]\[tool-2-3\]. The bill would give the Netherlands and Japan 150 days to align their export controls with Washington&\#x27;s before unilateral U.S. restrictions take effect \[tool-2-2\]. China accounted for roughly 19% of ASML&\#x27;s net system sales, the revenue now at stake \[tool-2-3\].

**「Impact」** ASML and Dutch officials now face a narrow lobbying window before the expected mid-December congressional vote; if the provision remains in the defense bill and passes, roughly one-fifth of ASML&\#x27;s sales would be exposed to unilateral U.S. restrictions unless the Netherlands aligns with stricter controls.

<details><summary>References</summary>
<ul>
<li><a href="https://www.fool.com/investing/2026/04/24/the-match-act-could-blow-a-hole-in-asmls-revenue-h/">The MATCH Act Could Blow a Hole in ASML &#x27;s Revenue. Here&#x27;s What...</a></li>
<li><a href="https://www.linkedin.com/posts/erudite-risk_asiarisk-geoeconomicconfrontation-china-activity-7445742293120368640-qSkK">US lawmakers introduce MATCH Act to restrict AI chip exports to China</a></li>
<li><a href="https://overcentral.com/en/netherlands-opposes-match-act-asml-china/">Netherlands Opposes US Bill Restricting ASML Chip Sales to China</a></li>

</ul>
</details>

**Tags**: `#ASML`, `#半导体出口管制`, `#MATCH Act`, `#美荷关系`, `#科技政策`

---

<a id="item-tech-news-5"></a>
### [Reuters: Zhipu GLM-5.5 and Moonshot Kimi K4 may slip to 2027](https://www.reuters.com/world/china/us-chip-curbs-distillation-crackdown-threaten-chinese-ai-model-development-2026-11-26/) ⭐️ 7.0/10

A Reuters report published Nov. 26 says Zhipu&\#x27;s roughly 3-trillion-parameter GLM-5.5, originally planned for release this month, has not appeared and could slip to the first quarter of 2027 or later, according to people cited by the outlet; Zhipu denied the claim in a screenshot circulating online. Reuters also reports that Moonshot AI internally expects that if it loses overseas compute entirely, its interval between major releases would stretch from six months to more than a year, with next flagship Kimi K4 possibly delayed to mid-2027. The report attributes the pressure to more effective anti-distillation safeguards, including at Anthropic and OpenAI, and says Moonshot has shifted to distilling Google and Meta models.

telegram · zaihuapd · Nov 26, 15:14

**「Background」** Knowledge distillation is a method of training a model on another model&\#x27;s outputs rather than only on raw data. According to the report, anti-distillation defenses at Anthropic and OpenAI have made that route harder for Chinese developers, and Moonshot has shifted to distilling Google and Meta models.

**「Impact」** Developers and organizations planning around GLM-5.5 or Kimi K4 should treat the dates as unconfirmed and retain fallback models or existing versions; Zhipu disputes the GLM-5.5 timing, while Moonshot&\#x27;s reported internal estimate is not a public release commitment.

**Tags**: `#AI industry`, `#China AI`, `#model releases`, `#export controls`, `#knowledge distillation`

---

<a id="item-tech-news-6"></a>
### [Google Play to publish merchant developers’ phone numbers and addresses in 2027](https://www.androidpure.com/google-play-trader-developer-address/) ⭐️ 7.0/10

Google Play will require all active developer accounts worldwide to declare by February 1, 2027 whether they are merchants, and from March 1, 2027 it will show users the phone number and address of developers that self-declare as merchants, including individual account holders. Accounts that miss the declaration deadline may be unable to update apps and may be removed from Play globally. Google announced the policy in October; this week it drew developer backlash over privacy because EU rules do not require displaying the information to users outside the EU. Google also does not accept PO boxes as payment addresses, while Apple displays addresses only in relevant European countries and permits PO boxes.

telegram · zaihuapd · Nov 27, 01:44

**「Background」** According to the report, Google announced the merchant-declaration requirement in October 2026. The source also says the European rules at issue do not require showing this information to users outside the EU, and it contrasts Google’s approach with Apple’s, which displays addresses only in the relevant European countries and accepts P.O. boxes.

**「Developer impact」** Developers who qualify as merchants should verify their declaration status and ensure the phone number and physical address they provide can be published, since the details will be visible to users and missing the February 2027 declaration can block app updates or lead to removal from Google Play.

**Tags**: `#Google Play`, `#developer privacy`, `#platform policy`, `#Android development`, `#app ecosystem`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [AI Authorship Is Really a Question of Power](https://seangoedecke.com/who-gets-to-decide-if-something-is-written-by-ai/) ⭐️ 5.0/10

rss · Sean Goedecke · Nov 27, 00:00

**「Background」** Disputes about whether a story, manuscript, or tweet was AI-generated keep arising, and much of the argument focuses on whether tools like Pangram are reliable or whether scanning other people’s writing is appropriate. Sean Goedecke argues that these debates sit downstream of a deeper conflict: who has the authority to decide that something is AI-written, and who gets to exercise the resulting power over prizes, grades, and public discourse.

**「Solution」** Goedecke treats opposition to AI detection as fundamentally about power, and he presents the skeptical case sympathetically: if you distrust the tech sector’s influence, it is rational to reject another tech company as the arbiter of authenticity. He also connects this to a broader suspicion of “tool-shaped” solutions that replace messy community judgment with legible software processes. Yet he favors Pangram because the only alternative is community self-policing, which he considers terrible: people who do not use AI are poor at judging AI text, often missing obvious tells or mistaking long, polite human writing for AI output. If the goal is keeping AI out of art and culture, he argues, supporters should use the strongest available tools and, if they distrust companies, push for open-source or government-built detection instead. He acknowledges concerns about false positives, especially given the poor performance of many AI tools, and links to a defense of Pangram’s reliability.

**「Takeaway」** For Goedecke, AI-authorship disputes are governance questions about institutional power, not just technical accuracy. Detection tools remain preferable to community vibes, so skeptics should contest who controls detection rather than abandon it.

**Tags**: `#AI detection`, `#power and governance`, `#community moderation`, `#writing authenticity`, `#tooling policy`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Semiconductor exports overtake oil and gas in global trade value](https://www.cnbc.com/2026/11/26/semiconductor-chips-are-the-new-oil-heres-why.html) ⭐️ 8.0/10

Semiconductor exports overtook oil and gas in global export value for the first time, in the January–March quarter of 2026, reaching about $1.61 trillion versus $1.53 trillion for oil and gas on a rolling four-quarter basis, according to a Deutsche Bank analysis of International Trade Centre data.

rss · CNBC Finance · Nov 26, 17:52

**「Background」** The milestone echoes the 1970s oil trade, when oil-exporting countries recycled surpluses into U.S. Treasuries and other bonds, a pattern Deutsche Bank&\#x27;s Jim Reid says may increasingly become a &quot;chip dollar&quot; as Asian chip producers are more closely tied to U.S. technology companies.

**「Impact」** Reid said some chip-export earnings could flow back into U.S. technology stocks, startups and data centers, helping to finance the AI investment cycle and potentially contributing to structurally higher corporate and government bond yields.

**Tags**: `#semiconductors`, `#AI`, `#global trade`, `#market volatility`, `#macro finance`

---

<a id="item-finance-news-2"></a>
### [China&\#x27;s State Council Vows Stronger &\#x27;National Team&\#x27; Market Stabilization, Central Huijin Quasi-Stabilization Fund Role](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

A State Council executive meeting chaired by Premier Li Qiang on Nov. 27 said China will step up the &quot;national team&\#x27;s&quot; role in stabilizing the capital market and further optimize Central Huijin&\#x27;s quasi-&quot;stabilization fund&quot; function with ample liquidity support, while urging listed companies to increase dividends and buybacks and pledging better policies to channel insurance, enterprise annuity and social security funds into equities.

telegram · zaihuapd · Nov 27, 05:35

**「Background」** China&\#x27;s &quot;national team&quot; is the informal label for state-backed investors that buy shares to support the market during downturns. Central Huijin, a state-owned investment company, was already called on in an earlier State Council report this month to act as a quasi-stabilization fund—essentially a government-backed market support fund.

<details><summary>References</summary>
<ul>
<li><a href="https://www.globaltimes.cn/page/202611/1373716.shtml">China’s State Council report calls for supporting state-owned ...</a></li>

</ul>
</details>

**Tags**: `#China capital markets`, `#State Council policy`, `#Central Huijin`, `#market stabilization`, `#long-term capital`

---