🚅 基于 LLM 与拉姆齐法则的成渝中线高铁差异化定价研究

Research on Differentiated Pricing of Chengdu-Chongqing Middle Line HSR: An Approach Based on LLM-Augmented Utility Function and Ramsey Pricing

![alt text](https://img.shields.io/badge/Python-3.8%2B-blue)


![alt text](https://img.shields.io/badge/LaTeX-Overleaf-green)


![alt text](https://img.shields.io/badge/Course-Transportation%20Economics-orange)

📖 项目简介 (Introduction)

本项目是 《交通运输与经济》 课程的期末研究报告。

针对传统定价模型难以量化“服务舒适度”等隐性指标的痛点，本项目尝试了一种跨学科的解决方案：将**大语言模型（LLM）**引入交通经济学，利用 AI 对真实旅客评论进行语义挖掘，量化服务效用，并结合 Logit 离散选择模型 与 拉姆齐（Ramsey）定价法则，为即将开通的成渝中线高铁制定科学的差异化票价方案。

💡 核心思路 (Methodology)

本项目构建了 "LLM - Logit - Ramsey" 三阶段闭环模型：

数据获取 (Data Mining)：利用 Python 爬虫采集携程、12306 等平台的成渝通道真实旅客评论数据。

参数量化 (LLM Quantification)：调用 Qwen-Plus (通义千问) API，通过 Prompt Engineering 从非结构化文本中提取“舒适度”、“便捷性”、“服务态度”评分，计算综合服务效用指数 (
𝑄
Q
)。

模型测算 (Economic Modeling)：

构建 Logit 模型，测算不同票价下的市场分担率与需求价格弹性 (
𝐸
𝑝
E
p
	​

)。

应用 拉姆齐反弹性法则，在覆盖边际成本的前提下求解社会福利最大化的最优票价。

📂 文件结构 (Structure)
code
Bash
download
content_copy
expand_less
├── code/                        # 核心代码目录
│   ├── step1_llm_analysis.py    # 调用 LLM API 进行评论情感分析与量化
│   ├── step2_build_dataset.py   # 构建离散选择模型所需的训练数据集
│   ├── step3_logit_model.py     # 运行 Logit 回归，计算系数与 WTP
│   ├── step4_elasticity.py      # 测算需求价格弹性
│   └── step5_ramsey_pricing.py  # 求解拉姆齐最优定价并绘图
├── data/                        # 数据文件
│   ├── raw_comments.csv         # 爬取的原始评论数据
│   └── processed_scores.csv     # LLM 评分后的结构化数据
├── paper/                       # 论文源文件
│   ├── main.tex                 # LaTeX 主文件
│   ├── references.bib           # 参考文献
│   └── figures/                 # 生成的图表 (如弹性曲线、定价方案图)
└── README.md                    # 项目说明文档
🚀 快速开始 (Quick Start)
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
📊 关键成果 (Key Findings)

服务价值量化：测算出成渝通道旅客对服务质量的支付意愿 (WTP) 约为 97 元/单位评分。

最优定价建议：

🚅 二等座：建议基准价 180 元（比既有线微涨 17%）。

💎 商务座：建议降价至 360 元（比既有线低 22%），以激活闲置运能。

博弈结论：在双寡头竞争中，成渝中线凭借高 
𝑄
Q
 值壁垒，采取“非价格竞争”策略可实现纳什均衡。

👨‍💻 写在前面 (Personal Note)

作为一个生活在川渝地区的大学生，我对成渝中线高铁充满了期待。

这个项目是我将 《交通运输规划原理》（Logit模型）、《运输经济学》（拉姆齐法则）与 《大数据与人工智能》（爬虫与LLM）多门课程知识进行融合的一次尝试。

虽然目前的模型在样本量和参数标定上还存在局限，但这代表了我从“被动接受知识”到“主动探索问题”的思维跃迁。本项目将长期维护，未来计划：

引入混合 Logit 模型 (Mixed Logit) 考虑个体异质性。

补充节假日与春运期间的特殊样本数据。

如果您发现任何问题，欢迎提 Issue 或 PR，您的指正是我进步的动力！

Last Updated: Jan 2026
