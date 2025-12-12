# 🎯 OrderFlow 六大子模組 - Vibe Coding 完整指南

## 📋 Vibe Coding 設計原則

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      Vibe Coding 核心思維                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   【什麼是 Vibe Coding?】                                                   │
│   用自然語言描述你要什麼 → AI 幫你寫程式 → 快速迭代調整                     │
│                                                                             │
│   【Prompt 設計四要素】                                                     │
│   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐                   │
│   │ Context │ → │  Task   │ → │ Format  │ → │ Example │                   │
│   │ 背景脈絡 │   │ 具體任務 │   │ 輸出格式 │   │ 範例參考 │                   │
│   └─────────┘   └─────────┘   └─────────┘   └─────────┘                   │
│                                                                             │
│   【每個模組 Prompt 結構】                                                  │
│   1. 🎯 模組目標說明                                                        │
│   2. 📐 技術規格定義                                                        │
│   3. 📝 分階段 Prompt (Step-by-Step)                                       │
│   4. ✅ 驗收檢查清單                                                        │
│   5. 🔧 常見問題調整 Prompt                                                 │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

# 模組 1️⃣：會員登入系統

## 🎯 模組目標

```
┌─────────────────────────────────────────────────┐
│  實現用戶註冊、登入、JWT 認證、角色權限控制      │
│  技術：Python + FastAPI + Supabase              │
└─────────────────────────────────────────────────┘
```

## 📐 架構思路

```
┌─────────────────────────────────────────────────────────────────┐
│                    會員系統架構思路                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   【資料流】                                                    │
│   用戶輸入 → API 接收 → 密碼驗證 → 產生 JWT → 回傳 Token       │
│                                                                 │
│   【核心概念】                                                  │
│   • 密碼不能明文存，要用 bcrypt 加密                           │
│   • JWT = 用戶身份證，每次請求都要帶著                         │
│   • 角色權限 = 不同人能做不同事                                │
│                                                                 │
│   【檔案結構預覽】                                              │
│   auth/                                                         │
│   ├── router.py    ← API 路由 (接收請求)                       │
│   ├── service.py   ← 業務邏輯 (處理邏輯)                       │
│   ├── models.py    ← 資料模型 (定義結構)                       │
│   └── utils.py     ← 工具函數 (JWT 處理)                       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 📝 Vibe Coding Prompts

### **Step 1: 建立資料模型**

```markdown
## Prompt 1-1: 建立 User 資料模型

【背景】
我正在用 Python + FastAPI + Supabase 建立一個訂單管理系統的會員模組。

【任務】
請幫我建立 User 相關的 Pydantic 資料模型，需要包含：

1. UserBase - 基礎欄位
   - email: 電子郵件 (必填，需驗證格式)
   - role: 角色 (admin/staff/customer，預設 customer)

2. UserCreate - 註冊用
   - 繼承 UserBase
   - password: 密碼 (必填，最少8字元)

3. UserLogin - 登入用
   - email: 電子郵件
   - password: 密碼

4. UserInDB - 資料庫存的完整資料
   - id: UUID
   - email, role
   - password_hash: 加密後的密碼
   - is_active: 是否啟用
   - created_at: 建立時間

5. UserResponse - 回傳給前端的 (不含密碼)
   - id, email, role, is_active, created_at

6. TokenResponse - 登入成功回傳
   - access_token: JWT token
   - token_type: "bearer"
   - user: UserResponse

【技術要求】
- 使用 Pydantic v2 語法
- 加入適當的 Field 驗證
- 加入 model_config 設定

【輸出格式】
請給我完整的 models.py 檔案內容
```

### **Step 2: JWT 工具函數**

```markdown
## Prompt 1-2: 建立 JWT 工具函數

【背景】
延續上一步，我需要處理 JWT token 的產生和驗證。

【任務】
請幫我建立 JWT 相關的工具函數 utils.py：

1. 設定常數
   - SECRET_KEY: 從環境變數讀取
   - ALGORITHM: HS256
   - ACCESS_TOKEN_EXPIRE_MINUTES: 60 分鐘

2. create_access_token(data: dict) 函數
   - 接收要編碼的資料
   - 加入過期時間 (exp)
   - 回傳 JWT token 字串

3. verify_token(token: str) 函數
   - 解碼並驗證 token
   - 回傳 payload 或 None (如果無效)

4. get_current_user 依賴注入函數
   - 從 Request Header 取得 Bearer token
   - 驗證 token
   - 從資料庫查詢用戶
   - 回傳 UserInDB 或拋出 401 錯誤

5. require_role(allowed_roles: list) 裝飾器
   - 檢查當前用戶角色是否在允許列表中
   - 不允許則拋出 403 錯誤

【技術要求】
- 使用 python-jose 套件
- 使用 FastAPI 的 Depends 機制
- 適當的錯誤處理

【輸出格式】
完整的 utils.py 檔案
```

### **Step 3: 業務邏輯層**

```markdown
## Prompt 1-3: 建立認證服務層

【背景】
我需要處理密碼加密、用戶查詢等業務邏輯。

【任務】
請建立 service.py 包含以下函數：

1. hash_password(password: str) -> str
   - 使用 bcrypt 加密密碼

2. verify_password(plain: str, hashed: str) -> bool
   - 驗證密碼是否正確

3. async get_user_by_email(email: str) -> UserInDB | None
   - 從 Supabase 查詢用戶
   - 使用 supabase-py 套件

4. async create_user(user: UserCreate) -> UserInDB
   - 檢查 email 是否已存在
   - 加密密碼
   - 寫入 Supabase
   - 回傳新建的用戶

5. async authenticate_user(email: str, password: str) -> UserInDB | None
   - 查詢用戶
   - 驗證密碼
   - 成功回傳用戶，失敗回傳 None

【Supabase 連線資訊】
```python
from supabase import create_client
supabase = create_client(
    os.getenv("SUPABASE_URL"),
    os.getenv("SUPABASE_KEY")
)
```

【輸出格式】
完整的 service.py 檔案
```

### **Step 4: API 路由**

```markdown
## Prompt 1-4: 建立認證 API 路由

【背景】
最後一步，我需要建立對外的 API 端點。

【任務】
請建立 router.py 包含以下端點：

1. POST /auth/register
   - 接收 UserCreate
   - 建立新用戶
   - 回傳 UserResponse
   - 錯誤：400 (email 已存在)

2. POST /auth/login
   - 接收 UserLogin
   - 驗證帳密
   - 成功回傳 TokenResponse
   - 錯誤：401 (帳密錯誤)

3. GET /auth/me
   - 需要認證 (Bearer token)
   - 回傳當前用戶資訊 UserResponse

4. PUT /auth/me
   - 需要認證
   - 可更新自己的 email
   - 回傳更新後的 UserResponse

5. GET /auth/users (限 admin)
   - 需要 admin 角色
   - 回傳所有用戶列表

