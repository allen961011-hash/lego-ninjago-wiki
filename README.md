# 樂高旋風忍者（LEGO NINJAGO）LLM Wiki 與教學型 HTML 簡報

本專案為「生成式 AI：文字與圖像生成的原理與實務」第十週作業成果。專案先透過「先討論、後生成」的方式建立結構化的 **LEGO NINJAGO LLM Wiki**（共 Ingest 6 篇官方與百科資料），再以該 Wiki 作為唯一知識來源，製作出適合完全零基礎新手的互動式教學簡報。

* **線上教學簡報（GitHub Pages）**：https://allen961011-hash.github.io/lego-ninjago-wiki/
* **LLM Wiki 知識庫目錄**：[wiki/index.md](./wiki/index.md)
* **Wiki 維護與 Ingest 日誌**：[wiki/log.md](./wiki/log.md)

---

## 步驟三：Loop / Graph 流程設計說明

### 1. 整體運作流程（Graph 與 Loop 結構）

```mermaid
flowchart TD
    A[1. 先討論：定義 Wiki 範圍與檔案架構] --> B{Human-in-the-Loop 確認}
    B -->|調整主題與來源清單| A
    B -->|確認定案| C[2. 分批 Ingest 外部資料<br/>共 6 篇來源 / 分 3 批次]
    C --> D[萃取重點並寫入 Wiki 條目<br/>01~05.md]
    D --> E[同步更新 index.md 與 log.md]
    E --> F{檢查點 1：交叉連結與譯名一致性}
    F -->|尚有未完成來源或斷鏈| C
    F -->|6 篇全數完成且結構完整| G[3. 僅以 Wiki 為來源生成 HTML 簡報]
    G --> H{檢查點 2：新手可讀性與互動驗收}
    H -->|內容過深或版面需調整| G
    H -->|通過檢查| I[4. 部署 GitHub Pages 完成交付]
