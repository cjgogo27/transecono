
# 🚅 基于 LLM 与拉姆齐法则的成渝中线高铁差异化定价研究

## 📖 项目简介 (Introduction)

本项目是 《交通运输与经济》 课程的期末研究报告。

针对传统定价模型难以量化“服务舒适度”等隐性指标的痛点，本项目尝试了一种**跨学科**的解决方案：将**大语言模型（LLM）**引入交通经济学，利用 AI 对真实旅客评论进行语义挖掘，量化服务效用，并结合 **Logit 离散选择模型** 与 **拉姆齐（Ramsey）定价法则**，为即将开通的成渝中线高铁制定科学的差异化票价方案。

## 💡 核心思路 (Methodology)

本项目构建了 **"LLM - Logit - Ramsey"** 三阶段闭环模型：

1.  **数据获取 (Data Mining)**：利用 Python 爬虫采集携程、12306 等平台的成渝通道真实旅客评论数据。
2.  **参数量化 (LLM Quantification)**：调用 **Qwen(通义千问)** API，通过 Prompt Engineering 从非结构化文本中提取“舒适度”、“便捷性”、“服务态度”评分，计算综合服务效用指数 ($Q$)。
3.  **模型测算 (Economic Modeling)**：
    *   构建 **Logit 模型**，测算不同票价下的市场分担率与需求价格弹性 ($E_p$)。
    *   应用 **拉姆齐反弹性法则**，在覆盖边际成本的前提下求解社会福利最大化的最优票价。

# 🚀 快速开始 (Quick Start)
1. 环境依赖

本项目基于 Python 3.8+ 开发，需安装以下依赖库：

code
Bash
download
content_copy
expand_less
pip install pandas numpy matplotlib seaborn statsmodels requests scikit-learn
2. 配置 API Key

在 code/step1_llm_analysis.py 中填入你的阿里云 DashScope API Key：

code
Python
download
content_copy
expand_less
API_KEY = "your_api_key_here"
3. 运行模型

按顺序运行代码即可复现论文结果：

code
Bash
download
content_copy
expand_less
python code/step1_llm_analysis.py   # 生成 Q 值
python code/step3_logit_model.py    # 估计参数
python code/step5_ramsey_pricing.py # 输出最终定价方案图
# 📊 关键成果 (Key Findings)

服务价值量化：测算出成渝通道旅客对服务质量的支付意愿 (WTP) 约为 97 元/单位评分。

最优定价建议：

🚅 二等座：建议基准价 180 元（比既有线微涨 17%）。

💎 商务座：建议降价至 360 元（比既有线低 22%），以激活闲置运能。

## 👨‍💻 写在最后 (Personal Note)

这个项目是我将 《交通运输规划原理》（Logit模型）、《运输经济学》（拉姆齐法则）与 《大数据与人工智能》（爬虫与LLM）多门课程知识进行融合的一次尝试。

如果您发现任何问题，欢迎提 Issue 或 PR，您的指正是我进步的动力！