【技術要求】
- 使用 FastAPI 的 APIRouter
- 適當的 response_model
- 完整的錯誤處理
- OpenAPI 文檔註解 (summary, description)

【輸出格式】
完整的 router.py 檔案，並告訴我如何在 main.py 中引入
```

## ✅ 驗收檢查清單

```
□ 可以成功註冊新用戶
□ 相同 email 註冊會報錯
□ 可以登入取得 JWT token
□ 錯誤密碼會回傳 401
□ 帶 token 可以存取 /auth/me
□ 不帶 token 存取 /auth/me 會 401
□ 非 admin 存取 /auth/users 會 403
□ 密碼在資料庫是加密的
```

## 🔧 調整用 Prompts

```markdown
【如果 token 過期太快】
請把 ACCESS_TOKEN_EXPIRE_MINUTES 改成 480 (8小時)

【如果要加入 refresh token】
請在 TokenResponse 加入 refresh_token 欄位，
並新增 POST /auth/refresh 端點來換發新 token

【如果要加入登出功能】
請實作 token 黑名單機制，使用 Redis 儲存已登出的 token
```

---

# 模組 2️⃣：後台管理系統

## 🎯 模組目標

```
┌─────────────────────────────────────────────────┐
│  商品 CRUD、訂單管理、系統設定                   │
│  限 admin/staff 角色存取                        │
└─────────────────────────────────────────────────┘
```

## 📐 架構思路

```
┌─────────────────────────────────────────────────────────────────┐
│                    後台管理架構思路                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   【權限層級】                                                  │
│   admin ──► 全部功能 (包含用戶管理)                            │
│   staff ──► 商品管理 + 訂單管理                                │
│                                                                 │
│   【API 路徑設計】                                              │
│   /admin/products/*   商品相關                                  │
│   /admin/orders/*     訂單相關                                  │
│   /admin/users/*      用戶管理 (僅 admin)                       │
│   /admin/stats/*      統計數據                                  │
│                                                                 │
│   【CRUD 統一模式】                                             │
│   GET    /items       列表 (支援分頁、篩選)                    │
│   GET    /items/{id}  單筆詳情                                  │
│   POST   /items       新增                                      │
│   PUT    /items/{id}  完整更新                                  │
│   PATCH  /items/{id}  部分更新                                  │
│   DELETE /items/{id}  刪除                                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 📝 Vibe Coding Prompts

### **Step 1: 商品管理模型**

```markdown
## Prompt 2-1: 商品管理資料模型

【背景】
我正在建立後台管理系統，先從商品管理開始。
這是一個食品批發商的系統，商品有分類、價格、庫存等資訊。

【任務】
請建立商品相關的 Pydantic 模型：

1. ProductCategory (Enum)
   - FRUIT: 水果
   - VEGETABLE: 蔬菜
   - MEAT: 肉類
   - SEAFOOD: 海鮮
   - DAIRY: 乳製品
   - OTHER: 其他

2. ProductBase
   - name: 商品名稱 (必填，最長100字)
   - category: 分類 (ProductCategory)
   - price: 單價 (Decimal，必須 > 0)
   - unit: 單位 (如：公斤、箱、包)
   - description: 描述 (選填)

3. ProductCreate (繼承 ProductBase)
   - stock: 初始庫存 (整數，預設 0)

4. ProductUpdate (所有欄位選填)
   - 用於部分更新

5. ProductInDB
   - id: UUID
   - 包含所有欄位
   - stock: 庫存數量
   - is_active: 是否上架
   - created_at, updated_at

6. ProductResponse (回傳用)
   - 同 ProductInDB

7. ProductListResponse (列表用)
   - items: List[ProductResponse]
   - total: 總筆數
   - page: 當前頁
   - page_size: 每頁筆數

【輸出】
完整的 products/models.py
```

### **Step 2: 商品 CRUD 服務**

```markdown
## Prompt 2-2: 商品 CRUD 服務層

【背景】
基於剛才的模型，我需要實作商品的資料庫操作。

【任務】
請建立 products/service.py：

1. async list_products(
     page: int = 1,
     page_size: int = 20,
     category: ProductCategory | None = None,
     search: str | None = None,
     is_active: bool | None = None
   ) -> ProductListResponse
   - 支援分頁
   - 支援依分類篩選
   - 支援名稱搜尋 (模糊搜尋)
   - 支援上架狀態篩選

2. async get_product(product_id: UUID) -> ProductInDB | None
   - 依 ID 查詢單筆

3. async create_product(data: ProductCreate) -> ProductInDB
   - 新增商品
   - 自動設定 created_at

4. async update_product(
     product_id: UUID, 
     data: ProductUpdate
   ) -> ProductInDB | None
   - 部分更新 (只更新有傳入的欄位)
   - 自動更新 updated_at

5. async delete_product(product_id: UUID) -> bool
   - 軟刪除 (設定 is_active = False)

6. async update_stock(
     product_id: UUID, 
     quantity_change: int
   ) -> ProductInDB
   - 更新庫存 (可正可負)
   - 庫存不足時拋出錯誤

【Supabase 查詢範例】
```python
# 列表查詢
result = supabase.table("products").select("*").eq("is_active", True).execute()

# 模糊搜尋
result = supabase.table("products").select("*").ilike("name", f"%{search}%").execute()

# 分頁
result = supabase.table("products").select("*", count="exact").range(start, end).execute()
```

【輸出】
完整的 products/service.py
```

### **Step 3: 商品 API 路由**

```markdown
## Prompt 2-3: 商品管理 API 路由

【背景】
我需要對外暴露商品管理的 API，只有 admin 和 staff 可以存取。

【任務】
請建立 products/router.py：

1. GET /admin/products
   - 查詢參數：page, page_size, category, search, is_active
   - 回傳 ProductListResponse
   - 需要 admin 或 staff 角色

2. GET /admin/products/{product_id}
   - 回傳單筆 ProductResponse
   - 找不到回傳 404

3. POST /admin/products
   - 接收 ProductCreate
   - 回傳 ProductResponse
   - 需要 admin 或 staff 角色

4. PUT /admin/products/{product_id}
   - 接收 ProductUpdate
   - 回傳更新後的 ProductResponse
   - 找不到回傳 404

5. DELETE /admin/products/{product_id}
   - 軟刪除
   - 回傳 {"success": true}

6. POST /admin/products/{product_id}/stock
   - 接收 {"quantity_change": int}
   - 回傳更新後的 ProductResponse
   - 庫存不足回傳 400

【權限控制】
使用模組1建立的 require_role 裝飾器
```python
from ..auth.utils import get_current_user, require_role

@router.get("/admin/products")
async def list_products(
    current_user: UserInDB = Depends(require_role(["admin", "staff"]))
):
    ...
```

【輸出】
完整的 products/router.py
```

### **Step 4: 訂單管理**

```markdown
## Prompt 2-4: 訂單管理完整模組

【背景】
訂單是系統的核心，需要追蹤狀態流轉。

【訂單狀態流程】
pending (待處理) → processing (處理中) → shipped (已出貨) → completed (完成)
                                      ↘ cancelled (取消)

【任務】
請一次建立完整的訂單管理模組：

**models.py 需要：**
1. OrderStatus (Enum): pending, processing, shipped, completed, cancelled
2. OrderItemCreate: product_id, quantity
3. OrderCreate: customer_id, items: List[OrderItemCreate], notes
4. OrderItemResponse: product_id, product_name, quantity, unit_price, subtotal
5. OrderResponse: id, customer_id, customer_name, items, status, total_amount, created_at, updated_at
6. OrderListResponse: items, total, page, page_size
7. OrderStatusUpdate: status, notes (用於更新狀態)

**service.py 需要：**
1. list_orders(page, page_size, status, customer_id, date_from, date_to)
2. get_order(order_id)
3. create_order(data) - 需要同時扣庫存
4. update_order_status(order_id, new_status, notes)
5. cancel_order(order_id) - 需要恢復庫存
6. get_order_stats() - 回傳統計：各狀態數量、今日訂單數、本月營收

**router.py 需要：**
- GET /admin/orders (列表)
- GET /admin/orders/{id} (詳情)
- PATCH /admin/orders/{id}/status (更新狀態)
- GET /admin/orders/stats (統計數據)

【重要邏輯】
- 建立訂單時要計算 total_amount = sum(quantity * unit_price)
- 建立訂單時要從 products 表扣除庫存
- 取消訂單時要恢復庫存
- 狀態只能按流程前進，不能倒退 (除了取消)

【輸出】
三個完整檔案：models.py, service.py, router.py
```

## ✅ 驗收檢查清單

```
□ 商品 CRUD 全部正常運作
□ 分頁和搜尋功能正常
□ 建立訂單會扣庫存
□ 庫存不足無法下單
□ 取消訂單會恢復庫存
□ 訂單狀態只能往前走
□ 統計數據正確
□ 非 admin/staff 無法存取
```

---

# 模組 3️⃣：前端儀表板 (Lovable)

## 🎯 模組目標

```
┌─────────────────────────────────────────────────┐
│  使用 Lovable 快速產生 React 前端                │
│  包含登入、儀表板、訂單管理、客戶管理頁面        │
└─────────────────────────────────────────────────┘
```

## 📐 架構思路

```
┌─────────────────────────────────────────────────────────────────┐
│                    前端架構思路                                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   【頁面結構】                                                  │
│   /login          ← 登入頁 (無需認證)                          │
│   /               ← 儀表板 (需認證)                            │
│   /orders         ← 訂單列表                                   │
│   /orders/:id     ← 訂單詳情                                   │
│   /customers      ← 客戶列表 (CRM)                             │
│   /customers/:id  ← 客戶詳情                                   │
│   /products       ← 商品管理                                   │
│                                                                 │
│   【狀態管理】                                                  │
│   AuthContext ──► 管理登入狀態、JWT token                      │
│   localStorage ──► 持久化 token                                │
│                                                                 │
│   【API 串接】                                                  │
│   axios instance ──► 自動帶入 Bearer token                     │
│                  ──► 401 時自動導向登入頁                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 📝 Vibe Coding Prompts (for Lovable)

### **Step 1: 專案初始化 + 登入頁**

```markdown
## Lovable Prompt 3-1: 建立專案與登入頁

Create a React + TypeScript project for a B2B Order Management System called "OrderFlow".

## Project Setup
- Use Vite + React + TypeScript
- Tailwind CSS for styling
- React Router v6 for navigation
- Axios for API calls
- Recharts for charts
- Lucide React for icons

## First, create the Login Page (/login)

### Layout
- Centered card on a light gray background (#F3F4F6)
- Card width: max 400px
- White background with subtle shadow

### Components
1. Logo area at top
   - "OrderFlow" text in blue (#3B82F6), bold, 24px
   - Subtitle: "訂單管理系統" in gray

2. Login Form
   - Email input with mail icon
   - Password input with lock icon (toggle visibility)
   - "記住我" checkbox
   - "登入" button (full width, blue, rounded)
   - Loading spinner on submit

3. Form validation
   - Email format validation
   - Password minimum 8 characters
   - Show error messages below inputs in red

### API Integration Setup
Create src/lib/api.ts:
```typescript
import axios from 'axios';

const api = axios.create({
  baseURL: import.meta.env.VITE_API_URL || 'http://localhost:8000/api',
});

// Add auth token to requests
api.interceptors.request.use((config) => {
  const token = localStorage.getItem('token');
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});

// Handle 401 errors
api.interceptors.response.use(
  (response) => response,
  (error) => {
    if (error.response?.status === 401) {
      localStorage.removeItem('token');
      window.location.href = '/login';
    }
    return Promise.reject(error);
  }
);

export default api;
```

### Auth Context
Create src/contexts/AuthContext.tsx:
- Store user info and token
- login(email, password) function
- logout() function
- isAuthenticated boolean

### Protected Route Component
Create a wrapper that redirects to /login if not authenticated

Please generate all the code with proper TypeScript types.
```

### **Step 2: 主要佈局 + 導覽列**

```markdown
## Lovable Prompt 3-2: 主要佈局與導覽

Create the main layout for authenticated pages.

## Layout Structure

### Sidebar Navigation (Left side)
- Width: 240px (collapsible to 64px on mobile)
- Dark blue background (#1E3A5F)
- Logo at top

Navigation items with icons:
1. 📊 儀表板 (/) - LayoutDashboard icon
2. 📦 訂單管理 (/orders) - Package icon
3. 👥 客戶管理 (/customers) - Users icon
4. 🏷️ 商品管理 (/products) - Tag icon

- Active item: lighter background, white text
- Hover effect on items
- Collapse button at bottom

### Top Navbar
- White background
- Left: Breadcrumb navigation
- Right: 
  - Notification bell icon (with red badge for unread)
  - User avatar dropdown
    - 用戶名稱
    - 角色 badge
    - Divider
    - 設定
    - 登出

### Main Content Area
- Light gray background (#F9FAFB)
- Padding: 24px
- Max width: 1400px, centered
- Scrollable

### Responsive Behavior
- < 768px: Sidebar hidden, hamburger menu in navbar
- Sidebar overlays content when open on mobile

## Code Structure
```
src/
├── layouts/
│   └── MainLayout.tsx
├── components/
│   ├── Sidebar.tsx
│   ├── Navbar.tsx
│   ├── Breadcrumb.tsx
│   └── UserDropdown.tsx
```

Please implement with smooth transitions and proper TypeScript.
```

### **Step 3: 儀表板頁面**

```markdown
## Lovable Prompt 3-3: 儀表板頁面

Create the Dashboard page (/) with real-time stats and charts.

## Stats Cards Row (4 cards)

Each card has:
- Icon in colored circle (left)
- Value (large, bold)
- Label (small, gray)
- Trend indicator (↑ or ↓ with percentage)

Cards:
1. 本月營收 - DollarSign icon, green circle
   - Value: NT$ 1,234,567
   - Trend: ↑ 12.5%

2. 待處理訂單 - Clock icon, yellow circle
   - Value: 23
   - Trend: ↓ 5%

3. 本月訂單數 - ShoppingBag icon, blue circle
   - Value: 156
   - Trend: ↑ 8.3%

4. 客戶總數 - Users icon, purple circle
   - Value: 48
   - Trend: ↑ 2

## Charts Row (2 charts side by side)

### Left: 營收趨勢圖 (Line Chart)
- Title: "近7日營收趨勢"
- X-axis: 日期 (12/04 - 12/10)
- Y-axis: 金額 (NT$)
- Blue line with gradient fill
- Tooltip showing exact value
- Using Recharts

### Right: 訂單狀態分布 (Pie Chart)
- Title: "訂單狀態分布"
- Segments:
  - 待處理 (pending): Yellow
  - 處理中 (processing): Blue
  - 已出貨 (shipped): Purple
  - 已完成 (completed): Green
  - 已取消 (cancelled): Gray
- Legend at bottom
- Tooltip with count and percentage

## Recent Orders Table

Title: "最近訂單" with "查看全部 →" link

Table columns:
- 訂單編號 (ORD-XXXX)
- 客戶名稱
- 金額
- 狀態 (colored badge)
- 建立時間
- 操作 (eye icon to view)

Show 5 rows with mock data.

Status badge colors:
- pending: yellow bg
- processing: blue bg
- shipped: purple bg
- completed: green bg
- cancelled: gray bg

## API Endpoints to Call
```typescript
// On page load, call:
GET /admin/orders/stats
GET /admin/orders?page=1&page_size=5

// Response type for stats:
interface DashboardStats {
  monthlyRevenue: number;
  revenueGrowth: number;
  pendingOrders: number;
  monthlyOrders: number;
  totalCustomers: number;
  revenueByDay: { date: string; amount: number }[];
  ordersByStatus: { status: string; count: number }[];
}
```

## Loading States
- Skeleton loaders for cards and charts
- Spinner for table

Please make it look professional and polished.
```

### **Step 4: 訂單列表頁**

```markdown
## Lovable Prompt 3-4: 訂單列表頁

Create the Orders List page (/orders).

## Page Header
- Title: "訂單管理"
- Subtitle: "管理所有客戶訂單"

## Filter Bar

Row of filters:
1. 日期範圍選擇器 (DateRangePicker)
   - 預設顯示本月
   - Quick options: 今天, 本週, 本月, 上月

2. 狀態下拉選單
   - 全部狀態
   - 待處理
   - 處理中
   - 已出貨
   - 已完成
   - 已取消

3. 搜尋框
   - Placeholder: "搜尋訂單編號或客戶..."
   - Search icon inside
   - Debounced search (300ms)

4. 匯出按鈕
   - "匯出 Excel" with download icon
   - Secondary style (outlined)

## Orders Table

Sortable columns:
- 訂單編號 (clickable, links to detail)
- 客戶名稱
- 商品數量
- 總金額 (NT$ formatted)
- 狀態 (colored badge)
- 建立時間 (relative time: "2小時前")
- 操作
  - Eye icon: 查看詳情
  - Edit icon: 更新狀態 (opens modal)

## Status Update Modal

When clicking edit icon:
- Modal title: "更新訂單狀態"
- Current status shown
- Dropdown to select new status
  - Only show valid next statuses
- Notes textarea (optional)
- Cancel and Confirm buttons

## Pagination

At bottom of table:
- "顯示 1-20 筆，共 156 筆"
- Page size selector: 10, 20, 50
- Page number buttons with prev/next

## Empty State
When no orders:
- Illustration or icon
- "尚無訂單資料"
- "當有新訂單時會顯示在這裡"

## API Integration
```typescript
// List orders
GET /admin/orders?page=1&page_size=20&status=pending&date_from=2024-01-01&search=xxx

// Update status
PATCH /admin/orders/{id}/status
Body: { status: "processing", notes: "開始處理" }
```

Please include proper TypeScript interfaces and loading states.
```

### **Step 5: 客戶管理頁 (CRM)**

```markdown
## Lovable Prompt 3-5: 客戶管理頁面

Create the Customers page (/customers) as a CRM module.

## Page Header
- Title: "客戶管理"
- "新增客戶" button (blue, with plus icon)

## View Toggle
- Grid view / Table view toggle buttons
- Save preference to localStorage

## Filter & Search
- Search box: "搜尋公司名稱、聯絡人、電話..."
- Credit Level filter: All / A級 / B級 / C級
- Sort by: 最近更新 / 公司名稱 / 消費金額

## Customer Cards (Grid View)

Card layout:
```
┌─────────────────────────────┐
│  [Avatar]  公司名稱         │
│            聯絡人           │
├─────────────────────────────┤
│  📞 0912-345-678            │
│  📧 contact@company.com     │
│  📍 台北市信義區...          │
├─────────────────────────────┤
│  信用等級: [A] 本月消費: NT$50,000 │
│  訂單數: 12    最後訂單: 2天前     │
├─────────────────────────────┤
│  [查看詳情]    [新增訂單]    │
└─────────────────────────────┘
```

Credit level badges:
- A級: Green badge
- B級: Blue badge  
- C級: Gray badge

## Customer Table (Table View)

Columns:
- 公司名稱
- 聯絡人
- 電話
- 信用等級
- 總消費金額
- 訂單數
- 最後訂單日
- 操作 (view/edit/delete)

## Add/Edit Customer Modal

Form fields:
- 公司名稱 * (required)
- 聯絡人 *
- 電話 *
- Email
- 地址
- 信用等級 (dropdown: A/B/C)
- 備註 (textarea)

Validation:
- Phone format: 09XX-XXX-XXX or 02-XXXX-XXXX
- Email format

## Customer Detail Page (/customers/:id)

Tabs:
1. 基本資料 - Display all customer info, edit button
2. 訂單記錄 - Table of customer's orders
3. 互動記錄 - Timeline of notes/interactions

Stats at top:
- 總消費金額
- 訂單次數
- 平均單價
- 客戶等級

## API Endpoints
```typescript
GET /api/customers
GET /api/customers/{id}
POST /api/customers
PUT /api/customers/{id}
DELETE /api/customers/{id}
GET /api/customers/{id}/orders
```

Please make the cards look modern with subtle shadows and hover effects.
```

## ✅ 驗收檢查清單

```
□ 登入頁面可正常登入
□ JWT token 存入 localStorage
□ 未登入時自動導向登入頁
□ 側邊欄導覽正常
□ 儀表板數據正確顯示
□ 圖表正常渲染
□ 訂單列表分頁正常
□ 訂單狀態可更新
□ 客戶 CRUD 正常
□ RWD 在手機上正常
```

---

# 模組 4️⃣：雲端資料庫 (Supabase)

## 🎯 模組目標

```
┌─────────────────────────────────────────────────┐
│  在 Supabase 建立完整的資料庫結構                │
│  包含資料表、關聯、索引、RLS 政策               │
└─────────────────────────────────────────────────┘
```

## 📐 架構思路

```
┌─────────────────────────────────────────────────────────────────┐
│                    資料庫架構思路                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   【資料表關聯】                                                │
│                                                                 │
│   users ────┐                                                   │
│             │ 1:N                                               │
│             ▼                                                   │
│   orders ◄────── customers (1:N)                               │
│      │                                                          │
│      │ 1:N                                                      │
│      ▼                                                          │
│   order_items ────► products (N:1)                             │
│                                                                 │
│   【設計原則】                                                  │
│   • UUID 作為主鍵 (避免序號猜測)                               │
│   • created_at / updated_at 必備                               │
│   • 軟刪除用 is_active 或 deleted_at                           │
│   • 金額用 DECIMAL(12,2)                                       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 📝 Vibe Coding Prompts

### **Step 1: 建立資料表**

```markdown
## Prompt 4-1: 建立 Supabase 資料表 SQL

【背景】
我要在 Supabase (PostgreSQL) 建立訂單管理系統的資料表。

【任務】
請給我完整的 SQL 腳本來建立以下資料表：

**1. users 表 (用戶)**
- id: UUID, 主鍵, 預設 gen_random_uuid()
- email: VARCHAR(255), 唯一, 不可空
- password_hash: VARCHAR(255), 不可空
- role: VARCHAR(20), 預設 'customer', CHECK (admin/staff/customer)
- is_active: BOOLEAN, 預設 true
- created_at: TIMESTAMPTZ, 預設 NOW()
- updated_at: TIMESTAMPTZ, 預設 NOW()

**2. customers 表 (客戶/CRM)**
- id: UUID, 主鍵
- company_name: VARCHAR(100), 不可空
- contact_person: VARCHAR(50), 不可空
- phone: VARCHAR(20), 不可空
- email: VARCHAR(255)
- address: TEXT
- credit_level: CHAR(1), 預設 'C', CHECK (A/B/C)
- notes: TEXT
- created_at, updated_at

**3. products 表 (商品)**
- id: UUID, 主鍵
- name: VARCHAR(100), 不可空
- category: VARCHAR(20), CHECK 列舉值
- price: DECIMAL(12,2), 不可空, CHECK > 0
- unit: VARCHAR(20), 預設 '個'
- description: TEXT
- stock: INTEGER, 預設 0, CHECK >= 0
- is_active: BOOLEAN, 預設 true
- created_at, updated_at

**4. orders 表 (訂單)**
- id: UUID, 主鍵
- order_number: VARCHAR(20), 唯一, 不可空 (格式: ORD-YYYYMMDD-XXXX)
- user_id: UUID, 外鍵 → users(id)
- customer_id: UUID, 外鍵 → customers(id)
- status: VARCHAR(20), 預設 'pending'
- total_amount: DECIMAL(12,2), 預設 0
- notes: TEXT
- created_at, updated_at

**5. order_items 表 (訂單明細)**
- id: UUID, 主鍵
- order_id: UUID, 外鍵 → orders(id), ON DELETE CASCADE
- product_id: UUID, 外鍵 → products(id)
- quantity: INTEGER, 不可空, CHECK > 0
- unit_price: DECIMAL(12,2), 不可空 (下單當時價格)
- subtotal: DECIMAL(12,2), GENERATED ALWAYS AS (quantity * unit_price)
- created_at

【額外需求】
1. 每個表都要有適當的索引
2. 建立 updated_at 自動更新的 trigger
3. 建立訂單編號自動產生的 function

【輸出格式】
完整的 SQL 腳本，包含：
1. CREATE TABLE 語句
2. CREATE INDEX 語句
3. CREATE FUNCTION 和 TRIGGER
4. 註解說明每個部分
```

### **Step 2: 測試資料**

```markdown
## Prompt 4-2: 產生測試資料 (Seed Data)

【背景】
資料表已建好，我需要一些測試資料來開發和 Demo。

【任務】
請產生 SQL INSERT 語句，包含：

**1. Users (5筆)**
- 1 個 admin (admin@orderflow.com / admin123)
- 2 個 staff
- 2 個 customer

**2. Customers (10筆)**
- 使用真實感的台灣公司名稱
- 電話格式：09XX-XXX-XXX
- 地址使用台灣地址格式
- 信用等級分布：2個A級、3個B級、5個C級

**3. Products (15筆)**
食品批發商的商品，包含：
- 3個水果類 (FRUIT)
- 3個蔬菜類 (VEGETABLE)
- 3個肉類 (MEAT)
- 3個海鮮類 (SEAFOOD)
- 3個乳製品 (DAIRY)

價格範圍：50-500 元
庫存範圍：10-200

**4. Orders (20筆)**
- 分布在過去30天
- 各種狀態都要有
- 每筆訂單有 2-5 個品項

**5. Order Items**
- 根據訂單自動產生
- 數量 1-10
- unit_price 使用商品當時價格

【格式要求】
- 密碼要用 bcrypt 加密 (給我 Python 程式碼來產生)
- 日期使用相對於今天的天數
- UUID 使用 gen_random_uuid()

【輸出】
1. seed.sql 檔案
2. 產生加密密碼的 Python 程式碼
```

### **Step 3: Python 連線設定**

```markdown
## Prompt 4-3: Python Supabase 連線模組

【背景】
我需要從 FastAPI 連線到 Supabase 資料庫。

【任務】
請建立 database.py 連線模組：

**1. 環境變數配置**
```python
# .env 檔案格式
SUPABASE_URL=https://xxxx.supabase.co
SUPABASE_KEY=eyJxxxx
DATABASE_URL=postgresql://postgres:xxx@db.xxxx.supabase.co:5432/postgres
```

**2. Supabase Client 初始化**
- 使用 supabase-py 套件
- Singleton 模式
- 連線測試函數

**3. 通用的 CRUD 工具函數**
```python
class DatabaseService:
    def __init__(self, table_name: str):
        self.table = table_name
    
    async def find_all(self, filters: dict = None, page: int = 1, page_size: int = 20)
    async def find_one(self, id: str)
    async def find_by(self, column: str, value: any)
    async def create(self, data: dict)
    async def update(self, id: str, data: dict)
    async def delete(self, id: str, soft: bool = True)
    async def count(self, filters: dict = None)
```

**4. 交易處理**
- 使用 psycopg2 或 asyncpg 處理需要交易的操作
- 提供 context manager

**5. 錯誤處理**
- 自定義例外類別
- 連線重試機制

【輸出】
完整的 database.py 和 .env.example
```

## ✅ 驗收檢查清單

```
□ 所有資料表成功建立
□ 外鍵關聯正確
□ 索引已建立
□ updated_at 自動更新
□ 測試資料已匯入
□ Python 可成功連線
□ CRUD 操作正常
□ 密碼正確加密
```

---

# 模組 5️⃣：Google Sheet 整合

## 🎯 模組目標

```
┌─────────────────────────────────────────────────┐
│  將資料庫數據同步到 Google Sheet                 │
│  供非技術人員查看報表                            │
└─────────────────────────────────────────────────┘
```

## 📐 架構思路

```
┌─────────────────────────────────────────────────────────────────┐
│                    Google Sheet 整合思路                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   【認證方式】                                                  │
│   Service Account ──► 不需用戶登入，背景執行                    │
│                                                                 │
│   【同步策略】                                                  │
│   ┌─────────┐      ┌─────────┐      ┌─────────┐               │
│   │ 手動觸發 │      │ 定時任務 │      │ 事件觸發 │               │
│   │ API 呼叫 │      │ 每日凌晨 │      │ 訂單完成 │               │
│   └─────────┘      └─────────┘      └─────────┘               │
│                                                                 │
│   【Sheet 結構】                                                │
│   📊 OrderFlow 報表                                             │
│   ├── 本週訂單明細                                              │
│   ├── 月營收彙總                                                │
│   ├── 客戶消費排行                                              │
│   └── 商品銷量統計                                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 📝 Vibe Coding Prompts

### **Step 1: 設定 Service Account**

```markdown
## Prompt 5-1: Google Service Account 設定指南

【背景】
我需要讓 Python 程式自動寫入 Google Sheet，不需要用戶手動授權。

【任務】
請給我完整的設定步驟教學：

**1. Google Cloud Console 設定**
- 建立專案
- 啟用 Google Sheets API
- 啟用 Google Drive API
- 建立 Service Account
- 下載 JSON 金鑰

**2. Google Sheet 權限設定**
- 如何將 Sheet 分享給 Service Account
- Service Account 的 email 格式說明

**3. 環境變數配置**
- JSON 金鑰的處理方式
- 建議的 .env 格式

**4. 安全注意事項**
- 不要把 JSON 金鑰 commit 到 git
- 生產環境的建議做法

【輸出格式】
Step by step 教學，包含截圖位置說明
```

### **Step 2: Google Sheet 服務模組**

```markdown
## Prompt 5-2: Google Sheet 操作服務

【背景】
Service Account 已設定好，我需要 Python 模組來操作 Google Sheet。

【任務】
請建立 sheets/service.py：

**1. 初始化連線**
```python
import gspread
from google.oauth2.service_account import Credentials

class GoogleSheetService:
    def __init__(self):
        # 從環境變數或 JSON 檔案載入憑證
        # 連接到指定的 Spreadsheet
        pass
```

**2. 基本操作函數**
```python
def get_worksheet(self, sheet_name: str)
    """取得或建立工作表"""

def clear_worksheet(self, sheet_name: str)
    """清空工作表內容"""

def write_header(self, sheet_name: str, headers: list)
    """寫入標題列（粗體、凍結）"""

def append_rows(self, sheet_name: str, data: list[list])
    """批次新增多列資料"""

def update_cell(self, sheet_name: str, row: int, col: int, value)
    """更新單一儲存格"""

def format_as_currency(self, sheet_name: str, column: str)
    """將指定欄位格式化為貨幣"""

def format_as_date(self, sheet_name: str, column: str)
    """將指定欄位格式化為日期"""
```

**3. 報表產生函數**
```python
async def generate_weekly_orders_report(self, start_date, end_date)
    """
    產生週訂單明細報表
    欄位：訂單編號、客戶、商品明細、金額、狀態、日期
    """

async def generate_monthly_revenue_summary(self, year: int, month: int)
    """
    產生月營收彙總
    欄位：日期、訂單數、營收、平均單價
    最後一列：當月合計
    """

async def generate_customer_ranking(self, top_n: int = 20)
    """
    產生客戶消費排行
    欄位：排名、公司名稱、聯絡人、總消費、訂單數、平均單價、等級
    """

async def generate_product_sales_report(self, start_date, end_date)
    """
    產生商品銷量報表
    欄位：商品名稱、分類、銷售數量、銷售金額、佔比
    """
```

**4. 錯誤處理**
- API 限流處理 (429 Too Many Requests)
- 重試機制 (exponential backoff)
- 操作失敗通知

【輸出】
完整的 sheets/service.py
```

### **Step 3: API 端點**

```markdown
## Prompt 5-3: 報表 API 端點

【背景】
我需要在後台提供「匯出報表」的功能。

【任務】
請建立 sheets/router.py：

**1. 手動觸發報表產生**
```python
POST /admin/reports/weekly-orders
Body: { "start_date": "2024-01-01", "end_date": "2024-01-07" }
Response: { 
    "success": true, 
    "sheet_url": "https://docs.google.com/spreadsheets/d/xxx",
    "rows_written": 150
}

POST /admin/reports/monthly-revenue
Body: { "year": 2024, "month": 1 }

POST /admin/reports/customer-ranking
Body: { "top_n": 20 }

POST /admin/reports/product-sales
Body: { "start_date": "...", "end_date": "..." }
```

**2. 取得報表狀態**
```python
GET /admin/reports/status
Response: {
    "last_sync": "2024-01-10T08:00:00Z",
    "sheet_url": "https://...",
    "available_sheets": ["週訂單明細", "月營收彙總", ...]
}
```

**3. 定時任務設定**
```python
# 每天凌晨 2 點執行
POST /admin/reports/schedule
Body: { "report_type": "weekly-orders", "cron": "0 2 * * *" }
```

【權限】
僅限 admin 角色存取

【輸出】
完整的 sheets/router.py
```

### **Step 4: 定時任務**

```markdown
## Prompt 5-4: 定時同步任務

【背景】
我希望每天自動產生報表到 Google Sheet。

【任務】
請用 APScheduler 實作定時任務：

**1. 安裝與設定**
```python
from apscheduler.schedulers.asyncio import AsyncIOScheduler
from apscheduler.triggers.cron import CronTrigger
```

**2. 排程任務定義**
```python
# 每天凌晨 2:00 - 同步昨日訂單
# 每週一 3:00 - 產生上週週報
# 每月 1 號 4:00 - 產生上月月報
```

**3. 任務執行記錄**
- 記錄每次執行的時間、結果
- 失敗時發送通知 (可選)

**4. 整合到 FastAPI**
```python
# main.py
@app.on_event("startup")
async def start_scheduler():
    ...

@app.on_event("shutdown")
async def shutdown_scheduler():
    ...
```

【輸出】
scheduler.py 和 main.py 的整合程式碼
```

## ✅ 驗收檢查清單

```
□ Service Account 設定完成
□ Python 可連線 Google Sheet
□ 可寫入資料到工作表
□ 報表格式正確 (貨幣、日期)
□ API 可觸發報表產生
□ 定時任務正常執行
□ 錯誤有適當處理
□ Google Sheet 有適當權限
```

---

# 模組 6️⃣：CRM 客戶管理系統

## 🎯 模組目標

```
┌─────────────────────────────────────────────────┐
│  完整的客戶關係管理功能                          │
│  客戶分級、消費分析、流失預警                    │
└─────────────────────────────────────────────────┘
```

## 📐 架構思路

```
┌─────────────────────────────────────────────────────────────────┐
│                       CRM 架構思路                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   【CRM 核心功能】                                              │
│   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐         │
│   │  客戶資料   │   │  消費分析   │   │  智能標籤   │         │
│   │  CRUD       │   │  RFM 模型   │   │  自動分級   │         │
│   └─────────────┘   └─────────────┘   └─────────────┘         │
│                                                                 │
│   【RFM 分析模型】                                              │
│   R (Recency)  = 最近一次消費距今天數                          │
│   F (Frequency) = 消費頻率 (過去90天訂單數)                    │
│   M (Monetary)  = 消費金額 (過去90天總金額)                    │
│                                                                 │
│   【自動分級邏輯】                                              │
│   A級: RFM 總分 >= 12 或 月消費 > 50,000                       │
│   B級: RFM 總分 >= 8  或 月消費 > 10,000                       │
│   C級: 其他                                                     │
│                                                                 │
│   【流失預警】                                                  │
│   ⚠️ 超過 30 天未下單的活躍客戶                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 📝 Vibe Coding Prompts

### **Step 1: CRM 資料模型**

```markdown
## Prompt 6-1: CRM 資料模型設計

【背景】
我要建立 CRM 模組，除了基本 CRUD 還需要客戶分析功能。

【任務】
請建立 customers/models.py：

**1. CreditLevel Enum**
- A: 高價值客戶
- B: 中等價值客戶
- C: 一般客戶

**2. CustomerBase**
- company_name: 公司名稱 (必填，最長100字)
- contact_person: 聯絡人 (必填，最長50字)
- phone: 電話 (必填，驗證格式)
- email: 電子郵件 (選填，驗證格式)
- address: 地址 (選填)
- notes: 備註 (選填)

**3. CustomerCreate** (繼承 CustomerBase)

**4. CustomerUpdate** (所有欄位選填)

**5. CustomerInDB**
- id: UUID
- 所有 Base 欄位
- credit_level: CreditLevel
- created_at, updated_at

**6. CustomerStats** (客戶統計)
- total_orders: 總訂單數
- total_spent: 總消費金額
- average_order_value: 平均單價
- last_order_date: 最後訂單日
- days_since_last_order: 距上次下單天數
- monthly_average: 月平均消費

**7. CustomerRFM** (RFM 分析結果)
- recency_score: 1-5
- frequency_score: 1-5
- monetary_score: 1-5
- total_score: 3-15
- segment: 客戶分群標籤

**8. CustomerResponse** (完整回傳)
- 基本資訊 + stats + rfm
- is_at_risk: 是否有流失風險

**9. CustomerListResponse**
- items: List[CustomerResponse]
- total, page, page_size
- at_risk_count: 有風險的客戶數

【輸出】
完整的 customers/models.py
```

### **Step 2: CRM 業務邏輯**

```markdown
## Prompt 6-2: CRM 服務層 - 分析與智能功能

【背景】
CRM 的核心價值在於數據分析，幫助識別高價值客戶和流失風險。

【任務】
請建立 customers/service.py：

**1. 基本 CRUD**
```python
async def list_customers(
    page: int = 1,
    page_size: int = 20,
    credit_level: CreditLevel = None,
    search: str = None,
    sort_by: str = "updated_at",
    sort_order: str = "desc",
    at_risk_only: bool = False
) -> CustomerListResponse

async def get_customer(customer_id: UUID) -> CustomerResponse | None

async def create_customer(data: CustomerCreate) -> CustomerResponse

async def update_customer(customer_id: UUID, data: CustomerUpdate) -> CustomerResponse

async def delete_customer(customer_id: UUID) -> bool
```

**2. 統計計算**
```python
async def calculate_customer_stats(customer_id: UUID) -> CustomerStats
    """
    計算單一客戶的消費統計
    查詢該客戶所有訂單，計算：
    - 總訂單數
    - 總消費金額
    - 平均單價
    - 最後訂單日期
    - 月平均消費 (過去12個月)
    """
```

**3. RFM 分析**
```python
async def calculate_rfm(customer_id: UUID) -> CustomerRFM
    """
    計算 RFM 分數
    
    Recency 評分 (距上次下單天數):
    - <= 7 天: 5分
    - <= 14 天: 4分
    - <= 30 天: 3分
    - <= 60 天: 2分
    - > 60 天: 1分
    
    Frequency 評分 (過去90天訂單數):
    - >= 10 筆: 5分
    - >= 6 筆: 4分
    - >= 3 筆: 3分
    - >= 1 筆: 2分
    - 0 筆: 1分
    
    Monetary 評分 (過去90天消費):
    - >= 100,000: 5分
    - >= 50,000: 4分
    - >= 20,000: 3分
    - >= 5,000: 2分
    - < 5,000: 1分
    
    分群標籤:
    - 總分 >= 13: "VIP客戶"
    - 總分 >= 10: "高價值客戶"
    - 總分 >= 7: "一般客戶"
    - 總分 >= 4: "低活躍客戶"
    - 總分 < 4: "流失風險客戶"
    """

async def calculate_all_rfm() -> list[dict]
    """批次計算所有客戶的 RFM"""
```

**4. 自動分級**
```python
async def auto_update_credit_levels()
    """
    根據 RFM 分數自動更新客戶等級
    每日執行一次
    """
```

**5. 流失預警**
```python
async def get_at_risk_customers() -> list[CustomerResponse]
    """
    找出有流失風險的客戶:
    - 過去 90 天有消費
    - 最近 30 天沒有消費
    - 原本是 A 或 B 級客戶
    """

async def get_churn_analysis() -> dict
    """
    流失分析報告:
    - 本月流失客戶數
    - 流失客戶總價值
    - 流失原因分析 (如果有備註)
    """
```

**6. 客戶旅程**
```python
async def get_customer_timeline(customer_id: UUID) -> list
    """
    取得客戶互動時間軸:
    - 訂單記錄
    - 等級變更記錄
    - 備註記錄
    按時間排序
    """
```

【輸出】
完整的 customers/service.py
```

### **Step 3: CRM API 端點**

```markdown
## Prompt 6-3: CRM API 路由

【背景】
需要對外暴露 CRM 功能的 API。

【任務】
請建立 customers/router.py：

**1. 基本 CRUD**
```
GET    /api/customers              列表 (支援篩選)
GET    /api/customers/{id}         單筆詳情 (含 stats + rfm)
POST   /api/customers              新增
PUT    /api/customers/{id}         更新
DELETE /api/customers/{id}         刪除
```

**2. 分析相關**
```
GET    /api/customers/{id}/stats      該客戶統計
GET    /api/customers/{id}/rfm        該客戶 RFM
GET    /api/customers/{id}/orders     該客戶訂單歷史
GET    /api/customers/{id}/timeline   該客戶互動時間軸
```

**3. 批次操作**
```
GET    /api/customers/at-risk         流失風險客戶列表
GET    /api/customers/analysis        整體客戶分析報告
POST   /api/customers/recalculate     重新計算所有客戶等級
```

**4. 匯出功能**
```
GET    /api/customers/export          匯出客戶資料 (CSV)
```

【完整回傳範例】
```json
{
  "id": "uuid",
  "company_name": "好味餐廳",
  "contact_person": "王小明",
  "phone": "0912-345-678",
  "email": "wang@goodtaste.com",
  "address": "台北市信義區松高路1號",
  "credit_level": "A",
  "notes": "偏好有機蔬菜",
  "created_at": "2024-01-01T00:00:00Z",
  "stats": {
    "total_orders": 45,
    "total_spent": 567800,
    "average_order_value": 12617,
    "last_order_date": "2024-01-08",
    "days_since_last_order": 2,
    "monthly_average": 47316
  },
  "rfm": {
    "recency_score": 5,
    "frequency_score": 4,
    "monetary_score": 5,
    "total_score": 14,
    "segment": "VIP客戶"
  },
  "is_at_risk": false
}
```

【輸出】
完整的 customers/router.py
```

### **Step 4: 前端 CRM 頁面 Prompt (Lovable)**

```markdown
## Lovable Prompt 6-4: CRM 進階功能頁面

Enhance the existing Customers page with advanced CRM features.

## Customer Detail Page (/customers/:id)

### Header Section
- Large customer name
- Credit level badge (A/B/C with colors)
- "At Risk" warning badge if applicable
- Edit and Delete buttons

### Stats Cards Row (4 cards)
1. 總消費金額 - NT$ XXX,XXX
2. 訂單次數 - XX 筆
3. 平均單價 - NT$ X,XXX
4. 上次消費 - X 天前

### RFM Score Card
Visual representation:
```
┌─────────────────────────────────────┐
│  RFM 分析                [VIP客戶] │
├─────────────────────────────────────┤
│  R (Recency)    ████████░░  4/5    │
│  F (Frequency)  ██████████  5/5    │
│  M (Monetary)   ████████░░  4/5    │
├─────────────────────────────────────┤
│  總分: 13/15                        │
└─────────────────────────────────────┘
```

### Tabs
1. **訂單記錄** 
   - Table of customer's orders
   - Status filter
   - Date range filter

2. **消費趨勢**
   - Line chart: 月消費趨勢 (past 12 months)
   - Bar chart: 商品類別偏好

3. **互動時間軸**
   - Timeline component showing:
     - 🛒 Order placed
     - ⭐ Credit level changed
     - 📝 Note added
   - Each item shows date and details

4. **基本資料**
   - Editable form
   - Company info
   - Contact info
   - Notes textarea

## At-Risk Customers Page (/customers/at-risk)

### Alert Banner
"⚠️ 目前有 X 位客戶有流失風險，建議立即關懷"

### Customer Cards
Each card shows:
- Customer name and contact
- Last order: X days ago
- Previous monthly average
- "Contact" button (opens email)
- "Add Note" button

### Actions
- "匯出名單" button
- "發送關懷信" button (future feature placeholder)

## Customer Analysis Dashboard (/customers/analysis)

### Overview Stats
- Total customers by level (pie chart)
- Monthly new customers (line chart)
- Churn rate trend (line chart)

### RFM Distribution
- Scatter plot: R vs F vs M
- Customer segments breakdown

### Top Customers Table
- Top 10 by revenue
- Top 10 by order frequency

Please implement with smooth animations and proper loading states.
```

## ✅ 驗收檢查清單

```
□ 客戶 CRUD 正常運作
□ 統計數據正確計算
□ RFM 分數計算正確
□ 自動分級邏輯正確
□ 流失預警功能正常
□ 客戶時間軸顯示正確
□ 前端 RFM 視覺化正常
□ At-Risk 列表正確篩選
□ 匯出功能正常
```

---

# 📋 總整理：Prompt 使用順序

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        建議開發順序                                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Phase 1: 基礎建設 (Week 1)                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  模組4 Prompt 4-1 → 建立資料表                                      │   │
│  │  模組4 Prompt 4-2 → 匯入測試資料                                    │   │
│  │  模組4 Prompt 4-3 → Python 連線                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                               ▼                                             │
│  Phase 2: 會員系統 (Week 2)                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  模組1 Prompt 1-1 → 資料模型                                        │   │
│  │  模組1 Prompt 1-2 → JWT 工具                                        │   │
│  │  模組1 Prompt 1-3 → 服務層                                          │   │
│  │  模組1 Prompt 1-4 → API 路由                                        │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                               ▼                                             │
│  Phase 3: 後台管理 (Week 3)                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  模組2 Prompt 2-1 → 商品模型                                        │   │
│  │  模組2 Prompt 2-2 → 商品服務                                        │   │
│  │  模組2 Prompt 2-3 → 商品路由                                        │   │
│  │  模組2 Prompt 2-4 → 訂單管理                                        │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                               ▼                                             │
│  Phase 4: 前端介面 (Week 4)                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  模組3 Prompt 3-1 → 登入頁                                          │   │
│  │  模組3 Prompt 3-2 → 主要佈局                                        │   │
│  │  模組3 Prompt 3-3 → 儀表板                                          │   │
│  │  模組3 Prompt 3-4 → 訂單頁                                          │   │
│  │  模組3 Prompt 3-5 → 客戶頁                                          │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                               ▼                                             │
│  Phase 5: 進階功能 (Week 5)                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  模組6 Prompt 6-1~6-4 → CRM 完整功能                                │   │
│  │  模組5 Prompt 5-1~5-4 → Google Sheet 整合                           │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🎁 額外資源

需要我提供以下任何項目嗎？

1. **完整的 requirements.txt** - Python 套件清單
2. **Docker 部署設定** - docker-compose.yml
3. **環境變數範本** - .env.example
4. **API 文檔範本** - OpenAPI/Swagger 設定
5. **測試案例 Prompt** - 單元測試和整合測試