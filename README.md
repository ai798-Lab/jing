# 镜 jing

给一人公司立的四面镜子。让 AI 用你自己的协作数据，每月认真地审你一次，最后给这个月上一个谥号。

Four mirrors for a company of one. A Claude Code skill that audits you, not your code, from your own AI-collaboration data, and condenses each month into a single posthumous-style character.

**[中文](#中文)** · **[English](#english)**

---

<a id="中文"></a>

## 中文

> 以铜为镜，可以正衣冠；以史为镜，可以知兴替；以人为镜，可以明得失。
> 唐太宗有魏征（他身边那位专职当面说真话的谏臣），一人公司没有。这四面镜子就是给自己立的。

### 它是什么

「镜」是一个 [Claude Code](https://claude.com/claude-code) skill。你和 AI 协作得越多，留下的行为数据就越诚实：几百条 user 消息里藏着你打回产出的真实理由、你的高频批评词、你拍板时的犹豫、你说了没做的每一条「下一步」。这些数据你自己从来不看，它替你看。

每月照一次，输入是本地数据的七层取证：

| 取证层 | 照出什么 |
|---|---|
| 时间与分布 | 时间的真实流向，与你嘴上说的优先级对不对得上 |
| 语言指纹 | 你打回产出的真实理由、高频批评词、拍板方式、说法随时间的漂移 |
| 产出物实检 | 真实完成度（打开逐帧检查，不看清单） |
| 言行差账本 | 说了没做、做了没说、说法漂移 |
| **AI 产出的命运** | 你让 AI 做的东西后来死于何处：被采纳 / 被重做 N 版 / 被扔掉 / 完工后再没打开 |
| **taste diff** | 从打回案例的 v1 与终版对比里，编译出你的品味函数 |
| **协作病理与浪费账本** | 人机界面本身在哪漏水，AI 侧哪些劳动毫无意义，以及每条浪费对应的禁令 |
| **工具存量盘点** | skill / MCP / 插件三类分开算成本，多少是活的。含「自建但从未被自己用过」清单、零调用 MCP 的常驻 schema 开销、hook 每会话注入的无声成本 |
| **踩坑萃取率** | 踩了之后是长记性还是反复踩。萃取与复发交叉出四象限，最值钱的是「已萃取但仍复发」那一格 |
| **判断力指纹** | 唯一照你自己的一层。你的判断力是在变强，还是在被 AI 稀释 |

后六层是 v0.2 新增的：前四层照的是「你做了什么」，后六层第一次照「AI 做了什么、结局如何、你的品味长什么样、你的工具有多少在活着、你的坑有多少变成了资产、以及你自己还在不在判断」。

输出是一份镜鉴：数据速览、环比裁决、四镜成像、作废清单、浪费账本与禁令、共识与分歧、决议与跟踪，末尾为这个月上一字谥号。

### 四面镜子

| 镜 | 照什么 | 一句典型照法 |
|---|---|---|
| 以乔布斯为镜 | 产品力：你做的东西该不该存在 | 如果只许留一件事，留哪件、凭什么？ |
| 以王小波为镜 | 自欺：你有没有在骗自己 | 你一直回避验收的项目是哪个？ |
| 以库布里克为镜 | 完成度：细节配得上野心吗 | 最好的一件产出，经得起逐帧暂停吗？ |
| 以第一性原理为镜 | 事实：剥掉类比和惯性 | 时间分布和你嘴上说的优先级一致吗？ |

（王小波：以反讽和诚实著称的中国作家，毕生的写作主题是人如何不骗自己，所以由他照自欺。）

四镜独立成像，成像前不许看彼此的输出。镜与镜矛盾是特性不是 bug，分歧原样保留进纪要。每面镜子都带失效条件：乔镜对探索期工作降音量，王镜必须带幽默感否则变刻薄，库镜不许对原型要求完美，一原镜对关系、玩、审美只报数据不下结论。

### 它和普通「AI 复盘」的区别

多数复盘产出的是你自己五分钟就能总结出来的东西。镜有八条硬规则防止这件事：

1. **只照见，不安慰**：每条判断必须引用具体证据（某个会话、某个文件、某段数据），说不出证据的意见不进纪要。
2. **本人测试**：交稿前每条观察问一遍「照镜人自己五分钟能总结出这条吗」，能，就删。镜只留有证据的意外。
3. **照人，不只照事**：项目清单是事，镜子照的是人。行为层数据（user 消息流）比元数据（会话数量）值钱一个量级。
4. **对抗复核**：四镜成像后，一个独立复核 agent 专职攻击四镜的证据引用：引文属实吗？解读唯一吗？有没有更平凡的解释？必须回原始文件亲验，不采信转述。
5. **环比裁决**：从第二期起，上期暴露的问题、决议、预测必须逐条判「实质改变 / 无变化 / 恶化」，禁止和稀泥词，边界情况按更差的判。
6. **可证伪预测**：每个大结论附一条对下月具体行为的预测，下次照镜先验预测，预测错了结论降级。
7. **指标的构造效度**：任何自造指标在用它下结论前，先问这个定义会不会让结论变成同义反复。过不了就改名，改名后站不住就删。
8. **越抓眼球的发现，验得越狠**：「与常识相反」是危险信号不是加分项，必须额外亲验并公示记录。

第 7、8 条是被自己的复核打脸打出来的，故事见下。

### 关于「判断力指纹」这一层

这是整个 skill 里最容易做成假指标的一层，所以把它的设计写在这里。

有人会担心：长期用 AI，自己的判断力会不会退化？把这个担忧变成指标的第一直觉，是统计「按你的来」「继续」「好」这类消息的占比。**这个做法是错的**，它把表达成本当成了判断含量。「A」可能是全月最重的一次拍板，长消息也可能零判断。更关键的是，把不该自己做的事交出去是正确分工，**委托不等于退化**。

真正的判据是这一条：

> 「按你的来」本身没问题。「按你的来」之后再也没打开过那个产物，才是问题。

健康的委托和真正的放弃，在消息文本上一模一样，区别只在于**之后有没有回来看**。这把一个不可测的心理状态（有没有在思考），换成了一个可测的行为（有没有回访）。所以核心指标是**放行后的回访率**，不是放行占比。

配三条趋势信号看衰减：打回时自带正样本的比例、回应里引用产物具体细节的比例、追问密度。再配两条反向证据：自己查证与纠正 AI 事实错误的次数（上升则退化假说被证伪），以及一条交叉判定（反驳率下降可能是 AI 变准了，必须和「事后被证明 AI 错了」的次数交叉看）。

**结论纪律**：数据不支持退化就明确写不支持。这一层的价值不在于确认担忧，在于给出一个能逐月跟踪的真指标。

### 谥

谥号：中国古代给帝王将相死后上的一字评价，一个字盖棺定论一生（隋炀帝的「炀」，是这套制度里最狠的差评之一）。镜借这个制度，一个字盖棺定论一个月。

每月末，四镜合议，参照《谥法》传统用字为本月上谥，附出处与理由。比如一个月勤于建造却从不验收，可能得「炀」（去礼远众曰炀）；开线极多劳苦功高但地开了没守，可能得「襄」（辟地有德曰襄、甲胄有劳曰襄）；补上欠账、立住规矩，可以改谥「成」（安民立政曰成）。

次月凭决议执行情况可改谥。谥号的作用不是羞辱，是把一个月压缩成一个字，让你记得住。

### 镜的自知

这个 skill 最重要的部分可能是它对自身局限的声明。八条局限，每条配对应机制，随每次照镜执行，不是免责声明：

| 局限 | 对策 |
|---|---|
| 裁判即同案犯（AI 自审自己参与的产出） | 独立复核 agent 攻击四镜证据 |
| 只照得见 AI 协作面 | 结论声明置信度上限 |
| 负面偏置（越狠显得越深） | 复核专拦「把多数说成全部」 |
| 单月样本无基线 | 基线库逐月落盘，词频必须报环比 |
| 动机归因易越界 | 行为反推心理必须标「推测」 |
| 药方易违反诊断 | 决议必须带外部钩子，否则不准进纪要 |
| 四镜独立是弱独立（共享数据包） | 分歧原样保留，不许调和 |
| 结论缺可证伪性 | 大结论必附下月预测，下期先验预测 |

### 安装与使用

```bash
git clone https://github.com/ai798-Lab/jing.git ~/.claude/skills/jing
```

然后在 Claude Code 里说：

- 「照一下这个月」：全镜（数据收集并行取证 → 四镜隔离成像 → 对抗复核 → 合稿）
- 「照一下这周」：单镜快照，一个 agent 依次过四面镜子，产出精简版
- 「我在浪费生命吗」：也能触发，镜会用数据回答

前置条件与成本，装之前看清楚：

- **数据门槛（最重要）**：镜照的是你的历史行为，刚装 Claude Code 的新用户没有东西可照。建议至少活跃使用 2 至 4 周、积累几百条自己的消息之后再照第一次。数据不足时镜应明确说数据不足，而不是硬凑一份镜鉴。
- **环境**：需要支持个人 skills 目录（`~/.claude/skills/`）的 Claude Code 版本；取证脚本用 python3。
- **memory 是可选数据源**：没开 auto-memory 的用户，「言行差账本」这一层会跳过并在镜鉴里声明，其余三层照常。
- **成本量级**：一次月度全镜要跑约 9 至 10 个 agent（四路取证 + 四镜 + 复核），通常几十分钟、百万 token 量级。建议月末专门跑一次，日常用单镜快照。

首次照镜会和你确认归档目录（镜鉴 HTML 与基线库的落盘处）。

### 隐私

镜不向任何第三方发送数据：没有自己的服务器，不做任何额外上传，镜鉴归档在你指定的本地目录。分析本身由你的 Claude Code 会话完成，会话数据经由模型 API 处理，隐私边界与你日常使用 Claude Code 完全相同。开源的只是方法，不是任何人的数据。

### 两个真实的教训

**第一个：不够深。**这套 skill 的第一版产出被照镜人当场打回：「很多都是我自己能观察到的。」升级后才有了本人测试、语言指纹取证和对抗复核。如果你用它照出来的东西让你觉得「还行，都知道」，那就是镜子失职，应该按这个标准打回它。

**第二个：为了深而超调。**第三次照镜时，四镜交出了一条漂亮的反直觉发现：「人一离场，AI 不减速，AI 加速，自驱返工率从 50% 跳到 97%。」还配了图。

对抗复核回原始数据一查，发现这个指标的定义是「两次写入之间没夹真人消息的比例」。人离场时它必然趋近 100%，这是算术不是发现。更糟的是，那些被称作「返工」的轮次里 74% 在往文件里净增内容，某个文件的全部内容都是通过这些所谓的返工轮次写到盘上的。同一次复核还整条驳回了另外三条观察，查出 7 处假数字。

那一版报告如果直接交出去，会比修正后的版本读起来更精彩。**这就是负面偏置：一面被「不够深」驱动的镜子，有把审视变成表演的激励。**所以现在的镜鉴里有一节叫「作废清单」，专门公示复核驳回了什么。读者有权知道这份纪要差点告诉他什么。

如果你的复核某次零驳回，先怀疑复核在放水，而不是镜子变准了。

---

<a id="english"></a>

## English

> "With bronze as a mirror, one can straighten one's robes; with history as a mirror, one can know the rise and fall of dynasties; with a person as a mirror, one can see one's own gains and losses."
> Emperor Taizong of Tang had Wei Zheng, the minister whose entire job was telling the emperor the truth to his face. A company of one has nobody. These four mirrors are the ones you install for yourself.

### What it is

jing (镜, "mirror") is a [Claude Code](https://claude.com/claude-code) skill. The more you work with AI, the more honest a behavioral record you leave behind: hundreds of user messages containing the real reasons you rejected outputs, your recurring words of criticism, your hesitation at decision points, and every "next step" you promised and never took. You never look at this data. The mirror does.

Once a month, it runs seven layers of forensics over local data:

| Layer | What it reveals |
|---|---|
| Time and distribution | Where your time actually went, and whether that matches your stated priorities |
| Linguistic fingerprint | Why you really reject work, your recurring criticisms, how you decide, how your story drifts |
| Artifact inspection | Real completion quality (opened and inspected frame by frame, not judged from a list) |
| Said-versus-done ledger | Promised but not done, done but never recorded, quietly rewritten history |
| **The fate of AI output** | Where the things you asked for actually died: adopted / redone N times / thrown away / never opened again after completion |
| **Taste diff** | Your taste function, compiled from v1-versus-final diffs of the work you rejected |
| **Collaboration pathology and waste ledger** | Where the human-AI interface leaks, which AI labor was meaningless, and the specific prohibition each waste item implies |
| **Tooling inventory** | Skills, MCP servers and plugins costed separately, and how many are actually alive: the ones you built and never used, the resident schema cost of MCP servers you never call, the silent per-session injection cost of hooks |
| **Pitfall-to-asset rate** | Whether hitting a wall taught you anything. Extraction and recurrence cross into four quadrants; the valuable one is "extracted and still recurring" |
| **Judgment fingerprint** | The only layer that examines you. Is your judgment getting sharper, or being diluted by the AI |

The last six layers are new in v0.2. The first four examine what you did; these six are the first look at what the AI did, how it ended, what your taste looks like written down, how much of your tooling is alive, how many of your mistakes became assets, and whether you are still the one judging.

The output is a mirror report: data overview, month-over-month rulings, four independent mirror readings, a retraction list, the waste ledger with its prohibitions, consensus and disagreements, resolutions with follow-ups, and at the end, one character that names your month.

### The four mirrors

| Mirror | What it examines | A typical question |
|---|---|---|
| Jobs as mirror | Product sense: should this thing exist at all | If you could keep only one thing, which one, and on what grounds? |
| Wang Xiaobo as mirror | Self-deception: are you lying to yourself | Which project have you been avoiding the verdict on? |
| Kubrick as mirror | Craft: do the details deserve the ambition | Does your best work survive a frame-by-frame pause? |
| First principles as mirror | Facts: strip the analogies and inertia | Does your time distribution match your stated priorities? |

(Wang Xiaobo: a Chinese writer famous for irony and ruthless honesty, whose lifelong subject was how people avoid deceiving themselves. That is why he guards this mirror.)

The four mirrors read independently and may not see each other's output before committing their own. Contradiction between mirrors is a feature, not a bug; disagreements are preserved verbatim. Each mirror carries its own failure conditions: the Jobs mirror lowers its voice for exploratory work, the Wang mirror must keep its sense of humor or it turns cruel, the Kubrick mirror may not demand polish from prototypes, and the first-principles mirror reports data only, no verdicts, on relationships, play, and aesthetics.

### How it differs from ordinary "AI retrospectives"

Most retrospectives produce what you could have summarized yourself in five minutes. Eight hard rules prevent that:

1. **Reflect, never console.** Every judgment must cite concrete evidence: a specific session, file, or data range. Opinions without evidence do not enter the report.
2. **The self-test.** Before delivery, every observation gets asked: could the person summarize this themselves in five minutes? If yes, delete it. The mirror keeps only evidenced surprises.
3. **Mirror the person, not just the work.** Project lists are events; the mirror studies you: how you give instructions, why you reject outputs, your verbal tics, how your story drifts over time. Behavioral data is worth an order of magnitude more than metadata.
4. **Adversarial review.** After the four mirrors commit, an independent agent attacks their evidence: are the quotes real? Is the interpretation unique? Is there a more mundane explanation? It must verify against raw files, never against the forensic layer's own summary.
5. **Month-over-month rulings.** From the second session on, every problem, resolution, and prediction from previous reports gets an explicit verdict: substantially changed, unchanged, or worse. No hedging language; borderline cases get the harsher ruling.
6. **Falsifiable predictions.** Every major conclusion ships with a concrete prediction about next month's behavior. The next session verifies predictions first; failed predictions demote their conclusions.
7. **Construct validity of every metric.** Before any home-made metric supports a conclusion, ask whether its definition makes that conclusion a tautology. Fails the test, rename it; still doesn't stand after renaming, delete it.
8. **The more striking the finding, the harder it gets verified.** "Counterintuitive" is a warning sign, not a selling point. Such claims require extra hand-verification against raw data, with the verification log published in the report.

Rules 7 and 8 exist because the mirror's own reviewer caught it cheating. That story is below.

### On the judgment layer

This is the layer most easily turned into a fake metric, so here is its design.

A natural worry: does leaning on AI erode your own judgment? The first instinct is to count messages like "sure, go ahead" and "continue" and call that abdication. **That is wrong.** It mistakes cost of expression for amount of judgment. A single letter "A" can be the heaviest decision of the month; a long message can carry none. And delegating what you should not be doing yourself is correct division of labor. **Delegation is not decay.**

The real criterion is this:

> "Go ahead" is fine. "Go ahead" followed by never opening that artifact again is not.

Healthy delegation and genuine abdication look identical in the message text. The only difference is whether you came back to look. That converts an unmeasurable mental state (were you thinking?) into a measurable behavior (did you return?). So the core metric is **the revisit rate after a green light**, not the share of green lights.

Three trend signals track erosion: the share of rejections that arrive with a positive example attached, the share of responses citing concrete details of the artifact, and question density. Two counter-signals guard against a foregone conclusion: how often you verify things yourself or correct the AI on facts (rising falsifies the decay hypothesis), and a cross-check (a falling rebuttal rate may mean the AI got more accurate, so it must be read against how often the AI later turned out wrong).

**Discipline on conclusions**: if the data does not support decay, say so plainly. The value of this layer is not confirming the worry; it is producing a real metric you can track month over month.

### The posthumous name

In imperial China, an emperor or minister received a posthumous name: one character that passed final judgment on an entire life. Emperor Yang of Sui got 炀 ("yang": neglected his people, abandoned the rites), one of the harshest verdicts the system ever issued. The mirror borrows this institution to pass judgment on a month.

At each month's end the four mirrors deliberate and select one character, following traditional usage from the Shifa (the classical book of posthumous naming), with source and reasoning attached. A month of tireless building with zero verification might earn 炀. A month that opened many fronts with real toil but defended none of the ground might earn 襄 ("xiang": expanded territory with merit, labored in armor). Pay off the debts and establish real rules, and the name can be revised to 成 ("cheng": brought peace and sound governance).

The point of the name is not humiliation. It compresses a month into one character you will actually remember.

### Self-knowledge

The most important part of this skill may be its declared limitations. Eight of them, each paired with a working mechanism that runs at every session, not a disclaimer:

| Limitation | Countermeasure |
|---|---|
| The judge is an accomplice (AI auditing output it helped produce) | Independent adversarial reviewer attacks the evidence |
| Only the AI-facing side of life is visible | Conclusions declare their confidence ceiling |
| Negativity bias (harsher reads as deeper) | Reviewer specifically hunts "most" inflated into "all" |
| A single month has no baseline | Baselines persisted monthly; word frequencies must report deltas |
| Motive attribution overreach | Psychology inferred from behavior must be tagged as speculation |
| The cure can repeat the disease | Resolutions without an external hook may not enter the report |
| Four-mirror independence is weak (shared evidence pack) | Disagreements preserved verbatim, never reconciled |
| Conclusions resist falsification | Every major conclusion ships a testable prediction, verified first next session |

### Install and use

```bash
git clone https://github.com/ai798-Lab/jing.git ~/.claude/skills/jing
```

Then tell Claude Code (Chinese trigger phrases work best; English equivalents in parentheses):

- 「照一下这个月」("mirror this month"): full session, with parallel evidence collection, four isolated mirror readings, adversarial review, and a final report
- 「照一下这周」("mirror this week"): quick snapshot, one agent walks through all four mirrors, condensed output
- 「我在浪费生命吗」("am I wasting my life"): also triggers; the mirror answers with data

Read before installing:

- **Data threshold (matters most).** The mirror reads your history. A fresh Claude Code install has nothing to reflect. Use it actively for 2 to 4 weeks and accumulate a few hundred of your own messages before the first session. With insufficient data the mirror should say so plainly instead of forcing a report.
- **Environment.** Requires a Claude Code version that supports the personal skills directory (`~/.claude/skills/`); evidence scripts use python3.
- **Memory is optional.** Without auto-memory, the "said versus done ledger" layer is skipped and declared in the report; the other three layers run as normal.
- **Cost.** A full monthly session runs about 9 to 10 agents (four evidence collectors, four mirrors, one reviewer), typically tens of minutes and on the order of a million tokens. Run the full session at month's end; use snapshots day to day.

The first session will confirm an archive directory with you (where mirror reports and the baseline file live).

### Privacy

The mirror sends nothing to any third party: no server of its own, no extra uploads, and reports are archived in a local directory you choose. The analysis itself is performed by your own Claude Code session, so your data passes through the model API exactly as it does in your everyday usage; the privacy boundary is identical. What is open-sourced here is the method, never anyone's data.

### Two true lessons

**First: not deep enough.** The first version of this skill had its output rejected on the spot: "Most of this I could have observed myself." Only after that rejection did the self-test, linguistic-fingerprint forensics, and adversarial review exist. If what it shows you feels like "fine, I knew all that," the mirror has failed, and you should reject it by exactly that standard.

**Second: overcorrecting toward depth.** On the third run, the four mirrors delivered a beautiful counterintuitive finding: "When the human leaves, the AI does not slow down. It accelerates. Self-driven rework jumps from 50% to 97%." It even came with a chart.

The adversarial reviewer went back to the raw data and found that the metric was defined as "the share of writes with no human message in between." When the human is away, that share necessarily approaches 100%. That is arithmetic, not a discovery. Worse: 74% of those so-called rework rounds were net-additive, and one file's entire contents had reached disk through them. The same review threw out three more observations outright and caught seven false numbers.

Had that version shipped, it would have read better than the corrected one. **That is negativity bias in the flesh: a mirror driven by "not deep enough" has an incentive to turn scrutiny into performance.** So every report now carries a retraction section that publishes what the review threw out. Readers deserve to know what the report almost told them.

If your review ever comes back with zero rejections, suspect the reviewer of going soft before you conclude the mirror got accurate.

## License

MIT
