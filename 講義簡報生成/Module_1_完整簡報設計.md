# Module 1：Python基礎與開發環境 - 完整簡報設計
## 🎯 45分鐘掌握程式基礎

---

## 📊 簡報基本資訊
- **總頁數**：20頁
- **預計時長**：45分鐘
- **設計主色**：科技藍 (#2E86AB)
- **次要色彩**：橙色強調 (#F18F01)

---

## 🎬 P1：章節封面 [定位導航]
### 版面配置
```
左側：大數字 "1" (200pt, 10% 透明度)
右側：內容區域
底部：進度條
```

### 內容文字
**主標題** (40pt, 深藍)
```
Module 1
Python 基礎與開發環境
```

**學習目標** (24pt)
```
本節你將學會：
📌 變數與資料類型
📌 邏輯控制流程
📌 開發環境設置
📌 版本控制基礎
```

**預估時間**
```
⏱️ 45 分鐘
💻 70% 實作
📖 30% 講解
```

### 進度指示
```
[■□□□□□□] Module 1/7
```

### 動畫效果
- 數字 "1" 淡入
- 學習目標逐項滑入
- 進度條填充動畫

---

## 🎬 P2：為什麼從變數開始 [概念引入]
### 版面配置
```
上下分割 (30/70)
```

### 內容文字
**標題** (32pt)
```
🎯 程式的基礎：變數
```

**類比說明**
```
生活中的容器 → 程式中的變數

📦 紙箱          = 變數名稱
📝 標籤          = 變數名稱
🎁 內容物        = 變數的值
🏷️ 類型標記      = 資料型態
```

**實際對應**
```
現實世界                程式世界
─────────────────────────────────
姓名牌: "王小明"    →    name = "王小明"
年齡: 25           →    age = 25
薪水: 45000        →    salary = 45000.0
已婚: 是           →    is_married = True
```

### 視覺元素
- 使用圖標增強理解
- 箭頭顯示對應關係

### 講師口述
```
"變數就像是貼了標籤的盒子，
我們可以把資料放進去，需要時再拿出來。
這是所有程式設計的基礎！"
```

---

## 🎬 P3：Python 變數命名規則 [規範說明]
### 版面配置
```
規則清單 + 範例對比
```

### 內容文字
**標題** (32pt)
```
📝 變數命名規則
```

**命名規則**
```
✅ 可以這樣命名：
• 使用字母、數字、底線
• 必須以字母或底線開頭
• 區分大小寫
• 使用有意義的名稱

❌ 不能這樣命名：
• 不能用數字開頭
• 不能包含空格
• 不能用 Python 保留字
• 不要用中文（雖然可以）
```

**好壞範例對比**
```python
# ✅ 好的命名
customer_name = "張三"
total_amount = 10000
is_vip_member = True
product_list = ["手機", "電腦"]

# ❌ 壞的命名
1st_customer = "張三"     # 數字開頭
total-amount = 10000      # 包含減號
class = "VIP"             # 保留字
客戶名稱 = "張三"          # 中文命名
```

### 命名慣例
```
🎨 Python 命名風格（PEP8）：
• 變數：snake_case（小寫底線）
• 常數：UPPER_CASE（大寫底線）
• 類別：PascalCase（首字大寫）
```

### 動畫效果
- 錯誤範例顯示紅色警告
- 正確範例顯示綠色勾號

### 講師口述
```
"好的命名讓程式碼像文章一樣易讀。
記住：程式碼是寫給人看的，順便給電腦執行。"
```

---

## 🎬 P4：四大基本資料型態 [核心知識]
### 版面配置
```
四宮格展示
```

### 內容文字
**標題** (32pt)
```
🔤 Python 資料型態
```

**四大類型**
```
┌─────────────┬─────────────┐
│   整數 int   │   浮點數 float│
│             │             │
│  age = 25   │ price = 99.9│
│  count = 100│ rate = 3.14 │
│   數學運算   │   精確計算   │
├─────────────┼─────────────┤
│  字串 str    │  布林 bool   │
│             │             │
│name = "小明" │ is_ok = True│
│msg = '您好'  │has_data=False│
│   文字處理   │   邏輯判斷   │
└─────────────┴─────────────┘
```

**型態轉換**
```python
# 型態轉換範例
age = "25"          # 字串
age_int = int(age)  # 轉成整數
age_float = float(age) # 轉成浮點數

price = 100         # 整數
price_str = str(price) # 轉成字串 "100"
```

### 實務應用
```
💼 實際應用場景：
• int：庫存數量、客戶編號
• float：金額、匯率、百分比
• str：姓名、地址、商品描述
• bool：是否會員、是否付款
```

### 動畫效果
- 四宮格依序展開
- 型態轉換箭頭動畫

### 講師口述
```
"記住這四種型態就能處理 90% 的資料。
Python 會自動判斷型態，但了解型態很重要！"
```

---

## 🎬 P5：實作練習 - 建立客戶資料 [動手時間]
### 版面配置
```
左側：任務說明 (40%)
右側：程式碼區 (60%)
```

### 內容文字
**標題** (32pt)
```
🏃 實作時間：建立客戶資料
```

**任務說明**
```
📋 任務：創建一個客戶資料
需包含：
• 客戶姓名
• 年齡
• 消費金額
• 是否為 VIP
```

**程式碼模板**
```python
# TODO: 建立客戶資料變數
customer_name = "請輸入姓名"
customer_age = 0
purchase_amount = 0.0
is_vip = False

# 顯示客戶資料
print("===== 客戶資料卡 =====")
print(f"姓名: {customer_name}")
print(f"年齡: {customer_age} 歲")
print(f"消費金額: ${purchase_amount:,.0f}")
print(f"VIP會員: {'是' if is_vip else '否'}")

# 計算會員等級
if purchase_amount > 10000:
    level = "金卡會員"
elif purchase_amount > 5000:
    level = "銀卡會員"
else:
    level = "一般會員"

print(f"會員等級: {level}")
```

### 預期輸出
```
===== 客戶資料卡 =====
姓名: 王小明
年齡: 35 歲
消費金額: $12,000
VIP會員: 是
會員等級: 金卡會員
```

### 計時器
```
⏱️ 練習時間：5 分鐘
[顯示倒數計時器]
```

### 講師口述
```
"請大家動手試試看，把自己當作客戶。
有問題隨時舉手，我和助教會協助。"
```

---

## 🎬 P6：條件判斷 - if/else [邏輯控制]
### 版面配置
```
流程圖 + 程式碼對照
```

### 內容文字
**標題** (32pt)
```
🚦 條件判斷：做決定的邏輯
```

**生活場景類比**
```
         下雨了嗎？
            ↓
        ┌───┴───┐
        │       │
       Yes      No
        ↓       ↓
      帶傘    不帶傘
```

**Python 語法**
```python
# 基本 if 結構
weather = "下雨"

if weather == "下雨":
    print("記得帶傘！☂️")
else:
    print("享受好天氣！☀️")

# 多重條件
temperature = 28

if temperature > 30:
    print("太熱了！開冷氣")
elif temperature > 20:
    print("溫度適中")
elif temperature > 10:
    print("有點涼，穿外套")
else:
    print("好冷！多穿點")
```

### 商業應用範例
```python
# 客戶折扣計算
purchase_amount = 8500
member_type = "VIP"

if member_type == "VIP":
    if purchase_amount > 10000:
        discount = 0.20  # VIP滿萬 8折
    else:
        discount = 0.10  # VIP 9折
else:
    if purchase_amount > 10000:
        discount = 0.05  # 一般滿萬 95折
    else:
        discount = 0     # 無折扣

final_price = purchase_amount * (1 - discount)
print(f"原價: ${purchase_amount:,}")
print(f"折扣: {discount*100:.0f}%")
print(f"應付: ${final_price:,.0f}")
```

### 注意事項
```
⚠️ 縮排很重要！
Python 用縮排表示程式區塊
通常使用 4 個空格
```

### 動畫效果
- 流程圖路徑高亮
- 程式碼執行路徑追蹤

### 講師口述
```
"if-else 就像十字路口，
根據條件選擇要走哪條路。
注意 Python 的縮排，這是它的特色！"
```

---

## 🎬 P7：比較運算子 [判斷工具]
### 版面配置
```
表格 + 實例
```

### 內容文字
**標題** (32pt)
```
⚖️ 比較運算子
```

**運算子列表**
```
運算子    意義        範例          結果
──────────────────────────────────────
==      等於        5 == 5        True
!=      不等於      5 != 3        True
>       大於        5 > 3         True
<       小於        5 < 3         False
>=      大於等於    5 >= 5        True
<=      小於等於    3 <= 5        True
in      包含       'a' in 'apple' True
not in  不包含     'x' in 'apple' False
```

**實務範例**
```python
# 年齡判斷
age = 20
can_vote = age >= 18
can_drink = age >= 21
is_student = 18 <= age <= 22

print(f"可以投票: {can_vote}")    # True
print(f"可以飲酒: {can_drink}")   # False
print(f"學生身份: {is_student}")  # True

# 會員資格檢查
vip_list = ["王小明", "李大華", "張美麗"]
customer = "王小明"

if customer in vip_list:
    print(f"{customer} 是 VIP 會員")
```

### 邏輯運算組合
```python
# and, or, not 組合條件
age = 25
income = 45000

# 信用卡申請資格
qualify_credit = age >= 20 and income >= 30000
print(f"信用卡資格: {qualify_credit}")  # True

# 優惠活動資格（學生或長者）
is_student = age <= 22
is_senior = age >= 65
get_discount = is_student or is_senior
print(f"優惠資格: {get_discount}")  # False
```

### 動畫效果
- 比較結果即時顯示
- True/False 顏色區分

### 講師口述
```
"這些運算子是判斷的工具。
記住：一個等號是賦值，兩個等號才是比較！"
```

---

## 🎬 P8：迴圈 - 重複的力量 [自動化基礎]
### 版面配置
```
對比展示：手動 vs 自動
```

### 內容文字
**標題** (32pt)
```
🔄 迴圈：讓電腦幫你重複
```

**為什麼需要迴圈**
```
❌ 沒有迴圈（重複程式碼）：
print("發送郵件給客戶 1")
print("發送郵件給客戶 2")
print("發送郵件給客戶 3")
... (寫 100 次？)

✅ 使用迴圈（一次搞定）：
for i in range(1, 101):
    print(f"發送郵件給客戶 {i}")
```

**for 迴圈結構**
```python
# 基本 for 迴圈
customers = ["王小明", "李大華", "張美麗", "陳建國"]

for customer in customers:
    print(f"正在處理 {customer} 的訂單...")
    print(f"✅ {customer} 訂單完成！")
    print("-" * 30)

# 使用 range() 產生數字序列
print("倒數計時：")
for i in range(10, 0, -1):
    print(f"{i}...")
print("🚀 發射！")
```

### 實務應用
```python
# 計算總銷售額
sales = [1200, 3400, 2100, 4500, 1800]
total = 0

for amount in sales:
    total = total + amount
    print(f"累計銷售: ${total:,}")

print(f"\n總銷售額: ${total:,}")
print(f"平均銷售: ${total/len(sales):,.0f}")

# 批次處理折扣
prices = [100, 200, 150, 300, 250]
discount_rate = 0.8  # 8折

print("折扣後價格：")
for price in prices:
    discounted = price * discount_rate
    print(f"原價 ${price} → 特價 ${discounted:.0f}")
```

### 效率對比
```
⏱️ 時間比較：
手動處理 100 筆：30 分鐘
迴圈處理 100 筆：0.01 秒
效率提升：180,000 倍！
```

### 動畫效果
- 迴圈執行可視化
- 數字滾動效果

### 講師口述
```
"迴圈是程式設計的精髓！
讓電腦做重複的事，我們專注在邏輯。"
```

---

## 🎬 P9：while 迴圈 [條件控制]
### 版面配置
```
流程圖 + 程式碼
```

### 內容文字
**標題** (32pt)
```
🔁 while 迴圈：條件式重複
```

**while vs for**
```
for 迴圈：知道要重複幾次
while 迴圈：不確定次數，直到條件滿足
```

**基本結構**
```python
# while 基本語法
count = 0
while count < 5:
    print(f"第 {count + 1} 次執行")
    count = count + 1

# 實際應用：密碼驗證
password = "1234"
input_pwd = ""
attempts = 0

while input_pwd != password and attempts < 3:
    input_pwd = input("請輸入密碼: ")
    attempts += 1

    if input_pwd == password:
        print("✅ 登入成功！")
    elif attempts < 3:
        print(f"❌ 密碼錯誤，還有 {3-attempts} 次機會")
    else:
        print("🔒 帳號已鎖定")
```

### 無窮迴圈應用
```python
# 選單系統
while True:
    print("\n===== 主選單 =====")
    print("1. 查看餘額")
    print("2. 存款")
    print("3. 提款")
    print("4. 離開")

    choice = input("請選擇功能: ")

    if choice == "1":
        print("餘額: $10,000")
    elif choice == "2":
        print("存款功能")
    elif choice == "3":
        print("提款功能")
    elif choice == "4":
        print("謝謝使用，再見！")
        break  # 跳出迴圈
    else:
        print("無效選擇，請重試")
```

### 注意事項
```
⚠️ 避免無窮迴圈！
確保有條件能讓迴圈結束
使用 break 可強制跳出
使用 continue 可跳過這次繼續下次
```

### 動畫效果
- 流程圖循環動畫
- 條件判斷路徑高亮

### 講師口述
```
"while 就像'當...的時候就一直...'
記得要有出口，不然會永遠執行下去！"
```

---

## 🎬 P10：實作練習 - 簡易計算機 [綜合應用]
### 版面配置
```
任務需求 + 程式框架
```

### 內容文字
**標題** (32pt)
```
🧮 綜合練習：打造計算機
```

**任務需求**
```
📋 功能需求：
1. 顯示選單
2. 接受兩個數字輸入
3. 執行加減乘除
4. 顯示結果
5. 可重複使用
```

**程式碼框架**
```python
print("🧮 Python 計算機")
print("=" * 30)

while True:
    # 顯示選單
    print("\n請選擇運算：")
    print("1. 加法 (+)")
    print("2. 減法 (-)")
    print("3. 乘法 (×)")
    print("4. 除法 (÷)")
    print("5. 離開")

    choice = input("你的選擇 (1-5): ")

    if choice == "5":
        print("👋 再見！")
        break

    if choice in ["1", "2", "3", "4"]:
        # 輸入數字
        num1 = float(input("第一個數字: "))
        num2 = float(input("第二個數字: "))

        # 執行運算
        if choice == "1":
            result = num1 + num2
            op = "+"
        elif choice == "2":
            result = num1 - num2
            op = "-"
        elif choice == "3":
            result = num1 * num2
            op = "×"
        elif choice == "4":
            if num2 != 0:
                result = num1 / num2
                op = "÷"
            else:
                print("❌ 錯誤：不能除以零！")
                continue

        # 顯示結果
        print(f"\n📊 結果：{num1} {op} {num2} = {result}")
    else:
        print("❌ 無效選擇，請重試")
```

### 延伸挑戰
```
🌟 進階功能（選做）：
• 加入記憶功能（儲存上次結果）
• 支援連續運算
• 加入開根號、次方功能
• 顯示計算歷史
```

### 講師口述
```
"這個練習結合了我們學的所有概念。
慢慢來，有問題就問。完成後會很有成就感！"
```

---

## 🎬 P11：函式 - 程式碼重複利用 [模組化]
### 版面配置
```
概念說明 + 實例
```

### 內容文字
**標題** (32pt)
```
📦 函式：打包你的程式碼
```

**為什麼要用函式**
```
問題：相同邏輯重複出現
解法：包裝成函式，隨時呼叫

就像：
• 微波爐的"快速加熱"按鈕
• 手機的"快速撥號"
• Word 的"另存新檔"
```

**函式結構**
```python
# 定義函式
def 函式名稱(參數1, 參數2):
    """函式說明"""
    # 執行內容
    return 結果

# 基本範例
def greet(name):
    """打招呼函式"""
    message = f"你好，{name}！歡迎光臨！"
    return message

# 使用函式
print(greet("王小明"))
print(greet("李大華"))
```

### 實務應用
```python
# 計算折扣價格
def calculate_discount(price, discount_rate):
    """
    計算折扣後價格
    price: 原價
    discount_rate: 折扣率 (0.8 = 8折)
    """
    final_price = price * discount_rate
    saved = price - final_price
    return final_price, saved

# 使用函式
original = 1000
rate = 0.75  # 75折

final, discount = calculate_discount(original, rate)
print(f"原價: ${original}")
print(f"折扣後: ${final:.0f}")
print(f"節省: ${discount:.0f}")

# 批次處理
prices = [500, 1000, 1500, 2000]
print("\n批次計算折扣：")
for p in prices:
    f, d = calculate_discount(p, 0.8)
    print(f"${p} → ${f:.0f} (省${d:.0f})")
```

### 內建函式介紹
```python
# Python 常用內建函式
numbers = [45, 23, 67, 12, 89]

print(f"總和: {sum(numbers)}")      # 236
print(f"最大值: {max(numbers)}")    # 89
print(f"最小值: {min(numbers)}")    # 12
print(f"長度: {len(numbers)}")      # 5
print(f"平均: {sum(numbers)/len(numbers):.1f}")  # 47.2
```

### 動畫效果
- 函式呼叫流程動畫
- 參數傳遞可視化

### 講師口述
```
"函式就像工具箱裡的工具，
定義一次，到處使用。
好的函式讓程式碼更簡潔、更好維護！"
```

---

## 🎬 P12：開發環境選擇 [工具介紹]
### 版面配置
```
三種環境對比
```

### 內容文字
**標題** (32pt)
```
🛠️ 選擇你的開發環境
```

**環境比較**
```
┌────────────────────────────────────────┐
│         Jupyter Notebook              │
│  👍 適合：資料分析、學習、實驗          │
│  ⚡ 特色：即時執行、結果可視化          │
│  📊 評分：初學者 ★★★★★              │
├────────────────────────────────────────┤
│         VS Code                       │
│  👍 適合：專業開發、大型專案           │
│  ⚡ 特色：強大擴充、整合 Git          │
│  📊 評分：進階用戶 ★★★★★            │
├────────────────────────────────────────┤
│         Google Colab                  │
│  👍 適合：雲端協作、無需安裝           │
│  ⚡ 特色：免費 GPU、隨處可用          │
│  📊 評分：輕量使用 ★★★★☆            │
└────────────────────────────────────────┘
```

**快速設置指南**
```bash
# Jupyter Notebook 安裝
pip install jupyter
jupyter notebook

# VS Code 設定
1. 下載 VS Code
2. 安裝 Python 擴充套件
3. 選擇 Python 直譯器

# Google Colab
1. 開啟 colab.research.google.com
2. 登入 Google 帳號
3. 新增筆記本
```

### 推薦設置
```
🎯 課程推薦：
初學者 → Jupyter Notebook
理由：
✓ 區塊執行，易於調試
✓ 結果即時可見
✓ 支援 Markdown 筆記
✓ 適合學習和實驗
```

### 動畫效果
- 環境截圖輪播
- 特色項目高亮

### 講師口述
```
"今天我們用 Jupyter，因為最適合學習。
之後可以根據需求選擇其他環境。"
```

---

## 🎬 P13：Git 版本控制基礎 [專業習慣]
### 版面配置
```
概念圖 + 指令
```

### 內容文字
**標題** (32pt)
```
📝 Git：程式碼的時光機
```

**為什麼要版本控制**
```
沒有版本控制：
report_final.py
report_final_v2.py
report_final_v2_修改.py
report_final_真的最後版本.py
report_final_真的最後版本_老闆修改.py
😱 哪個才是最新的？

有版本控制：
report.py + Git 歷史記錄
✅ 清楚、專業、可追溯
```

**基本 Git 流程**
```
工作區 → 暫存區 → 儲存庫
  ↓        ↓        ↓
編輯檔案  git add  git commit
```

**必學四個指令**
```bash
# 1. 初始化專案
git init

# 2. 加入暫存區
git add .              # 加入所有檔案
git add filename.py    # 加入特定檔案

# 3. 提交變更
git commit -m "加入客戶分析功能"

# 4. 查看狀態
git status            # 查看目前狀態
git log --oneline     # 查看歷史記錄
```

### GitHub 連結
```bash
# 連結遠端儲存庫
git remote add origin https://github.com/你的帳號/專案名稱
git push -u origin main

# 之後更新
git push
```

### 實務情境
```
📅 日常工作流程：
早上：git pull（取得最新版本）
編碼：修改程式碼
測試：確認功能正常
提交：git add . → git commit
下班：git push（上傳到雲端）
```

### 動畫效果
- Git 流程動畫
- 指令執行模擬

### 講師口述
```
"Git 就像檔案的時光機，
可以回到任何時間點的版本。
養成版本控制習慣，受用一生！"
```

---

## 🎬 P14：虛擬環境 [環境管理]
### 版面配置
```
類比說明 + 實作
```

### 內容文字
**標題** (32pt)
```
🏠 虛擬環境：專案的獨立空間
```

**為什麼需要虛擬環境**
```
類比：每個專案像一間房子
• 專案 A：需要 pandas 1.3
• 專案 B：需要 pandas 2.0
• 專案 C：需要特殊套件

虛擬環境 = 每個專案的獨立房間
不會互相干擾！
```

**建立與使用**
```bash
# 建立虛擬環境
python -m venv myenv

# 啟動虛擬環境
# Windows:
myenv\Scripts\activate
# Mac/Linux:
source myenv/bin/activate

# 安裝套件
pip install pandas numpy matplotlib

# 匯出套件清單
pip freeze > requirements.txt

# 離開虛擬環境
deactivate
```

### requirements.txt
```
# 專案相依套件
pandas==1.5.3
numpy==1.24.0
matplotlib==3.6.2
seaborn==0.12.1
```

### 最佳實踐
```
✅ 良好習慣：
1. 每個專案一個虛擬環境
2. 環境名稱統一（如 venv 或 .env）
3. 將環境加入 .gitignore
4. 使用 requirements.txt 記錄套件
```

### 動畫效果
- 環境切換示意圖
- 套件安裝進度條

### 講師口述
```
"虛擬環境避免'在我電腦上可以跑'的問題。
每個專案獨立，乾淨俐落！"
```

---

## 🎬 P15：程式設計最佳實踐 [專業素養]
### 版面配置
```
DO's and DON'Ts
```

### 內容文字
**標題** (32pt)
```
💎 寫出專業的程式碼
```

**良好習慣**
```
✅ DO's - 應該這樣做：

1. 有意義的變數名稱
   customer_age ✓ (不是 ca 或 x)

2. 適當的註解
   # 計算客戶終身價值
   lifetime_value = purchase * frequency

3. 保持程式碼簡潔
   一個函式做一件事

4. 遵循 PEP8 規範
   使用 4 格縮排，行長不超過 79 字元

5. 定期測試
   每寫完一個功能就測試
```

**避免錯誤**
```
❌ DON'Ts - 不要這樣做：

1. 魔術數字
   if age > 18:  # 18 是什麼？
   改成：LEGAL_AGE = 18

2. 過長的函式
   超過 20 行考慮拆分

3. 忽略錯誤處理
   always try-except 重要操作

4. 複製貼上程式碼
   重複邏輯要寫成函式

5. 不備份程式碼
   一定要用 Git！
```

### 程式碼範例
```python
# ❌ 不好的程式碼
def calc(a,b,c):
    d = a * 0.1
    e = b * 0.2
    return d + e + c

# ✅ 好的程式碼
def calculate_total_cost(base_price, tax_rate=0.1,
                         shipping_rate=0.2, shipping_base=50):
    """
    計算包含稅金與運費的總成本
    """
    tax = base_price * tax_rate
    shipping = shipping_base * shipping_rate
    total = base_price + tax + shipping
    return total
```

### 動畫效果
- 好壞對比淡入淡出
- 重點項目脈衝效果

### 講師口述
```
"好的程式碼像好文章，清晰易讀。
記住：你未來的自己會感謝現在認真的你！"
```

---

## 🎬 P16：錯誤處理 [除錯技能]
### 版面配置
```
常見錯誤 + 解決方案
```

### 內容文字
**標題** (32pt)
```
🐛 Debug：與錯誤做朋友
```

**常見錯誤類型**
```python
# 1. 語法錯誤 SyntaxError
print("Hello"  # 缺少括號

# 2. 名稱錯誤 NameError
print(nmae)    # 變數名拼錯

# 3. 型態錯誤 TypeError
"10" + 5       # 字串不能加數字

# 4. 索引錯誤 IndexError
lst = [1,2,3]
print(lst[5])  # 超出範圍

# 5. 值錯誤 ValueError
int("abc")     # 無法轉換
```

**錯誤處理技巧**
```python
# try-except 結構
def safe_divide(a, b):
    try:
        result = a / b
        return result
    except ZeroDivisionError:
        print("錯誤：不能除以零")
        return None
    except TypeError:
        print("錯誤：請輸入數字")
        return None
    finally:
        print("計算完成")

# 實務範例：讀取使用者輸入
while True:
    try:
        age = int(input("請輸入年齡: "))
        if age < 0:
            raise ValueError("年齡不能是負數")
        break
    except ValueError as e:
        print(f"輸入錯誤: {e}")
        print("請重新輸入")
```

### Debug 小技巧
```
🔍 除錯三步驟：
1. 讀錯誤訊息（看最後一行）
2. 找到錯誤位置（看行號）
3. 理解錯誤原因（Google 是朋友）

💡 預防勝於治療：
• 使用 print() 追蹤變數
• 寫一點測一點
• 使用 IDE 的除錯工具
```

### 動畫效果
- 錯誤訊息高亮
- 解決方案飛入

### 講師口述
```
"錯誤是最好的老師！
每個錯誤都是學習機會，不要害怕紅字。"
```

---

## 🎬 P17：實戰專案 - 成績管理系統 [綜合練習]
### 版面配置
```
專案需求 + 程式架構
```

### 內容文字
**標題** (32pt)
```
🎯 期末專案：成績管理系統
```

**專案需求**
```
📋 功能需求：
1. 新增學生成績
2. 查詢學生成績
3. 計算班級平均
4. 找出最高/最低分
5. 產生成績報表
```

**完整程式碼**
```python
# 成績管理系統
students = {}

def add_student():
    """新增學生成績"""
    name = input("學生姓名: ")
    try:
        score = float(input("成績 (0-100): "))
        if 0 <= score <= 100:
            students[name] = score
            print(f"✅ 已新增 {name} 的成績")
        else:
            print("❌ 成績須在 0-100 之間")
    except ValueError:
        print("❌ 請輸入數字")

def view_scores():
    """查看所有成績"""
    if not students:
        print("尚無學生資料")
        return

    print("\n===== 成績單 =====")
    for name, score in students.items():
        grade = get_grade(score)
        print(f"{name}: {score}分 ({grade})")

def get_grade(score):
    """將分數轉換為等級"""
    if score >= 90: return "A"
    elif score >= 80: return "B"
    elif score >= 70: return "C"
    elif score >= 60: return "D"
    else: return "F"

def show_statistics():
    """顯示統計資料"""
    if not students:
        print("尚無資料")
        return

    scores = list(students.values())
    print(f"\n📊 統計資料")
    print(f"學生人數: {len(scores)}")
    print(f"平均分數: {sum(scores)/len(scores):.1f}")
    print(f"最高分: {max(scores)} ({get_top_student()})")
    print(f"最低分: {min(scores)}")

def get_top_student():
    """找出最高分學生"""
    return max(students, key=students.get)

# 主程式
print("🎓 成績管理系統")
while True:
    print("\n1. 新增成績")
    print("2. 查看成績")
    print("3. 統計資料")
    print("4. 離開")

    choice = input("選擇功能: ")

    if choice == "1":
        add_student()
    elif choice == "2":
        view_scores()
    elif choice == "3":
        show_statistics()
    elif choice == "4":
        print("再見！")
        break
```

### 講師口述
```
"這個專案綜合了今天學的所有概念。
完成它，你就掌握了 Python 基礎！"
```

---

## 🎬 P18：Python 學習資源 [持續成長]
### 版面配置
```
資源分類展示
```

### 內容文字
**標題** (32pt)
```
📚 繼續你的 Python 之旅
```

**推薦資源**
```
📖 必讀書籍：
• Python Crash Course (初學者)
• Automate the Boring Stuff (自動化)
• Clean Code (程式設計思維)

🎓 線上課程：
• Coursera - Python for Everybody
• DataCamp - Python 基礎
• YouTube - Corey Schafer

🌐 練習網站：
• LeetCode (演算法)
• HackerRank (程式挑戰)
• Kaggle Learn (資料科學)

📱 社群資源：
• Python Taiwan 社群
• PyLadies Taiwan
• Stack Overflow

🛠️ 必裝套件：
• jupyter - 互動式開發
• pandas - 資料處理
• requests - 網路請求
• black - 程式碼格式化
```

### 學習路徑建議
```
🗺️ 建議學習路徑：
Week 1-2: Python 基礎語法 ✅
Week 3-4: 資料結構深入
Week 5-6: 函式與模組
Week 7-8: 檔案處理
Week 9-12: 實作專案
```

### 動畫效果
- 資源卡片滑入
- 路徑圖展開

### 講師口述
```
"學習是持續的過程。
這些資源能幫助你不斷進步！"
```

---

## 🎬 P19：模組總結 [成果確認]
### 版面配置
```
成就清單 + 下階段預告
```

### 內容文字
**標題** (32pt)
```
🎉 Module 1 完成！
```

**成就解鎖**
```
🏆 你已經學會：
✅ Python 基本語法
  • 變數與資料型態
  • 條件判斷 (if/else)
  • 迴圈控制 (for/while)

✅ 程式設計概念
  • 函式定義與呼叫
  • 錯誤處理
  • 程式碼組織

✅ 開發環境設置
  • Jupyter Notebook
  • Git 版本控制
  • 虛擬環境管理

✅ 實戰能力
  • 計算機程式
  • 成績管理系統
```

### 信心指數
```
💪 你現在可以：
• 寫出基本的 Python 程式
• 解決簡單的自動化問題
• 閱讀並理解他人的程式碼
```

### 下一步預告
```
📅 Module 2 預告：
「Pandas 數據處理」
• 讀取真實數據檔案
• DataFrame 操作
• 數據清理技巧
• 1,000 筆超市銷售數據分析
```

### 動畫效果
- 成就徽章旋轉
- 進度條填充完成

### 講師口述
```
"恭喜！你已經是 Python 程式設計師了！
休息一下，準備處理真實數據！"
```

---

## 🎬 P20：過渡頁 [章節銜接]
### 版面配置
```
全屏過渡效果
```

### 內容文字
**主文字** (48pt)
```
Next Up... 📊
```

**副文字** (32pt)
```
Module 2
Pandas 數據處理與資料庫基礎
```

**重點提示**
```
準備處理 1,000 筆真實銷售數據！
```

### 視覺元素
```
背景：藍色粒子效果
進度：[■■□□□□□] 2/7
```

### 動畫效果
- Morph 轉場
- 數據表格預覽淡入

### 講師口述
```
"接下來是最實用的部分 - Pandas！
準備好處理真實數據了嗎？"
```

---

## 📋 Module 1 教學檢核表

### 時間控制 (45分鐘)
- [ ] P1-P5: 10分鐘 (概念導入)
- [ ] P6-P10: 15分鐘 (邏輯控制)
- [ ] P11-P15: 10分鐘 (環境設置)
- [ ] P16-P20: 10分鐘 (實戰總結)

### 互動檢查點
- [ ] P5: 變數練習完成率
- [ ] P10: 計算機完成率
- [ ] P17: 專案理解度
- [ ] P19: 學習成果確認

### 準備材料
- [ ] 程式碼範例檔案
- [ ] 環境設置說明書
- [ ] 練習題目答案
- [ ] 延伸學習資源

---

*Module 1 設計完成 - 確保初學者能建立程式設計基礎*