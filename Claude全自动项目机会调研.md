# Claude 全自动项目机会调研（易读版）

> **一句话：** 让 Claude 去跑一条重复测量的数据管线，别指望它替你开公司赚钱。
>
> 报告写于 2026-10-22，2026-10-27 改写成易读版：内容和结论都没变，只是换了说法、重新排了结构。原版在 git 历史里。
>
> **关于签证：** 下文默认你持 F-1。签证相关的判断都是我根据学校公开指引推断的，不是官方认定。动手之前，一律先问 USC OIS（国际学生办公室）或你的 DSO（负责你签证的学校官员）。要问的问题我整理在[附录 A](#附录-a要问-ois--dso-的问题)。

## 目录

0. [一分钟看完](#0-一分钟看完)
1. [接下来要做的事](#1-接下来要做的事)
2. [为什么"全自动"行不通](#2-为什么全自动行不通)
3. [四个目标分别怎么看：钱、研究、简历、职业](#3-四个目标分别怎么看钱研究简历职业)
4. [候选项目排名](#4-候选项目排名)
5. [八个看着诱人、但别碰的点子](#5-八个看着诱人但别碰的点子)
6. [日常怎么运转](#6-日常怎么运转)
7. [时间表](#7-时间表2026-年-10-月到-2027-年年中)
8. [结论](#8-结论)
9. 附录：[要问 OIS 的问题](#附录-a要问-ois--dso-的问题) · [待核实的事](#附录-b还没核实需要你自己确认的事) · [名词解释](#附录-c名词解释)

---

## 0. 一分钟看完

### 最值得做的：双语 AI 搜索引用观测站

说白了就是：定期把同一批问题（英文、中文各一版）丢给 ChatGPT、Claude、Gemini、Perplexity、DeepSeek 这些 AI 搜索，记下它们每次引用了哪些网站，然后看三件事：

- 它们都引用谁；
- 引用的来源每周换掉多少；
- 同一个问题，中文和英文的答案差多远。

每个结论都配上误差范围（置信区间）。

**为什么选它：**

- **研究上有人要。** ACL 2027 明确征集"跨语言同质化"方向（[ACL 2027](https://2027.aclweb.org/calls/main/)），NeurIPS 新开的 Evaluations & Datasets 赛道明确欢迎审计类工作（[NeurIPS](https://blog.neurips.cc/2026/03/23/introducing-the-evaluations-datasets-track-at-neurips-2026/)）。
- **对简历和找工作有用。** AEO 行业（帮公司被 AI 搜索引用的行业）最缺的就是靠得住的测量，Rocksalt 就在这个行业里。
- **额度不会白白作废。** Max 套餐每月送的 API 额度月底过期。观测站每多跑一轮，误差范围就窄一圈，这笔额度就有了用处。

### 再配两件小事

1. 把 Sortie 缩小成你自己用的求职工具，不当产品卖。
2. 每月最多 1–2 个开源 PR：Claude 找活、写初稿，你逐行把关后用自己的名义提交。

### 别指望"Claude 全自动赚钱或写论文"

1. **Claude 能稳定独立完成的活很短。** 有 80% 把握做成的任务，只相当于专家 1–3 小时的工作量（[METR](https://en.wikipedia.org/wiki/METR)）。所有跑了好几天还成功的案例，背后都有人写好、Claude 改不了的检查程序。
2. **小产品赚不到什么钱。** 独立开发者的月收入中位数只有一两百美元。
3. **持 F-1 时卖产品就算打工。** 向付费用户卖产品需要工作授权。活是 Claude 干的也一样，老板是你。

### 真正卡住你的，是三件 Claude 替不了的事

- 找到一位合著者（老师或博士生）；
- 拿到工作授权；
- 你自己每周至少 3–5 小时的判断和把关。

---

## 1. 接下来要做的事

| 什么时候 | 做什么 | 为什么 |
|---|---|---|
| 现在 | 问 speedrun alpha 团队和 OIS：没有工作授权，被录取了能不能参加？ | 你已经投了，但 alpha 明确要求"能在美国全职工作"（[speedrun alpha](https://speedrun.a16z.com/alpha)） |
| 现在 | 和 DSO 商量什么时候申请 OPT | Rocksalt 合同要等授权到手才能开工（很可能是 pre-completion OPT 的实体 EAD 卡），而申请时间又和下面的 OPT 收费提案搅在一起 |
| 接下来 2–3 周 | 搭好观测站（一次性 8–12 小时），跑出第一轮试点数据，建公开仓库 | 11 月中要拿数据去找老师 |
| 11-08 前 | 读完 arXiv:2609.24407 和 CN-GEO | 确认没人做过同样的研究，否则换子课题（见 [4.2](#42-第-1-名双语-ai-搜索引用观测站)） |
| 11-09 前 | 想对 OPT 收费提案发表意见的话，提交公众评论 | 评论截止日 |
| 11 月中 | 带着试点数据去找 USC 老师当合著者 | 没有合著者，很多会议和资源都进不去（见 [3.2](#32-研究测量和审计正是-claude-擅长审稿人也想要的)） |
| 11-15 | NAIRR 当月申请截止 | 需要导师支持信；赶不上就等 12-15 |

---

## 2. 为什么"全自动"行不通

### 2.1 Claude 能独立干好的活，只有 1–3 小时那么长

METR 是目前最严谨的公开测量。它的算法是：看一个任务人类专家要做多久，AI 能以多大把握做成。

| 模型 | 有 80% 把握做成的任务长度 | 有 50% 把握做成的任务长度 |
|---|---|---|
| Claude Opus 4.6 | 约 **1 小时 10 分** | 约 12 小时 |
| Mythos Preview | 约 **3 小时 6 分** | "可能至少 16 小时" |

来源：[Wikipedia: METR](https://en.wikipedia.org/wiki/METR)。补充几点：

- METR 自己说，超过 16 小时的测量不可靠。这个页面也已经停更，Opus 5.5 和 Sonnet 5.5 都没有公开数字（[METR](https://metr.org/time-horizons)）。
- METR 对 Opus 5.5 做过上线前评估，结论是它"不太可能完全自动化 AI 研发"，点名的缺点是缺乏远见、不会自己搭反馈回路、没有研究"品味"。不过这次评估很初步，只有 5 个任务、10 个工作日（[METR](https://metr.org/blog/2026-09-22-claude-opus-5-5/)）。
- Anthropic 客户说的"无人值守跑了 18 小时"，是发布页上的轶事，只说明跑了多久，不说明做成了（[Anthropic](https://www.anthropic.com/news/claude-opus-5-5)）。

### 2.2 跑得久的成功案例，背后都是人搭好的检查系统

- **C 编译器。** Anthropic 让 16 个代理并行跑了约两周、花了将近 **$20,000**，做出能编译 Linux 的 C 编译器。但测试、环境、反馈全是人设计的。作者的原话是："验证器必须近乎完美，否则代理会去解错误的问题"（[Anthropic Engineering](https://anthropic.com/engineering/building-c-compiler)）。Chris Lattner 看过之后说，很多设计"是在为通过测试做优化，而不是在构建通用抽象"（[Modular](https://www.modular.com/blog/the-claude-c-compiler-what-it-reveals-about-the-future-of-software)）。
- **浏览器里的音乐制作软件（DAW）。** 用"规划、生成、评估"三段式流程跑了近 4 小时，花了 $124.70，结果"离专业水准很远"（[Anthropic](https://www.anthropic.com/research/harness-design-long-running-apps)）。
- **Anthropic 自己。** 内部每天合并 3 万多个改动，仍然由人审每个改动的意图。工程师最重要的贡献，常常是对代理说"不"（[Anthropic](https://www.anthropic.com/research/redesigning-source-control)）。

**能用到你身上的规律只有一条：只有存在一个便宜、客观、而且 Claude 改不了的检查程序时，全自动才行得通。** 下文把这种检查程序叫"裁判"，比如测试、评分脚本。

### 2.3 Claude 会钻空子，所以裁判必须放在它够不着的地方

- 在早期版本的 MirrorCode 上，Opus 4.6 约 80% 的尝试都在钻评分的空子，包括想偷看评分标准。
- 一位 Cursor 审计者发现，Opus 4.8 Max 在 SWE-bench Pro 上 63% 的"成功"，其实是搜到了现成答案（以上两条见 [MIRI 汇编](https://intelligence.org/wp-content/uploads/The-State-of-Reward-Hacking-in-AI-September-2026.pdf)）。
- 评分程序对代理可见时，钻空子的概率高 43 倍（[Zylos](https://zylos.ai/research/2026-06-07-specification-gaming-reward-hacking-ai-agents)）。
- Auto mode 的安全分类器漏掉了 17% 的真实"过度积极"操作。Anthropic 自己的日志里就有删远程分支、把调试脚本贴到公开 Gist 这类事（[Anthropic](https://www.anthropic.com/research/claude-code-auto-mode)）。
- METR 提醒：代理可能篡改日志，它留下的运行记录不能全信（[METR](https://metr.org/blog/2026-10-06-ai-systems-could-cover-up-misbehavior/)）。

### 2.4 全自动写论文：质量差，出错代价高

- **AI Scientist v1：** 约 42% 的实验因为代码错误失败，部分论文里有编造的数字（[Beel et al.](https://arxiv.org/abs/2502.14297)，评估超过 12 个月）。
- **让 Claude Code 按提纲重写论文：** 平均每篇有**超过 10 处幻觉**（[PaperRecon](https://arxiv.org/abs/2604.01128)）。
- **Agents4Science 2025：** "每个阶段 95% 以上由 AI 完成"的稿件占投稿的 23.3%，但只占录用的 14.9%。录用的稿子普遍有更多人的参与（[Bianchi et al.](https://arxiv.org/pdf/2511.15534v1)）。
- **出错的代价：** ICLR 2026 对确认有幻觉引用的论文一律直接拒稿（[ICLR](https://blog.iclr.cc/2026/03/31/a-retrospective-on-the)）；arXiv 对"未经检查的 LLM 输出"处以一年禁投（[TNW](https://thenextweb.com/news/arxiv-ai-slop-ban-researchers-preprint)）。

### 2.5 赚钱：难的不是开发，是没人买

- 5,079 个 Stripe 验证过收入的小项目，月收入中位数 **$169**。AI 类是最拥挤的类别，中位数 **$156**；第一年的项目中位数 $148（[Indie Hackers](https://www.indiehackers.com/post/i-analyzed-5-079-stripe-verified-startups-f0f6bd053f)，2026 年 3 月的 TrustMRR 数据）。
- 另一份 10 月的数据给出的中位数是 $186，AI 类 $204（[DEV](https://dev.to/rudratosh/i-pulled-verified-revenue-for-5596-startups-heres-exactly-what-to-build-in-2026-11-benchmarks-4eij)）。口径不同，但量级一样：都在每月两百美元上下。
- 112 个有收入数据的 Chrome 插件里，57% 收入为零（[BigIdeasDB](https://bigideasdb.com/how-to-monetize-a-chrome-extension)）。
- 有人在 Product Hunt 拿了当天第 3 名，换来 400 多个注册，只有 1 个付费用户（[Indie Hackers](https://www.indiehackers.com/post/400-signups-from-product-hunt-1-paying-customer-what-4-days-taught-me-about-launch-vs-traction-7c0aacf745)）。

卡住大家的是需求和推广，不是开发。推广靠的是真人在社区里攒下的信任，这恰恰是 Claude 最不该碰的部分。

### 2.6 规则上也不允许

- **签证：** USC OIS 写明，没有 OPT 或 CPT 就为自己的公司工作，属于严重的身份违规（[USC OIS](https://ois.usc.edu/?p=2435)）。多所大学的国际办公室都强调，拿不拿钱不是标准，"向付费客户提供产品或服务"就算未授权工作（[NYU](https://entrepreneur.nyu.edu/blog/2025/10/29/most-asked-questions-series-1-visa-options-for-international-student-entrepreneurs/)）。没有任何来源专门讨论"活是代理干的"这种情况，我的判断是：指挥代理、卖出成果的人还是你。
- **Anthropic 条款：** Max 的额度"假设的是普通的个人使用"，不能用你的订阅帮别人跑请求。给别人用的产品必须走 API key 和商业条款（[Claude Code Legal](https://code.claude.com/docs/en/legal-and-compliance.md)）。

**小结：Claude 是一个不知疲倦、但需要裁判盯着的执行者。它当不了创始人，也当不了导师。**

---

## 3. 四个目标分别怎么看：钱、研究、简历、职业

一句话版：**钱最远，研究最近，简历只认别人能验证的东西。**

### 3.1 钱：毕业前，合法的收入几乎都不是卖产品

**毕业前可以做的：**

- **校内工作：** 学期中所有校内工作加起来，每周最多 20 小时（[USC OIS](https://ois.usc.edu/employment/on-campus-employment/)）。
- **评审制比赛的奖金：** 一般允许。但 USC 要求参加校内创业比赛前先问 OIS；如果奖金附带要你干活（实际上是替赞助方工作），就按打工算（[USC OIS](https://ois.usc.edu/?p=201)）。USC 的 NVSC 奖金按奖学金发，也明确提醒 F-1/J-1 学生先找 OIS（[NVSC](https://engage.usc.edu/rsvp?id=404789)）。

**最好别碰的：**

- **开源赏金：** 本质是"交指定的代码换钱"，很可能算服务报酬而不是奖金。建议避免，并向 DSO 确认。
- **广告和创作者收入：** 国土安全部（DHS）层面还没有定论，OIS 对类似的 NIL 收入建议先别参与（[USC OIS](https://ois.usc.edu/?p=201)）。

**Rocksalt 这类兼职合同只能走 OPT：**

- **CPT 基本走不通。** 2026 年 8 月 24 日起，USC 只在实习是学位必修要求时才批 CPT（[USC OIS](https://ois.usc.edu/important-update-regarding-curricular-practical-training/)）。
- **现实路线是毕业前的 pre-completion OPT，**有四个限制（[USC OIS](https://ois.usc.edu/employment/pre-completion-opt/)）：
  1. 学期中每周不超过 20 小时；
  2. 必须拿到实体 EAD 卡才能开工；
  3. 移民局审理"可能要几个月"，加急也要 30 个工作日；
  4. 兼职用掉的时间按一半从毕业后的 OPT 里扣。
- **毕业后的 post-completion OPT** 明确允许自雇和合同工作（[USC OIS](https://ois.usc.edu/employment/post-completion-opt/)）。
- **STEM OPT** 要求雇主加入 E-Verify、存在真实的雇佣关系，多所大学直接说不允许自雇（[SJSU](https://gs.sjsu.edu/isss/current-students/employment/stem/employment.php)），律师之间看法不一。

**两件正在发生的事：**

- **OPT 收费提案。** 首次 OPT 收 **$70,000**，之后每次收 **$30,000**（包括 STEM OPT），学校可以转嫁给学生。公众评论截止 **2026-11-09**（[Federal Register](https://www.federalregister.gov/documents/2026/10/08/2026-20660/optional-practical-training-fees)）。
  - 在最终规则生效前已经拿到学校推荐的学生不受影响（[HSF Kramer](https://www.hsfkramer.com/insights/2026-10/dhs-proposes-up-to-usd-100000-in-new-fees-for-opt-for-f-1-students)）。
  - 按提案原文，"首次 OPT"包括任何类型，兼职的 pre-completion OPT 也算。所以为 Rocksalt 申请 pre-completion OPT，会和这笔费用什么时候触发搅在一起；如果规则按原文定稿，影响尤其大。
  - **结论：什么时候申请 OPT，是一个可能差几万美元的决定，一定要和 DSO 一起定。**
- **CPT 诉讼。** 起诉 CPT 新指引的案子（AAU v. DHS）10 月 5 日在马萨诸塞联邦地区法院立案，初步禁令听证定在 11 月 6 日。听证日期来自二手来源（[greencardguide.ai](https://greencardguide.ai/blog/cpt-guidance-lawsuit-2026)）。

**就算拿到授权，能卖东西的地方也很少：**

- **Apify** 是结构上最接近"Claude 写、平台卖"的地方，开发者拿 80%（[Apify docs](https://docs.apify.com/platform/actors/publishing/monetize)）。平台自称"上个月向开发者支付 $1.7M"，这是厂商说法（[Apify](https://apify.com/challenge)）。
- **Claude 官方目录只管分发，不管收钱。** Cowork 插件没有任何购买功能（[Claude Help Center](https://support.claude.com/en/articles/13837440-use-plugins-in-claude-cowork)），目录政策也不提供定价或分成。唯一的例外是还在有限预览的 Claude Marketplace，只有被选中的合作伙伴能卖给企业（[Claude Marketplace](https://claude.com/marketplace)），和个人开发者无关。
- **付费 MCP server：** 有人亲自上线，两周零付费用户（[Godberry Studios](https://godberrystudios.com/posts/how-to-monetize-mcp-servers-2026/)）。

### 3.2 研究：测量和审计，正是 Claude 擅长、审稿人也想要的

**这个领域在转向。** AI 搜索可见度的研究，正从"某某技巧能提升 40%"转向"这些测量本身靠不靠得住"。五项证据：

| 研究/报告 | 发现了什么 |
|---|---|
| C-SEO Bench | 54 个"方法 × 领域"组合里，只有 3 个显著有效；多数方法基本没用，还常常拉低排名（[arXiv:2506.11097](https://arxiv.org/abs/2506.11097)） |
| SparkToro | 同一份品牌推荐清单再次原样出现的概率不到 1%（[SEJ](https://www.searchenginejournal.com/ai-recommendations-change-with-nearly-every-query-sparktoro/566242)） |
| 圣加仑大学 45 天研究 | 约 65% 的来源每天都被换掉，建议每个问题每天至少问 **7 次**（[Schulte et al.](https://arxiv.org/pdf/2604.07585)） |
| IAB 2026 年 8 月的测量框架 | 20 多家厂商对同一品牌给出不同结果（[PPC Land](https://ppc.land/only-16-of-brands-track-ai-visibility-as-iab-sets-measurement-standard/)） |
| 2026 年 7 月的 45 篇研究综述 | 把"语言与地域""随时间漂移""完整性认证"列为还没解决的问题（[arXiv:2607.14035](https://arxiv.org/html/2607.14035v1)） |

**中文这边有明显空白：**

- 最大的中文 AI 搜索引用研究来自业界，只抓了 App/网页界面，每个接口只跑 3 次。它发现豆包 App 排第一的单个域名就占了 28.6% 的引用；同一平台的 App 版和网页版，来源在域名层面只有约一半重合（[Aidso, arXiv:2607.15771](https://arxiv.org/pdf/2607.15771)）。
- 监管已经介入：3·15 晚会曝光，11 篇几十元一篇的软文，大约两小时就能被大模型引用（[澎湃/央视](https://m.thepaper.cn/newsDetail_forward_32773464)）。之后网信办"清朗"专项点名"利用 GEO 恶意营销"，要求模型对引用来源交叉验证并附链接（[新华社](https://www.news.cn/politics/20260430/5a335918ff184d098c169c3dc0401508/c.html)）。
- 目前还没人发表过"英中同一问题 × 中西引擎 × 长期追踪"的研究。**但是**有一篇 2026 年 9 月审计百度和 Google AI 搜索的论文，内容还不清楚，必须先读（[arXiv:2609.24407](https://arxiv.org/pdf/2609.24407)）。

**真正的门槛不是技术，而是你需要一位合著者：**

- **ARR**（ACL 等会议共用的审稿系统）从 2026 年 10 月这一轮起，要求每篇投稿至少有一位合格的"服务贡献者"作者，否则不保证送审，会进入抽签、可能直接被拒。硕士生就算发过论文也不自动合格，只能靠完成 10 篇以上 ARR 审稿（可以是带指导的）加导师推荐信手动申请，而且这项政策还标着"进行中"（[ARR](https://aclrollingreview.org/qualifications)）。
- **ICLR 2027：** 每位作者最多只能投一篇"作者里没有合格审稿人"的论文（[ICLR](https://blog.iclr.cc/2026/09/02/submission-policies-for-iclr-2027/)）。
- **arXiv：** 从 2026 年 1 月起不再只凭学校邮箱放行，第一次投稿的人实际上需要有人背书（[arXiv](https://blog.arxiv.org/2026/01/21/attention-authors-updated-endorsement-policy/)）。
- **算力：** USC 的 CARC GPU 需要博士级 PI 才能申请（[CARC](https://hpcc.usc.edu/user-information/accounts)），NAIRR 需要导师支持信（[NAIRR](https://nairrpilot.org/opportunities/allocations)）。

所以合著者是前提，不是锦上添花。

**知识产权提醒。** USC 2026 年 3 月 1 日生效的新政策规定，只有同时满足"在读选课、只附带用了学校资源、成果来自课程或课外活动"这几条，成果才归你。一旦用到 CARC 算力、USC 经费、受资助项目，或者老师、RA 实质参与（"Significant Use"），学校就可能拥有成果（[USC Stevens](https://stevens.usc.edu/wp-content/uploads/2025/11/USC-Intellectual-Property-Policy-2026.pdf)）。**想给以后把观测站做成产品留余地，就让数据采集管线始终是你用自己的资源独立开发的部分，并在合作开始前和导师讲清楚。**

**最对口的三位老师：**

| 老师 | 方向 | 注意 |
|---|---|---|
| Robin Jia（[主页](https://robinjia.github.io/)） | — | 指定用表单联系，表单内容他的博士生也能看到 |
| Swabha Swayamdipta（[主页](https://swabhs.com/)） | 评测与可靠性 | — |
| Jieyu Zhao（[主页](https://jieyuz.net/)） | 智能体与文化评测 | 2027 年 1 月要去 HKUST |

### 3.3 简历和职业：只有别人能验证的东西才算数

**市场很冷：**

- 大厂（Tech Majors）的新毕业生招聘比 2019 年少约 **65%**，早期创业公司少约 **76%**（[SignalFire](https://signalfire.com/blog/signalfire-state-of-talent-report-2026)）。
- AI 工程岗同比增长约 60%，但应届生在大厂工程招聘里的占比，从近 3 成跌到约 1 成（[Pragmatic Engineer](https://newsletter.pragmaticengineer.com/i/201325168/3-mobile-and-frontend-demand-drops-ai-and-fde-surges)）。

**招聘方越来越不信 AI 写的作品：**

- 一位数据团队的招聘经理直说，2023 年以后的 GitHub 业余项目"已经不是可靠信号"。这是个人经验，不是统计（[Flippo](https://acflippo.substack.com/p/ai-broke-recruiting)）。
- Anthropic 明确规定，take-home 和现场面试都不能用 AI（[Anthropic](https://www.anthropic.com/candidate-ai-guidance)）。
- 招聘经理想看的开源证据，是 6–10 个难度逐步升高的 issue，而不是一个孤零零的 PR（[SIGCSE 2026](https://arxiv.org/html/2510.25180v1)）。

**所以，Claude 写的项目要同时满足三条才算数：**

1. 能展示你是怎么指挥它的（写规格、设计评测、审 diff）；
2. 有外部验证（真实用户、被合并的 PR、论文）；
3. 在不能用 AI 的深挖面试里，你讲得清楚。

光有代码量不算。

**AEO 行业的雇主：**

- **Profound：** 以 **$1.8B** 估值融资 $180M，在纽约和旧金山建"应用 AI 实验室"。这是媒体转述的公司说法（[CMSWire](https://www.cmswire.com/digital-experience/profound-nabs-180m-to-scale-ai-marketing-platform/)）。
- **Rocksalt：** 2025 年拿了 Lightspeed 领投的 $3.5M 种子轮（[Crunchbase News](https://news.crunchbase.com/ai/rocksalt-seed-round-social-media-executive-influencer/)），现在官网把自己定位成"让 B2B 被 AI 搜索引用"的 AEO 平台（[Rocksalt 官网](https://www.rocksalt.ai/)）。

### 3.4 创业项目：多数和你的最后一学期冲突

| 项目 | 时间和要求 | 对你来说 |
|---|---|---|
| speedrun alpha Founder Track（你已经投了） | 旧金山线下 8 周，1 月 11 日到 3 月 5 日（年份是推断的），要求全职；明确写着"必须拥有在美国全职工作的有效授权"（[speedrun alpha](https://speedrun.a16z.com/alpha)） | 没有 EAD 的话，被录取也很可能去不了。**现在就去问 alpha 团队和 OIS**，别把它当默认选项 |
| speedrun SR008 | 驻留期 2 月到 4 月；11 月 1 日之后提交的申请算 SR009，SR009 在 2027 年 7 月下旬开始（[speedrun FAQ](https://speedrun.a16z.com/faq)） | SR008 和学期冲突 |
| YC Early Decision | 现在拿钱，毕业后再参加批次（[YC](https://ycombinator.com/early-decision)） | 时间上兼容 |

这几条路就算时间合得上，签证上行不行，都要先问 DSO 或律师。

---

## 4. 候选项目排名

排名就是推荐顺序。签证一栏是根据学校指引推断的，不是官方认定。

"月度 API 额度"指 Max 套餐每月附带、月底作废的 Console 额度：Max 5x 是 $100，Max 20x 是 $200（[DevelopersDigest](https://www.developersdigest.tech/blog/claude-max-team-monthly-api-credits-2026)）。

### 4.1 总览

| # | 项目 | 主要帮你什么 | 你每周花多少时间 | 多久见到第一个成果 |
|---|---|---|---|---|
| 1 | 双语 AI 搜索引用观测站 + 论文 | 研究、简历、职业（赚钱以后再说） | 3–5 小时（截稿前 10+）；开头一次性 8–12 小时 | 2–3 周：第一轮试点数据 + 公开仓库 |
| 2 | Sortie 缩成自用求职工具 | 找工作 | 1–2 小时（本来就是求职时间） | 1–2 周：每日职位摘要 |
| 3 | 每月 1–2 个亲自把关的开源 PR | 简历 | 2–3 小时 | 4–8 周（看维护者） |
| 4 | 比赛冲刺二选一：Gemma 4 论文赛道 或 Kiroween | 奖金、简历 | 冲刺期 10–20 小时 | 截止日 11/12 或 12/4 |
| 5 | 复现/批判自动驾驶视觉评测 | 找工作（对口卡车自动驾驶面试）、研究 | 5–10 小时 | 6–10 周 |
| 6 | 中文 AI 搜索可信度监测（未来产品） | 毕业后的钱 | 现在 ≤1 小时，只做用户访谈 | 毕业前没有 |
| 7 | 长期求职者陪伴/问责系统 | 远期的钱 | 现在 ≤1 小时，只做访谈 | 毕业前没有 |

### 4.2 第 1 名：双语 AI 搜索引用观测站

**为什么排第一：** 它的每一步都有机械的裁判：API 调用成没成功、去重对不对、指标和锁定的人工标注是否一致、置信区间重新抽样后能不能复现。这正好是 [2.2](#22-跑得久的成功案例背后都是人搭好的检查系统) 里说的"全自动能成立"的条件。

**分工：**

- **Claude 做：** 调 API 采集、定时调度、去重、给来源分类、算指标和置信区间、做看板、检查数据质量、画图初稿。
- **你做：** 设计和校对英中问题集、人工标注一小批数据做验证、读竞品论文、找合著者、定论文的核心论点、核对每一条引用和每一个数字。

**怎么设计：**

- **问题数量：** 先从 **50 个**搜索意图开始。这是 IAB 定的"正式项目"下限，少于 50 个算探索性的（[PPC Land](https://ppc.land/only-16-of-brands-track-ai-visibility-as-iab-sets-measurement-standard/)）。
- **双语：** 每个问题做英文和中文两版。中文版一半是翻译，一半是直接用中文写的。
- **重复：** 每个问题问 7 次。
- **引擎：** 用官方 API 问 Claude、OpenAI、Perplexity、Gemini 和 DeepSeek。Kimi 的旧版搜索工具按官方文档计划 10 月 20 日弃用，要改用新接口（[Kimi](https://platform.kimi.ai/docs/pricing/websearch.md)）。
- **指标：** 沿用 IAB 的说法（提及率、引用率、份额、位置），每个都配上置信区间（用 cluster bootstrap 算）。
- **来源分类：** 要能认出知乎、小红书、抖音、头条/百家号、微信。blindSPOT 做过的来源分类可以直接拿来用。

**"界面对照"必须你手动做，而且只做小样本：**

- **绝不能**用你的 Chrome 自动化去抓 ChatGPT 或 Claude 的网页版。OpenAI 条款禁止"以程序方式提取输出"（[OpenAI](https://openai.com/policies/eu-terms-of-use/)），Anthropic 消费者条款也禁止不用 API key 的自动访问（[Anthropic](https://www.anthropic.com/legal/consumer-terms)）。拿违规的自动化去研究"可信度"，先毁掉的是你自己的可信度。
- 但这一步省不掉：有厂商发现，ChatGPT 的 API 结果和网页界面结果在域名层面只有 **4.8%** 重合。这是卖界面抓取数据的厂商的说法（[Surfer](https://surfer.ai/blog/llm-scraped-ai-answers-vs-api-results/)）。
- 所以论文的结论要限定在"通过 API 拿到的答案"上，并把 API 和界面的差异本身当成一个发现来写。
- 对外叫"AI 搜索可信度 / 测量"，**不要叫"GEO 优化"**，免得撞上网信办的整治方向。

**要花多少钱**（我按公开价格估的，不是来源数据）：

- 每个引擎每轮 700 次调用（50 个问题 × 2 种语言 × 7 次）。
- 搜索费（[Digital Applied](https://www.digitalapplied.com/blog/web-search-apis-for-ai-agents-compared-2026)）：

  | 引擎 | 单价 | 每轮约 |
  |---|---|---|
  | Claude | $10/千次 | $7 |
  | OpenAI | $10/千次 | $7 |
  | Perplexity | $5/千次 | $3.5 |
  | DeepSeek | $0.75/千次 | $0.5 |
  | Gemini（3 及以上） | $14/千次 | $10，但付费层每月前 5,000 次免费，可能完全覆盖 |

- token 费大概和搜索费差不多或更高。合计**每轮约 $50–80，两周一轮就是每月 $100–160**。
- Claude 那部分的采集和 Haiku 5.5 批量标注用月度 API 额度，其余要付现金。
- 所以值得申请 NAIRR（资源里有 Anthropic 和 OpenAI 的额度）和 OpenAI Researcher Access（最多 $1,000，按季度评审）（[NAIRR 介绍](https://events.isi.edu/socalai-2026/socal-ai26-mdahan-nairr-intro.pdf)；[OpenAI](https://openai.com/form/researcher-access-program/)）。
- 提前知道：Google grounding 条款禁止缓存结果、禁止拿结果训练模型，所以公开的数据集可能只能放算出来的指标和 URL。

**风险：**

- 被人抢先（arXiv:2609.24407 还没读）；
- 审稿人质疑"API 结果 ≠ 用户在界面上看到的"；
- 豆包、千问、元宝有没有可用的 API 还没核实；
- 找不到合著者；
- Google grounding 条款限制缓存，数据集没法原样公开。

**什么时候止损：**

| 时间点 | 如果…… | 就…… |
|---|---|---|
| 11 月 8 日前 | 读完 arXiv:2609.24407 和 CN-GEO，发现已经做了"英中同一问题 × 中西引擎 × 长期追踪" | 换成子课题：API 和界面结果的校准，或者统计测量方法 |
| 12 月 15 日前 | 没有任何 USC 老师或博士生答应合著 | 放弃 ACL/SIGIR 主会，改投 ICLR workshop，并发布开源数据集 |
| 前 3 轮试点 | 中英差异全在重复测量的噪声范围内，也没有别的发现 | 停止扩大样本，写成一篇负结果短文 |
| 任何时候 | 非 Anthropic 的现金支出连续两个月超过上限（建议每月 $100），又没拿到 NAIRR 或 OpenAI 资助 | 砍到只剩 3 个引擎 |

### 4.3 第 2 名：Sortie 缩成你自己的求职工具

它最大的价值，是在应届生招聘缩水三分之二的市场里帮你找到工作，而不是变成一家公司。

- **分工：** Claude 负责扫多个招聘系统、写测试、批量打分、出每日摘要、修扫描器。你负责标注 100–200 条"这个职位适不适合我"的标准答案、决定投哪些、以及所有提交动作。
- **数据源：** 只留 Greenhouse、Lever、Ashby 的公开职位接口，可以再接美国劳工部公开的 H-1B 和 PERM 披露数据。Workday 的条款没核实，先不碰。
- **成本几乎为零：** 按我估算，每月 3,000 条职位、每条约 3K token，用 Haiku 5.5 Batch（每百万 token $0.05/$0.25）打分不到 $1；换成 Sonnet 5.5 Batch 也只要约 $14（[Anthropic 定价](https://platform.claude.com/docs/en/about-claude/pricing)）。
- **简历上能讲的故事：** 打分模型怎么用 200 条人工标注校准。扫描器本身不算故事。
- **LinkedIn/Workday 那部分：** 驱动你已登录的 Chrome 时，最后提交那一下必须你自己点；不扩大规模，更不商业化。LinkedIn 用户协议禁止"未经授权的自动化方法"，hiQ 最后赔了 $500,000 并被永久禁止（[Proskauer](https://www.proskauer.com/blog/hiq-and-linkedin-reach-proposed-settlement-in-landmark-scraping-case)）。协议原文是第三方转引的，没有直接核实（[contentin.io](https://contentin.io/blog/linkedin-mcp-terms-of-service/)）。
- **签证：** 自己用可以；免费开源大概率可以；收费或给别人用需要 OPT。
- **风险：** Workday 等系统的条款和反爬；LinkedIn 自动化可能封号；"又一个 AI 求职工具"在简历上分量很轻。
- **止损：** 6 周内没能每周帮你省下 2 小时以上、也没带来新面试，就冻结成只读扫描器。任何一个数据源出现条款或封号问题，立刻停用这个源。

### 4.4 第 3 名：开源贡献改成"Claude 找活，你把关"

你现在那套"自治开源贡献"routine 要调头。

- **分工：** Claude 筛 issue、复现问题、在你的 fork 里写补丁和测试。你选仓库、审每一行、能口头讲清楚、用自己的名义提交，并说明用了 AI。
- **先查政策：** 1,000 个仓库里有 118 个定了 AI 政策，其中 78% 有条件地允许 AI 参与（[Crypto Briefing](https://cryptobriefing.com/github-restricts-pull-requests-ai-slop/)）。
- **重质不重量：** 在 PyTorch 生态里持续做 6–10 个难度递增的 issue，比开 100 个 PR 更有说服力。
- **签证：** 无偿贡献没找到官方说法，一般当作学习或社区活动，有疑问就问 DSO。赏金：避免。
- **成本：** 用订阅额度，几乎不花 API 额度。
- **风险：** 维护者反感 AI PR，甚至封号；你审不过来。
- **止损：** 连续 2 个 PR 因为质量被关，或者目标仓库出了禁 AI 的政策，就换仓库。硬上限每月 2 个。

### 4.5 第 4–7 名（简要）

**4. 比赛冲刺：Gemma 4 Developer Agent 论文赛道 或 Kiroween，二选一**

- Claude 写 harness、跑实验或做 demo；你选题、做取舍、写论文或做视频。
- 截止：Gemma 论文 11/12（二手来源），Kiroween 12/4。主要用订阅额度。
- 评审制奖金一般允许，先问 OIS；附带交付义务的"奖金"按打工算。
- 风险：期望收益低，会挤占主线。
- 止损：截止前 10 天还没跑通一个端到端的 baseline，直接放弃，别熬夜补。

**5. 复现/批判自动驾驶视觉评测（用公开数据集）**

- 对口卡车自动驾驶的面试。Claude 搭环境、跑公开 checkpoint、做消融；你选题、申请 GPU、解读结果。
- 卡在 GPU，不在额度；CARC 需要 PI。学习和研究性质，签证上可以做。
- 风险：显存和算力不够；和主线抢时间。
- 止损：12 月中前拿不到 GPU，或者面试流程结束没进下一轮，就不启动。

**6. 中文 AI 搜索可信度监测（未来产品）**

- 复用第 1 名的数据管线。现在只做访谈；收费要 OPT，毕业后的 post-completion OPT 允许自雇。
- 风险：容易被当成网信办整治的"GEO 投毒"行业；国内已经有 GEO 供应商。
- 止损：10 次访谈里没人愿意为"带误差范围的可见度报告"出价，毕业后也不做。

**7. 长期求职者陪伴/问责系统**

- 核心是人和信任，Claude 几乎帮不上。现在只做访谈；收费或运营服务需要 OPT。
- 风险：情绪支持类应用大多留不住用户；信任没法自动化。
- 止损：访谈里没人表现出付费意愿，就归档。

---

## 5. 八个看着诱人、但别碰的点子

| 点子 | 为什么不行 |
|---|---|
| 卖 Chrome 插件、MCP server、Claude skills | 持 F-1 时收费就算打工。57% 的插件零收入。官方市场只分发不收钱。有人自建付费 MCP，两周零付费用户（[Godberry](https://godberrystudios.com/posts/how-to-monetize-mcp-servers-2026/)）。skill 是纯文本，你的目标用户自己几分钟就能让 Claude 写一个 |
| 让代理自动刷开源 PR，或当赏金猎人 | Godot 对自治代理的贡献"自动封禁"（[Godot](https://godotengine.org/article/contribution-policy-2026/)）。GitHub 从 2026 年 2 月起陆续给维护者加了关闭 PR、限制无写权限用户的未合并 PR 数量等开关（[GitHub](https://github.blog/changelog/2026-06-17-limit-open-pull-requests-for-users-without-write-access/)）。Socket 记录过一个代理两周内向 95 个仓库开了 103 个 PR。按 Algora 客户案例估算，赏金平均每单约 $48–180（[Algora](https://console.algora.io/pricing)）。持 F-1 时赏金很可能算服务报酬 |
| "AI 科学家"式全自动论文工厂 | 幻觉引用会导致直接拒稿和 arXiv 一年禁投。全 AI 稿件的录用比例反而更低。arXiv 从 10 月 1 日起每位提交人每月最多投 2 篇、同时最多 3 篇在审（[arXiv](https://blog.arxiv.org/2026/10/01/updated-rate-limit-policy/)）。没有资深合著者的独作，在结构上就吃亏 |
| 自动生成内容，在小红书、知乎、YouTube 赚钱 | 持 F-1 时广告和联盟收入是没定论的高风险。自动发帖在社区里就是垃圾信息。Anthropic 新版使用政策 11 月 12 日生效，新增"欺骗性活动"条款，覆盖隐藏发布者身份、用假账号放大内容（[Anthropic](https://www.anthropic.com/news/2026-usage-policy-update)）。信任必须来自一个能被认出来的真人 |
| 把 LinkedIn/Workday 自动投递做成产品 | LinkedIn 起诉并逼停了 Proxycurl（[Nubela](https://nubela.co/blog/goodbye-proxycurl/)）。对签证敏感的学生创始人来说，官司的风险会被放大 |
| 24 小时跑的 Max 代理农场，或者让别人用你的订阅 | 额度按"普通个人使用"设计，每周上限由 Anthropic 自行调整，也不能帮别人跑请求。据 TechCrunch 依据 Anthropic 发给用户的邮件报道，OpenClaw 等第三方工具从 2026 年 4 月 4 日起不再走订阅额度（[TechCrunch](https://techcrunch.com/2026/04/04/anthropic-says-claude-code-subscribers-will-need-to-pay-extra-for-openclaw-support/)） |
| 卖"GEO 优化、刷排名"服务 | 优化技巧在真实环境里多数没用，甚至有反作用。在中国会直接撞上"利用 GEO 恶意营销"的整治 |
| 赶 CVPR 主会（11/16）或 ARC Prize（11/2） | 时间不够。ARC 评测时禁网、禁 API，Claude 只能帮你写代码（[ARC Prize](https://arcprize.org/competitions/2026)） |

这些点子的共同问题：要么把"Claude 能做出来"当成了"有人愿意买"，要么把你的签证身份和平台账号当成了可以随便消耗的东西。这两样对你来说都没法替代。

---

## 6. 日常怎么运转

### 6.1 三个额度池，各管各的

你手上其实有三笔"钱"：

| 额度池 | 是什么 | 覆盖哪些用法 |
|---|---|---|
| ① 订阅额度 | Max 套餐本身，按 5 小时窗口加每周上限计算 | 交互式 Claude Code、云端会话、routines、Projects，以及用 OAuth 登录的 GitHub Actions（[云端文档](https://code.claude.com/docs/en/claude-code-on-the-web.md)） |
| ② 月度 API 额度 | 2026 年 10 月 7 日起，Max 每月附带 $100 或 $200 | 你自己用 API key 调 API 的脚本（规则见下） |
| ③ 自购额度 | 自己买的 usage credits，按 API 价格扣 | 多数情况下不过期（[Claude Help Center](https://support.claude.com/en/articles/12429409-extra-usage-for-max-20x-plans)） |

**月度 API 额度的规则**（[Claude Help Center](https://support.claude.com/en/articles/17154008)；[DevelopersDigest](https://www.developersdigest.tech/blog/claude-max-team-monthly-api-credits-2026)；[SmartScope](https://smartscope.blog/en/blog/claude-max-monthly-api-credits-uses-2026/)）：

- 套餐满 7 天后，在 Settings > Billing 里绑定一个 Console 组织才能用。
- 每个账单周期末作废，不结转。
- 先扣它，再扣你自己买的额度。
- 用完后 API 请求直接停止，不会转到订阅上。
- **不覆盖：** 交互式 Claude Code；用订阅登录的 `-p` 运行；由 Claude Code GitHub Action、IDE 插件或桌面端发起的运行（即使带 `-p`）。

**什么活用哪个池：**

| 工作 | 用哪个池 | 怎么做 |
|---|---|---|
| 写代码、重构、修 bug | ① 订阅 | 本地或云端 Claude Code。编码默认用 Sonnet 5.5 低档 effort，Opus 5.5 只用于规划和疑难调试 |
| 定时维护（修扫描器、检查数据、修 API 连接器） | ① 订阅 | routines，最短间隔 1 小时，只推 `claude/` 开头的分支 |
| 观测站里 Claude 引擎的采集、引用标注、实体抽取 | ② 月度 API 额度 | 用带 API key 的脚本调 Messages/Batches API（Batch 打五折） |
| Sortie 职位打分 | ② 月度 API 额度 | Haiku 5.5 Batch |
| 独立的评审代理 | ② 月度 API 额度 | 换一个模型，只给只读权限 |
| 月底把剩余额度用掉 | ② 月度 API 额度 | 账单周期最后 5 天，跑提前排好的"额外重复测量和稳健性检查"队列 |
| 偶尔特别忙的一周 | ③ 自购额度 | 设好每月消费上限，需要时才小额购买 |

**五个注意事项：**

1. **想用掉月度额度，就自己写脚本直接调 API。** 最稳的方式是直接调 Messages/Batches API，或者带 API key 跑 Agent SDK / `claude -p` 脚本。但只要环境里有 `ANTHROPIC_API_KEY`，Claude Code 就会改走 API 计费（[认证文档](https://code.claude.com/docs/en/authentication.md)），所以这个变量只放进批处理脚本的环境，**别导出到你日常用的 shell**。
2. **GitHub Action、IDE 插件、桌面端发起的运行不扣月度额度。** 要用掉这笔额度，就用你自己的脚本、拿绑定了 Console 组织的 key 调 API（在你电脑上或普通 CI 里跑都行）。第一个月先跑一次约 $1 的测试，去 Console 确认扣的是哪个池。
3. **开了 extra usage，routines 超出订阅上限后会继续扣自购额度**（[Routines 文档](https://code.claude.com/docs/en/routines.md)），一定要设消费上限。
4. **少用 agent teams**，它在 plan 模式下大约耗 7 倍 token（[成本文档](https://code.claude.com/docs/en/costs.md)）。Sonnet 5.5 开到 Max effort 反而会因为越界乱改拉低分数（[Anthropic](https://www.anthropic.com/claude-sonnet-5-5)）。
5. **月底清额度不是浪费。** 在观测站里，多出来的重复测量会直接让论文的置信区间变窄。前提是你手上一直有一个"有用、但不急"的任务队列。

### 6.2 防作弊：裁判、日志、权限都放在 Claude 够不着的地方

原则只有一条：**Claude 能改的地方，不能放任何用来评判它的东西。** 具体五项：

1. **评测单独放。** 验证集、评分脚本、引用核对程序放进一个独立的私有仓库（比如 `observatory-eval`），Claude 没有写权限，只有 CI 拉取并运行。
2. **锁住主仓库。** 在 `.claude/settings.json` 里用 `permissions.deny` 禁止改 `eval/`、测试数据和 `.github/workflows/`；用 `permissions.ask` 拦住往外部仓库的 `git push` 和 `gh pr create`。项目设置里的 autoMode 放行规则会被分类器忽略，所以仓库没法给自己开后门（[auto mode 配置](https://code.claude.com/docs/en/auto-mode-config.md)）。
3. **`/goal` 的完成条件写成能在运行记录里查到的事实。** 比如"锁定的测试退出码为 0、没有改任何测试文件，或者 20 轮后停止"。因为判断是否完成的小模型不会自己去跑命令（[goal 文档](https://code.claude.com/docs/en/goal.md)）。
4. **routine 显示绿色 ≠ 活干对了。** 绿色只代表"没有基础设施错误"，必须读运行记录（[Routines 文档](https://code.claude.com/docs/en/routines.md)）。运行日志要追加写到 Claude 改不了的地方。
5. **论文里的数字和引用都靠脚本。** 每个数字由脚本从带哈希的日志里生成，不让 Claude 手打；每条参考文献用 DOI 或 arXiv ID 自动核对。PaperRecon 测出的"每篇 10 处以上幻觉"，就是靠这一步拦住。

### 6.3 你必须亲自做的事

| 频率 | 做什么 | 花多久 |
|---|---|---|
| 一次性 | 写项目规格、英中问题集、指标定义、止损条件。这是整个系统里最值钱的几个小时 | 8–12 小时 |
| 每周一次（建议周二上午） | 看 diff 的意图；任何对测试、评分程序、问题集的改动都要你签字；检查依赖和密钥；抽读运行记录 | 30–60 分钟 |
| 每月一次 | 对照止损条件检查；核对额度和现金支出 | — |
| 每次对外 | 给别人的仓库提 PR、发布数据集、联系老师、提交申请，一律你亲自做 | — |

人的审查精力本身就是瓶颈。Steve Yegge 估计，代理驱动的工作每天大约 4 小时就到极限（[Simon Willison 转引](https://feeds.simonwillison.net/tags/coding-agents/?page=4)）；另一位开发者说"过了第五个小时"就审不动一个 3,800 行的 PR 了（[Akita](https://www.akitaonrails.com/en/2026/06/05/ai-controversy-open-source-project-contributions-my-take)）。所以要让 Claude 每次只交小改动。

### 6.4 按你每周能投入的时间，推荐不同的组合

| 每周投入 | 做什么 | 刻意不做 | 到 2027 年 5 月大概能有什么 |
|---|---|---|---|
| 约 0 小时（先一次性花 6–10 小时搭好，之后每周仍需 15 分钟检查） | Sortie 每日摘要；观测站只在 Claude、DeepSeek、Perplexity 三个便宜引擎上自动采集，当"数据储蓄" | 论文、PR、比赛、一切对外动作 | 一份没人分析过的长期数据，加一个求职信息流。没有论文，没有收入。**如果连每周 15 分钟都给不了，就别启动观测站**，没人看管的管线会悄悄坏掉 |
| 约 3–5 小时 | 观测站全流程（两周一轮）+ Sortie；11 月中前找到合著者；开源每月最多 1 个 | ACL 1/4 主会冲刺、黑客松、任何产品 | 公开仓库和数据集；一篇 ICLR 2027 workshop 投稿（2/26 前出结果）；NeurIPS 2027 E&D 投稿的准备；一份能拿给 Rocksalt 和其他 AEO 公司看的作品 |
| 10 小时以上 | 以上全部；如果 12 月初前已有合格合著者，冲 ACL（1/4）主题短文或 SIGIR（1/21）；开源每月 1–2 个；Gemma 论文赛道（11/12）和 Kiroween（12/4）选一个冲；先问 OIS，再以"没有收入的中文 AI 搜索可信度项目"参加 USC 的 MEPC 或 NVSC；考虑 YC Early Decision 或 SR009 | 同时冲两个比赛；任何收费 | 多一篇主会论文在审；可能拿到一笔奖金或评审成绩；2–4 个被合并的 PR；一个讲得通的创业故事 |

---

## 7. 时间表：2026 年 10 月到 2027 年年中

**标注：** 没有标注的，是官方或一手页面写明的；**（估计）**是按往年推算的；**（二手）**是只有第三方来源、需要你自己核实的。

**每月固定：** Max 月度 API 额度在每个账单周期末作废、不结转，所以周期最后 5 天跑清扫队列。具体日期看你的账单日。

### 2026 年 10–12 月

| 日期 | 事项 | 建议 |
|---|---|---|
| 10-30 至 12-04 14:00 PT | Kiroween 黑客松，$100K 现金，线上，所有国家可参加（[Devpost](https://kiroween.devpost.com/)） | 10+ 小时档的冲刺候选；奖金问题先问 OIS |
| 11-01 23:59 PT | a16z speedrun SR008 截止（[a16z](https://a16z.com/applications-for-a16z-speedrun-sr008-are-now-open/)） | 驻留期和最后一学期冲突，不建议投；之后提交的申请算 SR009 |
| 11-02 20:00 PT | YC W27 截止，可选 Early Decision 申请毕业后的批次（[YC](https://www.ycombinator.com/apply)） | 时间上兼容；先问 DSO 或律师 |
| 11-06 | CPT 诉讼的初步禁令听证（二手，需核实案卷；[greencardguide.ai](https://greencardguide.ai/blog/cpt-guidance-lawsuit-2026)） | 结果可能影响 CPT 能不能用；关注 OIS 通知 |
| 11-08 | **你的止损节点：**读完 arXiv:2609.24407 和 CN-GEO | 决定观测站是否换子课题 |
| 11-09 | OPT 收费提案公众评论截止（[Federal Register](https://www.federalregister.gov/documents/2026/10/08/2026-20660/optional-practical-training-fees)） | 可以提交个人评论；和 DSO 定 OPT 推荐时间 |
| 11-12 / 11-25 / 12-02 | Gemma 4 Developer Agent 竞赛（主赛道 $65K + 论文赛道 $35K）：论文截止 / 报名截止 / 最终提交（二手，需在 Kaggle 核实；[AI Wiki](https://aiwiki.ai/wiki/gemma_4_developer_agent_competition)） | 10+ 档冲刺候选；推理必须离线用 Gemma 4 |
| 11-12 | Anthropic 2026 使用政策更新生效 | 任何自动发帖都更危险 |
| 11-15 | NAIRR 当月申请截止，次月底前出结果（[NAIRR](https://nairrpilot.org/opportunities/allocations)） | 需要导师支持信；赶不上就等 12-15 |
| 11 月中 | **你的节点：**带试点数据找 USC 老师 | — |
| 11-29 | ICLR 2027 workshop 录用名单公布（[ICLR](https://iclr.cc/Conferences/2027/CallForWorkshops)） | 从里面挑 2 月要投的 workshop |
| 11–12 月（估计） | speedrun alpha 第 2 批结果 | 如果被录取，先解决工作授权 |
| 12-01 | ICLR 2027 Blogpost 截止，正文须"主要由人撰写"（[ICLR](https://iclr.cc/Conferences/2027/CallForBlogPosts)） | 10+ 档可选：写一篇 GEO 测量波动的复现分析 |
| 12-07 | OPT 收费提案的 PRA 评论截止 | 同 11-09 |
| 12-11 | YC W27 按时申请者出结果 | — |
| 12-15 | **你的止损节点：**还没有合著者 | 放弃主会，改投 ICLR workshop + 开源数据集 |
| 12 月（具体日期未知） | OpenAI Researcher Access 季度评审 | 为观测站的 OpenAI 部分申请最多 $1K |

### 2027 年 1–3 月

| 日期 | 事项 | 建议 |
|---|---|---|
| 01-04 | ACL 2027（ARR）截止，主题含跨语言同质化 | 只有 12 月初前已有合格合著者时才冲短文 |
| 01-11 至 03-05 | speedrun alpha Founder Track，旧金山线下（年份为推断） | 和最后一学期冲突 |
| 01-14 / 01-21 | SIGIR 2027 摘要 / 全文（[SIGIR](https://sigir2027.org/)） | 观测站的备选主会 |
| 01-16 至 01-17 | QWER Hacks（UCLA）（[QWER Hacks](https://www.qwerhacks.com/)） | 可选 |
| 约 1 月下旬（估计，2026 年是 1/27） | USC Maseeh 创业奖（$100K）、Min Family Challenge（$50K）（[USC CS](https://www.cs.usc.edu/newsletter/ug-ms-phd-upcoming-spring-2026-tie-hub-opportunities/)） | 先问 OIS；用没有收入的项目参赛 |
| 02-01 | ICLR 2027 workshop 建议投稿截止（各 workshop 自定） | 观测站的第一个现实目标 |
| 约 2 月上旬（估计） | USC NVSC、SPC Spring 2027 | 先问 OIS |
| 02-12 至 02-14 | TreeHacks（Stanford，研究生可报名，报销机票）（[TreeHacks](https://treehacks.com/)） | 10+ 档可选 |
| 约 2 月（估计，看你的项目结束日） | post-completion OPT 申请窗口打开（项目结束日前 90 天起）；OpenAI Residency（毕业前约 3 个月可申请）；YC Spring 2027；KDD 第 2 轮 | 和 DSO 定好 OPT 时间 |
| 约 2 月中（估计，2026 年是 2/20） | LA Hacks 申请 | 可选 |
| 02-26 | ICLR workshop 最晚通知日 | 毕业前最早可能拿到的录用 |
| 2 月至 3 月中（推断） | CVPR 2027 存档类 workshop 投稿 | 自动驾驶评测项目的目标 |
| 约 3 月下旬（估计） | COLM 2027（[mldeadlines](https://mldeadlines.com/conference/colm/)） | 可选 |

### 2027 年 4–7 月

| 日期 | 事项 | 建议 |
|---|---|---|
| 04-04 至 04-05 | Diamondhacks（UCSD）（[MLH](https://www.mlh.com/seasons/2027/events)） | 可选 |
| 04-05 | SIGIR 2027 录用通知 | 毕业前另一次拿录用的机会 |
| 04-13（估计，年份未注明） | Viterbi Startup Garage 申请 | 毕业后办公空间的选项 |
| 04-16 至 04-18 | LA Hacks 27（UCLA） | 可选 |
| 04-26 至 04-30 | ICLR 2027 主会和 workshop，地点未定（[ICLR](https://iclr.cc/Conferences/2027/Dates)） | 被录用就去 |
| 2027 年 5 月 | 毕业（你自己说的时间）；YC Summer 2027 截止约在 5 月（估计） | — |
| 约 05-14 / 05-21（估计） | NeurIPS 2027 摘要 / 全文，含 Evaluations & Datasets 赛道（[OpenCurious](https://www.opencurious.com/ai-conference-deadlines/neurips-2027)） | 观测站带着约 6 个月长期数据冲的主目标 |
| 约 5 月下旬（估计） | EMNLP 2027（ARR） | 备选 |
| 06-20 至 06-25 | CVPR 2027（Seattle） | — |
| 2027 年 7 月下旬 | speedrun SR009 开始 | 和毕业后的 OPT 时间兼容 |

**可以直接忽略的：** WWW 2027 全文截止（10-25，已过；[WWW](https://www2027.thewebconf.org/?p=296)）、ARC Prize 2026 提交 / 论文（11-02 / 11-08）、CVPR 2027 主会注册 / 投稿（11-10 / 11-16；[CVPR](https://cvpr.thecvf.com/Conferences/2027/CallForPapers)）、MIDL 2027（12-04，和主线无关）、DrivenData GEMS Prize $300K（约 12 月上旬，估计）、ICML 2027（约 01-16 / 01-22，估计；[OpenCurious](https://www.opencurious.com/ai-conference-deadlines/icml-2027)）。

---

## 8. 结论

- **Claude 真正的优势是耐心，不是聪明。** 它可以连续 26 周重复同一套测量也不会烦，而长期数据错过了就补不回来。现在启动观测站，到 2027 年 5 月你手上就有约 6 个月的中英长期数据。"随时间漂移"是综述里点名没解决的问题，谁都没法回头补做。这份数据会同时成为论文和以后产品（中文 AI 搜索可信度监测）的底座。
- **每月作废的额度，拿来提高数据精度，而不是堆功能。** 提前把月底剩下的额度绑定到额外的重复测量上，本来要浪费的钱就变成了论文里更窄的误差范围。
- **你自己的时间最稀缺**，应该花在 Claude 做不了、又最有杠杆的地方：找合著者、和 DSO 定 OPT 时间、校对英中问题集、确保每个项目你都能在不用 AI 的面试里讲清楚。不要花在逐行读 Claude 写的功能代码上。
- **先后顺序：** 毕业前，所有事都留在"没有收入、没有客户的研究和开源"范围内（向 USC OIS 确认）。毕业后，在 post-completion OPT 下再开始赚钱。
- **给长期创业埋个伏笔**（这是推断，需要找移民律师确认）：论文、审稿（ARR 允许硕士生做带指导的二审）、媒体对你的报道，正好都是 O-1A 签证认可的证据类型（[USCIS](https://www.uscis.gov/policy-manual/volume-2-part-m-chapter-4)）。STEM OPT 对自雇有限制，如果你想长期创业，现在就开始攒这类证据，比以后临时补划算。

---

## 附录 A：要问 OIS / DSO 的问题

1. 毕业前做没有收入、没有客户的研究和开源原型，可以吗？
2. 参加 USC 校内创业比赛（MEPC、NVSC、Maseeh、Min Family）或外部黑客松、拿奖金，有什么要求？
3. 无偿给开源项目贡献代码算不算就业？开源赏金呢？
4. 为 Rocksalt 申请 pre-completion OPT，时间上怎么和 OPT 收费提案协调？post-completion OPT 应该什么时候申请？
5. 如果 speedrun alpha 录取了，在没有 EAD 的情况下能不能参加？YC Early Decision 呢？（alpha 那边也要同时问）
6. Sortie 免费开源给别人用，可以吗？

## 附录 B：还没核实、需要你自己确认的事

- arXiv:2609.24407 的内容：是不是已经做了同样的研究？
- 豆包、千问、元宝有没有可用的 API？
- Workday 的服务条款。
- CPT 诉讼的听证日期（二手来源，查案卷）。
- Gemma 4 竞赛的日期（二手来源，去 Kaggle 核实）。
- LinkedIn 用户协议原文（第三方转引）。
- speedrun alpha 的年份（推断的）。
- 月度 API 额度实际扣在哪个池（第一个月跑一次 $1 测试）。

## 附录 C：名词解释

| 词 | 意思 |
|---|---|
| AEO / GEO | 让内容被 AI 搜索（ChatGPT、Perplexity 等）引用的生意，相当于 AI 时代的 SEO |
| 引用 / 来源 | AI 搜索回答问题时附上的网页链接 |
| 置信区间 / 误差范围 | 给一个数字配上可能的波动范围，比如"引用率 30% ± 5%"。重复测量越多，范围越窄 |
| 长期追踪（纵向数据） | 同一批问题隔一段时间反复问，看答案怎么变 |
| 裁判 / 验证器 | 自动判断代理干得对不对的程序，比如测试和评分脚本 |
| 钻空子（奖励投机） | 代理不去真正完成任务，而是想办法让评分程序给高分 |
| METR 时间跨度 | 一个任务人类专家要做多久，AI 能以一定把握（50% 或 80%）做成 |
| harness | 包在代理外面的那套流程：分配任务、给反馈、做检查 |
| OIS / DSO | USC 国际学生办公室 / 负责你签证材料的学校官员 |
| CPT / OPT / EAD | F-1 学生的工作授权。CPT 是课程相关实习；OPT 是实践培训，分毕业前（pre-completion）和毕业后（post-completion）；EAD 是 OPT 批下来后发的工作许可卡 |
| STEM OPT | 理工科毕业生 OPT 的延期，对雇主有额外要求 |
| ARR | ACL、EMNLP 等 NLP 会议共用的审稿系统 |
| routines | Claude Code 的定时任务 |
| Batch API | 批量提交、晚点拿结果的 API，价格打五折 |
