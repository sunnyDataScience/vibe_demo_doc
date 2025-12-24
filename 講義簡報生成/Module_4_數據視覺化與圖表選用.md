# Module 4：數據視覺化與圖表選用
## 時間：14:00-15:00（60分鐘）

📁 **資料集：Supermarket Sales（繼續使用）- 視覺化分析結果**

---

## 成果預覽
```
【你將完成的視覺化作品】
✅ 分店銷售對比圖
✅ 產品線業績排名
✅ 時間趨勢分析
✅ 客戶類型分析
```

---

## 時間配置
- **14:00-14:20**：圖表類型與應用場景（20分鐘）
- **14:20-14:40**：Matplotlib 基礎概念（20分鐘）
- **14:40-15:00**：Seaborn 進階視覺化（20分鐘）

---

## Part 1：圖表類型與應用場景（20分鐘）

### 圖表選用決策樹
```
要展示什麼？
    ├─比較（Comparison）→ 誰最大？
    │   ├─類別間比較 → 長條圖
    │   ├─時間點比較 → 柱狀圖
    │   └─多維度比較 → 分組長條圖、雷達圖
    │
    ├─趨勢（Trend）→ 如何變化？
    │   ├─單一趨勢 → 折線圖
    │   ├─多重趨勢 → 多線圖
    │   └─累積趨勢 → 面積圖
    │
    ├─分布（Distribution）→ 怎麼分布？
    │   ├─單變數分布 → 直方圖、密度圖
    │   ├─統計分布 → 箱形圖、小提琴圖
    │   └─多變數分布 → 熱力圖
    │
    ├─關係（Relationship）→ 有何關聯？
    │   ├─兩變數關係 → 散點圖
    │   ├─多變數關係 → 散點矩陣
    │   └─相關性 → 相關矩陣熱力圖
    │
    └─組成（Composition）→ 佔比多少？
        ├─靜態組成 → 圓餅圖、甜甜圈圖
        ├─動態組成 → 堆疊面積圖
        └─層級組成 → 樹狀圖、旭日圖
```

### 1. 比較類圖表
```python
# 長條圖：比較不同類別
# 適用：各產品銷量、各地區業績
import matplotlib.pyplot as plt

# 垂直長條圖
plt.bar(categories, values)

# 水平長條圖（類別名稱較長時）
plt.barh(categories, values)

# 分組長條圖（多維度比較）
# 適用：不同分店的各產品銷量
```

**應用場景**
- TOP N 排名（最暢銷產品）
- 分類比較（各部門業績）
- 時點對比（本月 vs 上月）

### 2. 趨勢類圖表
```python
# 折線圖：時間序列變化
# 適用：月銷售趨勢、股價走勢
plt.plot(dates, values)

# 面積圖：累積變化
plt.fill_between(dates, values)
```

**應用場景**
- 銷售趨勢（月/季/年）
- KPI追蹤（日活躍用戶）
- 預測vs實際（計劃vs執行）

### 3. 分布類圖表
```python
# 直方圖：數值分布
# 適用：客戶年齡分布、消費金額分布
plt.hist(data, bins=20)

# 箱形圖：統計分布
# 顯示中位數、四分位數、異常值
plt.boxplot(data)
```

**應用場景**
- 客戶畫像（年齡/收入分布）
- 品質管控（良率分布）
- 風險評估（損失分布）

### 4. 關係類圖表
```python
# 散點圖：兩變數關係
# 適用：價格vs銷量、廣告支出vs收入
plt.scatter(x, y)

# 熱力圖：多變數相關性
# 適用：特徵相關性分析
sns.heatmap(correlation_matrix)
```

**應用場景**
- 因果探索（投入vs產出）
- 異常檢測（離群值識別）
- 聚類分析（客戶分群）

### 5. 組成類圖表
```python
# 圓餅圖：比例組成
# 適用：市場份額、成本結構
plt.pie(sizes, labels=labels)

# 堆疊長條圖：組成變化
# 適用：收入結構變化
```

**應用場景**
- 市佔率分析
- 預算分配
- 產品組合

