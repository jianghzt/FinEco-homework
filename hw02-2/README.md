## HW02-2：房地产公司财务特征

- **学生**：孙睿江 (26317052)
- **题目**：[第二次作业：金融数据分析](https://lianxhcn.github.io/FinEco/exercises/hw-02.html)
- **数据来源**：CSMAR 国泰安数据库，仅供中山大学使用
- **数据期间**：2014–2025 年（作业网页要求 2005–2015，CSMAR 下载接口实际提供 2014–2025）

### 文件说明

| 文件 | 用途 |
|------|------|
| `26317052_孙睿江_HW02-2.ipynb` | 主 Notebook，含全部分析 |
| `data/real_estate_financials.csv` | 合并后的公司-年份财务数据（1781 条） |
| `data/yearly_stats.csv` | 按年-分组汇总的指标统计 |
| `data/company_counts.csv` | 每年各产权类型公司数量 |
| `requirements.txt` | Python 依赖 |

### 复现步骤

1. 从 CSMAR 下载四张表：资产负债表 (FS_Combas)、利润表 (FS_Comins)、股权性质文件 (EN_EquityNatureAll)、上市公司基本信息年度表 (STK_LISTEDCOINFOANL)
2. 将 ZIP 文件放入 `~/Downloads/raw-zip-CSMAR-2014-2025/raw-zip-CSMAR-2014-2025/`
3. `pip install -r requirements.txt`
4. 打开 Notebook，重启内核 → 从头运行

### 产权分类说明

- **国企**：CSMAR `EquityNature` = "国企"
- **非国企**：民营、外资、其他（均归入非国企组）

### CSMAR 字段映射

| 指标 | 公式 | 原始字段 |
|------|------|---------|
| 资产负债率 | 总负债/总资产 | A002000000/A001000000 |
| 银行借款占比 | (短期+长期借款)/总负债 | (A002101000+A002201000)/A002000000 |
| 长期负债占比 | (总负债-流动负债)/总负债 | (A002000000-A002100000)/A002000000 |
| ROA | 净利润/平均总资产 | B002000000/avg(A001000000) |
| ROE | 净利润/平均所有者权益 | B002000000/avg(A003000000) |
| 现金持有比率 | 货币资金/总资产 | A001101000/A001000000 |

**⚠️ 数据不随仓库公开**：CSMAR 数据受版权和学校授权限制，本仓库仅保留已执行的 `.ipynb` 和分析结果。原始 ZIP 和提取后的 CSV 不推送到 GitHub。
