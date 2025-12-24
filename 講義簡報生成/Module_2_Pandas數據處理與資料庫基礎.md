# Module 2：Pandas數據處理核心 + 資料庫基礎
## 時間：10:15-12:00（105分鐘，含休息）

📁 **資料集：Supermarket Sales（1,000筆）- 開始使用真實資料**

---

## 時間配置
- **10:15-10:30**：資料庫基礎概念（15分鐘）
- **10:30-10:45**：休息時間
- **10:45-11:00**：Pandas DataFrame入門（15分鐘）
- **11:00-12:00**：Pandas實戰練習（60分鐘）

---

## Part 1：資料庫基礎知識（15分鐘）

### 關聯式資料庫核心概念

#### 實體關係模型（ER Model）
```
【概念】
- 實體（Entity）：真實世界的對象（如客戶、產品）
- 屬性（Attribute）：實體的特徵（如客戶姓名、產品價格）
- 關係（Relationship）：實體間的關聯

【範例】
客戶 ──購買──> 產品
  ↓              ↓
姓名、地址     價格、庫存
```

#### 主鍵與外鍵
```sql
-- 主鍵（Primary Key）：唯一識別每筆記錄
CustomerID: C001, C002, C003...

-- 外鍵（Foreign Key）：連結到其他表格
訂單表.CustomerID -> 客戶表.CustomerID
```

#### SQL JOIN 操作對應 Pandas
| SQL | Pandas | 說明 |
|:----|:-------|:-----|
| INNER JOIN | pd.merge(how='inner') | 只保留兩表都有的 |
| LEFT JOIN | pd.merge(how='left') | 保留左表全部 |
| RIGHT JOIN | pd.merge(how='right') | 保留右表全部 |
| FULL JOIN | pd.merge(how='outer') | 保留兩表全部 |

### 樞紐分析（Pivot）概念

#### 樞紐轉換 = 長轉寬
```python
# 長格式 -> 寬格式
# 原始數據
月份  產品  銷售額
1月   A    1000
1月   B    2000
2月   A    1500

# 樞紐後
產品   1月   2月
A     1000  1500
B     2000   NaN

# Pandas操作
df.pivot(index='產品', columns='月份', values='銷售額')
```

#### Prompt模板
```
"將[欄位A]的值轉換為新的欄位，
以[欄位B]為索引，[欄位C]為值"
```

---

## Part 2：Pandas 數據處理核心（75分鐘）

### 2-1 認識 DataFrame（15分鐘）

#### DataFrame = Excel的Python版
```python
# 載入數據
import pandas as pd
df = pd.read_csv('supermarket_sales.csv')

# 基本查看
df.head()      # 前5筆
df.info()      # 資料類型
df.describe()  # 統計摘要
df.shape       # (筆數, 欄位數)
```

#### 選取資料
```python
# 選欄位
df['Branch']           # 單一欄位
df[['Branch', 'Total']]  # 多個欄位

# 選列
df.iloc[0]      # 第一列
df.iloc[0:5]    # 前5列
```

### 2-2 數據篩選與過濾（20分鐘）

#### 條件篩選
```python
# 單一條件
高消費 = df[df['Total'] > 1000]

# 多重條件
vip_女性 = df[(df['Total'] > 1000) & (df['Gender'] == 'Female')]

# 包含條件
特定分店 = df[df['Branch'].isin(['A', 'B'])]
```

#### Prompt模板
```
"篩選出[欄位]符合[條件]的所有記錄，
並顯示筆數和前10筆"
```

### 2-3 數據聚合與分組（20分鐘）

#### GroupBy分組統計
```python
# 基本分組
分店統計 = df.groupby('Branch')['Total'].sum()

# 多重聚合
統計結果 = df.groupby('Branch').agg({
    'Total': ['sum', 'mean', 'count'],
    'Quantity': 'sum'
})

# 多層分組
df.groupby(['Branch', 'Product line'])['Total'].sum()
```

#### 商業應用範例
- 各分店銷售總額
- 各產品線平均單價
- 各客戶類型購買頻率

### 2-4 數據合併（20分鐘）

#### 合併操作
```python
# 橫向合併（JOIN）
結果 = pd.merge(客戶表, 訂單表, on='CustomerID', how='left')

# 縱向合併（堆疊）
全年數據 = pd.concat([Q1, Q2, Q3, Q4])

# 實用技巧
# 處理重複欄位名
pd.merge(df1, df2, on='ID', suffixes=('_左', '_右'))
```

---

## Part 3：實戰練習（60分鐘）

### 10:15-11:00 Pandas入門練習

#### 練習1：Top 10產品（15分鐘）
```python
# 任務：找出銷售額最高的10個產品線
# 步驟：
# 1. 按產品線分組
# 2. 計算總銷售額
# 3. 排序取前10

top_products = df.groupby('Product line')['Total'].sum()\
                 .sort_values(ascending=False)\
                 .head(10)
```

#### 練習2：分店比較（15分鐘）
```python
# 任務：比較ABC三家分店的業績
# 計算：總銷售、平均客單價、客戶數

branch_analysis = df.groupby('Branch').agg({
    'Total': ['sum', 'mean'],
    'Invoice ID': 'count'
})
```

### 11:00-12:00 數據清洗實戰

#### 練習3：髒數據挑戰（30分鐘）
```python
# 處理問題數據
# 1. 檢查缺失值
df.isnull().sum()

# 2. 處理重複值
df.drop_duplicates()

# 3. 數據類型轉換
df['Date'] = pd.to_datetime(df['Date'])

# 4. 異常值處理
Q1 = df['Total'].quantile(0.25)
Q3 = df['Total'].quantile(0.75)
IQR = Q3 - Q1
異常值 = df[(df['Total'] < Q1 - 1.5*IQR) |
           (df['Total'] > Q3 + 1.5*IQR)]
```

#### 練習4：創建新特徵（30分鐘）
```python
# 創建有用的新欄位
# 1. 提取月份
df['Month'] = pd.to_datetime(df['Date']).dt.month

# 2. 客戶分級
df['Customer_Level'] = df['Total'].apply(
    lambda x: 'VIP' if x > 500 else '一般'
)

# 3. 時段分析
df['Hour'] = pd.to_datetime(df['Time']).dt.hour
df['時段'] = pd.cut(df['Hour'],
                    bins=[0, 12, 18, 24],
                    labels=['早上', '下午', '晚上'])
```

---

## 重點提醒

### DataFrame操作口訣
1. **讀取**：read_csv/read_excel
2. **查看**：head/info/describe
3. **篩選**：用布林索引
4. **分組**：groupby + agg
5. **合併**：merge/concat

### 常見錯誤
- 欄位名稱大小寫錯誤
- 忘記重新賦值（df = df.drop...）
- 資料類型不匹配

### Prompt萬用模板
```
"用pandas處理supermarket_sales.csv，
完成以下任務：
1. [具體任務描述]
2. [預期輸出格式]
3. [特殊要求]"
```

---

## 課堂筆記區
（學員可在此記錄重點）

---

## 延伸學習
- Pandas官方文檔
- 10 minutes to pandas
- SQL與Pandas對照表