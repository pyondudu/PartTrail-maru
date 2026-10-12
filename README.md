# PartTrail—maru 料件交期追蹤

網址：https://pyondudu.github.io/PartTrail-maru/

| 元件 | 說明 |
|---|---|
| `supabase/schema.sql` | 資料庫結構、權限（RLS）、附檔 Storage、交期與狀態歷程 trigger |
| `web/` | 追蹤總表網頁（Vue 3 + Vite），手機／電腦皆可用，可加到手機主畫面 |

狀態流程：**已報價** → **已下單** → **已收貨**

## 部署
push `web/**` 到 `main` 會自動部署到 GitHub Pages。需要的 Secrets：`SUPABASE_URL`、`SUPABASE_ANON_KEY`。

## 外觀
網站名稱、主題色、配色與圖示都在 `web/sites/main/`（`site.json`、`app-icon.svg`、`icon-192.png`、`icon-512.png`）。

## 帳號
Supabase 已關閉開放註冊。新增帳號：**Authentication → Users → Add user → Create new user**，勾選 **Auto Confirm User**。
登入時只輸入名字，網頁會自動補上 `@parttrail.local`。新帳號預設唯讀，要改成編輯者：
```sql
update public.profiles set role = 'editor' where email = '名字@parttrail.local';
```

## 本機試用
```bash
cd web
cp .env.example .env     # 填入 Project URL 與 anon key
npm install
npm run dev
```
