# Module 5：數據分析流程與問題拆解
## 時間：15:00-16:00（60分鐘）

📁 **資料集切換：Online Retail（54萬筆）- RFM分析實戰開始**

---

## 為什麼現在導入大數據集？
```
【切換時機的考量】
✅ 前面已建立信心（處理過1000筆數據）
✅ 展現Python威力（Excel開54萬筆會當機）
✅ RFM分析需要足夠交易歷史
✅ 體驗真實大數據分析場景

【緩解恐懼的方法】
1. 先展示：講師Demo處理54萬筆有多快
2. 漸進式：先取1萬筆練習，確認邏輯對了再跑全部
3. 強調：程式碼幾乎一樣，只是數據量變大
```

---

## 時間配置
- **15:00-15:20**：標準數據分析流程 CRISP-DM（20分鐘）
- **15:20-15:40**：麥肯錫問題拆解與MECE原則（20分鐘）
- **15:40-16:00**：從分析到洞察的轉換（20分鐘）

---

## Part 1：標準數據分析流程 CRISP-DM（20分鐘）

### CRISP-DM 流程框架
```
     ┌─────────────┐
     │商業理解     │←────┐
     └──────┬──────┘     │
            ↓            │
     ┌─────────────┐     │
     │數據理解     │     │
     └──────┬──────┘     │
            ↓            │
     ┌─────────────┐     │
     │數據準備     │     │
     └──────┬──────┘     │
            ↓            │
     ┌─────────────┐     │
     │分析建模     │     │
     └──────┬──────┘     │
            ↓            │
     ┌─────────────┐     │
     │評估結果     │─────┘
     └──────┬──────┘
            ↓
     ┌─────────────┐
     │部署應用     │
     └─────────────┘
```

### 1. 商業理解（Business Understanding）
```
【關鍵問題】
- What：要解決什麼商業問題？
- Why：為什麼要解決這個問題？
- How：成功的標準是什麼？
- Who：誰是利害關係人？

【實例：RFM分析】
問題：如何識別高價值客戶並制定差異化策略？
目標：將客戶分群，提升行銷ROI 20%
成功標準：完成分群並產出可執行策略

【Prompt 模板】
"幫我釐清這個分析專案的商業目標：
背景：[業務背景]
問題：[具體問題]
預期成果：[期望達成什麼]
成功指標：[如何衡量成功]"
```

### 2. 數據理解（Data Understanding）
```python
# 54萬筆數據初探
import pandas as pd

# 讀取大數據
df = pd.read_csv('online_retail.csv')

# 基本資訊
print(f"數據規模：{df.shape}")
print(f"時間範圍：{df['Date'].min()} 到 {df['Date'].max()}")
print(f"客戶數量：{df['CustomerID'].nunique()}")
print(f"產品數量：{df['StockCode'].nunique()}")

# 數據品質初評
missing = df.isnull().sum()
print(f"缺失值情況：\n{missing[missing > 0]}")
```

**Prompt 模板**
```
"探索online_retail數據集：
1. 數據規模和時間跨度
2. 主要欄位的分布
3. 數據品質問題
4. 潛在的分析機會"
```

### 3. 數據準備（Data Preparation）
```python
# RFM分析的數據準備
# R: Recency - 最近購買時間
# F: Frequency - 購買頻率
# M: Monetary - 購買金額

# 計算每個客戶的RFM
import datetime as dt

# 設定分析基準日
snapshot_date = df['Date'].max() + dt.timedelta(days=1)

# 計算RFM指標
rfm = df.groupby('CustomerID').agg({
    'Date': lambda x: (snapshot_date - x.max()).days,  # Recency
    'InvoiceNo': 'count',                              # Frequency
    'TotalAmount': 'sum'                               # Monetary
})
rfm.columns = ['Recency', 'Frequency', 'Monetary']
```

### 4. 分析建模（Modeling）
```python
# RFM分群
# 使用分位數進行分群
rfm['R_Score'] = pd.qcut(rfm['Recency'], 5, labels=[5,4,3,2,1])
rfm['F_Score'] = pd.qcut(rfm['Frequency'].rank(method='first'), 5, labels=[1,2,3,4,5])
rfm['M_Score'] = pd.qcut(rfm['Monetary'], 5, labels=[1,2,3,4,5])

# 合併RFM分數
rfm['RFM_Segment'] = rfm['R_Score'].astype(str) + \
                     rfm['F_Score'].astype(str) + \
                     rfm['M_Score'].astype(str)
```

