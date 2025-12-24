# Module 1：Python基礎概念速成 + 開發環境設置
## 時間：09:20-10:15（55分鐘）

📁 **資料集：簡單範例資料（自建5-10筆示範）+ Supermarket初探**

---

## 時間配置
- **09:20-09:30**：Python基礎語法（10分鐘講解）
- **09:30-10:00**：基礎實作練習（30分鐘動手）
- **10:00-10:15**：開發環境與工具介紹（15分鐘）

---

## Part 1：Python 基礎概念速成

### 1-1 變數與資料類型（10分鐘）

#### 概念講解
```python
# 變數 = 容器（裝數據的盒子）

# 數字
age = 32                    # 整數 (int)
price = 299.99             # 浮點數 (float)

# 文字
name = "王小明"            # 字串 (string)
product = "iPhone"

# 布林值
is_vip = True              # 布林 (boolean)
in_stock = False

# 列表（多個資料）
products = ["手機", "耳機", "充電線"]    # list

# 字典（有標籤的資料）
customer = {
    "name": "王小明",
    "age": 32,
    "is_vip": True
}                          # dict
```

#### Prompt 模板
```
"請幫我創建變數來儲存 [數據描述]，
例如 [具體例子]"
```

### 1-2 邏輯控制：條件判斷（10分鐘）

#### 概念：如果...就...否則...
```python
# 商業應用範例

# 客戶分級
if total_amount > 10000:
    customer_level = "VIP"
else:
    customer_level = "一般"

# 庫存警示
if stock < 100:
    print("庫存不足，請補貨！")

# 折扣計算
if quantity > 5:
    discount = 0.9  # 打9折
```

#### Prompt 模板
```
"請寫一個條件判斷：
如果 [條件描述]，
就 [動作1]，
否則 [動作2]"
```

### 1-3 迴圈：重複執行（10分鐘）

#### 概念：對每個...都做...
```python
# 批次處理範例

# 計算每個產品的毛利
products = ["A", "B", "C"]
for product in products:
    print(f"計算{product}的毛利")

# 發送郵件給每個客戶
for customer in customer_list:
    send_email(customer)
```

#### Prompt 模板
```
"請用迴圈處理 [資料集合]，
對每個 [項目] 執行 [動作]"
```

### 1-4 函數：打包重複使用（5分鐘）

#### 概念：工具包
```python
# 定義函數
def calculate_discount(price, quantity):
    if quantity > 5:
        return price * 0.9
    return price

# 使用函數
final_price = calculate_discount(1000, 6)
```

---

## Part 2：基礎實作練習（30分鐘）

### 練習1：Hello Data（10分鐘）
```python
# 任務：載入Supermarket銷售數據
# Prompt：「幫我用pandas讀取supermarket_sales.csv」
# 成功標準：看到前5筆數據

import pandas as pd
df = pd.read_csv("supermarket_sales.csv")
df.head()
```

### 練習2：我的第一個分析（10分鐘）
```python
# 任務：計算總銷售額
# Prompt：「計算Total欄位的總和」
# 成功標準：得出一個數字

total_sales = df['Total'].sum()
print(f"總銷售額: {total_sales}")
```

### 練習3：簡單篩選（10分鐘）
```python
# 任務：找出所有女性客戶的購買記錄
# Prompt：「篩選Gender欄位為Female的資料」
# 成功標準：顯示篩選結果

female_customers = df[df['Gender'] == 'Female']
print(f"女性客戶筆數: {len(female_customers)}")
```

---

## Part 3：開發環境與工具（15分鐘）

### CMD vs IDE 的選擇

| 工具 | 適用場景 | 優點 | 缺點 |
|:-----|:---------|:-----|:-----|
| **命令列** | 伺服器、自動化 | 輕量、快速 | 不友善 |
| **VS Code** | 日常開發 | 免費、擴充多 | 需設定 |
| **Jupyter** | 數據分析 | 互動式、視覺化 | 不適合大專案 |
| **PyCharm** | 大型專案 | 功能完整 | 付費、重 |

### GitHub：程式碼的雲端硬碟

#### 為什麼要學？
- **求職必備**：企業看GitHub比履歷重要
- **學習資源**：看別人的程式碼學習
- **備份保護**：永遠不怕檔案遺失

#### 4個必學命令
```bash
# 1. 下載專案
git clone [網址]

# 2. 保存修改
git add .
git commit -m "修改說明"

# 3. 上傳雲端
git push

# 4. 同步更新
git pull
```

### 虛擬環境：專案隔離

```bash
# 創建虛擬環境
python -m venv myenv

# 啟動（Windows）
myenv\Scripts\activate

# 安裝套件
pip install pandas

# 儲存套件清單
pip freeze > requirements.txt
```

### 良好開發習慣

#### 檔案命名
✅ `data_analysis_2024.py`
✅ `customer_segmentation.ipynb`
❌ `test.py`、`分析.py`、`my code.py`

#### 專案結構
```
my_project/
├── data/          # 原始數據
├── notebooks/     # Jupyter筆記本
├── src/          # 程式碼
├── outputs/      # 結果輸出
└── README.md     # 專案說明
```

---

## 除錯技巧速查

### 常見錯誤
1. **SyntaxError**：語法錯誤（少了冒號、括號）
2. **NameError**：變數未定義
3. **TypeError**：資料類型錯誤
4. **KeyError**：欄位名稱錯誤

### 除錯步驟
1. 讀錯誤訊息
2. Google錯誤
3. print()檢查
4. 請AI幫忙

### Prompt模板
```
"這是我的錯誤訊息：[錯誤]
程式碼是：[程式]
請幫我debug"
```

---

## 課堂筆記區
（學員可在此記錄重點）

---

## 作業
1. 創建自己的GitHub帳號
2. 練習基本git命令
3. 完成三個基礎練習