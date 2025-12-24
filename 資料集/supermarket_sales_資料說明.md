# 超市銷售資料集說明
## Supermarket Sales Dataset Documentation

---

## 資料集概述

- **資料來源**: [Kaggle - Supermarket Sales Dataset](https://www.kaggle.com/datasets/faresashraf1001/supermarket-sales)
- **授權方式**: Apache 2.0 License
- **資料筆數**: 1,000 筆交易記錄
- **時間範圍**: 2019年1月至3月
- **地區涵蓋**: 緬甸三個主要城市的超市分店

## 資料集描述

此資料集記錄了一家連鎖超市在緬甸三個城市分店的詳細交易資料。每筆記錄代表一個完整的銷售交易，包含客戶資訊、商品細節、付款方式及客戶滿意度評分等重要商業資訊。

## 欄位說明

### 基本交易資訊
| 欄位名稱 | 資料型態 | 說明 |
|---------|---------|------|
| Invoice ID | String | 唯一交易識別碼 (格式: XXX-XX-XXXX) |
| Date | Date | 交易日期 (MM/DD/YYYY) |
| Time | Time | 交易時間 (HH:MM:SS AM/PM) |

### 地點與客戶資訊
| 欄位名稱 | 資料型態 | 說明 |
|---------|---------|------|
| Branch | String | 分店代碼 (Alex, Cairo, Giza) |
| City | String | 城市名稱 (Yangon, Naypyitaw, Mandalay) |
| Customer type | String | 客戶類型 (Member: 會員, Normal: 一般客戶) |
| Gender | String | 客戶性別 (Male, Female) |

### 商品資訊
| 欄位名稱 | 資料型態 | 說明 |
|---------|---------|------|
| Product line | String | 商品類別 (共6類) |
| Unit price | Float | 單價 (美元) |
| Quantity | Integer | 購買數量 |

### 商品類別
1. **Health and beauty** - 健康與美容產品
2. **Electronic accessories** - 電子配件
3. **Home and lifestyle** - 家居生活用品
4. **Sports and travel** - 運動與旅遊用品
5. **Food and beverages** - 食品與飲料
6. **Fashion accessories** - 時尚配飾

### 財務資訊
| 欄位名稱 | 資料型態 | 說明 |
|---------|---------|------|
| Tax 5% | Float | 稅額 (5% 稅率) |
| Sales | Float | 銷售總額 (含稅) |
| Payment | String | 付款方式 (Cash, Credit card, Ewallet) |
| cogs | Float | 銷貨成本 (Cost of Goods Sold) |
| gross margin percentage | Float | 毛利率 (固定為 4.76%) |
| gross income | Float | 毛利 |

### 客戶反饋
| 欄位名稱 | 資料型態 | 說明 |
|---------|---------|------|
| Rating | Float | 客戶滿意度評分 (1.0 - 10.0) |

## 資料特徵

### 地理分布
- **三個分店**: Alex, Cairo, Giza
- **三個城市**:
  - Yangon (仰光) - 緬甸最大城市
  - Naypyitaw (奈比多) - 首都
  - Mandalay (曼德勒) - 第二大城市

### 付款方式
- 現金支付 (Cash)
- 信用卡支付 (Credit card)
- 電子錢包 (Ewallet)

### 關鍵指標
- **毛利率**: 所有交易固定為 4.76%
- **稅率**: 統一 5% 營業稅
- **評分範圍**: 1.0 至 10.0 分

## 適用分析類型

### 銷售分析
- 銷售趨勢分析
- 熱門商品類別識別
- 分店績效比較
- 時段銷售模式

### 客戶分析
- 客戶購買行為分析
- 會員與非會員消費差異
- 性別消費偏好
- 客戶滿意度影響因素

### 財務分析
- 營收分析
- 毛利分析
- 付款方式偏好
- 價格敏感度分析

### 預測模型
- 銷售預測
- 客戶流失預測
- 庫存需求預測
- 客戶滿意度預測

## 資料品質注意事項

1. **固定毛利率**: 所有交易毛利率皆為 4.76%，可能為簡化假設
2. **完整性**: 資料集無缺失值，適合初學者練習
3. **時間範圍**: 僅涵蓋三個月資料，長期趨勢分析受限
4. **地區限制**: 僅限緬甸市場，跨國分析不適用

## 使用建議

### 初學者
- 基礎統計分析練習
- 資料視覺化入門
- SQL 查詢練習

### 中階使用者
- 客戶分群 (Customer Segmentation)
- RFM 分析
- 關聯規則挖掘

### 進階使用者
- 時間序列預測
- 機器學習模型建立
- 商業智慧儀表板開發

## 資料載入範例

### Python (Pandas)
```python
import pandas as pd

# 載入資料
df = pd.read_csv('SuperMarket Analysis.csv')

# 基本資訊
print(df.info())
print(df.head())

# 資料型態轉換
df['Date'] = pd.to_datetime(df['Date'])
df['Time'] = pd.to_datetime(df['Time'], format='%I:%M:%S %p').dt.time
```

### 快速統計摘要
```python
# 數值欄位統計
print(df.describe())

# 類別欄位分布
print(df['Product line'].value_counts())
print(df['Payment'].value_counts())
print(df['Branch'].value_counts())
```

## 相關資源

- [Kaggle 資料集頁面](https://www.kaggle.com/datasets/faresashraf1001/supermarket-sales)
- [Apache 2.0 授權條款](https://www.apache.org/licenses/LICENSE-2.0)

---

*最後更新: 2024年12月*