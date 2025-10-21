---
layout: post
title: "Langchain多任务处理"
date: 2025-10-21 06:00:00  # 日期必须是当前或过去
tags: [langchain, AI]      # 标签（可多个）
description: "本文详细介绍 AI langchain多任务如何使用"  # 文章描述（用于SEO和列表页）
---

Langchain多任务工具链组合设计。用到的tools（serpApi，llm-math）。使用LCEL构建任务链。
![](./images/WP20251021134052.png)

一、prompt<mark>|</mark>>llm

```python
from langchain.prompts import PromptTemplate
from langchain_community.llms import Tongyi  # 导入通义千问Tongyi模型
import dashscope
import os

# 从环境变量获取 dashscope 的 API Key
api_key = "sk-3fe85fd028ca4b1f44"
dashscope.api_key = api_key
 
# 加载 Tongyi 模型
llm = Tongyi(model_name="qwen-turbo", dashscope_api_key=api_key)  # 使用通义千问qwen-turbo模型

# 创建Prompt Template
prompt = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?",
)

# 新推荐用法：将 prompt 和 llm 组合成一个"可运行序列"（串行）
chain = prompt | llm

# 使用 invoke 方法传入输入
result1 = chain.invoke({"product": "软件开发"})
print(result1)

# result2 = chain.invoke({"product": "广告设计"})
# print(result2)

```
输出

{% capture myfold %}

```txt
### English Names:
1. **CodeNova** – Suggests new, innovative code solutions.
2. **SoftSprint** – Implies speed and agility in software development.
3. **DevCraft** – Highlights craftsmanship in development.
4. **InnoSoft Labs** – Emphasizes innovation in software.
5. **Apex Code** – Conveys top-tier, high-performance development.
6. **NexGen Systems** – Suggests next-generation technology.
7. **LogicBridge** – Represents connecting ideas through smart software.
8. **Vertex Development** – Implies peak performance and precision.

### Bilingual or Chinese-Friendly Names:
1. **智码科技 (Zhì Mǎ Kējì)** – "Smart Code Technology" – blends intelligence and coding.
2. **云创软件 (Yún Chuàng Ruǎnjiàn)** – "Cloud Innovation Software" – great if you focus on cloud-based solutions.
3. **码力无限 (Mǎ Lì Wúxiàn)** – "Limitless Coding Power" – energetic and modern.
4. **软通未来 (Ruǎn Tōng Wèilái)** – "Software Connecting the Future."
5. **启点科技 (Qǐ Diǎn Kējì)** – "Starting Point Technology" – ideal for startups or innovative teams.

### Tips for Choosing:
- Keep it short and easy to pronounce.
- Check domain availability (.com, .cn, etc.).
- Ensure it’s not already trademarked.
- Consider your niche (e.g., mobile apps, enterprise software, AI).
```
{% endcapture %}
{% include fold.html title="展开查看" content=myfold %}

二、

```python 
#!/usr/bin/env python
# coding: utf-8

# In[2]:

import os
from langchain.agents import load_tools
from langchain.agents import initialize_agent
from langchain_community.llms import Tongyi  # 导入通义千问Tongyi模型
from langchain.agents import AgentType
import dashscope

# 你需要在环境变量中添加 OPENAI_API_KEY 和 SERPAPI_API_KEY
#os.environ["OPENAI_API_KEY"] = '*******'
#os.environ["SERPAPI_API_KEY"] = '*******'
# 从环境变量获取 dashscope 的 API Key
api_key = "sk-3fe85fd028ca44"
dashscope.api_key = api_key

# 加载模型
llm = Tongyi(model_name="qwen-turbo", dashscope_api_key=api_key)  # 使用通义千问qwen-turbo模型


# 加载 serpapi 工具 ⚠️这里用的SERPAPI_API_KEY全局变量 
# print(os.getenv("SERPAPI_API_KEY"))
tools = load_tools(["serpapi"])
 
"""
agent：代理类型  
    zero-shot-react-description: 根据工具的描述和请求内容的来决定使用哪个工具（最常用）
    react-docstore: 使用 ReAct 框架和 docstore 交互, 使用Search 和Lookup 工具, 前者用来搜, 后者寻找term, 举例: Wipipedia 工具
    self-ask-with-search 此代理只使用一个工具: Intermediate Answer, 它会为问题寻找事实答案(指的非 gpt 生成的答案, 而是在网络中,文本中已存在的), 如 Google search API 工具
    conversational-react-description: 为会话设置而设计的代理, 它的prompt会被设计的具有会话性, 且还是会使用 ReAct 框架来决定使用来个工具, 并且将过往的会话交互存入内存
"""
# 工具加载后需要初始化，verbose=True 代表打印执行详情
agent = initialize_agent(tools, llm, agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION, verbose=True)
 
# 运行 agent
agent.run("今天是几月几号?历史上的今天有哪些名人出生？")
```

{% capture myfold %}

[log](https://github.com/macRong/macrong.github.io/blob/main/_posts/20251021ailangchain-log.txt)


{% endcapture %}
{% include fold.html title="展开查看" content=myfold %}