### 選擇原則
```
【圖表選擇黃金法則】
1. 一圖一重點
   - 不要在一張圖表中塞太多資訊

2. 數據決定圖表
   - 類別資料 → 長條圖
   - 連續資料 → 折線圖
   - 比例資料 → 圓餅圖

3. 受眾決定複雜度
   - 高層：簡單直觀
   - 分析師：詳細完整
   - 大眾：故事導向
```

---

## Part 2：Matplotlib 基礎概念（20分鐘）

### 核心架構理解
```python
# Matplotlib 的層級結構
# Figure（畫布）→ Axes（子圖）→ Plot（圖形元素）

import matplotlib.pyplot as plt

# 創建畫布和子圖
fig, ax = plt.subplots(figsize=(10, 6))

# 繪製數據
ax.plot(x, y)

# 設定標籤
ax.set_title('銷售趨勢分析')
ax.set_xlabel('月份')
ax.set_ylabel('銷售額')

# 顯示圖表
plt.show()
```

### 基本圖表元素
```python
# 完整的圖表應包含
1. 標題（Title）- 說明圖表內容
2. 軸標籤（Labels）- X軸、Y軸說明
3. 圖例（Legend）- 多系列說明
4. 網格（Grid）- 輔助閱讀
5. 註解（Annotation）- 重點標注
```

### 實作：銷售趨勢圖
```python
# 任務：繪製月銷售趨勢
import matplotlib.pyplot as plt
import pandas as pd

# 準備數據
monthly_sales = df.groupby('Month')['Total'].sum()

# 創建圖表
plt.figure(figsize=(12, 6))
plt.plot(monthly_sales.index, monthly_sales.values,
         marker='o', linewidth=2, markersize=8)

# 美化圖表
plt.title('月銷售趨勢分析', fontsize=16, fontweight='bold')
plt.xlabel('月份', fontsize=12)
plt.ylabel('銷售總額', fontsize=12)
plt.grid(True, alpha=0.3)

# 加入數值標籤
for x, y in zip(monthly_sales.index, monthly_sales.values):
    plt.text(x, y, f'{y:,.0f}', ha='center', va='bottom')

plt.show()
```

### 多子圖布局
```python
# 創建2x2的子圖布局
fig, axes = plt.subplots(2, 2, figsize=(15, 10))

# 子圖1：銷售趨勢
axes[0, 0].plot(dates, sales)
axes[0, 0].set_title('銷售趨勢')

# 子圖2：產品分布
axes[0, 1].bar(products, amounts)
axes[0, 1].set_title('產品銷量')

# 子圖3：客戶分布
axes[1, 0].pie(customer_types, labels=labels)
axes[1, 0].set_title('客戶類型')

# 子圖4：分店比較
axes[1, 1].barh(branches, revenues)
axes[1, 1].set_title('分店業績')

plt.tight_layout()
plt.show()
```

### 樣式設定
```python
# 設定整體樣式
plt.style.use('seaborn')  # 使用預設樣式

# 自定義顏色
colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#96CEB4']

# 字體設定（支援中文）
plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']
plt.rcParams['axes.unicode_minus'] = False
```

### Prompt 模板
```
"請用matplotlib繪製[圖表類型]：
- 數據：[數據描述]
- X軸：[欄位名]，標籤為[文字]
- Y軸：[欄位名]，標籤為[文字]
- 標題：[標題文字]
- 加入網格和數值標籤
- 設定圖表大小為(12, 6)"
```

---

## Part 3：Seaborn 進階視覺化（20分鐘）

### 為什麼選擇 Seaborn？
```
【Seaborn 優勢】
✅ 更美觀的預設樣式
✅ 更簡潔的語法
✅ 內建統計功能
✅ 對 Pandas 友善
```

### 統計圖表
```python
import seaborn as sns

# 1. 分類比較圖
# 自動計算平均值和信賴區間
sns.barplot(data=df, x='Branch', y='Total')

# 2. 分布圖
# 顯示分布和密度
sns.histplot(data=df, x='Total', kde=True)

# 3. 箱形圖
# 顯示統計分布
sns.boxplot(data=df, x='Product line', y='Total')

# 4. 小提琴圖
# 結合箱形圖和密度圖
sns.violinplot(data=df, x='Gender', y='Total')
```

