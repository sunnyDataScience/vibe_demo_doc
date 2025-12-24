# Module 2：Pandas數據處理與資料庫基礎 - 完整簡報設計
## 🎯 60分鐘掌握數據處理核心

---

## 📊 簡報基本資訊
- **總頁數**：25頁
- **預計時長**：60分鐘
- **設計主色**：數據紫 (#A23B72)
- **輔助色彩**：科技藍 (#2E86AB)

---

## 🎬 P1：章節封面 [專業開場]
### 版面配置
```
背景：數據表格淡化效果
左側：大數字 "2" (透明度 15%)
右側：標題內容區
```

### 內容文字
**主標題** (40pt, 紫色)
```
Module 2
Pandas 數據處理與資料庫基礎
```

**副標題** (24pt)
```
從 Excel 到 DataFrame 的進化
處理 1,000 筆真實銷售數據
```

**學習重點** (20pt, 圖標列表)
```
📊 讀取各種數據格式
🔧 DataFrame 核心操作
🧹 數據清理與轉換
📈 數據聚合與分析
🔗 資料庫基礎概念
```

### 進度指示
```
[■■□□□□□] Module 2/7
預計時間：60分鐘
```

### 動畫效果
- 表格數據滾動背景
- 標題淡入效果
- 重點項目依序出現

### 講師口述
```
"歡迎來到 Module 2！
現在要用 Python 處理真實數據了。
Pandas 是 Python 的 Excel，但強大 100 倍！"
```

---

## 🎬 P2：為什麼要學 Pandas [動機建立]
### 版面配置
```
問題展示 → 解決方案
```

### 內容文字
**標題** (32pt)
```
🤔 Excel 的痛點
```

**痛點列表**
```
😰 Excel 的限制：
• 資料超過 100 萬列就崩潰
• VLOOKUP 又慢又容易出錯
• 樞紐分析表功能有限
• 無法自動化重複工作
• 圖表樣式選擇有限

💪 Pandas 的解決方案：
• 輕鬆處理數億筆資料
• 強大的合併與連接功能
• 靈活的分組聚合操作
• 完全自動化工作流程
• 無限的視覺化可能
```

### 實際案例
```
📊 真實案例對比：
任務：分析 500 萬筆交易記錄

Excel:
- 載入時間：無法開啟 ❌
- 需要分割檔案
- 手動操作 2 小時

Pandas:
- 載入時間：3 秒 ✅
- 一個檔案搞定
- 程式執行 10 秒
```

### 市場需求
```
💼 職場技能需求：
• 資料分析師：必備技能
• 商業分析師：加分技能
• 產品經理：競爭優勢
• 行銷人員：效率提升
```

### 動畫效果
- Excel 圖標顯示載入失敗
- Pandas 圖標快速完成
- 數字對比滾動效果

### 講師口述
```
"如果 Excel 是腳踏車，
Pandas 就是跑車。
學會後，你會回不去的！"
```

---

## 🎬 P3：認識 DataFrame [核心概念]
### 版面配置
```
視覺化 DataFrame 結構
```

### 內容文字
**標題** (32pt)
```
📊 DataFrame：Pandas 的核心
```

**結構說明**
```
DataFrame = 加強版的 Excel 表格

     列標籤 (Index)
      ↓
     Name    Age   Salary   Dept      ← 欄標籤 (Columns)
0    王小明   25    35000    Sales
1    李大華   30    42000    IT       ← 一列 (Row/Series)
2    張美麗   28    38000    HR
      ↑
   一欄 (Column/Series)
```

**關鍵特性**
```
🔑 DataFrame 特色：
• 二維表格結構
• 每欄可以不同資料型態
• 強大的索引系統
• 內建統計功能
• 支援缺失值處理
```

### 程式碼展示
```python
import pandas as pd

# 建立 DataFrame
data = {
    '姓名': ['王小明', '李大華', '張美麗'],
    '年齡': [25, 30, 28],
    '薪資': [35000, 42000, 38000],
    '部門': ['Sales', 'IT', 'HR']
}

df = pd.DataFrame(data)
print(df)
print(f"\n資料形狀: {df.shape}")  # (3, 4)
print(f"欄位名稱: {df.columns.tolist()}")
```

### 與 Excel 對照
```
Excel 術語    →    Pandas 術語
工作表        →    DataFrame
欄           →    Column/Series
列           →    Row
儲存格        →    單一值
```

### 動畫效果
- DataFrame 結構逐步構建
- 索引和欄位高亮顯示

### 講師口述
```
"DataFrame 就是 Python 裡的 Excel 表格，
但更聰明、更快速、更強大！"
```

---

## 🎬 P4：讀取真實數據 [實戰開始]
### 版面配置
```
程式碼 + 執行結果並排
```

### 內容文字
**標題** (32pt)
```
📥 載入台灣超市銷售數據
```

**支援的檔案格式**
```
Pandas 支援格式：
📄 CSV → pd.read_csv()
📊 Excel → pd.read_excel()
📋 JSON → pd.read_json()
🗄️ SQL → pd.read_sql()
🌐 HTML → pd.read_html()
📦 Parquet → pd.read_parquet()
```

### 實戰程式碼
```python
# 讀取超市銷售數據
import pandas as pd

# 載入 CSV 檔案
df = pd.read_csv('Taiwan_SuperMarket_Sales_2025.csv')

# 基本資訊探索
print(f"資料筆數: {len(df):,} 筆")
print(f"欄位數量: {df.shape[1]} 個")
print(f"\n前 5 筆資料:")
print(df.head())

# 欄位資訊
print("\n資料型態:")
print(df.dtypes)

# 基本統計
print("\n數值欄位統計:")
print(df.describe())
```

### 執行結果展示
```
資料筆數: 1,000 筆
欄位數量: 29 個

前 5 筆資料:
   Invoice_ID       Date  Branch   Sales  ...
0  INV-00001  2025-01-01  全聯     1250.50  ...
1  INV-00002  2025-01-01  好市多   3420.00  ...
[顯示實際數據表格]

資料型態:
Invoice_ID     object
Date          datetime64
Branch         object
Sales          float64
...
```

### 常用參數
```python
# 進階讀取技巧
df = pd.read_csv(
    'data.csv',
    encoding='utf-8',      # 編碼
    parse_dates=['Date'],  # 日期欄位
    index_col='ID',        # 索引欄
    nrows=100             # 只讀前100筆
)
```

### 動畫效果
- 載入進度條
- 資料逐行顯示

### 講師口述
```
"看！1000 筆資料瞬間載入。
這就是我們要分析的台灣超市數據。"
```

---

## 🎬 P5：探索數據 - 初步了解 [資料探索]
### 版面配置
```
指令區 + 輸出區上下排列
```

### 內容文字
**標題** (32pt)
```
🔍 快速了解你的數據
```

**必學探索指令**
```python
# 1. 查看資料結構
df.info()
# 顯示：欄位名稱、資料型態、非空值數量

# 2. 檢視前後資料
df.head(10)    # 前 10 筆
df.tail(10)    # 後 10 筆

# 3. 基本統計資訊
df.describe()  # 數值統計
df.describe(include='object')  # 類別統計

# 4. 檢查缺失值
df.isnull().sum()  # 各欄位缺失值數量
df.isnull().sum().sum()  # 總缺失值

# 5. 查看唯一值
df['Branch'].unique()  # 所有分店
df['Branch'].nunique()  # 分店數量
df['Branch'].value_counts()  # 各分店筆數
```

### 實際輸出範例
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 1000 entries, 0 to 999
Data columns (total 29 columns):
 #   Column         Non-Null Count  Dtype
---  ------         --------------  -----
 0   Invoice_ID     1000 non-null   object
 1   Date           1000 non-null   datetime64
 2   Branch         1000 non-null   object
 3   Sales          1000 non-null   float64
...

Branch 分布:
全聯      156
好市多    148
家樂福    145
全家      142
7-11     141
...
```

### 快速洞察
```
📊 數據洞察：
• 資料完整：無缺失值 ✅
• 時間範圍：2025 Q1
• 7 家主要品牌
• 銷售額範圍：320-35,252 元
• 平均客單價：5,322 元
```

### 動畫效果
- 指令逐一執行
- 結果依序顯示

### 講師口述
```
"探索資料是分析的第一步。
這些指令讓你 30 秒內了解資料全貌！"
```

---

## 🎬 P6：選取資料 - 基本索引 [核心操作]
### 版面配置
```
方法對比表格
```

### 內容文字
**標題** (32pt)
```
🎯 精準選取你要的資料
```

**選取方法大全**
```python
# 1. 選取單一欄位（Series）
df['Sales']              # 方法一
df.Sales                 # 方法二（欄名無空格時）

# 2. 選取多個欄位（DataFrame）
df[['Branch', 'Sales', 'Date']]

# 3. 選取列資料
df.loc[0]                # 用標籤選取
df.iloc[0]               # 用位置選取
df.loc[0:5]              # 選取 0-5 列
df.iloc[0:5]             # 選取前 5 列

# 4. 選取特定範圍
df.loc[0:5, 'Branch':'Sales']     # 列與欄範圍
df.iloc[0:5, 1:4]                 # 位置範圍

# 5. 條件選取（最重要！）
df[df['Sales'] > 10000]           # 高額交易
df[df['Branch'] == '全聯']        # 特定品牌
df[(df['Sales'] > 5000) & (df['Branch'] == '好市多')]
```

### loc vs iloc 比較
```
📍 loc vs iloc 差異：

loc[列, 欄] - 標籤索引
• 使用實際的標籤名稱
• 包含結束點
• df.loc[0:2] → 0,1,2 三列

iloc[列, 欄] - 位置索引
• 使用數字位置（從 0 開始）
• 不包含結束點
• df.iloc[0:2] → 0,1 兩列
```

### 實用範例
```python
# 找出好市多的高額消費
costco_vip = df[(df['Branch'] == '好市多') &
                 (df['Sales'] > 8000)]

print(f"好市多 VIP 交易: {len(costco_vip)} 筆")
print(f"平均消費: ${costco_vip['Sales'].mean():,.0f}")
```

### 動畫效果
- 選取區域高亮顯示
- 結果即時更新

### 講師口述
```
"選取資料是 Pandas 最常用的操作。
掌握這些，你就能隨心所欲操控資料！"
```

---

## 🎬 P7：篩選資料 - 布林索引 [進階選取]
### 版面配置
```
概念圖解 + 程式碼實作
```

### 內容文字
**標題** (32pt)
```
🔍 布林索引：強大的篩選器
```

**布林索引原理**
```
步驟解析：
1. 建立布林條件 → True/False 陣列
2. 套用布林遮罩 → 只保留 True 的列

     Sales > 5000 ?
[1200]  →  [False]  →  ✗
[6500]  →  [True]   →  ✓ 保留
[3200]  →  [False]  →  ✗
[8900]  →  [True]   →  ✓ 保留
```

### 實戰篩選
```python
# 單一條件
high_sales = df[df['Sales'] > 10000]
print(f"高額交易: {len(high_sales)} 筆")

# 多重條件（AND）
vip_costco = df[(df['Branch'] == '好市多') &
                 (df['Sales'] > 8000)]

# 多重條件（OR）
convenience = df[(df['Branch'] == '7-11') |
                  (df['Branch'] == '全家')]

# 包含檢查（isin）
top_brands = ['全聯', '好市多', '家樂福']
major_stores = df[df['Branch'].isin(top_brands)]

# 字串篩選
eco_products = df[df['Product_line'].str.contains('環保')]

# 日期篩選
weekend = df[df['Date'].dt.dayofweek.isin([5, 6])]
print(f"週末交易: {len(weekend)} 筆")
```

### 常用篩選技巧
```python
# 篩選 + 排序
top_10_sales = df.nlargest(10, 'Sales')

# 篩選 + 特定欄位
result = df[df['Sales'] > 5000][['Date', 'Branch', 'Sales']]

# 反向篩選（NOT）
not_vip = df[~df['Is_VIP']]

# 區間篩選
mid_range = df[df['Sales'].between(3000, 8000)]
```

### 效能提醒
```
⚡ 效能小技巧：
• 使用 & | ~ 而非 and or not
• 條件要加括號
• query() 方法更直觀：
  df.query('Sales > 5000 and Branch == "全聯"')
```

### 動畫效果
- 布林遮罩過程動畫
- 篩選結果高亮

### 講師口述
```
"布林索引是 Pandas 的精髓！
學會這個，Excel 的篩選功能就太簡單了。"
```

---

## 🎬 P8：資料排序 [組織數據]
### 版面配置
```
排序方法展示
```

### 內容文字
**標題** (32pt)
```
📊 排序：讓數據有序
```

**排序方法**
```python
# 1. 單欄排序
df.sort_values('Sales')                    # 遞增
df.sort_values('Sales', ascending=False)   # 遞減

# 2. 多欄排序
df.sort_values(['Branch', 'Sales'],
               ascending=[True, False])

# 3. 索引排序
df.sort_index()                           # 依索引排序
df.sort_index(ascending=False)            # 反向

# 4. 排序後重設索引
df_sorted = df.sort_values('Sales', ascending=False)
df_sorted = df_sorted.reset_index(drop=True)
```

### 實用範例
```python
# 找出各品牌最高銷售
for branch in df['Branch'].unique():
    branch_data = df[df['Branch'] == branch]
    top_sale = branch_data.nlargest(1, 'Sales')
    print(f"{branch} 最高: ${top_sale['Sales'].values[0]:,.0f}")

# 每月 Top 5
top_monthly = df.groupby(df['Date'].dt.month).apply(
    lambda x: x.nlargest(5, 'Sales')
)
```

### 排序 + 篩選組合
```python
# 找出週末的 Top 10 高額消費
weekend_top = (df[df['Is_Weekend'] == True]
                .sort_values('Sales', ascending=False)
                .head(10))

print("週末 Top 10 消費:")
print(weekend_top[['Date', 'Branch', 'Sales']])
```

### 視覺化排序結果
```python
# 品牌銷售排行
brand_sales = df.groupby('Branch')['Sales'].sum().sort_values()
brand_sales.plot(kind='barh', color='skyblue')
plt.title('品牌銷售總額排行')
```

### 動畫效果
- 資料重新排列動畫
- 排名變化效果

### 講師口述
```
"排序幫助我們快速找到最大、最小值，
發現數據中的模式和異常。"
```

---

## 🎬 P9：新增與修改欄位 [資料轉換]
### 版面配置
```
操作範例 + 結果展示
```

### 內容文字
**標題** (32pt)
```
➕ 創造新的資料欄位
```

**新增欄位方法**
```python
# 1. 直接賦值
df['Tax'] = df['Sales'] * 0.05

# 2. 基於條件
df['Customer_Level'] = df['Sales'].apply(
    lambda x: 'VIP' if x > 10000 else 'Regular'
)

# 3. 多欄位運算
df['Net_Profit'] = df['Sales'] - df['Cost'] - df['Tax']

# 4. 日期衍生欄位
df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Weekday'] = df['Date'].dt.day_name()
df['Is_Weekend'] = df['Date'].dt.dayofweek.isin([5, 6])

# 5. 分類轉換
df['Sales_Category'] = pd.cut(
    df['Sales'],
    bins=[0, 3000, 8000, 50000],
    labels=['低', '中', '高']
)
```

### 實務應用
```python
# 計算 RFM 分數
today = pd.Timestamp('2025-03-31')

# Recency: 最近購買
df['Recency'] = (today - df['Date']).dt.days

# 會員等級判定
def classify_customer(row):
    if row['Sales'] > 10000 and row['Frequency'] > 5:
        return '鑽石會員'
    elif row['Sales'] > 5000:
        return '金牌會員'
    elif row['Sales'] > 2000:
        return '銀牌會員'
    else:
        return '一般會員'

df['Membership'] = df.apply(classify_customer, axis=1)
```

### 修改現有欄位
```python
# 替換值
df['Branch'].replace({'7-11': '7-ELEVEN'}, inplace=True)

# 條件修改
df.loc[df['Sales'] < 0, 'Sales'] = 0

# 資料型態轉換
df['Date'] = pd.to_datetime(df['Date'])
df['Sales'] = df['Sales'].astype('float32')
```

### 批次處理
```python
# 對多個欄位同時操作
numeric_cols = ['Sales', 'Quantity', 'Tax']
df[numeric_cols] = df[numeric_cols].round(2)
```

### 動畫效果
- 新欄位逐一添加
- 數值計算過程顯示

### 講師口述
```
"新增欄位讓我們能創造更多分析維度。
這是特徵工程的基礎！"
```

---

## 🎬 P10：分組聚合 - GroupBy [核心分析]
### 版面配置
```
概念圖解 + 程式實作
```

### 內容文字
**標題** (32pt)
```
📊 GroupBy：分組統計的魔法
```

**GroupBy 概念**
```
Split → Apply → Combine
分組  →  運算  →  合併

原始資料        分組          聚合結果
全聯 1000   →  [全聯組]  →   全聯 3500
好市多 2000  →  [好市多組] →  好市多 5500
全聯 2500   →  [家樂福組] →  家樂福 2800
好市多 3500
家樂福 2800
```

### 基本分組操作
```python
# 1. 單一聚合
branch_sales = df.groupby('Branch')['Sales'].sum()
print("各品牌總銷售額:")
print(branch_sales.sort_values(ascending=False))

# 2. 多重聚合
summary = df.groupby('Branch')['Sales'].agg([
    'count',    # 交易筆數
    'mean',     # 平均
    'sum',      # 總和
    'min',      # 最小
    'max'       # 最大
])

# 3. 多欄位分組
daily_branch = df.groupby(['Date', 'Branch'])['Sales'].sum()

# 4. 自定義聚合
def sales_range(x):
    return x.max() - x.min()

custom_agg = df.groupby('Branch').agg({
    'Sales': ['sum', 'mean', sales_range],
    'Quantity': 'sum',
    'Customer_ID': 'nunique'
})
```

### 實戰案例
```python
# 品牌表現分析
brand_analysis = df.groupby('Branch').agg({
    'Sales': 'sum',
    'Invoice_ID': 'count',
    'Customer_ID': 'nunique'
}).round(0)

brand_analysis.columns = ['總銷售', '交易筆數', '客戶數']
brand_analysis['客單價'] = (brand_analysis['總銷售'] /
                           brand_analysis['交易筆數']).round(0)
brand_analysis['人均消費'] = (brand_analysis['總銷售'] /
                            brand_analysis['客戶數']).round(0)

print(brand_analysis.sort_values('總銷售', ascending=False))
```

### 時間序列分組
```python
# 每日銷售趨勢
daily_sales = df.groupby(df['Date'].dt.date)['Sales'].sum()

# 週末 vs 平日
weekend_comparison = df.groupby('Is_Weekend')['Sales'].agg([
    'mean', 'sum', 'count'
])
```

### 動畫效果
- 分組過程可視化
- 聚合結果逐步顯示

### 講師口述
```
"GroupBy 是資料分析的核心！
相當於 Excel 的樞紐分析表，但更強大。"
```

---

## 🎬 P11：樞紐分析表 [交叉分析]
### 版面配置
```
Excel 樞紐 vs Pandas Pivot
```

### 內容文字
**標題** (32pt)
```
🔄 Pivot Table：多維度分析
```

**樞紐分析概念**
```
將長資料 → 寬資料
更容易看出模式

長格式：              寬格式：
Date    Branch Sales  Branch   Mon  Tue  Wed
Mon     全聯   1000   全聯     1000 1500 1200
Mon     好市多 2000   好市多   2000 2500 2300
Tue     全聯   1500   家樂福   1800 1600 1900
```

### 建立樞紐分析表
```python
# 基本樞紐表
pivot1 = pd.pivot_table(
    df,
    values='Sales',          # 數值欄位
    index='Branch',          # 列索引
    columns='Product_line',  # 欄索引
    aggfunc='sum'           # 聚合函數
)

# 多重聚合
pivot2 = pd.pivot_table(
    df,
    values='Sales',
    index='Branch',
    columns='Is_Weekend',
    aggfunc=['mean', 'sum', 'count'],
    fill_value=0            # 填補空值
)

# 多層索引
pivot3 = pd.pivot_table(
    df,
    values='Sales',
    index=['Branch', 'Product_line'],
    columns=df['Date'].dt.month_name(),
    aggfunc='sum',
    margins=True,           # 加入總計
    margins_name='總計'
)
```

### 實戰應用
```python
# 品牌 x 時段 銷售矩陣
df['Hour'] = df['Date'].dt.hour
df['Period'] = pd.cut(
    df['Hour'],
    bins=[0, 12, 18, 24],
    labels=['早上', '下午', '晚上']
)

time_analysis = pd.pivot_table(
    df,
    values='Sales',
    index='Branch',
    columns='Period',
    aggfunc='mean'
)

# 熱力圖視覺化
import seaborn as sns
plt.figure(figsize=(10, 6))
sns.heatmap(time_analysis, annot=True, fmt='.0f', cmap='YlOrRd')
plt.title('各品牌不同時段平均銷售額')
```

### 交叉分析
```python
# crosstab 計算頻率
cross = pd.crosstab(
    df['Branch'],
    df['Customer_Level'],
    normalize='index'  # 轉換為百分比
) * 100

print("各品牌客戶等級分布(%):")
print(cross.round(1))
```

### 動畫效果
- 資料重組過程動畫
- 熱力圖漸進填色

### 講師口述
```
"樞紐分析表讓複雜的多維分析變簡單。
這是商業分析最常用的工具！"
```

---

## 🎬 P12：合併資料 - Merge [資料整合]
### 版面配置
```
圖解不同合併類型
```

### 內容文字
**標題** (32pt)
```
🔗 資料合併：整合多個資料源
```

**合併類型圖解**
```
Inner Join（內連接）- 保留共同部分
Left ●●●○○ Right = ●●●

Left Join（左連接）- 保留左邊全部
Left ●●●●● Right = ●●●●●

Right Join（右連接）- 保留右邊全部
Left ●●●○○ Right = ●●●○○

Outer Join（外連接）- 保留全部
Left ●●●●● Right = ●●●●●○○
```

### 程式碼實作
```python
# 準備示範資料
customers = pd.DataFrame({
    'Customer_ID': [1, 2, 3, 4],
    'Name': ['王小明', '李大華', '張美麗', '陳建國'],
    'Level': ['VIP', 'Regular', 'VIP', 'Regular']
})

orders = pd.DataFrame({
    'Order_ID': [101, 102, 103, 104],
    'Customer_ID': [1, 2, 1, 5],
    'Amount': [5000, 3000, 8000, 2000]
})

# 不同類型的合併
# Inner Join - 只保留雙方都有的客戶
inner = pd.merge(customers, orders, on='Customer_ID', how='inner')

# Left Join - 保留所有客戶
left = pd.merge(customers, orders, on='Customer_ID', how='left')

# 多欄位合併
result = pd.merge(
    df1, df2,
    left_on=['Date', 'Branch'],
    right_on=['日期', '分店'],
    how='left'
)
```

### 實務案例
```python
# 合併銷售與庫存資料
sales = df[['Date', 'Branch', 'Product', 'Sales']]
inventory = pd.DataFrame({
    'Branch': ['全聯', '好市多', '家樂福'],
    'Stock': [1000, 1500, 800]
})

# 加入庫存資訊
merged = pd.merge(
    sales,
    inventory,
    on='Branch',
    how='left'
)

# 計算庫存週轉率
merged['Turnover'] = merged['Sales'] / merged['Stock']
```

### 注意事項
```
⚠️ 合併注意事項：
• 確認 key 欄位資料型態一致
• 注意重複欄位的處理（suffixes）
• 留意記憶體使用（大資料）
• 檢查合併後的資料筆數
```

### 動畫效果
- 資料表連接動畫
- 不同 join 類型切換

### 講師口述
```
"Merge 就像 Excel 的 VLOOKUP，
但更靈活、更強大、更快速！"
```

---

## 🎬 P13：資料串接 - Concat [資料組合]
### 版面配置
```
垂直/水平串接示意
```

### 內容文字
**標題** (32pt)
```
📚 串接資料：縱向與橫向組合
```

**串接 vs 合併**
```
Concat：簡單堆疊（像堆積木）
Merge：依據關聯（像拼圖）
```

### 串接操作
```python
# 垂直串接（上下堆疊）
jan_data = pd.read_csv('sales_jan.csv')
feb_data = pd.read_csv('sales_feb.csv')
mar_data = pd.read_csv('sales_mar.csv')

# 合併三個月資料
q1_data = pd.concat([jan_data, feb_data, mar_data],
                    ignore_index=True)

# 水平串接（左右拼接）
basic_info = df[['Customer_ID', 'Name']]
purchase_info = df[['Customer_ID', 'Sales', 'Quantity']]

full_data = pd.concat([basic_info, purchase_info], axis=1)

# 多個 DataFrame 串接
frames = [df1, df2, df3, df4]
result = pd.concat(frames, keys=['Q1', 'Q2', 'Q3', 'Q4'])
```

### 實務應用
```python
# 整合多個分店資料
stores = []
for store in ['taipei', 'taichung', 'kaohsiung']:
    file = f'{store}_sales.csv'
    df_store = pd.read_csv(file)
    df_store['Region'] = store.title()
    stores.append(df_store)

all_stores = pd.concat(stores, ignore_index=True)
print(f"整合後總筆數: {len(all_stores):,}")

# 時間序列擴充
historical = pd.read_csv('sales_2024.csv')
current = pd.read_csv('sales_2025.csv')

all_time = pd.concat([historical, current])
all_time = all_time.sort_values('Date').reset_index(drop=True)
```

### 參數說明
```python
pd.concat(
    objs,              # 要串接的物件清單
    axis=0,            # 0=垂直, 1=水平
    join='outer',      # 'inner' 或 'outer'
    ignore_index=True, # 重新編號索引
    keys=['A', 'B'],   # 加入層級標籤
    sort=False         # 是否排序欄位
)
```

### 動畫效果
- 資料堆疊動畫
- 串接方向示意

### 講師口述
```
"Concat 用於簡單的資料組合，
像是合併多個月份或多個分店的資料。"
```

---

## 🎬 P14：資料庫概念 - ER Model [理論基礎]
### 版面配置
```
ER 圖解說明
```

### 內容文字
**標題** (32pt)
```
🗄️ 關聯式資料庫基礎
```

**ER Model 要素**
```
實體 (Entity) - 方框
屬性 (Attribute) - 橢圓
關係 (Relationship) - 菱形

┌──────────┐       ┌──────────┐
│  客戶     │───<購買>───│  商品     │
├──────────┤       ├──────────┤
│ ID (PK)  │       │ ID (PK)  │
│ 姓名     │       │ 名稱     │
│ 電話     │       │ 價格     │
│ 等級     │       │ 類別     │
└──────────┘       └──────────┘
```

**關係類型**
```
一對一 (1:1)：一個人 - 一張身分證
一對多 (1:N)：一個客戶 - 多筆訂單
多對多 (M:N)：多個學生 - 多門課程
```

### 主鍵與外鍵
```python
# 模擬資料庫結構
# 客戶表（主鍵：Customer_ID）
customers_table = pd.DataFrame({
    'Customer_ID': [1, 2, 3],  # Primary Key
    'Name': ['王小明', '李大華', '張美麗'],
    'Phone': ['0912345678', '0923456789', '0934567890']
})

# 訂單表（外鍵：Customer_ID）
orders_table = pd.DataFrame({
    'Order_ID': [101, 102, 103],  # Primary Key
    'Customer_ID': [1, 2, 1],     # Foreign Key
    'Product': ['手機', '電腦', '平板'],
    'Amount': [15000, 35000, 20000]
})

# 透過外鍵連接
full_orders = pd.merge(
    orders_table,
    customers_table,
    on='Customer_ID',
    how='left'
)
```

### 正規化概念
```
第一正規化 (1NF)：消除重複群組
第二正規化 (2NF)：消除部分相依
第三正規化 (3NF)：消除遞移相依

目的：減少資料重複，維持一致性
```

### 動畫效果
- 關係連線動畫
- 資料表關聯示意

### 講師口述
```
"了解資料庫概念，
能幫助你更好地組織和分析資料。"
```

---

## 🎬 P15：SQL vs Pandas [語法對照]
### 版面配置
```
左右對照表
```

### 內容文字
**標題** (32pt)
```
🔄 SQL ↔ Pandas 對照
```

**常用操作對照**
```python
# SELECT
SQL: SELECT * FROM df
Pandas: df

SQL: SELECT col1, col2 FROM df
Pandas: df[['col1', 'col2']]

# WHERE
SQL: SELECT * FROM df WHERE col > 100
Pandas: df[df['col'] > 100]

# GROUP BY
SQL: SELECT branch, SUM(sales)
     FROM df GROUP BY branch
Pandas: df.groupby('branch')['sales'].sum()

# JOIN
SQL: SELECT * FROM df1
     INNER JOIN df2 ON df1.id = df2.id
Pandas: pd.merge(df1, df2, on='id')

# ORDER BY
SQL: SELECT * FROM df ORDER BY sales DESC
Pandas: df.sort_values('sales', ascending=False)

# LIMIT
SQL: SELECT * FROM df LIMIT 10
Pandas: df.head(10)
```

### 複雜查詢範例
```python
# SQL 複雜查詢
"""
SELECT
    branch,
    COUNT(*) as count,
    AVG(sales) as avg_sales
FROM transactions
WHERE date >= '2025-01-01'
    AND sales > 1000
GROUP BY branch
HAVING COUNT(*) > 10
ORDER BY avg_sales DESC
"""

# Pandas 對應寫法
result = (df[(df['date'] >= '2025-01-01') &
             (df['sales'] > 1000)]
          .groupby('branch')
          .agg(count=('sales', 'count'),
               avg_sales=('sales', 'mean'))
          .query('count > 10')
          .sort_values('avg_sales', ascending=False))
```

### 使用 pandasql
```python
# 直接在 Pandas 中寫 SQL
from pandasql import sqldf

query = """
SELECT branch, SUM(sales) as total
FROM df
WHERE is_weekend = True
GROUP BY branch
ORDER BY total DESC
"""

result = sqldf(query, locals())
```

### 動畫效果
- 語法對應高亮
- 結果即時顯示

### 講師口述
```
"如果你會 SQL，學 Pandas 更容易。
如果不會，Pandas 的語法更直觀！"
```

---

## 🎬 P16：資料輸出 [保存成果]
### 版面配置
```
多種輸出格式展示
```

### 內容文字
**標題** (32pt)
```
💾 保存你的分析成果
```

**輸出格式**
```python
# 1. CSV（最通用）
df.to_csv('output.csv', index=False, encoding='utf-8-sig')

# 2. Excel（包含格式）
with pd.ExcelWriter('report.xlsx') as writer:
    df.to_excel(writer, sheet_name='銷售資料', index=False)
    summary.to_excel(writer, sheet_name='統計摘要')

# 3. JSON（網頁應用）
df.to_json('data.json', orient='records', force_ascii=False)

# 4. Parquet（大數據）
df.to_parquet('data.parquet', compression='snappy')

# 5. SQL 資料庫
from sqlalchemy import create_engine
engine = create_engine('sqlite:///sales.db')
df.to_sql('sales_table', engine, if_exists='replace')
```

### Excel 進階輸出
```python
# 加入格式化的 Excel 輸出
writer = pd.ExcelWriter('formatted_report.xlsx',
                        engine='xlsxwriter')
df.to_excel(writer, sheet_name='Data', index=False)

# 取得工作表
workbook = writer.book
worksheet = writer.sheets['Data']

# 加入格式
money_format = workbook.add_format({'num_format': '$#,##0'})
worksheet.set_column('D:D', 12, money_format)

# 加入圖表
chart = workbook.add_chart({'type': 'column'})
chart.add_series({
    'categories': '=Data!$A$2:$A$10',
    'values': '=Data!$D$2:$D$10',
})
worksheet.insert_chart('H2', chart)

writer.close()
```

### 輸出最佳實踐
```
✅ 輸出建議：
• CSV：純資料交換
• Excel：給非技術人員
• Parquet：大資料儲存
• JSON：API 傳輸
• 記得處理編碼（中文用 utf-8-sig）
```

### 動畫效果
- 檔案生成動畫
- 格式圖標展示

### 講師口述
```
"選對輸出格式很重要。
CSV 通用，Excel 漂亮，Parquet 快速！"
```

---

## 🎬 P17：實戰練習 - 銷售分析報表 [綜合應用]
### 版面配置
```
任務說明 + 完整解答
```

### 內容文字
**標題** (32pt)
```
💼 實戰：月度銷售分析報表
```

**任務需求**
```
📋 老闆要求：
1. 各品牌本月業績排名
2. 週末 vs 平日銷售對比
3. TOP 10 熱銷商品
4. VIP 客戶貢獻分析
5. 銷售趨勢圖表
```

**完整程式碼**
```python
# 讀取資料
df = pd.read_csv('Taiwan_SuperMarket_Sales_2025.csv')
df['Date'] = pd.to_datetime(df['Date'])

# 1. 品牌業績排名
brand_performance = (df.groupby('Branch')
                      .agg({'Sales': 'sum',
                           'Invoice_ID': 'count'})
                      .round(0)
                      .sort_values('Sales', ascending=False))

brand_performance.columns = ['總銷售額', '交易筆數']
brand_performance['平均客單價'] = (
    brand_performance['總銷售額'] /
    brand_performance['交易筆數']
).round(0)

print("=" * 50)
print("品牌業績排名")
print("=" * 50)
print(brand_performance)

# 2. 週末 vs 平日
weekend_analysis = df.groupby('Is_Weekend')['Sales'].agg([
    'mean', 'sum', 'count'
]).round(0)

weekend_analysis.index = ['平日', '週末']
weekend_analysis.columns = ['平均銷售', '總銷售', '交易數']

# 3. TOP 10 商品
top_products = (df.groupby('Product_line')['Sales']
                .sum()
                .nlargest(10)
                .round(0))

# 4. VIP 分析
vip_analysis = df[df['Sales'] > 8000].copy()
vip_contribution = (vip_analysis['Sales'].sum() /
                   df['Sales'].sum() * 100)

print(f"\nVIP客戶(消費>8000)貢獻: {vip_contribution:.1f}%")

# 5. 視覺化
import matplotlib.pyplot as plt
plt.rcParams['font.sans-serif'] = ['Microsoft JhengHei']

fig, axes = plt.subplots(2, 2, figsize=(15, 10))

# 品牌銷售
brand_performance['總銷售額'].plot(kind='bar', ax=axes[0,0])
axes[0,0].set_title('品牌銷售排名')

# 每日趨勢
daily = df.groupby(df['Date'].dt.date)['Sales'].sum()
daily.plot(ax=axes[0,1])
axes[0,1].set_title('每日銷售趨勢')

# 週末對比
weekend_analysis['總銷售'].plot(kind='pie', ax=axes[1,0])
axes[1,0].set_title('週末 vs 平日')

# 商品分類
top_products.plot(kind='barh', ax=axes[1,1])
axes[1,1].set_title('TOP 10 商品')

plt.tight_layout()
plt.show()

# 輸出報表
with pd.ExcelWriter('月度銷售報表.xlsx') as writer:
    brand_performance.to_excel(writer, sheet_name='品牌業績')
    weekend_analysis.to_excel(writer, sheet_name='週末分析')
    top_products.to_excel(writer, sheet_name='熱銷商品')
```

### 講師口述
```
"這就是真實的商業分析！
20 行程式碼完成 Excel 2小時的工作。"
```

---

## 🎬 P18：常見錯誤與解決 [疑難排解]
### 版面配置
```
錯誤類型 + 解決方案
```

### 內容文字
**標題** (32pt)
```
🐛 Pandas 常見錯誤
```

**常見錯誤集錦**
```python
# 1. SettingWithCopyWarning
# ❌ 錯誤寫法
df[df['Sales'] > 1000]['Discount'] = 0.1

# ✅ 正確寫法
df.loc[df['Sales'] > 1000, 'Discount'] = 0.1

# 2. KeyError（欄位不存在）
# ❌ 錯誤
df['sale']  # 欄位名稱錯誤

# ✅ 檢查欄位
print(df.columns.tolist())
df['Sales']  # 正確名稱

# 3. ValueError（形狀不匹配）
# ❌ 錯誤
df['New'] = [1, 2, 3]  # 資料筆數不對

# ✅ 正確
df['New'] = [1, 2, 3] * (len(df) // 3 + 1)[:len(df)]

# 4. TypeError（型態錯誤）
# ❌ 錯誤
df['Sales'] + '100'  # 數字加字串

# ✅ 正確
df['Sales'] + 100
df['Sales'].astype(str) + '100'  # 或轉字串

# 5. Memory Error（記憶體不足）
# 優化方法
df = pd.read_csv('big_file.csv',
                 chunksize=10000,  # 分批讀取
                 dtype={'id': 'int32'})  # 指定型態
```

### 除錯技巧
```python
# 檢查資料型態
df.dtypes
df.info()

# 檢查缺失值
df.isnull().sum()

# 檢查重複值
df.duplicated().sum()

# 檢查記憶體使用
df.memory_usage(deep=True)

# 顯示更多資訊
pd.set_option('display.max_rows', 100)
pd.set_option('display.max_columns', None)
```

### 效能優化
```
⚡ 加速技巧：
• 使用 vectorization 避免迴圈
• 選擇適當的資料型態
• 使用 .loc/.iloc 而非連鎖索引
• 考慮使用 Dask 處理超大資料
```

### 動畫效果
- 錯誤訊息高亮
- 解決方案飛入

### 講師口述
```
"遇到錯誤不要慌！
看錯誤訊息，Google 一下，都能解決。"
```

---

## 🎬 P19：Pandas 學習資源 [持續精進]
### 版面配置
```
資源分類卡片
```

### 內容文字
**標題** (32pt)
```
📚 Pandas 進階學習
```

**推薦資源**
```
📖 必讀文件：
• Pandas 官方文檔
• Pandas Cookbook
• Python for Data Analysis (Wes McKinney)

🎥 影片教程：
• Corey Schafer - Pandas Tutorials
• Keith Galli - Complete Pandas Tutorial

🏋️ 練習平台：
• Kaggle Learn - Pandas
• DataCamp - Data Manipulation
• HackerRank - Python Domain

📊 實戰資料集：
• Kaggle Datasets
• UCI Machine Learning Repository
• Google Dataset Search

💡 進階主題：
• 時間序列分析
• 大數據處理 (Dask, Vaex)
• 資料視覺化整合
• 機器學習前處理
```

### 學習路線圖
```
🗺️ Pandas 精通之路：
基礎 (1-2週)
├── Series & DataFrame
├── 索引與選取
└── 基本操作

進階 (3-4週)
├── GroupBy & Pivot
├── Merge & Join
└── 時間序列

專業 (5-8週)
├── 效能優化
├── 大數據處理
└── 自定義函數
```

### 動畫效果
- 資源卡片滑入
- 路線圖展開

### 講師口述
```
"Pandas 是資料科學的基石。
持續練習，你會越來越強！"
```

---

## 🎬 P20：模組總結 [成就確認]
### 版面配置
```
成就徽章 + 技能清單
```

### 內容文字
**標題** (32pt)
```
🎊 Module 2 完成！
```

**解鎖成就**
```
🏆 成就解鎖：
「資料操控大師」
- 處理 1,000 筆真實數據
- 完成 5+ 種資料操作
- 產出專業分析報表
```

**技能清單**
```
✅ 你現在會的技能：
□ 讀取各種資料格式
□ DataFrame 基本操作
□ 資料篩選與排序
□ 分組聚合分析
□ 樞紐分析表
□ 資料合併與串接
□ 輸出專業報表

💪 你能處理的任務：
• 每日銷售報表自動化
• 客戶分群分析
• 商品銷售排行
• 跨資料源整合
```

### 實戰統計
```
📊 本模組實戰成果：
• 處理資料：1,000 筆
• 完成分析：10+ 項
• 產出圖表：4 張
• 節省時間：2 小時 → 5 分鐘
```

### 下一步
```
⏭️ Module 3 預告：
「資料品質與處理」
• 缺失值處理策略
• 異常值檢測
• 資料轉換技巧
• 特徵工程基礎
```

### 動畫效果
- 徽章旋轉出現
- 技能逐項打勾

### 講師口述
```
"太棒了！你已經能處理真實商業數據了！
休息一下，準備學習資料清理的藝術。"
```

---

## 🎬 P21-25：補充投影片 [彈性運用]

### P21：Q&A 時間
```
❓ 常見問題解答
• Pandas vs NumPy 的選擇
• 大數據處理建議
• 資料庫 vs CSV 的使用時機
```

### P22：作業練習
```
📝 課後作業：
分析你公司/學校的資料
產出一份完整報告
```

### P23：延伸學習
```
🚀 進階技巧：
• MultiIndex 操作
• Window Functions
• 自定義聚合函數
```

### P24：實務經驗分享
```
💼 業界實戰：
• 電商資料分析案例
• 金融風控應用
• 製造業品質分析
```

### P25：過渡到 Module 3
```
Ready for Data Cleaning? 🧹
Module 3 即將開始...
```

---

## 📋 Module 2 教學檢核表

### 時間控制 (60分鐘)
- [ ] P1-P5: 10分鐘 (概念介紹)
- [ ] P6-P10: 20分鐘 (核心操作)
- [ ] P11-P15: 15分鐘 (進階功能)
- [ ] P16-P20: 15分鐘 (實戰應用)

### 關鍵檢查點
- [ ] P4: 成功載入數據
- [ ] P10: GroupBy 理解度
- [ ] P11: Pivot Table 掌握
- [ ] P17: 完成綜合練習

### 教材準備
- [ ] Taiwan_SuperMarket_Sales_2025.csv
- [ ] 程式碼範例檔
- [ ] 輸出報表模板
- [ ] 錯誤排解指南

---

*Module 2 設計完成 - 確保學員掌握 Pandas 核心操作*