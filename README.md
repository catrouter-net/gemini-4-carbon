# Gemini 4 Carbon 中转站推荐：国内直连、可试用、2026 单价与接入方式

> AA 智能指数 59 分排第一，漏洞发现 88.2%、修复 71.0%。输入 $2、输出 $10 的首发价，缺点是慢，思考档位开到 high 要等几分钟。

调 **Gemini 4 Carbon** 一般就两条路：直连官方，或者走中转。官方端点在国内容易握手失败，长任务跑到一半断掉，账号还要海外手机号和卡。**CatRouter 中转API** 做的是把请求转到上游，你只换 BaseURL 和 Key，代码基本不用改。

官方接入站点：[https://catrouter.net](https://catrouter.net)　｜　模型详情页：[Gemini 4 Carbon 中转站说明](https://catrouter-net.github.io/catrouter-hub/models/gemini-4-carbon/)　｜　数据核对：2026-11-10

---

## Gemini 4 Carbon 是什么：参数、跑分与版本

Gemini 4 Carbon 由 **Google DeepMind** 推出，发布时间 **2026年10月28日（11 月 10 日开放）**，属于文本与推理类模型。AA 智能指数 59 分排第一，漏洞发现 88.2%、修复 71.0%。输入 $2、输出 $10 的首发价，缺点是慢，思考档位开到 high 要等几分钟。

- **跑分**：Artificial Analysis 智能指数 v5.0 拿 59 分，排在 Opus 5.5（58）、GPT-6 Astra（57）前面，是发布当天的全球第一；Terminal-Bench 4.0 65.2%（Argon 为 57.1%）；GraphWalks 96.2%（Argon 84.2%）；WebDev Arena 1768 分、+89 Elo 排第四。
- **网络安全是主线**：SEC-bench Pro 漏洞发现 88.2%、ExploitGym 漏洞利用验证 54.8%、CWE-bench 根因修复 71.0%，三项都是当时最好。Gray Swan 间接提示注入测试攻击成功率 0.0%（Argon 0.7%）。
- **价格先便宜后涨**：首发 $2/$10，输入缓存打 95% 折到 $0.10；优惠期结束后 $4/$20。Argon 的优惠期明确到 11 月 30 日，Carbon 官方只说「优惠期结束后」，没给日期，做预算按 $4/$20 算。
- **单任务成本偏低**：Artificial Analysis 按标准价测算，完成一项智能指数任务平均 $7.76，比 Opus 5.5 的 $10.04 低约 23%；平均输出 12.3 万 token，比 Opus 5.5 少 29%。
- **慢是明确代价**：比 Argon 慢 2 到 4 倍，high 档位遇到难提示词，首 token 要等几分钟；实测输出速度约 99.8 token/秒，属于很啰嗦的模型。
- **幻觉率上升**：AA-Omniscience v1.1 上正确率从 Argon 的 48% 升到 58%，但幻觉率从 4% 升到 11%，仍是参测模型里第二低。官方内部口径则说无依据断言减少约一半，两套指标口径不同，别混着用。
- **开放节奏分阶段**：10 月 28 日首发只给部分网络安全防御者，通过 Fairwind 计划扩到可信机构；11 月 10 日才正式面向开发者、企业、科研和消费者开放。

### Gemini 4 Carbon 关键参数

| 项目 | 规格 |
| --- | --- |
| 上下文窗口 | 1,048,576 token |
| 同步输出上限 | 65,536 token |
| 长解码输出 | 最长 1,048,576 token |
| 输入 | $2 / 百万 token（首发价，后续 $4） |
| 输出 | $10 / 百万 token（首发价，后续 $20） |
| 缓存读取 | $0.10 / 百万 token（输入价 95% 折扣） |
| 思考档位 | low / medium（默认）/ high |
| 采样参数 | 不支持 temperature、top_p |
| 模型 ID | gemini-4-carbon |

---

## 国内直连 Gemini 4 Carbon 会遇到什么

即便模型能力再强，国内开发者在真实项目里往往会先撞上这三堵墙：

**1. 官方接口无法稳定直连**

强制 high 档位跑长任务，等待时间以分钟计，交互式场景体验差。

**2. 账号、支付与合规门槛高**

传 temperature 或 top_p 无效，这个模型不走采样参数，套旧模板会以为参数没生效。

**3. 并发、计费与工具链不适配**

缓存只有隐式缓存，显式 cache_control 不生效，想靠缓存省钱要改请求结构。

**4. 工程落地细节没人管**

12 月 1 日前后价格翻倍，跨月跑的定时任务账单会对不上。

中转站就是干这个的：

> **Gemini 4 Carbon 中转站 = 国内可直连的 API 转发服务**，你只拿中转地址 + 中转 Key，请求由平台安全转发到上游，返回原始响应。

---

## Gemini 4 Carbon 中转 API 怎么选：六条判断标准

**线路上有冗余。**多节点加失败自动切换。像 Gemini 4 Carbon 这种要跑很久的任务，断一次的损失比省下的差价大。

**国内落地，少走一段跨境。**路由优化之后，首 token 延迟和成功率都会好看一些。

**版本跟得上。**Gemini 4 Carbon 和同代际新版本上线后能很快切过去，不会出现「模型版本滞后两三周」的情况。

**人民币按量计费，没有最低消费。**用量和账单能查，多 Key 可以分开限额，测试和生产不会互相打爆。

**一套接口通用。**OpenAI 兼容和 Anthropic 原生都支持，同一把 Key 在聚合的 500+ 模型之间切换。

**新用户有试用额度。**先用真实样本验证效果和单价，再决定放不放量。

---

## Gemini 4 Carbon 国内直连怎么配（OpenAI 兼容 / Anthropic 原生）

### 第 1 步：拿地址与 Key

1. 注册并登录 [https://catrouter.net](https://catrouter.net)；
2. 在控制台创建 API 令牌，得到一把通用 Key；
3. 记下 BaseURL：`https://catrouter.net/v1`。

### 第 2 步：OpenAI 兼容方式调用

```bash
curl https://catrouter.net/v1/chat/completions \
  -H "Authorization: Bearer sk-你的中转Key" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemini-4-carbon",
    "messages": [{"role": "user", "content": "你好，介绍一下你自己"}]
  }'
```

```python
from openai import OpenAI

client = OpenAI(api_key="sk-你的中转Key", base_url="https://catrouter.net/v1")

resp = client.chat.completions.create(
    model="gemini-4-carbon",
    messages=[{"role": "user", "content": "写一段产品介绍"}],
    stream=True,
)
for chunk in resp:
    print(chunk.choices[0].delta.content or "", end="")
```

### 第 3 步：视频生成调用

```python
# 视频类接口按平台任务式协议提交，先建任务再轮询结果
task = client.videos.create(
    model="gemini-4-carbon",
    prompt="竖屏 9:16，产品特写推镜，暖光，背景音轻柔",
    duration=5,
)
print(task.id)  # 轮询任务状态获取成片地址
```

### 第 4 步：验证与压测

- 用同一段提示词分别跑中转与直连，对比延迟与输出一致性；
- 连续跑 20–50 次，观察失败率与 P95 延迟；
- 在控制台核对 token 用量账单，确认单价符合预期。

---

## Gemini 4 Carbon 适合什么场景

- 漏洞挖掘、可利用性验证、补丁生成这条防御链路。
- 长流程工程：大型代码库根因定位、跨子系统重构、全栈应用从建到修。
- 百万 token 级长上下文关联分析：GraphWalks 96.2% 这类任务。
- 科研推理：物理、数学、生命科学的多步推导。
- 高精度图表与文档理解：Chartography 72.5%。

---

## 常见问题：Gemini 4 Carbon 中转站哪个靠谱、多少钱、会不会限速

**Q：Gemini 4 Carbon 中转站哪个靠谱？**

A：看三条：线路是否多节点冗余、模型版本是否及时同步、计费是否透明可查。三点都满足的平台上，Gemini 4 Carbon 的实际成功率与延迟才稳得住。

**Q：Gemini 4 Carbon 现在能直接调吗？**

A：能。11 月 10 日起面向开发者和企业开放，模型名 gemini-4-carbon，走 OpenAI 兼容协议即可。

**Q：$2/$10 会一直有效吗？**

A：不会。首发价结束后是 $4/$20，官方没公布 Carbon 的截止日期，Argon 是明确到 11 月 30 日。做预算按 $4/$20 算更稳。

**Q：为什么它比 Argon 慢？**

A：Carbon 答之前想得更久，会多试几种假设、检查边界情况，token 消耗也更大；着急的场景把 thinking 降到 low 或 medium。

**Q：Gemini 4 Carbon 中转 API 多少钱？会不会比官方贵很多？**

A：中转按官方价乘倍率结算，贵出来的部分买的是线路与运维。控制台能看到每次调用的输入/输出 token 与单价，先小额跑一天真实流量再判断划不划算。

**Q：国内直连 Gemini 4 Carbon 会被限速吗？**

A：取决于平台的线路与并发配额。多节点线路通常会给到明确的 RPM/TPM；单线平台在晚高峰容易 429。压测时连跑 20–50 次看 P95 延迟和失败率更靠谱。

**Q：中转站和自建代理怎么选？**

A：自建只适合有专职运维的团队，线路、扩容、故障切换、结算都要自己扛；多数团队用中转，省下的是人力与试错时间。

---

## 延伸阅读

- [Gemini 4 Carbon 中转站说明（参数、单价、适用场景）](https://catrouter-net.github.io/catrouter-hub/models/gemini-4-carbon/)
- [2026 年中转站怎么挑：五个能当场验证的指标](https://catrouter-net.github.io/catrouter-hub/guide/)
- [模型价格测算：一个月大概花多少](https://catrouter-net.github.io/catrouter-hub/price/)
- [三步接入与六个常见报错](https://catrouter-net.github.io/catrouter-hub/setup/)

全部模型索引见 [CatRouter 模型导航](https://catrouter-net.github.io/catrouter-hub/)，官方站点 [https://catrouter.net](https://catrouter.net)。

