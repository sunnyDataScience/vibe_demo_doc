# Module 6：Vibe Coding工具與Prompt工程
## 完整簡報設計（20頁）

---

## Slide 1：開場頁
### 標題區（72pt，粗體）
**Vibe Coding工具與Prompt工程**
*Module 6 - AI輔助程式開發*

### 副標題區（36pt）
掌握AI工具，10倍提升開發效率

### 視覺元素
- 背景：AI青色漸層 (#4CC9F0 → #0A84FF)
- 中央：AI大腦與程式碼結合的3D動畫
- 底部：ChatGPT、Claude、Cursor圖標漂浮

### 動畫效果
1. 背景漸層緩慢流動
2. AI圖標依序出現（0.3秒間隔）
3. 程式碼片段飄浮效果

### 講師備註
- 開場強調：AI不是取代，而是賦能
- 分享個人使用AI提效的真實案例
- 預告本模組會實作完整功能

**時間控制**：2分鐘

---

## Slide 2：學習目標
### 標題（60pt）
**本模組學習目標**

### 內容區（32pt）
#### 🎯 你將學會
1. **AI工具生態全覽**
   - ChatGPT、Claude、Gemini比較
   - Cursor、GitHub Copilot實戰

2. **Prompt工程五要素**
   - 角色、任務、背景、格式、範例

3. **程式碼生成實戰**
   - 從需求到完整程式
   - 迭代優化技巧

### 成就預覽
```python
# 10分鐘內用AI完成的專案
"爬蟲程式" → "資料清理" → "視覺化報表" → "自動化腳本"
```

### 動畫效果
- 目標項目逐條飛入（Fly In）
- 成就預覽打字機效果

**時間控制**：2分鐘

---

## Slide 3：AI工具生態圈
### 標題（60pt）
**2025 AI開發工具全景圖**

### 視覺化佈局
```
        【對話式AI】
    ChatGPT    Claude    Gemini
         ↓        ↓        ↓

        【IDE整合】
    Cursor   Copilot   Codeium
         ↓        ↓        ↓

        【專業工具】
    Perplexity  Phind   You.com
```

### 工具對比表格
| 工具 | 強項 | 適用場景 | 免費額度 |
|------|------|----------|----------|
| ChatGPT | 通用性強 | 全方位開發 | GPT-3.5 |
| Claude | 程式理解深 | 複雜邏輯 | 有限對話 |
| Cursor | IDE整合 | 即時編程 | 200次/月 |

### 互動環節
💬 **現場調查**：誰用過這些工具？

**時間控制**：3分鐘

---

## Slide 4：Prompt工程核心概念
### 標題（60pt）
**什麼是好的Prompt？**

### 對比展示（分割畫面）
#### ❌ 錯誤示範
```
"幫我寫一個爬蟲"
```
結果：模糊、不完整、需多次修改

#### ✅ 正確示範
```
角色：你是Python爬蟲專家
任務：爬取PChome商品資料
背景：需要價格、名稱、庫存
格式：返回DataFrame
範例：[提供網頁結構]
```
結果：精準、可執行、一次到位

### 核心公式（放大顯示）
**好Prompt = 角色 + 任務 + 背景 + 格式 + 範例**

### 動畫效果
- 錯誤示範紅色警示動畫
- 正確示範綠色勾選動畫
- 公式逐個元素顯示

**時間控制**：3分鐘

---

## Slide 5：Prompt五要素詳解
### 標題（60pt）
**PROMPT五要素實戰**

### 實例分解（卡片式佈局）
```python
prompt = """
【角色】你是資深Python數據分析師
【任務】分析電商銷售數據找出TOP10產品
【背景】
- 資料：50萬筆交易記錄
- 時間：2024年Q1
- 目標：找出最賺錢產品
【格式】
1. 載入資料
2. 數據清理
3. 分析計算
4. 視覺化展示
【範例】
df.groupby('product')['profit'].sum()
"""
```

### 即時演示
- 現場輸入ChatGPT
- 展示生成結果
- 對比有無五要素差異

### 練習提示
🏃 **動手時間**：寫出你的第一個五要素Prompt

**時間控制**：4分鐘

---

## Slide 6：實戰演練 - 需求轉Prompt
### 標題（60pt）
**從業務需求到完美Prompt**

### 案例展示
#### 原始需求
"老闆要看上個月的銷售報告"

#### 拆解過程（流程圖）
```
需求分析 → 資料確認 → 邏輯梳理 → Prompt撰寫
    ↓          ↓           ↓            ↓
銷售報告   哪些資料    計算邏輯    五要素組合
```

#### 最終Prompt
```python
"""
角色：商業分析師
任務：生成2024年12月銷售報告
背景：
- 資料來源：sales_202412.csv
- 包含：日期、產品、金額、成本
- 需求：總營收、毛利率、TOP產品
格式：
1. 匯入必要套件
2. 讀取與清理資料
3. 計算關鍵指標
4. 生成視覺化圖表
5. 輸出PDF報告
範例：使用pandas和matplotlib
"""
```

### 現場編碼
- 貼入AI工具
- 執行生成的程式碼
- 展示報告結果

**時間控制**：4分鐘

---

## Slide 7：ChatGPT實戰技巧
### 標題（60pt）
**ChatGPT進階使用技巧**

### 技巧展示（並排卡片）
#### 1. 對話式開發
```python
# 第一輪
"幫我寫個爬蟲爬取Yahoo股價"
# 第二輪
"加上錯誤處理"
# 第三輪
"改成異步爬取提升速度"
```

#### 2. 程式碼審查
```python
# 貼上程式碼
"請審查這段程式碼的：
1. 效能瓶頸
2. 潛在bug
3. 最佳化建議"
```

#### 3. 除錯助手
```python
# 貼上錯誤訊息
"Error: KeyError 'price'
程式碼：[貼上]
請幫我除錯"
```

### 實用指令集
- `簡化這段程式碼`
- `加上型別提示`
- `轉換為函數式寫法`
- `生成單元測試`

### 動畫效果
- 技巧卡片翻轉顯示
- 程式碼高亮重點部分

**時間控制**：3分鐘

---

## Slide 8：Claude特色功能
### 標題（60pt）
**Claude：程式理解專家**

### 獨特優勢（對比表格）
| 功能 | Claude | ChatGPT |
|------|---------|---------|
| 程式碼理解 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| 長文本處理 | 100K tokens | 8K tokens |
| 邏輯推理 | 極強 | 強 |
| 中文支援 | 優秀 | 優秀 |

### 實例展示
```python
# Claude擅長的任務
"""
這是一個複雜的遞迴演算法
[貼上200行程式碼]

請：
1. 解釋運作原理
2. 找出潛在問題
3. 提供優化方案
4. 生成完整文檔
"""
```

### 最佳實踐
- 複雜邏輯使用Claude
- 創意任務使用ChatGPT
- 搭配使用效果最佳

**時間控制**：3分鐘

---

## Slide 9：Cursor實戰 - IDE整合
### 標題（60pt）
**Cursor：AI原生IDE**

### 功能演示（螢幕錄影）
#### 核心功能
1. **智能自動完成**
   - Tab接受建議
   - 多行程式碼預測

2. **對話式編程**
   - Cmd+K 直接改程式碼
   - 自然語言描述需求

3. **全專案理解**
   - 理解專案結構
   - 跨文件重構

### 實作展示
```python
# 輸入註解
# 建立一個REST API處理用戶註冊

# Cursor自動生成：
from flask import Flask, request, jsonify
from werkzeug.security import generate_password_hash
import sqlite3

app = Flask(__name__)

@app.route('/register', methods=['POST'])
def register():
    data = request.json
    # [自動完成剩餘程式碼]
```

### 快捷鍵清單
- `Tab`：接受建議
- `Cmd+K`：編輯程式碼
- `Cmd+L`：開啟對話

**時間控制**：2分鐘

---

## Slide 10：程式碼生成實戰專案
### 標題（60pt）
**10分鐘完成：股價監控系統**

### 專案需求
```
建立股價即時監控系統：
1. 爬取台股即時股價
2. 設定價格警報
3. LINE通知功能
4. 資料視覺化
```

### 分步驟Prompt（時間軸展示）
```
[0-2分鐘] → 爬蟲模組
[2-4分鐘] → 資料處理
[4-6分鐘] → LINE整合
[6-8分鐘] → 視覺化
[8-10分鐘] → 整合測試
```

### 現場編碼
- 實時展示每個步驟
- AI生成 → 執行 → 調整
- 最終運行完整系統

### 成果展示
- 即時股價顯示
- LINE訊息推送
- 圖表呈現

**時間控制**：10分鐘

---

## Slide 11：迭代優化技巧
### 標題（60pt）
**讓AI生成更好的程式碼**

### 優化循環（圓形流程圖）
```
    生成 → 測試
     ↑      ↓
    優化 ← 反饋
```

### 實例演示
#### 第一版（基礎）
```python
def calculate_total(items):
    total = 0
    for item in items:
        total += item['price']
    return total
```

#### 第二版（加入錯誤處理）
```python
def calculate_total(items):
    if not items:
        return 0
    total = 0
    for item in items:
        total += item.get('price', 0)
    return total
```

#### 第三版（效能優化）
```python
from typing import List, Dict

def calculate_total(items: List[Dict[str, float]]) -> float:
    """計算商品總價"""
    return sum(item.get('price', 0) for item in items)
```

### 優化清單
- ✅ 加入型別提示
- ✅ 錯誤處理
- ✅ 效能改善
- ✅ 程式碼文檔

**時間控制**：3分鐘

---

## Slide 12：常見錯誤與解決
### 標題（60pt）
**AI生成程式碼的陷阱**

### 問題展示（警告框樣式）
#### ⚠️ 問題1：過時的套件版本
```python
# AI可能生成
import tensorflow  # 1.x版本語法

# 應該改為
import tensorflow as tf  # 2.x版本
```

#### ⚠️ 問題2：錯誤的資料假設
```python
# AI假設資料完美
df['price'].mean()

# 實際需要
df['price'].dropna().mean()
```

#### ⚠️ 問題3：安全性問題
```python
# 危險寫法
query = f"SELECT * FROM users WHERE id = {user_id}"

# 安全寫法
query = "SELECT * FROM users WHERE id = ?"
cursor.execute(query, (user_id,))
```

### 檢查清單
- [ ] 版本相容性
- [ ] 資料完整性
- [ ] 安全性考量
- [ ] 效能瓶頸

**時間控制**：2分鐘

---

## Slide 13：Prompt模板庫
### 標題（60pt）
**實用Prompt模板集**

### 模板展示（手風琴式）
#### 📊 資料分析模板
```
角色：資料科學家
任務：分析[資料集名稱]
背景：[業務背景]
格式：完整jupyter notebook
範例：包含EDA、清理、分析、視覺化
```

#### 🕷️ 爬蟲開發模板
```
角色：爬蟲工程師
任務：爬取[網站名稱]
背景：需要[欄位列表]
格式：Python scrapy/requests
範例：包含反爬處理、資料儲存
```

#### 🤖 API開發模板
```
角色：後端工程師
任務：開發[功能]的REST API
背景：[技術棧]
格式：FastAPI/Flask
範例：包含驗證、錯誤處理、文檔
```

### 下載連結
📥 **模板包下載**：[QR Code]

**時間控制**：2分鐘

---

## Slide 14：整合工作流程
### 標題（60pt）
**AI輔助開發最佳實踐**

### 工作流程圖
```
需求分析 → Prompt設計 → AI生成
    ↓           ↓           ↓
  拆解任務    五要素法    ChatGPT/Claude

程式審查 ← 測試驗證 ← 程式碼整合
    ↓           ↓           ↓
  AI審查      單元測試     Cursor整合

部署上線 ← 文檔生成 ← 優化調整
    ↓           ↓           ↓
  CI/CD      AI生成       效能優化
```

### 時間分配建議
- 需求分析：20%
- AI生成：30%
- 測試調整：30%
- 優化部署：20%

### 團隊協作
- 共享Prompt庫
- 程式碼審查標準
- AI使用準則

**時間控制**：2分鐘

---

## Slide 15：實作練習 - 完整專案
### 標題（60pt）
**🏃 實作：客戶流失預測系統**

### 任務說明
```python
"""
使用AI工具完成：
1. 資料載入與探索
2. 特徵工程
3. 模型訓練
4. 結果視覺化
5. 預測API

時間：10分鐘
資料：customer_churn.csv
"""
```

### 分工建議
1. ChatGPT：生成主程式
2. Claude：優化演算法
3. Cursor：整合開發

### 評分標準
- 完成度（40%）
- 程式碼品質（30%）
- AI工具使用（30%）

### 小組分享
- 各組展示成果
- 分享使用心得

**時間控制**：10分鐘

---

## Slide 16：AI工具比較總結
### 標題（60pt）
**選擇正確的工具**

### 決策矩陣（熱力圖）
```
        快速原型  複雜邏輯  長期專案  團隊協作
ChatGPT    ███      ██       ██       ███
Claude     ██       ███      ███      ██
Cursor     ███      ██       ███      ███
Copilot    ██       ██       ███      ███
```

### 使用建議
| 場景 | 推薦工具 | 原因 |
|------|----------|------|
| 快速POC | ChatGPT | 回應快、創意強 |
| 演算法開發 | Claude | 邏輯嚴謹 |
| 日常編碼 | Cursor | IDE整合佳 |
| 團隊開發 | Copilot | 企業方案完善 |

### 組合使用
**最佳搭配**：ChatGPT構思 + Claude優化 + Cursor實作

**時間控制**：2分鐘

---

## Slide 17：學習資源與社群
### 標題（60pt）
**持續學習資源**

### 資源分類（網格佈局）
#### 📚 官方文檔
- OpenAI Cookbook
- Anthropic Claude Docs
- Cursor Documentation

#### 🎓 線上課程
- Fast.ai Practical Deep Learning
- Prompt Engineering Guide
- AI輔助開發實戰

#### 👥 社群資源
- r/LocalLLaMA
- Discord: AI Developers Taiwan
- Facebook: Taiwan AI Group

#### 🔧 實用工具
- PromptPerfect
- FlowGPT
- Awesome ChatGPT Prompts

### QR Code區
[課程資源包下載]

**時間控制**：1分鐘

---

## Slide 18：未來趨勢展望
### 標題（60pt）
**AI開發的未來**

### 趨勢時間軸（2024-2026）
```
2024 Q4
├─ GPT-5發布
├─ 多模態編程
└─ 代碼理解增強

2025 Q2
├─ AI配對編程普及
├─ 自動化測試
└─ 智能重構

2025 Q4
├─ AI專案管理
├─ 全自動部署
└─ 程式碼自我優化

2026
├─ AI架構師
├─ 零代碼開發
└─ 意圖驅動編程
```

### 準備建議
1. 持續學習新工具
2. 培養Prompt能力
3. 理解AI限制
4. 保持創新思維

**時間控制**：2分鐘

---

## Slide 19：模組總結
### 標題（60pt）
**Module 6 關鍵收穫**

### 成就清單（打勾動畫）
✅ **掌握5+種AI工具**
✅ **學會Prompt五要素**
✅ **完成實戰專案**
✅ **建立AI開發流程**

### 能力提升
```python
before = {
    "開發速度": "1x",
    "程式碼品質": "基礎",
    "除錯效率": "一般"
}

after = {
    "開發速度": "5-10x",  # 🚀
    "程式碼品質": "專業",  # ⭐
    "除錯效率": "極高"    # ⚡
}
```

### 下一步
→ Module 7：整合所有技能，產出專業報告

**時間控制**：1分鐘

---

## Slide 20：轉場頁
### 視覺設計
- 背景：AI青 (#4CC9F0) 漸變到專業灰 (#8B8C89)
- 中央：Module 6 ✓ → Module 7

### 文字內容（48pt）
**準備好了嗎？**
*將所有技能整合，產出專業報告！*

### 進度指示
[■■■■■■□] 6/7 完成

### 動畫效果
- 色彩漸變過渡（2秒）
- 進度條填充動畫
- 模組圖標旋轉切換

### 講師備註
- 確認學員跟上進度
- 預告最終專案整合
- 激發完成課程的期待

**時間控制**：30秒

---

## 教學資源包

### 程式碼範例
```python
# prompt_template.py
class PromptTemplate:
    def __init__(self):
        self.role = ""
        self.task = ""
        self.background = ""
        self.format = ""
        self.example = ""

    def generate(self):
        return f"""
        角色：{self.role}
        任務：{self.task}
        背景：{self.background}
        格式：{self.format}
        範例：{self.example}
        """

# ai_workflow.py
def ai_development_workflow(requirement):
    """AI輔助開發工作流程"""
    # 1. 需求分析
    prompt = analyze_requirement(requirement)

    # 2. AI生成
    code = generate_with_ai(prompt)

    # 3. 測試驗證
    test_results = run_tests(code)

    # 4. 迭代優化
    if not test_results.passed:
        code = optimize_with_ai(code, test_results)

    return code
```

### 快捷鍵清單
```
ChatGPT:
- Ctrl+Enter: 送出訊息
- Ctrl+Shift+C: 複製程式碼

Claude:
- Cmd+K: 清除對話
- Cmd+Enter: 送出

Cursor:
- Tab: 接受建議
- Cmd+K: AI編輯
- Cmd+L: 開啟對話
```

### 延伸閱讀
1. [Prompt Engineering Guide](https://www.promptingguide.ai/)
2. [ChatGPT官方最佳實踐](https://platform.openai.com/docs/guides/prompt-engineering)
3. [Claude官方文檔](https://docs.anthropic.com/claude/docs)

---

## 講師教學指引

### 重點提醒
1. **實作為主**：確保每位學員都實際使用AI工具
2. **案例導向**：用真實案例展示AI能力
3. **錯誤示範**：展示AI的限制和常見錯誤
4. **互動討論**：分享各自的AI使用經驗

### 時間掌控
- 理論講解：30%（14分鐘）
- 實作練習：50%（23分鐘）
- 討論分享：20%（8分鐘）

### 常見問題處理
1. **Q: AI會取代程式設計師嗎？**
   A: AI是工具，提升效率而非取代

2. **Q: 哪個AI工具最好？**
   A: 依據任務選擇，建議組合使用

3. **Q: 如何確保AI生成的程式碼品質？**
   A: 永遠要測試、審查和優化

### 成功指標
- [ ] 學員能寫出完整的五要素Prompt
- [ ] 成功使用AI完成一個小專案
- [ ] 理解不同AI工具的特點
- [ ] 建立AI輔助開發的工作流程