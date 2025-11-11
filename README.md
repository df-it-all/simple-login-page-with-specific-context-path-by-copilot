# simple-login-page-with-specific-context-path-by-copilot

使用 Vite + Vue + SCSS 建立的簡單登入網站，支援環境變數設定不同的 Context Path。

## 功能特色

- ✅ 三個頁面：登入頁、登入後的歡迎頁、關於我們
- ✅ 使用 Vue Router 實現路由管理
- ✅ 簡單的登入驗證機制（使用 localStorage）
- ✅ 環境變數配置（開發/正式環境）
- ✅ 支援自訂 Context Path
- ✅ SCSS 樣式設計

## 環境設定

專案使用環境變數檔案來設定不同環境的 Context Path：

- **開發環境** (`.env.development`): `VITE_CONTEXT_PATH=/`
- **正式環境** (`.env.production`): `VITE_CONTEXT_PATH=/foo/bar`

## 可用的指令

```bash
# 安裝依賴
npm install

# 開發模式（使用開發環境設定）
npm run dev

# 開發模式（使用正式環境設定）
npm run dev:production

# 建置專案（使用正式環境設定）
npm run build

# 預覽建置結果
npm run preview
```

## 技術堆疊

- **Vue 3** - 前端框架
- **Vite** - 建置工具
- **Vue Router** - 路由管理
- **SCSS** - CSS 預處理器

## 專案結構

```
src/
├── router/           # 路由設定
│   └── index.js
├── views/            # 頁面元件
│   ├── Login.vue     # 登入頁
│   ├── Welcome.vue   # 歡迎頁
│   └── About.vue     # 關於我們
├── App.vue           # 主元件
└── main.js           # 入口檔案
```

## 開發說明

1. 登入頁面接受任何使用者名稱和密碼
2. 登入後會導向歡迎頁面
3. 未登入的使用者無法直接訪問歡迎頁面
4. 關於我們頁面可以在未登入狀態下訪問
5. 頁面會顯示當前環境模式和 Context Path

