# LLM 市場三圖儀表板

GitHub Pages：https://frankx180.github.io/llm-market-dashboard/

三張圖：
1. SDLLMTK 價格（USD / 百萬 tokens）
2. OpenRouter 各品牌 Token 使用量（billion tokens，日／週）
3. 價格 × 用量支出 proxy（USD / 天）

## 資料來源

- SDLLMTK 價格：Silicon Data public embed（`portal.silicondata.com/token-index-chart`），每天更新
- OpenRouter 用量：OpenRouter Datasets API（`openrouter.ai/api/v1/datasets/rankings-daily`），每週一更新

## 自動更新

GitHub Actions（`.github/workflows/update-dashboard.yml`）：
- 每天 08:00 UTC（台灣 16:00）：更新 SDLLMTK 單價
- 每週一 08:00 UTC：完整更新（OpenRouter 用量 + 單價）

更新後自動 commit `index.html`，GitHub Pages 即時生效。

## 手動觸發

Repo → Actions → update-dashboard → Run workflow（完整更新）。

## 本機對應

原始專案：`E:\_Project\股票研究\產業知識庫\03_產業鏈\SDLLMTK_LLM代幣支出指數\`
- `update_market_triple.py`：產生儀表板
- `fetch_openrouter_daily.py`：抓 OpenRouter 用量
- `run_sdllmtk_daily.py`：本機每日排程入口