### 5. 評估結果（Evaluation）
```
【評估檢查點】
□ 結果是否合理？（分群大小、特徵差異）
□ 是否回答了商業問題？
□ 統計顯著性如何？
□ 業務可解釋性如何？
□ 實施可行性如何？
```

### 6. 部署應用（Deployment）
```
【應用方案】
- 行銷策略：針對不同客群的差異化策略
- 系統整合：將模型整合到CRM系統
- 監控機制：定期更新和效果追蹤
- 知識傳遞：培訓業務團隊理解和應用
```

---

## Part 2：麥肯錫問題拆解與MECE原則（20分鐘）

### 麥肯錫七步分析法
```
1. 問題定義 → 2. 問題分解 → 3. 優先排序 → 4. 分析計劃
      ↓
5. 關鍵分析 → 6. 綜合發現 → 7. 溝通建議
```

### MECE原則（相互獨立，完全窮盡）
```
【MECE的核心】
Mutually Exclusive：各部分之間相互獨立，不重疊
Collectively Exhaustive：所有部分合起來完全窮盡，無遺漏

【檢驗方法】
1. 是否有重疊？（同一個事物被歸到多個類別）
2. 是否有遺漏？（某些事物沒有被任何類別涵蓋）
```

### 問題拆解實例：如何提升銷售額？
```
         提升銷售額
              |
    ─────────┼─────────
    |        |        |
增加客戶數 提高客單價 提升購買頻率
    |        |        |
  ──┼──    ──┼──    ──┼──
  |   |    |   |    |   |
新客 舊客  單價 數量  週期 重購
獲取 留存  提升 增加  縮短 提高
```

### 深度拆解：客戶流失問題
```
第一層：客戶流失
├─主動流失（客戶主動離開）
│  ├─產品問題
│  │  ├─品質問題
│  │  ├─功能不足
│  │  └─價格過高
│  ├─服務問題
│  │  ├─客服體驗差
│  │  ├─配送延遲
│  │  └─售後不佳
│  └─競爭問題
│     ├─競品更優
│     ├─轉換成本低
│     └─促銷吸引
└─被動流失（非主觀因素）
   ├─自然流失
   │  ├─需求消失
   │  ├─生命週期結束
   │  └─消費能力下降
   └─技術流失
      ├─支付失敗
      ├─帳號問題
      └─系統錯誤
```

### 假說驅動分析
```python
# 形成假說
假說1 = "新客戶流失主要因為首購體驗不佳"
假說2 = "VIP客戶流失因為缺乏專屬服務"
假說3 = "季節性客戶因為缺乏喚醒機制"

# 設計驗證
# 假說1驗證：分析首購後30天留存率
first_purchase_retention = df.groupby('CustomerID').apply(
    lambda x: calculate_retention(x)
)

# 假說2驗證：比較VIP流失率vs一般客戶
vip_churn = df[df['CustomerType']=='VIP']['ChurnRate'].mean()
normal_churn = df[df['CustomerType']=='Normal']['ChurnRate'].mean()

# 假說3驗證：分析季節性購買模式
seasonal_pattern = df.groupby(['CustomerID', 'Season']).size()
```

### 邏輯樹（Logic Tree）範例
```
問題：轉換率下降10%
         |
    原因分析邏輯樹
         |
    ─────┼─────
    |         |
流量品質    轉換漏斗
    |         |
  ──┼──     ──┼──
  |   |     |   |
來源 定向  頁面 流程
質量 精準  體驗 摩擦
```

### Prompt 模板
```
"使用MECE原則拆解[業務問題]：
1. 識別所有可能的維度
2. 確保維度間相互獨立
3. 驗證是否完全窮盡
4. 建立邏輯樹結構
5. 標注優先級"
```

---

## Part 3：從分析到洞察的轉換（20分鐘）

### What → So What → Now What 框架

#### 1. What - 發生了什麼？
```python
# 描述性發現
"數據顯示：
- 20%的客戶貢獻80%的收入
- 過去3個月客戶流失率上升5%
- 新客戶平均客單價下降15%"

# Prompt 模板
"分析結果顯示了什麼模式和趨勢？
請用數據事實描述發現"
```