### 關係圖表
```python
# 1. 散點圖（帶回歸線）
sns.scatterplot(data=df, x='Quantity', y='Total')
sns.regplot(data=df, x='Quantity', y='Total')

# 2. 配對圖（多變數關係）
sns.pairplot(df[['Total', 'Quantity', 'Unit price']])

# 3. 熱力圖（相關矩陣）
correlation = df.corr()
sns.heatmap(correlation, annot=True, cmap='coolwarm')
```

### 分面圖（FacetGrid）
```python
# 按類別分割子圖
g = sns.FacetGrid(df, col='Branch', row='Gender')
g.map(plt.hist, 'Total')

# 更複雜的分面
g = sns.FacetGrid(df, col='Payment', hue='Gender')
g.map(sns.scatterplot, 'Quantity', 'Total')
g.add_legend()
```

### 實戰案例：完整的視覺化報告
```python
# 創建視覺化儀表板
fig = plt.figure(figsize=(20, 12))

# 1. 分店業績對比
plt.subplot(2, 3, 1)
branch_sales = df.groupby('Branch')['Total'].sum().sort_values()
sns.barplot(x=branch_sales.values, y=branch_sales.index, palette='viridis')
plt.title('分店業績排名')

# 2. 產品線分析
plt.subplot(2, 3, 2)
product_sales = df.groupby('Product line')['Total'].mean().sort_values()
sns.barplot(y=product_sales.index, x=product_sales.values, palette='muted')
plt.title('產品線平均銷售額')

# 3. 時間趨勢
plt.subplot(2, 3, 3)
df['Date'] = pd.to_datetime(df['Date'])
daily_sales = df.groupby('Date')['Total'].sum()
plt.plot(daily_sales.index, daily_sales.values)
plt.xticks(rotation=45)
plt.title('每日銷售趨勢')

# 4. 客戶類型分析
plt.subplot(2, 3, 4)
sns.boxplot(data=df, x='Customer type', y='Total')
plt.title('客戶類型消費分布')

# 5. 支付方式分布
plt.subplot(2, 3, 5)
payment_counts = df['Payment'].value_counts()
plt.pie(payment_counts.values, labels=payment_counts.index, autopct='%1.1f%%')
plt.title('支付方式佔比')

# 6. 性別vs評分
plt.subplot(2, 3, 6)
sns.violinplot(data=df, x='Gender', y='Rating', palette='Set2')
plt.title('性別評分分布')

plt.tight_layout()
plt.show()
```

### Prompt 模板
```
"請用seaborn創建視覺化分析：
1. [圖表類型1]展示[分析目的1]
2. [圖表類型2]展示[分析目的2]
設定配色方案為[palette名稱]
加入統計資訊（平均值/信賴區間）
調整圖表大小和標籤可讀性"
```

---

## 視覺化最佳實踐

### 設計原則
```
【視覺化設計檢查清單】
□ 圖表類型適合數據類型
□ 顏色使用合理（不超過7種）
□ 標籤清晰完整
□ 比例尺正確（Y軸從0開始）
□ 去除不必要的元素（墨水比）
□ 重點突出（使用顏色/大小）
```

### 常見錯誤
1. **圓餅圖濫用**：類別太多（>5個）
2. **3D效果**：扭曲視覺判斷
3. **雙Y軸**：容易誤導
4. **過度裝飾**：喧賓奪主

### 顏色使用指南
- **定性數據**：使用不同色相
- **定量數據**：使用漸變色
- **強調重點**：使用對比色
- **考慮色盲**：避免紅綠組合

---

## 課堂筆記區
（學員可在此記錄重點）

---

## 作業練習
1. 用長條圖比較各分店銷售額
2. 用折線圖展示月度趨勢
3. 用熱力圖分析產品相關性
4. 創建包含4個子圖的儀表板

## 延伸學習
- Plotly：互動式視覺化
- D3.js：網頁視覺化
- Tableau：商業智慧工具
- Power BI：微軟BI平台