# medical-paper-reviser

**Version 1.0.0**

英文醫學 original paper（IMRAD 格式）改稿助手，以繁體中文提供建議。

---

## 快速開始

**第一步 — Clone 專案**
```bash
git clone https://github.com/LiangWeiTseng/medical-paper-reviser.git
cd medical-paper-reviser
```

**第二步 — 安裝套件**
```bash
pip install python-docx
```

**第三步 — 設定路徑**  
開啟 [`.claude/commands/revise-paper.md`](.claude/commands/revise-paper.md)，將最上方兩行改為本機的絕對路徑：
```
SOURCE_DIR  = /這台電腦上的絕對路徑/input
OUTPUT_DIR  = /這台電腦上的絕對路徑/output
```

**第四步 — 放入論文**  
將 `.docx` 放入 `input/`，圖片（選填）放入 `input/figures/`。

**第五步 — 執行**  
在此資料夾開啟 Claude Code，輸入：
```
/revise-paper
```
Claude 會引導後續步驟。

---

## 資料夾結構

```
medical-paper-reviser/
├── .claude/
│   └── commands/
│       └── revise-paper.md   ← slash command 定義（在此修改路徑）
├── input/
│   ├── paper.docx            ← 放論文檔案
│   └── figures/              ← 圖片（選填）
│       ├── fig1.png
│       └── fig2.png
├── output/                   ← 報告與修訂檔輸出位置
└── README.md
```

`input/figures/` 內的圖片會自動偵測，檔名需對應 Figure 編號（如 `fig1.png`、`figure_2.jpg`）。

---

## 使用方式

在此資料夾開啟 Claude Code，輸入 `/revise-paper`，Claude 會列出 `input/` 內的 `.docx` 供選擇。  
也可直接指定路徑：

```
/revise-paper path/to/paper.docx
/revise-paper path/to/paper.docx path/to/figures/
```

---

## 改稿項目

啟動後選擇項目（可多選，如 `1 3 6`；或輸入 `all`）：

| # | 項目 | 檢查內容 |
|---|------|---------|
| 1 | 語言潤飾 | 文法、時態、用字、代名詞、平行結構 |
| 2 | 學術寫作風格 | 被動語態、Hedging、正式程度、縮寫定義 |
| 3 | 結構與邏輯 | IMRAD 完整性、段落邏輯、Title 檢查 |
| 4 | 圖表細節 | 編號、圖說、圖文對應 |
| 5 | 參考文獻建議 | 標記缺 citation 的論點（不捏造文獻） |
| 6 | 段落補齊 | 缺失 IMRAD 章節 + 投稿必填欄位 |

---

## 輸出格式

| 選項 | 輸出 |
|------|------|
| A | `output/paper_feedback.md` — 繁體中文改稿報告 |
| B | `output/paper_revised.docx` — 修改處以紅字標示 |
| AB | 兩者都輸出 |

---

## 適用範圍

- **論文類型：** 英文醫學 original paper（IMRAD 結構）
- **建議語言：** 繁體中文
- **論文原文與修改建議：** 保持英文
- **文獻建議：** 僅提供搜尋方向，絕不捏造作者、標題或 DOI