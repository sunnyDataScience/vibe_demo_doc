# Module 4：數據視覺化與圖表選用 - 完整簡報設計
## 🎯 45分鐘讓數據說故事

---

## 📊 簡報基本資訊
- **總頁數**：20頁
- **預計時長**：45分鐘
- **設計主色**：活力橙 (#F18F01)
- **輔助色彩**：視覺藍 (#4CC9F0)

---

## 🎬 P1：章節封面 [視覺震撼]
### 版面配置
```
背景：各種圖表類型的半透明疊加
左側：大數字 "4" (透明度 15%)
右側：內容區域
```

### 內容文字
**主標題** (40pt, 橙色)
```
Module 4
數據視覺化與圖表選用
```

**副標題** (24pt)
```
一圖勝千言
讓數據說故事的藝術
```

**本節重點** (20pt, 圖標列表)
```
🎯 圖表選擇：選對圖表類型
🎨 設計原則：美觀且有效
📊 Matplotlib：基礎繪圖
📈 Seaborn：統計視覺化
🎮 互動圖表：動態儀表板
```

### 進度指示
```
[■■■■□□□] Module 4/7
預計時間：45分鐘
```

### 動畫效果
- 圖表輪播展示
- 標題淡入效果

### 講師口述
```
"人類大腦處理視覺資訊的速度
是文字的 60,000 倍！
這堂課教你用圖表說故事。"
```

---

## 🎬 P2：為什麼視覺化重要 [認知科學]
### 版面配置
```
視覺 vs 文字對比
```

### 內容文字
**標題** (32pt)
```
👁️ 視覺的力量
```

**安斯庫姆四重奏**
```
四組數據：完全相同的統計特性
• 平均數 X: 9.0
• 平均數 Y: 7.5
• 相關係數: 0.816
• 迴歸線: y = 3 + 0.5x

但是圖表顯示...
[顯示四個完全不同的散點圖]
完全不同的模式！
```

### 認知優勢
```
📊 視覺化的超能力：
• 發現模式：瞬間看出趨勢
• 識別異常：一眼找到問題
• 理解關係：複雜變簡單
• 記憶深刻：圖像記憶更持久
• 溝通有效：跨越語言障礙
```

### 商業影響
```
💰 視覺化的商業價值：
• 決策速度提升 5 倍
• 理解準確度提高 89%
• 會議時間縮短 24%
• 報告採納率增加 43%

台灣企業現況：
• 70% 仍用 Excel 基本圖表
• 僅 20% 使用專業視覺化
• 10% 有互動式儀表板
```

### 視覺元素
- 安斯庫姆四重奏動態展示
- 統計數字滾動

### 動畫效果
- 數據轉化為圖表動畫
- 效果對比展示

### 講師口述
```
"同樣的數據，不同的圖表，
完全不同的故事。
選對圖表，讓洞察一目了然！"
```

---

## 🎬 P3：圖表選擇決策樹 [核心框架]
### 版面配置
```
互動式決策樹
```

### 內容文字
**標題** (32pt)
```
🎯 如何選擇正確的圖表
```

**決策流程**
```
你想展示什麼？
├─ 比較 (Comparison)
│  ├─ 項目間 → 長條圖、雷達圖
│  └─ 時間上 → 折線圖、面積圖
├─ 分布 (Distribution)
│  ├─ 單變數 → 直方圖、箱形圖
│  └─ 雙變數 → 散點圖、熱力圖
├─ 組成 (Composition)
│  ├─ 靜態 → 圓餅圖、堆疊長條圖
│  └─ 動態 → 堆疊面積圖、瀑布圖
└─ 關係 (Relationship)
   ├─ 相關性 → 散點圖、泡泡圖
   └─ 網絡 → 網絡圖、桑基圖
```

### 圖表類型矩陣
```python
# 圖表選擇指南
chart_guide = {
    '比較大小': ['bar', 'column', 'bullet'],
    '顯示趨勢': ['line', 'area', 'sparkline'],
    '查看分布': ['histogram', 'box', 'violin'],
    '展示比例': ['pie', 'donut', 'treemap'],
    '分析關係': ['scatter', 'bubble', 'heatmap'],
    '地理分析': ['map', 'choropleth', 'flow']
}

# 根據資料特性選圖表
def recommend_chart(data_type, purpose):
    if data_type == 'categorical' and purpose == 'compare':
        return 'bar chart'
    elif data_type == 'time_series' and purpose == 'trend':
        return 'line chart'
    elif data_type == 'numerical' and purpose == 'distribution':
        return 'histogram'
    elif data_type == 'part_to_whole' and purpose == 'composition':
        return 'pie chart'
    else:
        return 'table'
```

### 實例展示
```
案例：月營收分析
• 資料：12 個月的營收數據
• 目的：展示趨勢 + 比較

推薦：
1. 折線圖（主要趨勢）
2. 長條圖（月份比較）
3. 組合圖（趨勢+比較）
```

### 動畫效果
- 決策路徑高亮
- 圖表範例浮現

### 講師口述
```
"記住這個決策樹，
你就能在 10 秒內選對圖表！"
```

---

## 🎬 P4：設計原則 - 少即是多 [美學原理]
### 版面配置
```
好壞對比展示
```

### 內容文字
**標題** (32pt)
```
🎨 圖表設計黃金法則
```

**設計原則**
```
1️⃣ 少即是多 (Less is More)
❌ 過度設計：3D效果、陰影、漸變
✅ 簡潔有力：平面、清晰、重點突出

2️⃣ 資料墨水比 (Data-Ink Ratio)
移除所有不必要的元素
保留傳達資訊的必要部分

3️⃣ 視覺層次 (Visual Hierarchy)
標題 > 主要數據 > 次要資訊 > 註解

4️⃣ 色彩策略
• 最多 5-7 種顏色
• 使用色盲友善配色
• 重點用亮色，背景用淡色

5️⃣ 黃金比例
圖表區域：標籤 = 3:1
留白：內容 = 1:2
```

### 實例改造
```python
import matplotlib.pyplot as plt
import seaborn as sns

# ❌ 不好的圖表
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

# 過度裝飾的圖表
ax1.bar(range(5), [10, 20, 15, 25, 30],
        color=['red', 'blue', 'green', 'yellow', 'purple'],
        edgecolor='black', linewidth=3)
ax1.set_title('Sales Data!!!', fontsize=20, fontweight='bold')
ax1.set_xlabel('Category', fontsize=15)
ax1.set_ylabel('Amount ($$$)', fontsize=15)
ax1.grid(True, linestyle='--', linewidth=2)
ax1.set_facecolor('lightgray')

# ✅ 優化後的圖表
ax2.bar(range(5), [10, 20, 15, 25, 30],
        color='#2E86AB', width=0.6)
ax2.set_title('銷售數據', fontsize=14)
ax2.set_ylim(0, 35)
ax2.spines['top'].set_visible(False)
ax2.spines['right'].set_visible(False)
ax2.set_xlabel('類別')
ax2.set_ylabel('金額')

# 加入數值標籤
for i, v in enumerate([10, 20, 15, 25, 30]):
    ax2.text(i, v + 0.5, str(v), ha='center')

plt.tight_layout()
```

### 色彩心理學
```
🎨 色彩含義：
• 紅色：警告、下降、虧損
• 綠色：成功、上升、獲利
• 藍色：穩定、可信、專業
• 橙色：活力、重點、行動
• 灰色：中性、背景、參考
```

### 動畫效果
- Before/After 滑動對比
- 設計元素逐一優化

### 講師口述
```
"好的圖表像好的設計，
不是無法再加，而是無法再減。"
```

---

## 🎬 P5：Matplotlib 基礎 [工具掌握]
### 版面配置
```
程式碼 + 輸出並排
```

### 內容文字
**標題** (32pt)
```
🔧 Matplotlib：Python 繪圖基石
```

**基本結構**
```python
import matplotlib.pyplot as plt
import numpy as np

# 圖表結構
fig = plt.figure(figsize=(10, 6))  # 畫布
ax = fig.add_subplot(111)          # 子圖

# 或簡化寫法
fig, ax = plt.subplots(figsize=(10, 6))

# 關鍵概念
# Figure: 整個圖表窗口
# Axes: 實際的繪圖區域
# Axis: X軸或Y軸
# Artist: 所有可見元素
```

### 基礎圖表類型
```python
# 準備數據
categories = ['Q1', 'Q2', 'Q3', 'Q4']
values = [25000, 32000, 28000, 35000]

# 1. 長條圖
fig, axes = plt.subplots(2, 3, figsize=(15, 10))

axes[0,0].bar(categories, values, color='steelblue')
axes[0,0].set_title('長條圖')
axes[0,0].set_ylabel('銷售額')

# 2. 折線圖
months = np.arange(1, 13)
sales = np.random.randint(20000, 40000, 12)
axes[0,1].plot(months, sales, marker='o', color='green')
axes[0,1].set_title('折線圖')
axes[0,1].set_xlabel('月份')

# 3. 散點圖
x = np.random.randn(100)
y = 2 * x + np.random.randn(100)
axes[0,2].scatter(x, y, alpha=0.6, color='purple')
axes[0,2].set_title('散點圖')

# 4. 圓餅圖
sizes = [30, 25, 20, 15, 10]
labels = ['產品A', '產品B', '產品C', '產品D', '其他']
axes[1,0].pie(sizes, labels=labels, autopct='%1.1f%%')
axes[1,0].set_title('圓餅圖')

# 5. 直方圖
data = np.random.normal(100, 15, 1000)
axes[1,1].hist(data, bins=30, color='orange', edgecolor='black')
axes[1,1].set_title('直方圖')

# 6. 箱形圖
data_box = [np.random.normal(100, 10, 200),
            np.random.normal(80, 30, 200),
            np.random.normal(90, 20, 200)]
axes[1,2].boxplot(data_box, labels=['A組', 'B組', 'C組'])
axes[1,2].set_title('箱形圖')

plt.tight_layout()
plt.show()
```

### 客製化技巧
```python
# 進階客製化
fig, ax = plt.subplots(figsize=(10, 6))

# 多系列資料
quarters = ['Q1', 'Q2', 'Q3', 'Q4']
product_a = [20, 35, 30, 35]
product_b = [25, 30, 35, 30]

x = np.arange(len(quarters))
width = 0.35

bars1 = ax.bar(x - width/2, product_a, width, label='產品 A')
bars2 = ax.bar(x + width/2, product_b, width, label='產品 B')

# 美化設定
ax.set_xlabel('季度', fontsize=12)
ax.set_ylabel('銷售量 (千)', fontsize=12)
ax.set_title('產品銷售比較', fontsize=14, fontweight='bold')
ax.set_xticks(x)
ax.set_xticklabels(quarters)
ax.legend()

# 加入數值標籤
def add_value_labels(ax, bars):
    for bar in bars:
        height = bar.get_height()
        ax.text(bar.get_x() + bar.get_width()/2., height,
                f'{height}',
                ha='center', va='bottom')

add_value_labels(ax, bars1)
add_value_labels(ax, bars2)

# 格線設定
ax.grid(True, axis='y', alpha=0.3)
ax.set_axisbelow(True)

# 移除上方和右方邊框
ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)

plt.tight_layout()
plt.show()
```

### 動畫效果
- 程式碼逐行出現
- 圖表逐步構建

### 講師口述
```
"Matplotlib 是基礎，掌握它，
其他視覺化工具都會變簡單！"
```

---

## 🎬 P6：Seaborn 統計圖表 [進階視覺化]
### 版面配置
```
Seaborn vs Matplotlib 對比
```

### 內容文字
**標題** (32pt)
```
📊 Seaborn：統計視覺化神器
```

**為什麼用 Seaborn**
```
Seaborn 優勢：
• 更美觀的預設樣式
• 內建統計功能
• 更簡潔的語法
• 對 Pandas 友善
• 專為統計分析設計
```

### 統計圖表展示
```python
import seaborn as sns
import pandas as pd

# 設定風格
sns.set_style("whitegrid")
sns.set_palette("husl")

# 載入資料
df = pd.read_csv('Taiwan_SuperMarket_Sales_2025.csv')

# 創建圖表網格
fig, axes = plt.subplots(3, 3, figsize=(15, 12))

# 1. 分布圖
sns.histplot(data=df, x='Sales', kde=True, ax=axes[0,0])
axes[0,0].set_title('銷售額分布')

# 2. 箱形圖
sns.boxplot(data=df, x='Branch', y='Sales', ax=axes[0,1])
axes[0,1].set_title('各分店銷售')
axes[0,1].tick_params(axis='x', rotation=45)

# 3. 小提琴圖
sns.violinplot(data=df, x='Product_line', y='Sales', ax=axes[0,2])
axes[0,2].set_title('產品線銷售分布')
axes[0,2].tick_params(axis='x', rotation=45)

# 4. 散點圖 + 回歸線
sns.regplot(data=df, x='Quantity', y='Sales', ax=axes[1,0])
axes[1,0].set_title('數量 vs 銷售額')

# 5. 聯合分布圖
# sns.jointplot(data=df, x='Quantity', y='Sales', kind='hex')

# 6. 熱力圖（相關矩陣）
numeric_cols = df.select_dtypes(include=[np.number]).columns
corr = df[numeric_cols].corr()
sns.heatmap(corr, annot=True, fmt='.2f', ax=axes[1,1])
axes[1,1].set_title('相關性熱力圖')

# 7. 計數圖
sns.countplot(data=df, x='Payment', ax=axes[1,2])
axes[1,2].set_title('支付方式統計')
axes[1,2].tick_params(axis='x', rotation=45)

# 8. 條形圖（帶誤差棒）
sns.barplot(data=df, x='Branch', y='Sales',
            estimator=np.mean, ci=95, ax=axes[2,0])
axes[2,0].set_title('平均銷售（含95%信賴區間）')
axes[2,0].tick_params(axis='x', rotation=45)

# 9. 群組散點圖
sns.swarmplot(data=df.sample(100), x='Product_line', y='Sales',
              hue='Gender', ax=axes[2,1])
axes[2,1].set_title('性別銷售分布')
axes[2,1].tick_params(axis='x', rotation=45)

# 10. 成對關係圖
# sns.pairplot(df[['Sales', 'Quantity', 'Tax', 'Total']])

plt.tight_layout()
plt.show()
```

### 進階應用
```python
# FacetGrid 多維度分析
g = sns.FacetGrid(df, col='Branch', row='Product_line',
                  height=3, aspect=1.2)
g.map(sns.histplot, 'Sales')
g.set_titles('{row_name} | {col_name}')
g.add_legend()

# 時間序列分析
df['Date'] = pd.to_datetime(df['Date'])
daily_sales = df.groupby(df['Date'].dt.date)['Sales'].sum().reset_index()

plt.figure(figsize=(12, 6))
sns.lineplot(data=daily_sales, x='Date', y='Sales')
plt.title('每日銷售趨勢')
plt.xticks(rotation=45)
plt.show()

# 分類箱型圖
plt.figure(figsize=(10, 6))
sns.boxplot(data=df, x='Product_line', y='Sales', hue='Is_Weekend')
plt.title('平日 vs 週末銷售')
plt.xticks(rotation=45)
plt.legend(title='週末', labels=['平日', '週末'])
plt.show()
```

### 視覺化最佳實踐
```python
# Seaborn 樣式設定
styles = ['darkgrid', 'whitegrid', 'dark', 'white', 'ticks']
contexts = ['paper', 'notebook', 'talk', 'poster']

# 為簡報設定
sns.set_style('whitegrid')
sns.set_context('talk')  # 放大字體
sns.set_palette('Set2')  # 柔和色彩

# 中文字體設定
plt.rcParams['font.sans-serif'] = ['Microsoft JhengHei']
plt.rcParams['axes.unicode_minus'] = False
```

### 動畫效果
- 圖表類型切換展示
- 統計功能高亮

### 講師口述
```
"Seaborn 讓統計圖表變得優雅。
一行程式碼，專業圖表！"
```

---

## 🎬 P7：互動式圖表 - Plotly [動態視覺化]
### 版面配置
```
靜態 vs 互動對比
```

### 內容文字
**標題** (32pt)
```
🎮 Plotly：讓圖表動起來
```

**互動功能**
```
🖱️ 互動式圖表優勢：
• 縮放：查看細節
• 懸停：顯示數值
• 選擇：篩選資料
• 導出：圖片下載
• 動畫：時間變化
```

### Plotly 基礎
```python
import plotly.graph_objects as go
import plotly.express as px

# 快速繪圖 (Express)
# 1. 散點圖
fig = px.scatter(df, x='Sales', y='Tax',
                 color='Branch',
                 size='Quantity',
                 hover_data=['Product_line'],
                 title='銷售額 vs 稅額分析')
fig.show()

# 2. 長條圖
branch_sales = df.groupby('Branch')['Sales'].sum().reset_index()
fig = px.bar(branch_sales, x='Branch', y='Sales',
             title='各分店總銷售',
             text='Sales')
fig.update_traces(texttemplate='%{text:,.0f}',
                  textposition='outside')
fig.show()

# 3. 折線圖
daily = df.groupby('Date')['Sales'].sum().reset_index()
fig = px.line(daily, x='Date', y='Sales',
              title='每日銷售趨勢',
              markers=True)
fig.show()
```

### 進階互動圖表
```python
# 自定義互動圖表
fig = go.Figure()

# 添加多個數據系列
for branch in df['Branch'].unique():
    branch_data = df[df['Branch'] == branch]
    daily = branch_data.groupby('Date')['Sales'].sum()

    fig.add_trace(go.Scatter(
        x=daily.index,
        y=daily.values,
        mode='lines+markers',
        name=branch,
        hovertemplate='%{x}<br>銷售額: $%{y:,.0f}'
    ))

# 更新布局
fig.update_layout(
    title='各分店銷售趨勢比較',
    xaxis_title='日期',
    yaxis_title='銷售額 (NT$)',
    hovermode='x unified',
    showlegend=True,
    height=500
)

# 加入範圍選擇器
fig.update_xaxes(
    rangeslider_visible=True,
    rangeselector=dict(
        buttons=list([
            dict(count=7, label="1週", step="day"),
            dict(count=1, label="1月", step="month"),
            dict(step="all", label="全部")
        ])
    )
)

fig.show()
```

### 動態儀表板
```python
# 創建儀表板布局
from plotly.subplots import make_subplots

fig = make_subplots(
    rows=2, cols=2,
    subplot_titles=('銷售趨勢', '分店比較', '產品分布', '付款方式'),
    specs=[[{'type': 'scatter'}, {'type': 'bar'}],
           [{'type': 'pie'}, {'type': 'bar'}]]
)

# 1. 銷售趨勢
daily = df.groupby('Date')['Sales'].sum()
fig.add_trace(
    go.Scatter(x=daily.index, y=daily.values, name='每日銷售'),
    row=1, col=1
)

# 2. 分店比較
branch_sales = df.groupby('Branch')['Sales'].sum()
fig.add_trace(
    go.Bar(x=branch_sales.index, y=branch_sales.values, name='分店'),
    row=1, col=2
)

# 3. 產品分布
product_sales = df.groupby('Product_line')['Sales'].sum()
fig.add_trace(
    go.Pie(labels=product_sales.index, values=product_sales.values),
    row=2, col=1
)

# 4. 付款方式
payment = df['Payment'].value_counts()
fig.add_trace(
    go.Bar(x=payment.index, y=payment.values, name='付款'),
    row=2, col=2
)

fig.update_layout(height=700, showlegend=False,
                  title_text="銷售儀表板")
fig.show()
```

### 動畫圖表
```python
# 時間動畫
df['Month'] = df['Date'].dt.month
monthly = df.groupby(['Month', 'Branch'])['Sales'].sum().reset_index()

fig = px.bar(monthly, x='Branch', y='Sales',
             animation_frame='Month',
             animation_group='Branch',
             title='月度銷售動畫',
             range_y=[0, monthly['Sales'].max() * 1.1])

fig.update_layout(
    updatemenus=[
        dict(
            buttons=list([
                dict(label="播放",
                     method="animate",
                     args=[None, {"frame": {"duration": 500}}])
            ])
        )
    ]
)

fig.show()
```

### 動畫效果
- 互動操作即時展示
- 圖表縮放示範

### 講師口述
```
"互動圖表讓使用者自己探索數據。
這是現代資料視覺化的標準！"
```

---

## 🎬 P8：圖表組合與布局 [版面設計]
### 版面配置
```
多圖組合範例
```

### 內容文字
**標題** (32pt)
```
🎨 圖表編排藝術
```

**布局策略**
```python
# 子圖布局方式
import matplotlib.pyplot as plt
import matplotlib.gridspec as gridspec

# 方法1：簡單網格
fig, axes = plt.subplots(2, 3, figsize=(15, 10))

# 方法2：不規則網格
fig = plt.figure(figsize=(15, 10))
gs = gridspec.GridSpec(3, 3)

ax1 = fig.add_subplot(gs[0, :])     # 第一行全部
ax2 = fig.add_subplot(gs[1, 0:2])   # 第二行前兩列
ax3 = fig.add_subplot(gs[1, 2])     # 第二行第三列
ax4 = fig.add_subplot(gs[2, 0])     # 第三行第一列
ax5 = fig.add_subplot(gs[2, 1:])    # 第三行後兩列

# 方法3：嵌套布局
fig = plt.figure(figsize=(15, 10))
gs0 = gridspec.GridSpec(1, 2)

gs00 = gridspec.GridSpecFromSubplotSpec(2, 2, subplot_spec=gs0[0])
gs01 = gridspec.GridSpecFromSubplotSpec(3, 1, subplot_spec=gs0[1])
```

### 實戰儀表板
```python
# 完整銷售分析儀表板
def create_dashboard(df):
    # 設定風格
    plt.style.use('seaborn-v0_8-darkgrid')
    fig = plt.figure(figsize=(20, 12))

    # 定義布局
    gs = gridspec.GridSpec(3, 4, hspace=0.3, wspace=0.3)

    # 1. 主要KPI（頂部橫幅）
    ax_kpi = fig.add_subplot(gs[0, :])
    ax_kpi.axis('off')

    # KPI 數據
    total_sales = df['Sales'].sum()
    total_trans = len(df)
    avg_sales = df['Sales'].mean()
    top_branch = df.groupby('Branch')['Sales'].sum().idxmax()

    # KPI 文字
    kpi_text = f"""
    總銷售額: NT${total_sales:,.0f}  |  交易筆數: {total_trans:,}  |
    平均客單價: NT${avg_sales:,.0f}  |  最佳分店: {top_branch}
    """
    ax_kpi.text(0.5, 0.5, kpi_text,
                ha='center', va='center',
                fontsize=16, fontweight='bold',
                bbox=dict(boxstyle='round', facecolor='lightblue'))

    # 2. 銷售趨勢（左上）
    ax1 = fig.add_subplot(gs[1, 0:2])
    daily = df.groupby('Date')['Sales'].sum()
    ax1.plot(daily.index, daily.values, marker='o', color='#2E86AB')
    ax1.fill_between(daily.index, daily.values, alpha=0.3)
    ax1.set_title('每日銷售趨勢', fontsize=14)
    ax1.set_xlabel('日期')
    ax1.set_ylabel('銷售額')
    ax1.tick_params(axis='x', rotation=45)

    # 3. 分店比較（右上）
    ax2 = fig.add_subplot(gs[1, 2:])
    branch_sales = df.groupby('Branch')['Sales'].sum().sort_values()
    colors = plt.cm.Blues(np.linspace(0.4, 0.8, len(branch_sales)))
    bars = ax2.barh(branch_sales.index, branch_sales.values, color=colors)
    ax2.set_title('分店銷售排名', fontsize=14)
    ax2.set_xlabel('總銷售額')

    # 加數值標籤
    for bar in bars:
        width = bar.get_width()
        ax2.text(width, bar.get_y() + bar.get_height()/2,
                f'${width:,.0f}',
                ha='left', va='center')

    # 4. 產品組合（左下）
    ax3 = fig.add_subplot(gs[2, 0])
    product_sales = df.groupby('Product_line')['Sales'].sum()
    wedges, texts, autotexts = ax3.pie(product_sales.values,
                                        labels=product_sales.index,
                                        autopct='%1.1f%%',
                                        startangle=90)
    ax3.set_title('產品組合', fontsize=14)

    # 5. 付款方式（中下）
    ax4 = fig.add_subplot(gs[2, 1])
    payment = df['Payment'].value_counts()
    ax4.bar(payment.index, payment.values, color='#F18F01')
    ax4.set_title('付款方式分布', fontsize=14)
    ax4.set_xlabel('付款方式')
    ax4.set_ylabel('交易數')
    ax4.tick_params(axis='x', rotation=45)

    # 6. 時段分析（右下）
    ax5 = fig.add_subplot(gs[2, 2:])
    df['Hour'] = pd.to_datetime(df['Date']).dt.hour
    hourly = df.groupby('Hour')['Sales'].mean()
    ax5.fill_between(hourly.index, hourly.values,
                     color='purple', alpha=0.4)
    ax5.plot(hourly.index, hourly.values,
             color='purple', linewidth=2)
    ax5.set_title('24小時銷售模式', fontsize=14)
    ax5.set_xlabel('小時')
    ax5.set_ylabel('平均銷售額')
    ax5.set_xlim(0, 23)

    # 整體標題
    fig.suptitle('台灣超市銷售分析儀表板', fontsize=20, fontweight='bold')

    return fig

# 生成儀表板
dashboard = create_dashboard(df)
plt.show()
```

### 動畫效果
- 布局動態構建
- 圖表依序出現

### 講師口述
```
"好的儀表板像一個故事，
有開頭、發展和結論。"
```

---

## 🎬 P9：色彩運用與無障礙設計 [專業考量]
### 版面配置
```
色彩理論 + 實踐指南
```

### 內容文字
**標題** (32pt)
```
🎨 色彩心理與無障礙設計
```

**色彩選擇原則**
```python
# 專業配色方案
color_schemes = {
    '商業專業': ['#003f5c', '#58508d', '#bc5090', '#ff6361', '#ffa600'],
    '科技現代': ['#0173B2', '#DE8F05', '#029E73', '#CC78BC', '#ECE133'],
    '自然清新': ['#2E7D32', '#66BB6A', '#A5D6A7', '#81C784', '#4CAF50'],
    '溫暖活力': ['#F94144', '#F3722C', '#F8961E', '#F9C74F', '#90BE6D'],
    '色盲友善': ['#0173B2', '#DE8F05', '#029E73', '#949494', '#ECE133']
}

# 色盲友善檢查
def check_colorblind_safe(colors):
    """檢查配色是否色盲友善"""
    # 避免紅綠組合
    # 使用藍橙對比
    # 加入圖案或標記區分
    pass

# 展示不同配色
fig, axes = plt.subplots(2, 3, figsize=(15, 8))
data = [30, 25, 20, 15, 10]
labels = ['A', 'B', 'C', 'D', 'E']

for idx, (name, colors) in enumerate(color_schemes.items()):
    row = idx // 3
    col = idx % 3
    axes[row, col].bar(labels, data, color=colors)
    axes[row, col].set_title(name)
    axes[row, col].set_ylim(0, 35)

plt.tight_layout()
```

### 無障礙設計
```python
# 無障礙圖表設計
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

x = ['Q1', 'Q2', 'Q3', 'Q4']
sales_a = [100, 120, 110, 130]
sales_b = [90, 110, 105, 125]

# ❌ 不友善設計
ax1.plot(x, sales_a, color='red', label='產品A')
ax1.plot(x, sales_b, color='green', label='產品B')
ax1.set_title('不友善：紅綠色盲無法區分')
ax1.legend()

# ✅ 友善設計
ax2.plot(x, sales_a, color='#0173B2', marker='o',
         linestyle='-', linewidth=2, label='產品A')
ax2.plot(x, sales_b, color='#DE8F05', marker='s',
         linestyle='--', linewidth=2, label='產品B')
ax2.set_title('友善：使用不同標記和線型')
ax2.legend()

# 加入網格幫助閱讀
ax2.grid(True, alpha=0.3)
ax2.set_axisbelow(True)

plt.tight_layout()
```

### 文字可讀性
```python
# 確保文字可讀性
def ensure_readability(ax):
    """確保圖表文字可讀"""

    # 1. 字體大小
    ax.title.set_fontsize(14)
    ax.xaxis.label.set_fontsize(12)
    ax.yaxis.label.set_fontsize(12)

    # 2. 對比度
    # 深色文字配淺色背景
    # 或淺色文字配深色背景

    # 3. 字體選擇
    plt.rcParams['font.family'] = 'sans-serif'
    plt.rcParams['font.sans-serif'] = ['Microsoft JhengHei']

    # 4. 避免文字重疊
    ax.tick_params(axis='x', rotation=45)

    return ax
```

### 實用工具
```python
# 色彩輔助工具
from matplotlib import cm

# 1. 色彩映射
cmap = cm.get_cmap('viridis')  # 色盲友善
colors = [cmap(i) for i in np.linspace(0, 1, 5)]

# 2. 色彩循環
from cycler import cycler
custom_cycler = cycler(color=['#1f77b4', '#ff7f0e', '#2ca02c'])
ax.set_prop_cycle(custom_cycler)

# 3. 透明度運用
ax.bar(x, y, alpha=0.7)  # 避免遮擋
```

### 動畫效果
- 色盲模擬切換
- 配色方案展示

### 講師口述
```
"好的視覺化要讓所有人都能理解，
包括 8% 的色盲使用者。"
```

---

## 🎬 P10：說故事的技巧 [敘事設計]
### 版面配置
```
故事結構 + 案例
```

### 內容文字
**標題** (32pt)
```
📖 用數據說故事
```

**故事三要素**
```
1. 背景 (Context)
   設定場景，說明為什麼重要

2. 衝突 (Conflict)
   指出問題或機會

3. 解決 (Resolution)
   提供洞察和建議
```

### 敘事結構範例
```python
# 故事化的圖表序列
fig, axes = plt.subplots(1, 3, figsize=(15, 5))

# 第一幕：設定背景
months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun']
sales = [100, 98, 95, 92, 88, 85]

axes[0].plot(months, sales, color='red', linewidth=2, marker='o')
axes[0].set_title('第一幕：銷售持續下滑', fontsize=14, color='red')
axes[0].set_ylabel('銷售額（萬）')
axes[0].set_ylim(80, 105)
axes[0].axhline(y=90, color='gray', linestyle='--', alpha=0.5)
axes[0].text(2.5, 91, '警戒線', ha='center')

# 第二幕：深入分析
categories = ['產品A', '產品B', '產品C', '產品D']
before = [40, 30, 20, 10]
after = [25, 25, 15, 20]

x = np.arange(len(categories))
width = 0.35

axes[1].bar(x - width/2, before, width, label='Q1', color='lightcoral')
axes[1].bar(x + width/2, after, width, label='Q2', color='darkred')
axes[1].set_title('第二幕：產品A銷量暴跌', fontsize=14)
axes[1].set_xticks(x)
axes[1].set_xticklabels(categories)
axes[1].legend()

# 標註問題
axes[1].annotate('下跌40%!',
                xy=(0, 25), xytext=(0.5, 35),
                arrowprops=dict(arrowstyle='->', color='red', lw=2),
                fontsize=12, color='red')

# 第三幕：提供解決方案
solutions = ['促銷活動', '產品改良', '新品上市']
impact = [15, 25, 30]
colors = ['#90EE90', '#32CD32', '#228B22']

axes[2].barh(solutions, impact, color=colors)
axes[2].set_title('第三幕：建議行動方案', fontsize=14, color='green')
axes[2].set_xlabel('預期銷售提升（%）')

# 加入數值
for i, v in enumerate(impact):
    axes[2].text(v + 0.5, i, f'+{v}%', va='center')

plt.suptitle('銷售危機分析報告', fontsize=16, fontweight='bold')
plt.tight_layout()
```

### 視覺層次
```python
# 建立視覺焦點
fig, ax = plt.subplots(figsize=(10, 6))

# 背景資料（灰色、淡化）
for i in range(5):
    ax.plot(np.random.randn(12).cumsum() + i*5,
            color='gray', alpha=0.3, linewidth=1)

# 重點資料（彩色、加粗）
important_data = np.array([1, 2, 3, 5, 8, 11, 14, 16, 17, 18, 19, 20])
ax.plot(important_data, color='#F18F01', linewidth=3,
        marker='o', markersize=8, label='關鍵指標')

# 標註重要時刻
ax.annotate('轉折點',
           xy=(4, 8), xytext=(6, 12),
           arrowprops=dict(arrowstyle='->', color='red', lw=2),
           fontsize=12, color='red',
           bbox=dict(boxstyle='round,pad=0.3', facecolor='yellow'))

ax.set_title('突出重點的視覺設計', fontsize=14)
ax.legend()
ax.grid(True, alpha=0.2)
```

### 動畫效果
- 故事情節依序展開
- 重點標註動畫

### 講師口述
```
"數據不會說話，但你可以讓它說故事。
記住：先有洞察，再有圖表！"
```

---

## 🎬 P11：常見錯誤與陷阱 [避坑指南]
### 版面配置
```
錯誤示例 + 正確做法
```

### 內容文字
**標題** (32pt)
```
⚠️ 視覺化的七宗罪
```

**常見錯誤**
```python
fig, axes = plt.subplots(3, 2, figsize=(12, 12))

# 錯誤1：誤導性Y軸
data = [98, 99, 100, 101, 102]
axes[0,0].bar(range(5), data)
axes[0,0].set_ylim(95, 105)
axes[0,0].set_title('❌ 誤導：Y軸不從0開始')

axes[0,1].bar(range(5), data)
axes[0,1].set_ylim(0, 110)
axes[0,1].set_title('✅ 正確：顯示完整範圍')

# 錯誤2：3D圖表
labels = ['A', 'B', 'C', 'D']
sizes = [30, 25, 20, 25]

# 3D餅圖（不推薦）
ax3d = fig.add_subplot(232, projection='3d')
ax3d.pie(sizes, labels=labels)
ax3d.set_title('❌ 3D餅圖難以判讀')

axes[1,1].pie(sizes, labels=labels, autopct='%1.1f%%')
axes[1,1].set_title('✅ 2D餅圖清晰明瞭')

# 錯誤3：雙Y軸濫用
x = range(10)
y1 = np.random.randn(10).cumsum()
y2 = np.random.randn(10).cumsum() * 1000

axes[2,0].plot(x, y1, 'b-', label='指標A')
ax2 = axes[2,0].twinx()
ax2.plot(x, y2, 'r-', label='指標B')
axes[2,0].set_title('❌ 雙Y軸容易混淆')

# 改用子圖
axes[2,1].plot(x, y1, 'b-')
axes[2,1].set_title('✅ 分開顯示更清楚')

plt.tight_layout()
```

### 視覺化倫理
```
📊 數據倫理守則：
1. 不扭曲數據
2. 不隱藏不利資訊
3. 不誇大差異
4. 提供完整背景
5. 標註資料來源
6. 說明限制條件
```

### 檢查清單
```python
def visualization_checklist(fig):
    """視覺化品質檢查"""
    checks = {
        '標題明確': True,
        'Y軸從0開始（長條圖）': True,
        '有圖例說明': True,
        '軸標籤清楚': True,
        '資料來源標註': True,
        '色彩不超過7種': True,
        '文字可讀': True,
        '無3D效果': True,
        '適當的圖表類型': True
    }

    print("視覺化檢查清單：")
    for item, status in checks.items():
        symbol = "✅" if status else "❌"
        print(f"{symbol} {item}")

    return all(checks.values())
```

### 動畫效果
- 錯誤示例警示動畫
- 正確做法對比

### 講師口述
```
"壞的圖表比沒有圖表更糟。
永遠記住：誠實、清晰、有效！"
```

---

## 🎬 P12：實戰專案 - 銷售儀表板 [綜合應用]
### 版面配置
```
完整儀表板實作
```

### 內容文字
**標題** (32pt)
```
🚀 實戰：打造專業儀表板
```

**任務需求**
```
📋 老闆要求：
1. 一頁看懂本月業績
2. 找出問題與機會
3. 提供行動建議
4. 要能每日自動更新
```

### 完整程式碼
```python
# 專業銷售儀表板
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime

class SalesDashboard:
    def __init__(self, df):
        self.df = df
        self.setup_style()

    def setup_style(self):
        """設定視覺風格"""
        plt.style.use('seaborn-v0_8-whitegrid')
        plt.rcParams['font.sans-serif'] = ['Microsoft JhengHei']
        plt.rcParams['axes.unicode_minus'] = False
        sns.set_palette("husl")

    def calculate_kpis(self):
        """計算關鍵指標"""
        total_sales = self.df['Sales'].sum()
        total_transactions = len(self.df)
        avg_transaction = self.df['Sales'].mean()
        growth_rate = 0.15  # 假設成長率

        return {
            'total_sales': total_sales,
            'transactions': total_transactions,
            'avg_transaction': avg_transaction,
            'growth_rate': growth_rate
        }

    def create_dashboard(self):
        """創建完整儀表板"""
        fig = plt.figure(figsize=(20, 12))
        fig.suptitle(f'銷售分析儀表板 - {datetime.now().strftime("%Y年%m月")}',
                    fontsize=20, fontweight='bold')

        # KPI 區域
        gs = fig.add_gridspec(4, 4, hspace=0.3, wspace=0.3)

        # KPI 卡片
        ax_kpi = fig.add_subplot(gs[0, :])
        self.create_kpi_cards(ax_kpi)

        # 銷售趨勢
        ax_trend = fig.add_subplot(gs[1, :2])
        self.plot_sales_trend(ax_trend)

        # 品牌比較
        ax_brand = fig.add_subplot(gs[1, 2:])
        self.plot_brand_comparison(ax_brand)

        # 產品分析
        ax_product = fig.add_subplot(gs[2, 0])
        self.plot_product_analysis(ax_product)

        # 時段分析
        ax_hour = fig.add_subplot(gs[2, 1])
        self.plot_hourly_pattern(ax_hour)

        # 支付方式
        ax_payment = fig.add_subplot(gs[2, 2])
        self.plot_payment_methods(ax_payment)

        # 客戶分析
        ax_customer = fig.add_subplot(gs[2, 3])
        self.plot_customer_segments(ax_customer)

        # 建議行動
        ax_action = fig.add_subplot(gs[3, :])
        self.create_action_items(ax_action)

        return fig

    def create_kpi_cards(self, ax):
        """創建KPI卡片"""
        ax.axis('off')
        kpis = self.calculate_kpis()

        # KPI 文字
        kpi_text = f"""
        💰 總營收: NT${kpis['total_sales']:,.0f}   |
        📊 交易數: {kpis['transactions']:,}   |
        🛒 客單價: NT${kpis['avg_transaction']:,.0f}   |
        📈 月成長: {kpis['growth_rate']:.1%}
        """

        ax.text(0.5, 0.5, kpi_text,
                ha='center', va='center',
                fontsize=16, fontweight='bold',
                bbox=dict(boxstyle='round,pad=0.5',
                         facecolor='lightblue',
                         edgecolor='darkblue',
                         linewidth=2))

    def plot_sales_trend(self, ax):
        """繪製銷售趨勢"""
        daily = self.df.groupby('Date')['Sales'].sum()
        ax.plot(daily.index, daily.values,
                color='#2E86AB', linewidth=2, marker='o')
        ax.fill_between(daily.index, daily.values,
                       color='#2E86AB', alpha=0.3)
        ax.set_title('每日銷售趨勢', fontsize=14)
        ax.set_xlabel('日期')
        ax.set_ylabel('銷售額 (NT$)')
        ax.grid(True, alpha=0.3)

        # 加入移動平均
        ma7 = daily.rolling(window=7).mean()
        ax.plot(daily.index, ma7, color='red',
                linestyle='--', label='7日均線')
        ax.legend()

    def plot_brand_comparison(self, ax):
        """品牌業績比較"""
        brand_stats = self.df.groupby('Branch').agg({
            'Sales': ['sum', 'mean', 'count']
        }).round(0)

        brand_sales = brand_stats['Sales']['sum'].sort_values()
        colors = plt.cm.Blues(np.linspace(0.4, 0.8, len(brand_sales)))

        bars = ax.barh(brand_sales.index, brand_sales.values, color=colors)
        ax.set_title('品牌銷售排名', fontsize=14)
        ax.set_xlabel('總銷售額 (NT$)')

        # 加數值標籤
        for bar in bars:
            width = bar.get_width()
            ax.text(width, bar.get_y() + bar.get_height()/2,
                   f'${width:,.0f}',
                   ha='left', va='center')

    def plot_product_analysis(self, ax):
        """產品組合分析"""
        product_sales = self.df.groupby('Product_line')['Sales'].sum()
        colors = plt.cm.Set3(range(len(product_sales)))

        wedges, texts, autotexts = ax.pie(
            product_sales.values,
            labels=product_sales.index,
            autopct='%1.1f%%',
            colors=colors,
            startangle=90
        )
        ax.set_title('產品組合', fontsize=14)

    def plot_hourly_pattern(self, ax):
        """時段銷售模式"""
        self.df['Hour'] = pd.to_datetime(self.df['Date']).dt.hour
        hourly = self.df.groupby('Hour')['Sales'].mean()

        ax.bar(hourly.index, hourly.values,
               color='purple', alpha=0.7)
        ax.set_title('24小時銷售模式', fontsize=14)
        ax.set_xlabel('時段')
        ax.set_ylabel('平均銷售額')
        ax.set_xticks(range(0, 24, 2))

    def plot_payment_methods(self, ax):
        """支付方式分析"""
        payment = self.df['Payment'].value_counts()
        colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#96CEB4']

        ax.bar(payment.index, payment.values, color=colors)
        ax.set_title('支付方式', fontsize=14)
        ax.set_xlabel('支付類型')
        ax.set_ylabel('交易次數')
        ax.tick_params(axis='x', rotation=45)

        # 加百分比
        for i, (k, v) in enumerate(payment.items()):
            ax.text(i, v, f'{v/payment.sum()*100:.1f}%',
                   ha='center', va='bottom')

    def plot_customer_segments(self, ax):
        """客戶分群"""
        # 簡單分群：依消費金額
        bins = [0, 5000, 10000, 50000]
        labels = ['一般', 'VIP', 'VVIP']
        self.df['Segment'] = pd.cut(self.df['Sales'], bins, labels=labels)

        segment_counts = self.df['Segment'].value_counts()
        colors = ['#FFA07A', '#98D8C8', '#FFD700']

        ax.pie(segment_counts.values,
               labels=[f'{l}\n({v}人)' for l, v in zip(segment_counts.index,
                                                       segment_counts.values)],
               colors=colors,
               autopct='%1.1f%%',
               startangle=90)
        ax.set_title('客戶分群', fontsize=14)

    def create_action_items(self, ax):
        """行動建議"""
        ax.axis('off')

        actions = """
        📌 行動建議：
        1. 週末促銷：數據顯示週末銷售較低，建議加強週末促銷活動
        2. 產品優化：產品C銷售佔比偏低，考慮調整產品組合或定價
        3. VIP經營：20%的VIP客戶貢獻60%營收，建議深化VIP服務
        4. 支付優化：電子支付使用率僅30%，可推出電子支付優惠
        """

        ax.text(0.1, 0.5, actions,
                ha='left', va='center',
                fontsize=12,
                bbox=dict(boxstyle='round,pad=0.5',
                         facecolor='lightyellow'))

# 使用儀表板
dashboard = SalesDashboard(df)
fig = dashboard.create_dashboard()
plt.show()

# 儲存儀表板
fig.savefig('sales_dashboard.png', dpi=300, bbox_inches='tight')
print("儀表板已儲存為 sales_dashboard.png")
```

### 講師口述
```
"這就是專業的儀表板！
一頁說清楚所有重要資訊。"
```

---

## 🎬 P13：自動化報表 [效率提升]
### 版面配置
```
自動化流程展示
```

### 內容文字
**標題** (32pt)
```
🤖 自動化：讓報表自己生成
```

**自動化架構**
```python
# 自動化報表生成系統
import schedule
import time
from datetime import datetime

class AutoReporter:
    def __init__(self, data_source, output_path):
        self.data_source = data_source
        self.output_path = output_path

    def fetch_data(self):
        """取得最新資料"""
        # 從資料庫或API取得資料
        df = pd.read_csv(self.data_source)
        return df

    def generate_report(self):
        """生成報表"""
        df = self.fetch_data()

        # 建立儀表板
        dashboard = SalesDashboard(df)
        fig = dashboard.create_dashboard()

        # 儲存報表
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        filename = f'{self.output_path}/report_{timestamp}.png'
        fig.savefig(filename, dpi=300, bbox_inches='tight')
        plt.close()

        print(f"報表已生成: {filename}")
        return filename

    def send_email(self, filename):
        """發送報表郵件"""
        # 這裡放郵件發送程式碼
        print(f"報表已發送: {filename}")

    def run_daily_report(self):
        """執行每日報表"""
        filename = self.generate_report()
        self.send_email(filename)

# 設定定時任務
reporter = AutoReporter('data.csv', './reports')

# 每天早上9點執行
schedule.every().day.at("09:00").do(reporter.run_daily_report)

# 或每小時執行
# schedule.every().hour.do(reporter.generate_report)

# 執行排程
while True:
    schedule.run_pending()
    time.sleep(60)
```

### 動畫效果
- 自動化流程動畫
- 報表生成過程

### 講師口述
```
"自動化讓你專注在分析，
而不是重複製作報表！"
```

---

## 🎬 P14：視覺化工具生態 [工具選擇]
### 版面配置
```
工具比較矩陣
```

### 內容文字
**標題** (32pt)
```
🛠️ 選對工具事半功倍
```

**工具比較**
```
Python 生態系：
├─ Matplotlib：基礎、靈活、完全控制
├─ Seaborn：統計圖表、美觀預設
├─ Plotly：互動圖表、網頁整合
├─ Bokeh：大數據、串流資料
├─ Altair：宣告式語法、Vega-Lite
└─ Dash：網頁應用、儀表板框架

其他選擇：
├─ Tableau：商業智慧、拖拉式
├─ Power BI：微軟生態、企業整合
├─ D3.js：網頁視覺化、完全客製
└─ Excel：簡單快速、普及度高
```

### 選擇決策
```python
def choose_viz_tool(requirements):
    """根據需求選擇工具"""

    if requirements['互動性'] == '高':
        if requirements['程式能力'] == '強':
            return 'Plotly 或 Bokeh'
        else:
            return 'Tableau 或 Power BI'

    elif requirements['統計分析'] == '多':
        return 'Seaborn + Matplotlib'

    elif requirements['即時更新'] == '需要':
        return 'Dash 或 Streamlit'

    elif requirements['網頁整合'] == '需要':
        return 'D3.js 或 Plotly'

    else:
        return 'Matplotlib（萬用）'
```

### 動畫效果
- 工具圖標展示
- 決策流程動畫

### 講師口述
```
"沒有最好的工具，只有最適合的工具。
先掌握一個，再學其他！"
```

---

## 🎬 P15：模組總結 [成就確認]
### 版面配置
```
作品集展示 + 技能總結
```

### 內容文字
**標題** (32pt)
```
🎉 Module 4 完成！
```

**成就解鎖**
```
🏆 成就解鎖：
「視覺化達人」
- 掌握圖表選擇決策
- 完成專業儀表板
- 學會三大視覺化工具
```

**技能清單**
```
✅ 你現在掌握的技能：
□ 圖表類型選擇
□ 設計原則運用
□ Matplotlib 基礎繪圖
□ Seaborn 統計圖表
□ Plotly 互動視覺化
□ 色彩與無障礙設計
□ 資料故事敘述
□ 儀表板設計
□ 報表自動化

💪 你能創造的價值：
• 1分鐘看懂複雜數據
• 專業商業報告
• 互動式儀表板
• 自動化日報表
```

### 作品展示
```
📊 本模組作品：
• 基礎圖表 6 種
• 統計圖表 5 種
• 互動圖表 3 種
• 完整儀表板 1 個
```

### 下階段預告
```
⏭️ Module 5 預告：
「數據分析流程與問題拆解」
• CRISP-DM 方法論
• 麥肯錫問題拆解
• 54萬筆資料實戰
• RFM 客戶分群
```

### 動畫效果
- 作品輪播展示
- 成就徽章旋轉

### 講師口述
```
"太棒了！你的圖表已經達到專業水準！
接下來，學習如何系統化分析問題。"
```

---

## 📋 Module 4 教學檢核表

### 時間控制 (45分鐘)
- [ ] P1-P4: 10分鐘 (原理介紹)
- [ ] P5-P7: 15分鐘 (工具實作)
- [ ] P8-P11: 12分鐘 (進階技巧)
- [ ] P12-P15: 8分鐘 (綜合應用)

### 關鍵檢查點
- [ ] P3: 圖表選擇理解
- [ ] P5: Matplotlib 基礎掌握
- [ ] P6: Seaborn 應用
- [ ] P12: 完成儀表板

### 教材準備
- [ ] 圖表類型速查表
- [ ] 色彩配置方案
- [ ] 程式碼範例檔
- [ ] 儀表板模板

---

*Module 4 設計完成 - 確保學員掌握專業視覺化技能*