#### 2. So What - 這代表什麼？
```python
# 解釋意義
"這意味著：
- 業務高度依賴少數高價值客戶（風險集中）
- 客戶滿意度可能在下降（流失率上升）
- 獲客質量下降或定價策略有問題（客單價降低）"

# Prompt 模板
"這個發現對業務意味著什麼？
有什麼潛在的風險或機會？"
```

#### 3. Now What - 該做什麼？
```python
# 行動建議
"建議行動：
1. 立即：對TOP 20%客戶啟動保留計畫
2. 短期：調查流失原因，改善痛點
3. 長期：優化獲客渠道，提升客戶質量"

# Prompt 模板
"基於這些發現，建議採取什麼行動？
請按優先級和時間維度給出建議"
```

### 洞察品質檢核標準
```
【好的洞察應該具備】
✓ 可行動性（Actionable）
  - 能轉化為具體行動
  - 不是空泛的觀察

✓ 相關性（Relevant）
  - 與業務目標相關
  - 對決策有影響

✓ 新穎性（Novel）
  - 提供新的視角
  - 不是顯而易見的

✓ 可驗證性（Verifiable）
  - 有數據支撐
  - 可以被檢驗
```

### 洞察提煉實戰
```python
# 從RFM分析到洞察
# Step 1: What - 分群結果
rfm_summary = rfm.groupby('RFM_Segment').agg({
    'Recency': 'mean',
    'Frequency': 'mean',
    'Monetary': 'mean',
    'CustomerID': 'count'
})

# Step 2: So What - 識別關鍵客群
champions = rfm[rfm['RFM_Segment'] == '555']  # 最佳客戶
at_risk = rfm[rfm['RFM_Segment'].isin(['255', '355'])]  # 流失風險
new_customers = rfm[rfm['RFM_Segment'].str.startswith('5')]  # 新客戶

print(f"Champions佔比：{len(champions)/len(rfm)*100:.1f}%")
print(f"但貢獻收入：{champions['Monetary'].sum()/rfm['Monetary'].sum()*100:.1f}%")

# Step 3: Now What - 策略建議
strategies = {
    'Champions': '提供VIP服務，交叉銷售高價值產品',
    'At Risk': '立即啟動挽回計畫，提供專屬優惠',
    'New Customers': '優化新手體驗，建立忠誠度計畫',
    'Lost': '分析流失原因，嘗試再激活'
}
```

### 故事化呈現
```
【數據故事三要素】
1. 背景（Context）
   - 為什麼要做這個分析
   - 相關的業務背景

2. 衝突（Conflict）
   - 發現了什麼問題
   - 與預期的差距

3. 解決（Resolution）
   - 如何解決問題
   - 預期的結果

【故事範例】
"我們發現公司80%的收入來自20%的客戶（背景），
但這些高價值客戶的流失率正在上升（衝突），
通過RFM分析和差異化策略，
我們可以降低流失率並提升CLV 30%（解決）"
```

---

## 實戰練習：完整分析流程

### 綜合任務（20分鐘）
```python
# 任務：對54萬筆交易數據執行完整RFM分析

# 1. 商業理解
"""
目標：識別不同價值客戶群，制定差異化策略
成功指標：完成分群並產出可執行建議
"""

# 2. 數據理解
df.info()
df.describe()

# 3. 數據準備
# 清洗、轉換、計算RFM

# 4. 分析建模
# 執行RFM分群

# 5. 評估結果
# 檢查分群合理性

# 6. 產出洞察
# What: 20%客戶貢獻80%收入
# So What: 業務風險集中
# Now What: 啟動VIP保留計畫
```

### Prompt 模板庫
```
"對這54萬筆交易數據：
1. 執行RFM分析
2. 識別關鍵客戶群
3. 分析各群特徵
4. 提供策略建議
5. 產生視覺化報告"
```

---

## 重點總結

### 分析流程口訣
1. **理解**問題本質
2. **拆解**成子問題（MECE）
3. **假說**驅動分析
4. **驗證**with數據
5. **提煉**出洞察
6. **行動**化建議

### 關鍵能力
- 問對問題 > 找對答案
- 邏輯思維 > 技術能力
- 業務理解 > 統計知識

---

## 課堂筆記區
（學員可在此記錄重點）

---

## 延伸學習
- 《金字塔原理》- 邏輯思考與表達
- 《用數據講故事》- 數據視覺化敘事
- McKinsey Problem Solving - 麥肯錫方法論