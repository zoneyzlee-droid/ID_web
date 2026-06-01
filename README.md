# 室內設計學程｜新聞自動發布系統

## 功能說明

填寫關鍵字、上傳照片 → Gemini AI 自動生成新聞稿 → 預覽編輯 → 一鍵發布到 WordPress

---

## 設定步驟

### 第一步：上傳檔案到 GitHub Repository

將以下檔案上傳到 `zoneyzlee-droid/ID_web` repository：

```
index.html
.github/
  workflows/
    preview.yml
    publish.yml
```

### 第二步：設定 GitHub Secrets

到 Repository → **Settings → Secrets and variables → Actions → New repository secret**

新增以下四個 Secrets：

| Secret 名稱 | 說明 | 範例 |
|------------|------|------|
| `GEMINI_API_KEY` | Google AI Studio API Key | `AIza...` |
| `WP_URL` | WordPress 網站網址 | `http://id.fcu.edu.tw` |
| `WP_USERNAME` | WordPress 使用者名稱 | `fcuid` |
| `WP_APP_PASSWORD` | WordPress 應用程式密碼 | `xxxx xxxx xxxx xxxx` |

### 第三步：建立 GitHub Label

到 Repository → **Issues → Labels → New label**

建立標籤：
- 名稱：`news-publish`
- 顏色：任意

### 第四步：啟用 GitHub Pages

到 Repository → **Settings → Pages**
- Source: `Deploy from a branch`
- Branch: `main` / `/(root)`

### 第五步：建立 GitHub Personal Access Token

到 [GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)](https://github.com/settings/tokens)
- 勾選 `repo` 權限
- 複製 Token（介面使用時需要輸入，只在本次瀏覽器 session 儲存）

---

## 使用流程

1. 開啟 GitHub Pages 網址
2. 輸入 GitHub Personal Access Token（首次使用時）
3. 上傳照片
4. 填寫關鍵字、選擇對象、語氣、語言
5. 點「送出預覽請求」
6. 等待 1~2 分鐘
7. 點「載入預覽結果」
8. 直接在頁面上編輯標題／內文
9. 點「確認發布到 WordPress」
10. 等待 1~2 分鐘，WordPress 自動更新

---

## 注意事項

- GitHub Personal Access Token 僅存在瀏覽器 session，關閉分頁後清除
- WordPress Application Password 存在 GitHub Secrets，完全不暴露在前端
- Gemini API Key 存在 GitHub Secrets，完全不暴露在前端
