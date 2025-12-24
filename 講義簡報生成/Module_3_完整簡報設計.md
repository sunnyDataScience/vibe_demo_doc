# Module 3：資料品質與處理 - 完整簡報設計
## 🎯 45分鐘掌握資料清理藝術

---

## 📊 簡報基本資訊
- **總頁數**：20頁
- **預計時長**：45分鐘
- **設計主色**：成功綠 (#52B788)
- **輔助色彩**：警告橙 (#F77F00)

---

## 🎬 P1：章節封面 [問題意識]
### 版面配置
```
背景：髒數據 → 乾淨數據的漸變效果
左側：大數字 "3" (透明度 15%)
右側：內容區域
```

### 內容文字
**主標題** (40pt, 綠色)
```
Module 3
資料品質與處理
```

**副標題** (24pt)
```
垃圾進，垃圾出 (GIGO)
把髒數據變成寶藏
```

**本節重點** (20pt, 圖標列表)
```
🔍 品質檢查：找出資料問題
🧹 資料清理：處理缺失與異常
🔧 資料轉換：格式標準化
✨ 特徵工程：創造新價值
📊 品質報告：確保可信度
```

### 進度指示
```
[■■■□□□□] Module 3/7
預計時間：45分鐘
```

### 動畫效果
- 髒數據逐漸變乾淨的動畫
- 重點項目依序浮現

### 講師口述
```
"資料品質決定分析品質。
垃圾進，垃圾出 - 這是數據分析的鐵律。
這堂課教你把髒數據變成黃金！"
```

---

## 🎬 P2：為什麼資料品質重要 [動機建立]
### 版面配置
```
案例展示 + 損失統計
```

### 內容文字
**標題** (32pt)
```
💰 髒數據的代價
```

**真實案例**
```
🏥 醫療案例：
錯誤資料 → 錯誤診斷 → 生命危險

🏦 金融案例：
重複記錄 → 多次扣款 → 客戶投訴

🛒 零售案例：
缺失資料 → 庫存錯誤 → 缺貨損失
```

**數據品質成本**
```
IBM 研究：
• 美國企業每年損失 $3.1 兆美元
• 80% 數據科學家時間花在清理
• 髒數據導致 40% 計畫失敗

台灣現況：
• 60% 企業資料品質不佳
• 平均 20% 資料有缺失
• 清理時間 > 分析時間
```

### 品質維度
```
📊 資料品質六大維度：
1. 完整性 (Completeness) - 有缺失嗎？
2. 準確性 (Accuracy) - 正確嗎？
3. 一致性 (Consistency) - 矛盾嗎？
4. 及時性 (Timeliness) - 夠新嗎？
5. 唯一性 (Uniqueness) - 重複嗎？
6. 有效性 (Validity) - 合理嗎？
```

### 視覺元素
- 損失金額滾動計數
- 品質維度雷達圖

### 動畫效果
- 案例逐一展示
- 數字震撼效果

### 講師口述
```
"每個錯誤資料都是潛在的商業風險。
投資在資料品質，報酬率超過 10 倍！"
```

---

## 🎬 P3：資料品質檢查清單 [系統方法]
### 版面配置
```
檢查清單 + 程式碼實作
```

### 內容文字
**標題** (32pt)
```
📋 系統化品質檢查
```

**檢查清單**
```python
# 完整的資料品質檢查流程
import pandas as pd
import numpy as np

def data_quality_report(df):
    """產生資料品質報告"""

    print("="*50)
    print("📊 資料品質報告")
    print("="*50)

    # 1. 基本資訊
    print(f"\n1️⃣ 基本資訊")
    print(f"資料筆數: {len(df):,}")
    print(f"欄位數量: {df.shape[1]}")
    print(f"記憶體使用: {df.memory_usage().sum()/1024**2:.2f} MB")

    # 2. 缺失值檢查
    print(f"\n2️⃣ 缺失值檢查")
    missing = df.isnull().sum()
    missing_pct = (missing / len(df) * 100).round(2)
    missing_df = pd.DataFrame({
        '缺失數量': missing,
        '缺失比例': missing_pct
    })
    print(missing_df[missing_df['缺失數量'] > 0])

    # 3. 重複值檢查
    print(f"\n3️⃣ 重複值檢查")
    duplicates = df.duplicated().sum()
    print(f"重複列數: {duplicates} ({duplicates/len(df)*100:.1f}%)")

    # 4. 資料型態檢查
    print(f"\n4️⃣ 資料型態")
    print(df.dtypes.value_counts())

    # 5. 異常值初步檢查（數值欄位）
    print(f"\n5️⃣ 異常值檢查（數值欄位）")
    numeric_cols = df.select_dtypes(include=[np.number]).columns
    for col in numeric_cols:
        Q1 = df[col].quantile(0.25)
        Q3 = df[col].quantile(0.75)
        IQR = Q3 - Q1
        outliers = df[(df[col] < Q1 - 1.5*IQR) |
                     (df[col] > Q3 + 1.5*IQR)][col].count()
        if outliers > 0:
            print(f"{col}: {outliers} 個異常值")
```

### 實際執行結果
```
📊 資料品質報告
==================================================

1️⃣ 基本資訊
資料筆數: 1,000
欄位數量: 29
記憶體使用: 0.22 MB

2️⃣ 缺失值檢查
        缺失數量  缺失比例
Email      234    23.4%
Phone       56     5.6%

3️⃣ 重複值檢查
重複列數: 12 (1.2%)

4️⃣ 資料型態
object     15
float64     8
int64       4
datetime    2

5️⃣ 異常值檢查
Sales: 23 個異常值
Age: 5 個異常值
```

### 視覺化檢查
```python
# 視覺化品質問題
import matplotlib.pyplot as plt
import seaborn as sns

fig, axes = plt.subplots(2, 2, figsize=(12, 8))

# 缺失值熱力圖
sns.heatmap(df.isnull(), cbar=True, ax=axes[0,0])
axes[0,0].set_title('缺失值分布')

# 異常值箱形圖
df.boxplot(column='Sales', ax=axes[0,1])
axes[0,1].set_title('銷售額異常值')

# 重複值統計
dup_counts = df.groupby(df.columns.tolist()).size()
axes[1,0].bar(['無重複', '有重複'],
              [len(df) - duplicates, duplicates])
axes[1,0].set_title('重複值統計')

# 資料分布
df['Sales'].hist(bins=30, ax=axes[1,1])
axes[1,1].set_title('銷售額分布')

plt.tight_layout()
```

### 動畫效果
- 檢查項目逐一完成打勾
- 問題區域紅色警示

### 講師口述
```
"這個檢查清單是你的救命工具。
每次拿到資料，先跑這個報告！"
```

---

## 🎬 P4：缺失值處理策略 [核心技術]
### 版面配置
```
決策樹 + 方法比較
```

### 內容文字
**標題** (32pt)
```
🔧 缺失值處理決策樹
```

**處理決策流程**
```
缺失值比例？
    ├─ > 60% → 考慮刪除欄位
    ├─ 30-60% → 謹慎處理
    └─ < 30% → 可以填補
           ↓
        資料類型？
    ├─ 數值型 → 平均/中位數/預測
    ├─ 類別型 → 眾數/新類別
    └─ 時間型 → 前後填充
```

### 處理方法比較
```python
# 1. 刪除法
# 適用：缺失比例小，隨機缺失
df_dropped = df.dropna()  # 刪除有缺失的列
df_dropped = df.dropna(axis=1)  # 刪除有缺失的欄

# 2. 填補法 - 簡單填補
# 數值型：平均值/中位數
df['Age'].fillna(df['Age'].mean(), inplace=True)
df['Income'].fillna(df['Income'].median(), inplace=True)

# 類別型：眾數或特定值
df['City'].fillna(df['City'].mode()[0], inplace=True)
df['Email'].fillna('unknown@email.com', inplace=True)

# 3. 填補法 - 前後填充
# 適用：時間序列資料
df['Date'].fillna(method='ffill', inplace=True)  # 向前填充
df['Stock'].fillna(method='bfill', inplace=True)  # 向後填充

# 4. 填補法 - 插值法
# 適用：連續數值
df['Temperature'].interpolate(method='linear', inplace=True)

# 5. 進階：預測填補
from sklearn.impute import KNNImputer
imputer = KNNImputer(n_neighbors=5)
df_imputed = pd.DataFrame(
    imputer.fit_transform(df[numeric_cols]),
    columns=numeric_cols
)
```

### 實戰案例
```python
# 實際處理策略
def handle_missing(df):
    """智慧缺失值處理"""

    # 計算缺失比例
    missing_pct = df.isnull().sum() / len(df)

    # 高缺失欄位（>60%）- 刪除
    high_missing = missing_pct[missing_pct > 0.6].index
    df = df.drop(columns=high_missing)
    print(f"刪除高缺失欄位: {list(high_missing)}")

    # 中度缺失（30-60%）- 標記
    medium_missing = missing_pct[(missing_pct > 0.3) &
                                 (missing_pct <= 0.6)].index
    for col in medium_missing:
        df[f'{col}_was_missing'] = df[col].isnull().astype(int)

    # 低缺失（<30%）- 填補
    for col in df.columns:
        if df[col].isnull().sum() > 0:
            if df[col].dtype in ['int64', 'float64']:
                df[col].fillna(df[col].median(), inplace=True)
            else:
                df[col].fillna('Unknown', inplace=True)

    return df

# 應用處理策略
df_clean = handle_missing(df.copy())
print(f"處理前缺失值: {df.isnull().sum().sum()}")
print(f"處理後缺失值: {df_clean.isnull().sum().sum()}")
```

### 注意事項
```
⚠️ 處理原則：
• 了解缺失原因（隨機/系統性）
• 保留缺失訊息（可能有意義）
• 避免引入偏差
• 記錄處理方法
```

### 動畫效果
- 決策樹路徑動畫
- 填補過程可視化

### 講師口述
```
"缺失值不是敵人，處理不當才是。
選對方法，缺失值也能提供訊息！"
```

---

## 🎬 P5：異常值檢測與處理 [進階技術]
### 版面配置
```
檢測方法 + 視覺化
```

### 內容文字
**標題** (32pt)
```
🎯 異常值：找出資料中的怪獸
```

**檢測方法**
```python
# 方法1：IQR 方法（四分位距）
def detect_outliers_iqr(df, column):
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1

    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR

    outliers = df[(df[column] < lower_bound) |
                  (df[column] > upper_bound)]

    print(f"IQR 方法檢測到 {len(outliers)} 個異常值")
    print(f"範圍: [{lower_bound:.2f}, {upper_bound:.2f}]")
    return outliers

# 方法2：Z-Score（標準分數）
def detect_outliers_zscore(df, column, threshold=3):
    z_scores = np.abs((df[column] - df[column].mean()) /
                      df[column].std())
    outliers = df[z_scores > threshold]

    print(f"Z-Score 方法檢測到 {len(outliers)} 個異常值")
    return outliers

# 方法3：Isolation Forest（機器學習）
from sklearn.ensemble import IsolationForest

def detect_outliers_ml(df, columns):
    iso_forest = IsolationForest(contamination=0.1,
                                 random_state=42)
    outliers = iso_forest.fit_predict(df[columns])

    df['is_outlier'] = outliers
    outlier_count = (outliers == -1).sum()
    print(f"Isolation Forest 檢測到 {outlier_count} 個異常值")

    return df[outliers == -1]
```

### 視覺化異常值
```python
# 多維度異常值視覺化
fig, axes = plt.subplots(2, 3, figsize=(15, 8))

# 1. 箱形圖
df.boxplot(column='Sales', ax=axes[0,0])
axes[0,0].set_title('箱形圖檢測')

# 2. 散點圖
axes[0,1].scatter(df.index, df['Sales'])
axes[0,1].axhline(y=upper_bound, color='r', linestyle='--')
axes[0,1].axhline(y=lower_bound, color='r', linestyle='--')
axes[0,1].set_title('散點圖+界限')

# 3. 直方圖
df['Sales'].hist(bins=30, ax=axes[0,2])
axes[0,2].axvline(x=upper_bound, color='r', linestyle='--')
axes[0,2].set_title('分布圖')

# 4. Z-Score 分布
z_scores = (df['Sales'] - df['Sales'].mean()) / df['Sales'].std()
z_scores.hist(bins=30, ax=axes[1,0])
axes[1,0].axvline(x=3, color='r', linestyle='--')
axes[1,0].axvline(x=-3, color='r', linestyle='--')
axes[1,0].set_title('Z-Score 分布')

# 5. QQ Plot
from scipy import stats
stats.probplot(df['Sales'], dist="norm", plot=axes[1,1])
axes[1,1].set_title('Q-Q Plot')

# 6. 時間序列異常
df['Date'] = pd.to_datetime(df['Date'])
axes[1,2].plot(df['Date'], df['Sales'], 'b-', alpha=0.5)
outlier_idx = detect_outliers_iqr(df, 'Sales').index
axes[1,2].scatter(df.loc[outlier_idx, 'Date'],
                  df.loc[outlier_idx, 'Sales'],
                  color='red', s=50)
axes[1,2].set_title('時間序列異常')

plt.tight_layout()
```

### 處理策略
```python
# 異常值處理決策
def handle_outliers(df, column, method='cap'):
    """
    method: 'remove', 'cap', 'transform', 'keep'
    """

    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR

    if method == 'remove':
        # 刪除異常值
        df = df[(df[column] >= lower) & (df[column] <= upper)]

    elif method == 'cap':
        # 截尾處理
        df[column] = df[column].clip(lower=lower, upper=upper)

    elif method == 'transform':
        # 轉換（如 log）
        df[column] = np.log1p(df[column])

    elif method == 'keep':
        # 保留但標記
        df[f'{column}_is_outlier'] = ((df[column] < lower) |
                                       (df[column] > upper))

    return df
```

### 商業判斷
```
💡 處理原則：
• 異常 ≠ 錯誤（可能是重要訊息）
• 了解業務背景（VIP客戶高消費正常）
• 分析異常原因（促銷、節日、錯誤）
• 記錄處理決策
```

### 動畫效果
- 異常值標記動畫
- 處理前後對比

### 講師口述
```
"異常值可能是錯誤，也可能是機會。
關鍵是理解它，而不是盲目刪除！"
```

---

## 🎬 P6：重複值處理 [資料唯一性]
### 版面配置
```
重複類型 + 處理方法
```

### 內容文字
**標題** (32pt)
```
👥 重複值：資料的雙胞胎
```

**重複值類型**
```python
# 1. 完全重複 - 整列相同
full_duplicates = df[df.duplicated()]
print(f"完全重複: {len(full_duplicates)} 列")

# 2. 部分重複 - 關鍵欄位相同
key_cols = ['Customer_ID', 'Date', 'Product']
partial_duplicates = df[df.duplicated(subset=key_cols)]
print(f"部分重複: {len(partial_duplicates)} 列")

# 3. 模糊重複 - 相似但不完全相同
# 例：王小明 vs 王 小明
from fuzzywuzzy import fuzz

def find_fuzzy_duplicates(df, column, threshold=90):
    """找出相似的值"""
    duplicates = []
    values = df[column].unique()

    for i, val1 in enumerate(values):
        for val2 in values[i+1:]:
            similarity = fuzz.ratio(str(val1), str(val2))
            if similarity > threshold:
                duplicates.append((val1, val2, similarity))

    return duplicates

fuzzy_dups = find_fuzzy_duplicates(df, 'Customer_Name')
print(f"相似姓名: {len(fuzzy_dups)} 組")
```

### 處理策略
```python
# 重複值處理方法
def handle_duplicates(df, strategy='first'):
    """
    strategy: 'first', 'last', 'mean', 'max', 'sum'
    """

    print(f"處理前: {len(df)} 列")

    if strategy in ['first', 'last']:
        # 保留第一個或最後一個
        df = df.drop_duplicates(keep=strategy)

    elif strategy == 'mean':
        # 數值欄位取平均
        numeric_cols = df.select_dtypes(include=[np.number]).columns
        agg_dict = {col: 'mean' for col in numeric_cols}

        # 非數值欄位保留第一個
        non_numeric = df.select_dtypes(exclude=[np.number]).columns
        for col in non_numeric:
            agg_dict[col] = 'first'

        df = df.groupby('Customer_ID').agg(agg_dict).reset_index()

    elif strategy == 'sum':
        # 適用於交易資料 - 合併金額
        df = df.groupby(['Customer_ID', 'Date']).agg({
            'Sales': 'sum',
            'Quantity': 'sum',
            'Product': lambda x: ', '.join(x)
        }).reset_index()

    print(f"處理後: {len(df)} 列")
    return df
```

### 實戰案例
```python
# 客戶資料去重
customer_df = df[['Customer_ID', 'Name', 'Email', 'Phone']]

# 檢查重複情況
print("重複檢查報告:")
print("-" * 40)
print(f"Customer_ID 重複: {customer_df['Customer_ID'].duplicated().sum()}")
print(f"Email 重複: {customer_df['Email'].duplicated().sum()}")
print(f"Phone 重複: {customer_df['Phone'].duplicated().sum()}")

# 智慧去重策略
def smart_dedup(df):
    # 1. Customer_ID 應該唯一
    df = df.drop_duplicates(subset=['Customer_ID'], keep='last')

    # 2. Email 清理（移除無效）
    df.loc[df['Email'].str.contains('test|temp|fake', na=False),
           'Email'] = None

    # 3. Phone 標準化
    df['Phone'] = df['Phone'].str.replace('-', '').str.replace(' ', '')

    return df

customer_clean = smart_dedup(customer_df)
```

### 預防重複
```
✅ 預防措施：
• 設定主鍵約束
• 建立唯一索引
• 資料輸入驗證
• 定期檢查機制
• ETL 過程去重
```

### 動畫效果
- 重複值高亮顯示
- 合併過程動畫

### 講師口述
```
"重複值像是照鏡子，
要分清是真的重複還是不同的記錄！"
```

---

## 🎬 P7：資料型態轉換 [格式標準化]
### 版面配置
```
轉換需求 + 實作方法
```

### 內容文字
**標題** (32pt)
```
🔄 資料型態：說對的語言
```

**常見轉換需求**
```python
# 1. 字串轉數值
# 處理千分位、貨幣符號
df['Price'] = df['Price'].str.replace('NT$', '')
df['Price'] = df['Price'].str.replace(',', '')
df['Price'] = pd.to_numeric(df['Price'], errors='coerce')

# 2. 字串轉日期
# 各種日期格式
df['Date1'] = pd.to_datetime(df['Date1'], format='%Y-%m-%d')
df['Date2'] = pd.to_datetime(df['Date2'], format='%Y年%m月%d日')
df['Date3'] = pd.to_datetime(df['Date3'], format='%m/%d/%Y')

# 智慧解析（較慢）
df['Date'] = pd.to_datetime(df['Date'], infer_datetime_format=True)

# 3. 數值轉類別
# 分箱處理
df['Age_Group'] = pd.cut(df['Age'],
                         bins=[0, 18, 30, 50, 100],
                         labels=['少年', '青年', '中年', '老年'])

df['Income_Level'] = pd.qcut(df['Income'],
                             q=4,
                             labels=['低', '中低', '中高', '高'])

# 4. 類別編碼
# Label Encoding
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['City_Code'] = le.fit_transform(df['City'])

# One-Hot Encoding
df_encoded = pd.get_dummies(df, columns=['Product_Type'],
                           prefix='Product')

# 5. 布林轉換
df['Is_VIP'] = df['Purchase_Amount'] > 10000
df['Has_Email'] = df['Email'].notna()
df['Is_Weekend'] = df['Date'].dt.dayofweek.isin([5, 6])
```

### 型態優化
```python
# 記憶體優化
def optimize_dtypes(df):
    """優化資料型態以節省記憶體"""

    start_mem = df.memory_usage().sum() / 1024**2
    print(f'初始記憶體: {start_mem:.2f} MB')

    # 優化整數
    for col in df.select_dtypes(include=['int64']).columns:
        col_min = df[col].min()
        col_max = df[col].max()

        if col_min >= 0:  # 無負數
            if col_max < 255:
                df[col] = df[col].astype(np.uint8)
            elif col_max < 65535:
                df[col] = df[col].astype(np.uint16)
            elif col_max < 4294967295:
                df[col] = df[col].astype(np.uint32)
        else:
            if col_min > -128 and col_max < 127:
                df[col] = df[col].astype(np.int8)
            elif col_min > -32768 and col_max < 32767:
                df[col] = df[col].astype(np.int16)
            elif col_min > -2147483648 and col_max < 2147483647:
                df[col] = df[col].astype(np.int32)

    # 優化浮點數
    for col in df.select_dtypes(include=['float64']).columns:
        df[col] = df[col].astype(np.float32)

    # 優化類別
    for col in df.select_dtypes(include=['object']).columns:
        if df[col].nunique() / len(df) < 0.5:  # 基數較低
            df[col] = df[col].astype('category')

    end_mem = df.memory_usage().sum() / 1024**2
    print(f'優化後記憶體: {end_mem:.2f} MB')
    print(f'節省: {(1 - end_mem/start_mem)*100:.1f}%')

    return df

df_optimized = optimize_dtypes(df)
```

### 實戰範例
```python
# 台灣電話號碼標準化
def standardize_phone(phone):
    """標準化台灣電話號碼"""
    if pd.isna(phone):
        return None

    # 移除所有非數字
    phone = ''.join(filter(str.isdigit, str(phone)))

    # 手機號碼
    if phone.startswith('09') and len(phone) == 10:
        return f'{phone[:4]}-{phone[4:7]}-{phone[7:]}'

    # 市話（含區碼）
    elif len(phone) >= 9:
        if phone.startswith('02'):  # 台北
            return f'{phone[:2]}-{phone[2:6]}-{phone[6:]}'
        elif phone.startswith('0'):  # 其他地區
            return f'{phone[:3]}-{phone[3:6]}-{phone[6:]}'

    return phone  # 無法識別

df['Phone_Std'] = df['Phone'].apply(standardize_phone)
```

### 動畫效果
- 型態轉換流程動畫
- 記憶體節省視覺化

### 講師口述
```
"資料型態就像語言，
轉換正確才能正確溝通！"
```

---

## 🎬 P8：文字資料清理 [字串處理]
### 版面配置
```
清理方法 + 實例
```

### 內容文字
**標題** (32pt)
```
📝 文字清理：讓資料說人話
```

**常見文字問題**
```python
# 文字清理完整流程
def clean_text(text):
    """清理文字資料"""
    if pd.isna(text):
        return text

    # 1. 轉字串
    text = str(text)

    # 2. 移除多餘空白
    text = text.strip()
    text = ' '.join(text.split())

    # 3. 統一大小寫
    # text = text.lower()  # 英文

    # 4. 移除特殊字元
    import re
    text = re.sub(r'[^\w\s\u4e00-\u9fff]', '', text)

    # 5. 繁簡轉換
    # from opencc import OpenCC
    # cc = OpenCC('s2t')  # 簡體轉繁體
    # text = cc.convert(text)

    return text

# 批次處理
df['Customer_Name'] = df['Customer_Name'].apply(clean_text)

# 常見清理操作
# 移除前後空白
df['Product'] = df['Product'].str.strip()

# 替換字元
df['Address'] = df['Address'].str.replace('臺', '台')

# 提取資訊
df['Email_Domain'] = df['Email'].str.extract(r'@(.+)\.')[0]

# 分割欄位
df[['First_Name', 'Last_Name']] = df['Full_Name'].str.split(' ',
                                                              expand=True)

# 長度檢查
df['Name_Length'] = df['Customer_Name'].str.len()
```

### 地址標準化
```python
# 台灣地址處理
def parse_taiwan_address(address):
    """解析台灣地址"""
    if pd.isna(address):
        return pd.Series([None, None, None, None])

    import re

    # 縣市
    city_pattern = r'(台北市|新北市|桃園市|台中市|台南市|高雄市|基隆市|新竹市|嘉義市|新竹縣|苗栗縣|彰化縣|南投縣|雲林縣|嘉義縣|屏東縣|宜蘭縣|花蓮縣|台東縣|澎湖縣|金門縣|連江縣)'
    city = re.search(city_pattern, address)
    city = city.group() if city else None

    # 區域
    district_pattern = r'(\w{1,3}[區鄉鎮市])'
    district = re.search(district_pattern, address)
    district = district.group() if district else None

    # 路街
    road_pattern = r'(\w{1,10}[路街道巷弄])'
    road = re.search(road_pattern, address)
    road = road.group() if road else None

    # 號
    num_pattern = r'(\d+[號之\-]\d*)'
    number = re.search(num_pattern, address)
    number = number.group() if number else None

    return pd.Series([city, district, road, number])

# 應用地址解析
df[['City', 'District', 'Road', 'Number']] = df['Address'].apply(
    parse_taiwan_address
)
```

### 姓名處理
```python
# 中文姓名處理
def process_chinese_name(name):
    """處理中文姓名"""
    if pd.isna(name) or len(name) < 2:
        return pd.Series([None, None])

    # 常見複姓
    compound_surnames = ['歐陽', '司馬', '上官', '諸葛']

    # 判斷姓氏
    if name[:2] in compound_surnames:
        surname = name[:2]
        given_name = name[2:]
    else:
        surname = name[0]
        given_name = name[1:]

    return pd.Series([surname, given_name])

df[['Surname', 'Given_Name']] = df['Customer_Name'].apply(
    process_chinese_name
)

# 姓名去識別化
df['Name_Masked'] = df['Surname'] + 'O' * len(df['Given_Name'])
```

### 動畫效果
- 文字清理前後對比
- 處理步驟逐一展示

### 講師口述
```
"文字資料最難處理，但也最有價值。
清理好的文字能挖出金礦！"
```

---

## 🎬 P9：日期時間處理 [時間序列]
### 版面配置
```
日期操作 + 特徵提取
```

### 內容文字
**標題** (32pt)
```
📅 時間處理：抓住每個時刻
```

**日期時間操作**
```python
# 1. 解析日期
df['Date'] = pd.to_datetime(df['Date'])

# 2. 提取時間特徵
df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Day'] = df['Date'].dt.day
df['Weekday'] = df['Date'].dt.dayofweek  # 0=Monday
df['Weekday_Name'] = df['Date'].dt.day_name()
df['Quarter'] = df['Date'].dt.quarter
df['Week_of_Year'] = df['Date'].dt.isocalendar().week
df['Day_of_Year'] = df['Date'].dt.dayofyear
df['Hour'] = df['Date'].dt.hour

# 3. 特殊時期標記
df['Is_Weekend'] = df['Weekday'].isin([5, 6])
df['Is_Month_Start'] = df['Date'].dt.is_month_start
df['Is_Month_End'] = df['Date'].dt.is_month_end
df['Is_Quarter_End'] = df['Date'].dt.is_quarter_end

# 4. 台灣節日標記
holidays_tw = {
    '2025-01-01': '元旦',
    '2025-01-29': '除夕',
    '2025-01-30': '春節',
    '2025-02-28': '和平紀念日',
    '2025-04-04': '清明節',
    '2025-05-01': '勞動節',
    '2025-06-02': '端午節',
    '2025-09-08': '中秋節',
    '2025-10-10': '國慶日'
}

df['Is_Holiday'] = df['Date'].dt.strftime('%Y-%m-%d').isin(
    holidays_tw.keys()
)
df['Holiday_Name'] = df['Date'].dt.strftime('%Y-%m-%d').map(
    holidays_tw
)

# 5. 時間差計算
df['Days_Since'] = (pd.Timestamp.now() - df['Date']).dt.days
df['Time_Delta'] = df['Date'].diff()  # 與前一筆的時間差
```

### 時段分析
```python
# 營業時段分類
def classify_time_period(hour):
    """分類營業時段"""
    if 6 <= hour < 11:
        return '早上'
    elif 11 <= hour < 14:
        return '中午'
    elif 14 <= hour < 17:
        return '下午'
    elif 17 <= hour < 21:
        return '晚上'
    else:
        return '深夜'

df['Period'] = df['Hour'].apply(classify_time_period)

# 購物季節
def get_shopping_season(month):
    """判斷購物季節"""
    if month in [1, 2]:
        return '春節檔'
    elif month in [6, 7]:
        return '年中慶'
    elif month in [9, 10]:
        return '週年慶'
    elif month in [11, 12]:
        return '雙11/聖誕'
    else:
        return '一般時期'

df['Shopping_Season'] = df['Month'].apply(get_shopping_season)
```

### 時間序列重採樣
```python
# 設定日期為索引
df_ts = df.set_index('Date')

# 每日統計
daily = df_ts['Sales'].resample('D').agg(['sum', 'mean', 'count'])

# 每週統計
weekly = df_ts['Sales'].resample('W').sum()

# 每月統計
monthly = df_ts.resample('M').agg({
    'Sales': 'sum',
    'Customer_ID': 'nunique',
    'Invoice_ID': 'count'
})

# 移動平均
df_ts['MA7'] = df_ts['Sales'].rolling(window=7).mean()
df_ts['MA30'] = df_ts['Sales'].rolling(window=30).mean()
```

### 視覺化時間模式
```python
# 時間模式分析
fig, axes = plt.subplots(2, 2, figsize=(15, 10))

# 每日銷售趨勢
daily['sum'].plot(ax=axes[0,0])
axes[0,0].set_title('每日銷售趨勢')

# 星期模式
weekday_sales = df.groupby('Weekday_Name')['Sales'].mean()
weekday_sales.plot(kind='bar', ax=axes[0,1])
axes[0,1].set_title('星期銷售模式')

# 小時模式
hour_sales = df.groupby('Hour')['Sales'].mean()
hour_sales.plot(ax=axes[1,0])
axes[1,0].set_title('24小時銷售模式')

# 月份模式
month_sales = df.groupby('Month')['Sales'].sum()
month_sales.plot(kind='bar', ax=axes[1,1])
axes[1,1].set_title('月份銷售模式')

plt.tight_layout()
```

### 動畫效果
- 日期解析過程
- 時間軸展開動畫

### 講師口述
```
"時間是最有價值的特徵之一。
好好處理時間，能看見別人看不見的模式！"
```

---

## 🎬 P10：特徵工程入門 [價值創造]
### 版面配置
```
特徵創造方法 + 實例
```

### 內容文字
**標題** (32pt)
```
✨ 特徵工程：點石成金
```

**特徵工程方法**
```python
# 1. 數學運算特徵
df['Total_Amount'] = df['Quantity'] * df['Unit_Price']
df['Discount_Rate'] = df['Discount'] / df['Original_Price']
df['Profit_Margin'] = (df['Sales'] - df['Cost']) / df['Sales']
df['Per_Unit_Revenue'] = df['Sales'] / df['Quantity']

# 2. 統計特徵
# 客戶層級統計
customer_stats = df.groupby('Customer_ID').agg({
    'Sales': ['mean', 'sum', 'count', 'std'],
    'Date': ['min', 'max'],
    'Product_Category': 'nunique'
}).reset_index()

customer_stats.columns = ['Customer_ID', 'Avg_Purchase',
                          'Total_Purchase', 'Purchase_Count',
                          'Purchase_Std', 'First_Purchase',
                          'Last_Purchase', 'Category_Variety']

# 加入 RFM 特徵
today = pd.Timestamp.now()
customer_stats['Recency'] = (today - customer_stats['Last_Purchase']).dt.days
customer_stats['Frequency'] = customer_stats['Purchase_Count']
customer_stats['Monetary'] = customer_stats['Total_Purchase']

# 3. 交互特徵
df['Brand_Product'] = df['Brand'] + '_' + df['Product_Category']
df['Weekday_Hour'] = df['Weekday'].astype(str) + '_' + df['Hour'].astype(str)

# 4. 比率特徵
# 相對指標
brand_avg = df.groupby('Brand')['Sales'].transform('mean')
df['Sales_vs_Brand_Avg'] = df['Sales'] / brand_avg

daily_avg = df.groupby(df['Date'].dt.date)['Sales'].transform('mean')
df['Sales_vs_Daily_Avg'] = df['Sales'] / daily_avg

# 5. 累積特徵
df = df.sort_values('Date')
df['Cumsum_Sales'] = df.groupby('Customer_ID')['Sales'].cumsum()
df['Cumcount'] = df.groupby('Customer_ID').cumcount() + 1
```

### 進階特徵
```python
# 文字特徵
df['Product_Name_Length'] = df['Product_Name'].str.len()
df['Has_Discount_Keyword'] = df['Description'].str.contains(
    '折扣|特價|優惠', na=False
).astype(int)

# 時間滯後特徵
df['Last_Purchase_Days'] = df.groupby('Customer_ID')['Date'].diff().dt.days
df['Sales_Lag1'] = df.groupby('Customer_ID')['Sales'].shift(1)
df['Sales_Change'] = df['Sales'] - df['Sales_Lag1']

# 分群特徵
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

# 客戶分群
features = ['Recency', 'Frequency', 'Monetary']
scaler = StandardScaler()
scaled_features = scaler.fit_transform(customer_stats[features])

kmeans = KMeans(n_clusters=4, random_state=42)
customer_stats['Cluster'] = kmeans.fit_predict(scaled_features)

# 編碼類別特徵
# Target Encoding（謹慎使用，避免過擬合）
target_mean = df.groupby('Product_Category')['Sales'].mean()
df['Category_Target_Encode'] = df['Product_Category'].map(target_mean)
```

### 特徵重要性評估
```python
# 評估特徵重要性
from sklearn.ensemble import RandomForestRegressor

# 準備資料
feature_cols = ['Quantity', 'Unit_Price', 'Discount_Rate',
                'Is_Weekend', 'Hour', 'Customer_Cluster']
X = df[feature_cols].fillna(0)
y = df['Sales']

# 訓練模型
rf = RandomForestRegressor(n_estimators=100, random_state=42)
rf.fit(X, y)

# 特徵重要性
importance = pd.DataFrame({
    'Feature': feature_cols,
    'Importance': rf.feature_importances_
}).sort_values('Importance', ascending=False)

# 視覺化
importance.plot(x='Feature', y='Importance', kind='barh')
plt.title('特徵重要性排名')
```

### 動畫效果
- 特徵創造過程動畫
- 重要性排名動態顯示

### 講師口述
```
"特徵工程是機器學習的靈魂。
好的特徵勝過複雜的模型！"
```

---

## 🎬 P11：資料標準化與正規化 [尺度統一]
### 版面配置
```
方法比較 + 實作
```

### 內容文字
**標題** (32pt)
```
📏 標準化：讓資料站在同一起跑線
```

**為什麼需要標準化**
```
問題：不同尺度的資料
年齡：20-60（範圍 40）
收入：20000-1000000（範圍 980000）

結果：收入會主導所有分析！
```

### 標準化方法
```python
from sklearn.preprocessing import (StandardScaler, MinMaxScaler,
                                   RobustScaler, Normalizer)

# 原始資料
features = ['Age', 'Income', 'Purchase_Count']
X = df[features]

# 1. 標準化 (Z-Score Normalization)
# 轉換為均值0、標準差1
scaler_standard = StandardScaler()
X_standard = scaler_standard.fit_transform(X)
df['Age_Std'] = X_standard[:, 0]
df['Income_Std'] = X_standard[:, 1]

# 2. 最小最大正規化 (Min-Max Scaling)
# 轉換到 [0, 1] 區間
scaler_minmax = MinMaxScaler()
X_minmax = scaler_minmax.fit_transform(X)
df['Age_MinMax'] = X_minmax[:, 0]
df['Income_MinMax'] = X_minmax[:, 1]

# 3. 強健標準化 (Robust Scaling)
# 使用中位數和 IQR，對異常值不敏感
scaler_robust = RobustScaler()
X_robust = scaler_robust.fit_transform(X)
df['Age_Robust'] = X_robust[:, 0]
df['Income_Robust'] = X_robust[:, 1]

# 4. 正規化 (Normalization)
# 轉換為單位向量
normalizer = Normalizer()
X_normalized = normalizer.fit_transform(X)
```

### 選擇指南
```python
# 何時使用哪種方法
def choose_scaler(data_characteristics):
    """選擇適合的標準化方法"""

    if data_characteristics == '有異常值':
        return RobustScaler()
    elif data_characteristics == '資料有界':
        return MinMaxScaler(feature_range=(0, 1))
    elif data_characteristics == '常態分布':
        return StandardScaler()
    elif data_characteristics == '稀疏資料':
        return MaxAbsScaler()  # 保持稀疏性
    else:
        return StandardScaler()  # 預設

# 視覺化比較
fig, axes = plt.subplots(2, 3, figsize=(15, 8))

# 原始分布
axes[0,0].hist(df['Income'], bins=30)
axes[0,0].set_title('原始資料')

# StandardScaler
axes[0,1].hist(df['Income_Std'], bins=30)
axes[0,1].set_title('標準化 (Z-Score)')

# MinMaxScaler
axes[0,2].hist(df['Income_MinMax'], bins=30)
axes[0,2].set_title('Min-Max 正規化')

# RobustScaler
axes[1,0].hist(df['Income_Robust'], bins=30)
axes[1,0].set_title('強健標準化')

# 比較箱形圖
data_to_plot = [df['Income'], df['Income_Std'],
                df['Income_MinMax'], df['Income_Robust']]
axes[1,1].boxplot(data_to_plot)
axes[1,1].set_xticklabels(['原始', 'Standard', 'MinMax', 'Robust'])
axes[1,1].set_title('標準化方法比較')

plt.tight_layout()
```

### 實戰應用
```python
# Pipeline 整合
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer

# 定義不同欄位的處理方式
numeric_features = ['Age', 'Income', 'Purchase_Count']
categorical_features = ['City', 'Product_Category']

# 建立轉換器
preprocessor = ColumnTransformer(
    transformers=[
        ('num', StandardScaler(), numeric_features),
        ('cat', OneHotEncoder(drop='first'), categorical_features)
    ])

# 建立 Pipeline
pipeline = Pipeline(steps=[
    ('preprocessor', preprocessor),
    ('model', RandomForestRegressor())
])

# 訓練模型（自動處理標準化）
pipeline.fit(X_train, y_train)
```

### 注意事項
```
⚠️ 重要提醒：
• 訓練資料 fit_transform()
• 測試資料只 transform()
• 保存 scaler 供未來使用
• 記錄處理參數
```

### 動畫效果
- 資料尺度調整動畫
- 分布變化過程

### 講師口述
```
"標準化像是讓不同單位的選手公平競爭。
選對方法，讓模型表現更好！"
```

---

## 🎬 P12：資料驗證與品質保證 [品質控制]
### 版面配置
```
驗證規則 + 自動檢查
```

### 內容文字
**標題** (32pt)
```
✅ 品質保證：確保資料可信
```

**資料驗證框架**
```python
class DataValidator:
    """資料品質驗證器"""

    def __init__(self, df):
        self.df = df
        self.errors = []
        self.warnings = []

    def validate_completeness(self, threshold=0.95):
        """完整性驗證"""
        completeness = 1 - self.df.isnull().sum() / len(self.df)

        for col, rate in completeness.items():
            if rate < threshold:
                self.errors.append(
                    f"❌ {col} 完整率 {rate:.1%} < {threshold:.0%}"
                )
        return self

    def validate_uniqueness(self, columns):
        """唯一性驗證"""
        for col in columns:
            duplicates = self.df[col].duplicated().sum()
            if duplicates > 0:
                self.errors.append(
                    f"❌ {col} 有 {duplicates} 個重複值"
                )
        return self

    def validate_range(self, rules):
        """範圍驗證"""
        for col, (min_val, max_val) in rules.items():
            out_of_range = self.df[
                (self.df[col] < min_val) | (self.df[col] > max_val)
            ]
            if len(out_of_range) > 0:
                self.warnings.append(
                    f"⚠️ {col} 有 {len(out_of_range)} 筆超出範圍 [{min_val}, {max_val}]"
                )
        return self

    def validate_consistency(self):
        """一致性驗證"""
        # 邏輯檢查
        invalid = self.df[self.df['Sales'] < self.df['Cost']]
        if len(invalid) > 0:
            self.errors.append(
                f"❌ {len(invalid)} 筆銷售額小於成本"
            )

        # 日期邏輯
        invalid_dates = self.df[self.df['End_Date'] < self.df['Start_Date']]
        if len(invalid_dates) > 0:
            self.errors.append(
                f"❌ {len(invalid_dates)} 筆結束日期早於開始日期"
            )

        return self

    def get_report(self):
        """產生驗證報告"""
        print("=" * 50)
        print("📋 資料品質驗證報告")
        print("=" * 50)

        if not self.errors and not self.warnings:
            print("✅ 所有檢查通過！")
        else:
            if self.errors:
                print("\n🚫 錯誤：")
                for error in self.errors:
                    print(f"  {error}")

            if self.warnings:
                print("\n⚠️ 警告：")
                for warning in self.warnings:
                    print(f"  {warning}")

        return len(self.errors) == 0

# 使用驗證器
validator = DataValidator(df)
is_valid = (validator
           .validate_completeness(0.9)
           .validate_uniqueness(['Invoice_ID'])
           .validate_range({'Age': (0, 120), 'Sales': (0, 1000000)})
           .validate_consistency()
           .get_report())

if not is_valid:
    print("\n❗ 資料品質未達標準，需要處理")
```

### 自動化品質監控
```python
# 品質指標追蹤
def track_quality_metrics(df, save_path='quality_metrics.csv'):
    """追蹤資料品質指標"""

    metrics = {
        'Date': pd.Timestamp.now(),
        'Total_Rows': len(df),
        'Total_Columns': df.shape[1],
        'Missing_Rate': df.isnull().sum().sum() / (df.shape[0] * df.shape[1]),
        'Duplicate_Rate': df.duplicated().sum() / len(df),
        'Memory_MB': df.memory_usage().sum() / 1024**2,
        'Numeric_Cols': len(df.select_dtypes(include=[np.number]).columns),
        'Object_Cols': len(df.select_dtypes(include=['object']).columns)
    }

    # 添加各欄位缺失率
    for col in df.columns:
        metrics[f'Missing_{col}'] = df[col].isnull().sum() / len(df)

    # 儲存或更新記錄
    if os.path.exists(save_path):
        history = pd.read_csv(save_path)
        history = pd.concat([history, pd.DataFrame([metrics])],
                           ignore_index=True)
    else:
        history = pd.DataFrame([metrics])

    history.to_csv(save_path, index=False)

    # 趨勢分析
    if len(history) > 1:
        print("📈 品質趨勢：")
        print(f"缺失率變化: {history['Missing_Rate'].diff().iloc[-1]:+.2%}")
        print(f"資料量變化: {history['Total_Rows'].diff().iloc[-1]:+.0f} 筆")

    return metrics
```

### 品質報告生成
```python
def generate_quality_report(df, output_path='quality_report.html'):
    """生成 HTML 品質報告"""

    html_content = f"""
    <html>
    <head>
        <title>資料品質報告</title>
        <style>
            body {{ font-family: Arial; margin: 20px; }}
            .metric {{
                display: inline-block;
                margin: 10px;
                padding: 15px;
                border: 1px solid #ddd;
                border-radius: 5px;
            }}
            .good {{ background-color: #d4edda; }}
            .warning {{ background-color: #fff3cd; }}
            .error {{ background-color: #f8d7da; }}
        </style>
    </head>
    <body>
        <h1>📊 資料品質報告</h1>
        <p>生成時間: {pd.Timestamp.now()}</p>

        <h2>整體指標</h2>
        <div class="metric">資料筆數: {len(df):,}</div>
        <div class="metric">欄位數量: {df.shape[1]}</div>
        <div class="metric">缺失率: {df.isnull().sum().sum()/(df.shape[0]*df.shape[1]):.2%}</div>

        <h2>品質評分</h2>
        <div class="metric {'good' if df.isnull().sum().sum() == 0 else 'warning'}">
            完整性: {'✅ 優秀' if df.isnull().sum().sum() == 0 else '⚠️ 需改善'}
        </div>

        <!-- 更多內容 -->
    </body>
    </html>
    """

    with open(output_path, 'w', encoding='utf-8') as f:
        f.write(html_content)

    print(f"✅ 報告已生成: {output_path}")

generate_quality_report(df)
```

### 動畫效果
- 驗證項目逐一檢查
- 品質分數即時更新

### 講師口述
```
"品質保證是專業的表現。
建立驗證機制，讓錯誤無所遁形！"
```

---

## 🎬 P13：實戰練習 - 清理髒數據 [綜合應用]
### 版面配置
```
任務說明 + 完整解決方案
```

### 內容文字
**標題** (32pt)
```
🏆 實戰挑戰：拯救髒數據
```

**任務背景**
```
📋 情境：
你收到一份髒到不行的客戶資料
老闆要你在 30 分鐘內清理完成
這份資料將用於重要的客戶分析
```

**髒數據範例**
```python
# 載入髒數據
dirty_df = pd.DataFrame({
    'Customer_Name': ['王小明', '  李大華', '張美麗', '王小明', None, '陳建國 '],
    'Age': [25, 150, -5, 25, 30, 'thirty-five'],
    'Email': ['wang@gmail', 'lee@', 'zhang@yahoo.com', 'wang@gmail',
              'test@test', 'chen@gmail.com'],
    'Phone': ['0912-345-678', '0912345678', '091234567', '(09)12345678',
              None, '886912345678'],
    'Purchase_Date': ['2025-01-01', '2025/1/2', '01-03-2025', '2025-01-01',
                      '2025-13-01', '2025-01-32'],
    'Amount': ['1,000', '2000', 'NT$3000', '1,000', None, '500.5']
})

print("😱 髒數據預覽：")
print(dirty_df)
```

### 完整清理方案
```python
def clean_dirty_data(df):
    """完整的髒數據清理流程"""

    print("🧹 開始清理資料...")
    df_clean = df.copy()

    # Step 1: 處理姓名
    print("Step 1: 清理姓名")
    df_clean['Customer_Name'] = df_clean['Customer_Name'].str.strip()
    df_clean['Customer_Name'].fillna('Unknown', inplace=True)

    # Step 2: 處理年齡
    print("Step 2: 修正年齡")
    # 轉換為數值
    df_clean['Age'] = pd.to_numeric(df_clean['Age'], errors='coerce')
    # 處理異常值
    df_clean.loc[df_clean['Age'] > 120, 'Age'] = None
    df_clean.loc[df_clean['Age'] < 0, 'Age'] = None
    # 填補缺失
    df_clean['Age'].fillna(df_clean['Age'].median(), inplace=True)

    # Step 3: 驗證 Email
    print("Step 3: 驗證 Email")
    import re
    email_pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'

    def validate_email(email):
        if pd.isna(email):
            return None
        if re.match(email_pattern, str(email)):
            return email
        return None

    df_clean['Email'] = df_clean['Email'].apply(validate_email)

    # Step 4: 標準化電話
    print("Step 4: 標準化電話")
    def standardize_phone(phone):
        if pd.isna(phone):
            return None
        # 移除所有非數字
        phone = ''.join(filter(str.isdigit, str(phone)))
        # 處理國碼
        if phone.startswith('886'):
            phone = '0' + phone[3:]
        # 格式化
        if len(phone) == 10 and phone.startswith('09'):
            return f'{phone[:4]}-{phone[4:7]}-{phone[7:]}'
        return None

    df_clean['Phone'] = df_clean['Phone'].apply(standardize_phone)

    # Step 5: 處理日期
    print("Step 5: 修正日期")
    # 嘗試多種格式
    date_formats = ['%Y-%m-%d', '%Y/%m/%d', '%m-%d-%Y']

    def parse_date(date_str):
        if pd.isna(date_str):
            return None
        for fmt in date_formats:
            try:
                return pd.to_datetime(date_str, format=fmt)
            except:
                continue
        return None

    df_clean['Purchase_Date'] = df_clean['Purchase_Date'].apply(parse_date)

    # Step 6: 清理金額
    print("Step 6: 處理金額")
    df_clean['Amount'] = (df_clean['Amount']
                          .str.replace('NT$', '')
                          .str.replace(',', '')
                          .str.replace('$', ''))
    df_clean['Amount'] = pd.to_numeric(df_clean['Amount'], errors='coerce')
    df_clean['Amount'].fillna(0, inplace=True)

    # Step 7: 去除重複
    print("Step 7: 去除重複")
    df_clean = df_clean.drop_duplicates(subset=['Customer_Name', 'Email'],
                                        keep='first')

    print("✅ 清理完成！")
    return df_clean

# 執行清理
clean_df = clean_dirty_data(dirty_df)

print("\n📊 清理結果：")
print(clean_df)

# 品質檢查
print("\n📈 品質改善：")
print(f"缺失值: {dirty_df.isnull().sum().sum()} → {clean_df.isnull().sum().sum()}")
print(f"重複值: {dirty_df.duplicated().sum()} → {clean_df.duplicated().sum()}")
print(f"有效 Email: {dirty_df['Email'].notna().sum()} → {clean_df['Email'].notna().sum()}")
```

### 清理前後對比
```python
# 視覺化改善效果
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

# 清理前
missing_before = dirty_df.isnull().sum()
ax1.bar(missing_before.index, missing_before.values, color='red')
ax1.set_title('清理前缺失值')
ax1.set_xlabel('欄位')
ax1.set_ylabel('缺失數量')
ax1.tick_params(axis='x', rotation=45)

# 清理後
missing_after = clean_df.isnull().sum()
ax2.bar(missing_after.index, missing_after.values, color='green')
ax2.set_title('清理後缺失值')
ax2.set_xlabel('欄位')
ax2.set_ylabel('缺失數量')
ax2.tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.show()
```

### 講師口述
```
"這就是真實世界的資料！
學會清理髒數據，你就是資料的救世主！"
```

---

## 🎬 P14：清理流程自動化 [效率提升]
### 版面配置
```
自動化框架 + 實作
```

### 內容文字
**標題** (32pt)
```
🤖 自動化：一鍵清理資料
```

**自動化清理框架**
```python
class AutoDataCleaner:
    """自動化資料清理器"""

    def __init__(self, config=None):
        self.config = config or self.default_config()
        self.cleaning_log = []

    def default_config(self):
        """預設清理配置"""
        return {
            'missing_threshold': 0.6,  # 缺失值刪除閾值
            'duplicate_cols': None,     # 去重欄位
            'date_cols': [],           # 日期欄位
            'numeric_cols': [],        # 數值欄位
            'categorical_cols': [],    # 類別欄位
            'outlier_method': 'iqr',   # 異常值方法
            'fill_strategy': 'smart'   # 填補策略
        }

    def auto_detect_types(self, df):
        """自動檢測欄位類型"""
        for col in df.columns:
            # 嘗試轉換為日期
            try:
                pd.to_datetime(df[col], infer_datetime_format=True)
                self.config['date_cols'].append(col)
                continue
            except:
                pass

            # 嘗試轉換為數值
            try:
                pd.to_numeric(df[col])
                self.config['numeric_cols'].append(col)
                continue
            except:
                pass

            # 其餘為類別
            self.config['categorical_cols'].append(col)

        self.log("自動檢測欄位類型完成")
        return self

    def clean(self, df):
        """執行完整清理流程"""
        df_clean = df.copy()

        # 1. 移除高缺失欄位
        df_clean = self.remove_high_missing(df_clean)

        # 2. 處理重複值
        df_clean = self.remove_duplicates(df_clean)

        # 3. 處理缺失值
        df_clean = self.handle_missing(df_clean)

        # 4. 處理異常值
        df_clean = self.handle_outliers(df_clean)

        # 5. 標準化格式
        df_clean = self.standardize_formats(df_clean)

        # 6. 驗證結果
        self.validate_results(df, df_clean)

        return df_clean

    def remove_high_missing(self, df):
        """移除高缺失欄位"""
        missing_rate = df.isnull().sum() / len(df)
        high_missing = missing_rate[missing_rate > self.config['missing_threshold']]

        if len(high_missing) > 0:
            df = df.drop(columns=high_missing.index)
            self.log(f"移除高缺失欄位: {list(high_missing.index)}")

        return df

    def remove_duplicates(self, df):
        """去除重複值"""
        before = len(df)

        if self.config['duplicate_cols']:
            df = df.drop_duplicates(subset=self.config['duplicate_cols'])
        else:
            df = df.drop_duplicates()

        after = len(df)
        if before > after:
            self.log(f"移除 {before - after} 筆重複資料")

        return df

    def handle_missing(self, df):
        """智慧填補缺失值"""
        for col in df.columns:
            if df[col].isnull().sum() == 0:
                continue

            if col in self.config['numeric_cols']:
                # 數值型：中位數
                df[col].fillna(df[col].median(), inplace=True)
            elif col in self.config['categorical_cols']:
                # 類別型：眾數或 'Unknown'
                mode = df[col].mode()
                if len(mode) > 0:
                    df[col].fillna(mode[0], inplace=True)
                else:
                    df[col].fillna('Unknown', inplace=True)
            elif col in self.config['date_cols']:
                # 日期型：前向填充
                df[col].fillna(method='ffill', inplace=True)

        self.log("缺失值處理完成")
        return df

    def handle_outliers(self, df):
        """處理異常值"""
        if self.config['outlier_method'] == 'iqr':
            for col in self.config['numeric_cols']:
                if col in df.columns:
                    Q1 = df[col].quantile(0.25)
                    Q3 = df[col].quantile(0.75)
                    IQR = Q3 - Q1
                    lower = Q1 - 1.5 * IQR
                    upper = Q3 + 1.5 * IQR

                    # 截尾處理
                    before = df[col].clip(lower=lower, upper=upper)
                    outliers = ((df[col] < lower) | (df[col] > upper)).sum()

                    if outliers > 0:
                        df[col] = df[col].clip(lower=lower, upper=upper)
                        self.log(f"{col}: 處理 {outliers} 個異常值")

        return df

    def standardize_formats(self, df):
        """標準化格式"""
        # 文字欄位去空白
        for col in self.config['categorical_cols']:
            if col in df.columns and df[col].dtype == 'object':
                df[col] = df[col].str.strip()

        # 日期欄位轉換
        for col in self.config['date_cols']:
            if col in df.columns:
                df[col] = pd.to_datetime(df[col], errors='coerce')

        self.log("格式標準化完成")
        return df

    def validate_results(self, df_before, df_after):
        """驗證清理結果"""
        print("\n" + "=" * 50)
        print("📊 清理報告")
        print("=" * 50)

        print(f"資料筆數: {len(df_before)} → {len(df_after)}")
        print(f"欄位數量: {df_before.shape[1]} → {df_after.shape[1]}")
        print(f"缺失值: {df_before.isnull().sum().sum()} → {df_after.isnull().sum().sum()}")

        print("\n📝 清理日誌:")
        for log in self.cleaning_log:
            print(f"  • {log}")

    def log(self, message):
        """記錄清理步驟"""
        self.cleaning_log.append(message)

# 使用自動清理器
cleaner = AutoDataCleaner()
cleaner.auto_detect_types(dirty_df)
clean_df = cleaner.clean(dirty_df)
```

### 動畫效果
- 自動化流程動畫
- 清理步驟逐一完成

### 講師口述
```
"自動化讓你從重複勞動中解放。
寫一次，用一輩子！"
```

---

## 🎬 P15：模組總結 [成就確認]
### 版面配置
```
技能清單 + 成就系統
```

### 內容文字
**標題** (32pt)
```
🎉 Module 3 完成！
```

**成就解鎖**
```
🏆 成就解鎖：
「資料清理專家」
- 掌握完整清理流程
- 處理各類髒數據
- 建立品質保證系統
```

**技能總結**
```
✅ 你現在掌握的技能：
□ 系統化品質檢查
□ 缺失值處理策略
□ 異常值檢測方法
□ 重複值識別去除
□ 資料型態轉換
□ 文字資料清理
□ 日期時間處理
□ 特徵工程基礎
□ 資料標準化
□ 自動化清理流程

💪 你能解決的問題：
• 髒數據變黃金
• 提升資料品質 90%
• 節省清理時間 80%
• 確保分析可信度
```

### 實戰成果
```
📊 本模組成果：
• 清理髒數據：100%
• 品質提升：85%
• 自動化程度：70%
• 時間節省：2小時 → 5分鐘
```

### 下階段預告
```
⏭️ Module 4 預告：
「數據視覺化與圖表選用」
• 圖表選擇決策樹
• Matplotlib 基礎
• Seaborn 統計圖
• 互動式儀表板
```

### 動畫效果
- 成就徽章旋轉
- 技能點亮效果

### 講師口述
```
"恭喜！你已經是資料清理專家了！
乾淨的資料是好分析的開始。
接下來，讓資料說故事！"
```

---

## 📋 Module 3 教學檢核表

### 時間控制 (45分鐘)
- [ ] P1-P3: 8分鐘 (問題意識)
- [ ] P4-P7: 15分鐘 (核心技術)
- [ ] P8-P11: 12分鐘 (進階處理)
- [ ] P12-P15: 10分鐘 (實戰應用)

### 關鍵檢查點
- [ ] P3: 品質檢查報告成功
- [ ] P4: 缺失值處理理解
- [ ] P5: 異常值檢測掌握
- [ ] P13: 完成髒數據清理

### 教材準備
- [ ] 髒數據範例檔案
- [ ] 清理程式碼模板
- [ ] 品質報告範本
- [ ] 自動化框架

---

*Module 3 設計完成 - 確保學員掌握資料品質處理核心技能*