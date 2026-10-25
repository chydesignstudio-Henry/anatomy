<h1 align="center">Anatomy</h1>

<p align="center"><b>一個 Claude skill，透過將概念建造成真實可運作的物件來解釋想法。</b><br>同時支援 Antigravity、OpenCode、Codex 與 MiniMax Code。<br>精心製作的互動式等角投影圖，包含許多小而精準的零件，使用 SVG、WebGL 與 3D。</p>

<p align="center">
  <a href="https://code.claude.com/docs/en/skills"><img src="https://img.shields.io/badge/Claude_Code-skill-1b1b19?style=flat-square&logo=claude&logoColor=white" alt="Claude Code skill"></a>
  <a href="https://agentskills.io"><img src="https://img.shields.io/badge/Agent_Skills-compatible-1b1b19?style=flat-square" alt="Agent Skills compatible"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-1b1b19?style=flat-square" alt="MIT license"></a>
  <a href="#requirements"><img src="https://img.shields.io/badge/node-%E2%89%A5%2020.10-1b1b19?style=flat-square&logo=nodedotjs&logoColor=white" alt="Node 20.10 or later"></a>
  <a href="#requirements"><img src="https://img.shields.io/badge/dependencies-0-1b1b19?style=flat-square" alt="No dependencies"></a>
  <a href="https://github.com/wheresryan22/anatomy/actions/workflows/ci.yml"><img src="https://github.com/wheresryan22/anatomy/actions/workflows/ci.yml/badge.svg" alt="CI"></a>
</p>

<p align="center">
  <a href="https://skills.wheresryan.sh/anatomy"><img src="https://img.shields.io/badge/Website-skills.wheresryan.sh%2Fanatomy-1b1b19?style=for-the-badge" alt="Website: skills.wheresryan.sh/anatomy"></a>
  &nbsp;
  <a href="https://github.com/wheresryan22/anatomy/archive/refs/heads/main.zip"><img src="https://img.shields.io/badge/Download-ZIP-1b1b19?style=for-the-badge&logo=github&logoColor=white" alt="Download ZIP"></a>
  &nbsp;
  <a href="#install"><img src="https://img.shields.io/badge/Install-npx_skills_add-d7d7d0?style=for-the-badge&labelColor=1b1b19&logo=npm&logoColor=white" alt="Install with npx"></a>
</p>

<p align="center">
  <a href="#quick-start">快速開始</a> ·
  <a href="#gallery">圖庫</a> ·
  <a href="#what-it-makes">它能製作什麼</a> ·
  <a href="#install">安裝</a> ·
  <a href="#usage">使用方式</a> ·
  <a href="#examples">範例</a> ·
  <a href="#how-it-works">運作原理</a> ·
  <a href="#limits">限制</a>
</p>

<p align="center">
  <img src=".github/assets/raptor-engine-firing.webp" width="640" alt="等角投影圖：Raptor 2 火箭引擎懸掛在測試台上點火，紅色排氣羽流由 WebGL 著色器繪製，噴向測試台底板。卡片顯示 Fig 1, Raptor 2 test stand, Pc 300 bar, 230 tf。">
</p>

<p align="center"><sub><code>examples/raptor-engine</code>，淺色主題，點火狀態。引擎與支架為 SVG；羽流為同一等角相機中的 WebGL 著色器。</sub></p>

---

向 Claude 要求一張解釋技術概念的圖，Anatomy 會讓它發明一個「運作方式本身就是該概念」的實體物件。一個在沒有變化時跳過工作的快取鍵，變成只有每個銷都對齊時才會轉動的銷釘彈子鎖。一個服務多個畫布的 GPU 上下文，變成單一列印頭巡訪 16 個井的龍門繪圖機。

接著 Claude 會用數十個小而實心、有陰影的零件建造這個物件，將它放入帶有標題、提示與即時讀數的框卡片中，讓它在滑鼠指標與鍵盤下平穩移動，並透過放大每個接頭來自我檢查。圖中顯示的每一個數字都來自驅動零件移動的同一個小型模型。

## 快速開始

```sh
npx skills add wheresryan22/anatomy -g
```

CLI 會詢問要設定哪些 agent（Claude Code、Antigravity、OpenCode、Codex、MiniMax Code）。若要跳過詢問，可加上 `-a claude-code`、`-a antigravity`、`-a opencode`、`-a codex` 或 `-a minimax-code`。

接著在 Claude Code 中輸入：

```text
/anatomy explain how a token bucket rate limiter works, interactive
```

對於 Antigravity、OpenCode、Codex 或 MiniMax Code，請指定該 agent：`-a antigravity`、`-a opencode`、`-a codex` 或 `-a minimax-code`。Antigravity、OpenCode 與 MiniMax Code 使用相同的 `/anatomy` 指令；在 Codex 中則輸入 `$anatomy`。

就這樣。不需要 API 金鑰，也不需要 `npm install`：工具包只使用 Node 的內建模組。

## 圖庫

<table>
  <tr>
    <td width="50%"><img src=".github/assets/raptor-engine-apart.webp" alt="Raptor 2 引擎在測試台上被拆解：其組件、管路與線束在支架柱之間彼此分開懸掛。"></td>
    <td width="50%"><img src=".github/assets/ripple-tank.webp" alt="四隻高腳的學校波動水槽，上方有燈臂。振動桿上的兩個探針產生干涉波，其焦散投射到水槽下方的紙幕上。"></td>
  </tr>
  <tr>
    <td><sub><b>raptor-engine</b>：懸停可拆解成 11 個組件。審計證明沒有管路穿過任何物件，無論靜止、拆解或中間每一幀皆然。</sub></td>
    <td><sub><b>ripple-tank</b>：SVG 裝置疊加兩層 WebGL（紙上的燈光與焦散、水中的反射），由色散與光學模型驅動。</sub></td>
  </tr>
  <tr>
    <td><img src=".github/assets/turning-dial.webp" alt="凸起門板上的密碼轉盤。一隻小金鉻機器人手躺在轉盤上並隨之轉動；一個指尖下方發出綠光。"></td>
    <td><img src=".github/assets/dial-indicator.webp" alt="支架上的千分表，底座有尺條。其測頭停在滑動托架上三個量塊之一上。"></td>
  </tr>
  <tr>
    <td><sub><b>turning-dial</b>：3D 模式（beta）。拖動轉盤時，約 90 個零件每幀重新投影並重新著色。</sub></td>
    <td><sub><b>dial-indicator</b>：最小範例，約 300 行。懸停可滑動托架；指針讀取每個量塊。</sub></td>
  </tr>
</table>

每張截圖皆為 [`examples/`](examples) 中頁面的淺色主題，由 skill 自身的 [`scripts/capture.mjs`](scripts/capture.mjs) 與 [`scripts/drive.mjs`](scripts/drive.mjs) 擷取。已建置的頁面已提交：開啟 `examples/` 中任何 `.html` 即可試用。

## 它能製作什麼

三種圖形。三者共享同一套工具包、同一台相機與同一套工藝規則。

| 類型 | 說明 | 範例 |
|---|---|---|
| **SVG** | 核心。實心等角零件，四色調陰影，由後往前繪製，置於帶即時讀數與緩動運動的卡片中。可輸出為獨立 HTML 頁面、內嵌樣式的單獨 `.svg` 檔，或 React/Next.js 元件。 | `dial-indicator`、`desk-computer`、`arcade-cabinet`、`test-rig` |
| **SVG + WebGL** | 用於線條無法繪製的內容：火焰、排氣、水、焦散、燈光、光暈、蒸汽。著色器在後 SVG 與前 SVG 之間的畫布中執行，使用圖形自身的等角相機，因此位於繪圖內部。無 WebGL 時 SVG 仍可閱讀。 | `raptor-engine`、`ripple-tank` |
| **3D** <sup>beta</sup> | 真正 3D 轉動的零件：可旋轉的轉盤或轉盤、可彎曲的手指、斷裂並掉落的部件。移動零件每幀由工具包規則重新投影與重新著色；其餘保持靜態藝術。 | `turning-dial` |

每個圖形可為淺色或深色。淺色是 skill 優先設計的主題（含著色器）。

## 安裝

Anatomy 是標準的 [Agent Skill](https://agentskills.io)：根目錄有 `SKILL.md` 的資料夾。本儲存庫即為該資料夾。選擇一種方式安裝：

| | 指令 | 安裝至 |
|---|---|---|
| **skills CLI**，為你安裝（Claude Code） | `npx skills add wheresryan22/anatomy -g -a claude-code` | `~/.claude/skills/anatomy` |
| **skills CLI**，為你安裝（Antigravity） | `npx skills add wheresryan22/anatomy -g -a antigravity` | `~/.gemini/antigravity/skills/anatomy` |
| **skills CLI**，為你安裝（OpenCode） | `npx skills add wheresryan22/anatomy -g -a opencode` | `~/.config/opencode/skills/anatomy` |
| **skills CLI**，為你安裝（Codex） | `npx skills add wheresryan22/anatomy -g -a codex` | `~/.agents/skills/anatomy` |
| **skills CLI**，為你安裝（MiniMax Code） | `npx skills add wheresryan22/anatomy -g -a minimax-code` | `~/.minimax/skills/anatomy` |
| **skills CLI**，為單一專案 | `npx skills add wheresryan22/anatomy` | Claude Code 為 `.claude/skills/anatomy`；Antigravity、OpenCode、Codex 為 `.agents/skills/anatomy`；MiniMax Code 為 `.minimax/skills/anatomy` |
| **git**，為你安裝（Claude Code） | `git clone https://github.com/wheresryan22/anatomy.git ~/.claude/skills/anatomy` | `~/.claude/skills/anatomy` |
| **git**，為你安裝（Antigravity） | `git clone https://github.com/wheresryan22/anatomy.git ~/.gemini/antigravity/skills/anatomy` | `~/.gemini/antigravity/skills/anatomy` |
| **git**，為你安裝（OpenCode） | `git clone https://github.com/wheresryan22/anatomy.git ~/.config/opencode/skills/anatomy` | `~/.config/opencode/skills/anatomy` |
| **git**，為你安裝（Codex） | `git clone https://github.com/wheresryan22/anatomy.git ~/.agents/skills/anatomy` | `~/.agents/skills/anatomy` |
| **git**，為你安裝（MiniMax Code） | `git clone https://github.com/wheresryan22/anatomy.git ~/.minimax/skills/anatomy` | `~/.minimax/skills/anatomy` |
| **git**，為單一專案 | `git clone https://github.com/wheresryan22/anatomy.git .claude/skills/anatomy` | `.claude/skills/anatomy`（Claude Code 與 OpenCode）或 `.agents/skills/anatomy`（Antigravity、OpenCode、Codex 與 MiniMax Code） |
| **下載**，無需 git | 見下方 | 上述任一資料夾 |

<details>
<summary><b>使用 skills CLI</b></summary>

<br>

[`skills`](https://github.com/vercel-labs/skills) CLI 會在本儲存庫根目錄找到 `SKILL.md` 並以 `anatomy` 名稱安裝。預設安裝至目前專案並詢問要設定哪些 agent。`-g` 為你的使用者安裝，`-a claude-code` 只設定 Claude Code。使用 `-a antigravity`、`-a opencode`、`-a codex` 或 `-a minimax-code` 可只設定對應 agent。

CLI 會複製整個儲存庫（含範例，約 10 MB）。需要較新的 Node.js：CLI 1.7.1 版要求 22.20 或更新。

</details>

<details>
<summary><b>使用 git</b></summary>

<br>

將儲存庫 clone 到 skill 資料夾之一，使 `SKILL.md` 位於 `<skills 資料夾>/anatomy/SKILL.md`。Claude Code 使用 `~/.claude/skills/anatomy` 或 `.claude/skills/anatomy`。Antigravity 使用 `~/.gemini/antigravity/skills/anatomy` 或 `.agents/skills/anatomy`。OpenCode 使用 `~/.config/opencode/skills/anatomy` 或 `.opencode/skills/anatomy`；OpenCode 也會讀取 Claude Code 與 `.agents` 資料夾。Codex 使用 `~/.agents/skills/anatomy` 或 `.agents/skills/anatomy`。MiniMax Code 使用 `~/.minimax/skills/anatomy`（或若移動資料夾則為 `$MINIMAX_DATA_DIR/skills/anatomy`）或 `.minimax/skills/anatomy`；MiniMax Code 也會讀取 Claude Code、Codex 與 `.agents` 資料夾。專案安裝時請將資料夾 commit，讓團隊也能取得。之後更新只需在該資料夾內 `git pull`。

</details>

<details>
<summary><b>下載（無需 git）</b></summary>

<br>

[下載 ZIP](https://github.com/wheresryan22/anatomy/archive/refs/heads/main.zip)，解壓縮，將資料夾從 `anatomy-main` 重新命名為 `anatomy`，並移至 `~/.claude/skills/`（Claude Code）、`~/.gemini/antigravity/skills/`（Antigravity）、`~/.config/opencode/skills/`（OpenCode）、`~/.agents/skills/`（Codex）或 `~/.minimax/skills/`（MiniMax Code）。

或在 macOS / Linux 上一行完成：

```sh
mkdir -p ~/.claude/skills/anatomy && curl -L https://github.com/wheresryan22/anatomy/archive/refs/heads/main.tar.gz | tar -xz --strip-components=1 -C ~/.claude/skills/anatomy
```

對於 Antigravity、OpenCode、Codex 或 MiniMax Code，將相同檔案放到 `~/.gemini/antigravity/skills/anatomy`、`~/.config/opencode/skills/anatomy`、`~/.agents/skills/anatomy` 或 `~/.minimax/skills/anatomy`：

```sh
mkdir -p ~/.gemini/antigravity/skills/anatomy && curl -L https://github.com/wheresryan22/anatomy/archive/refs/heads/main.tar.gz | tar -xz --strip-components=1 -C ~/.gemini/antigravity/skills/anatomy
```

```sh
mkdir -p ~/.config/opencode/skills/anatomy && curl -L https://github.com/wheresryan22/anatomy/archive/refs/heads/main.tar.gz | tar -xz --strip-components=1 -C ~/.config/opencode/skills/anatomy
```

</details>

Claude Code 會在執行中的工作階段自動載入新 skill。若工作階段開始時 `skills` 資料夾本身不存在，請執行 `/reload-skills`。Antigravity 與 OpenCode 會在聊天中顯示為 `/anatomy`；若未出現請重新啟動。Codex 會列在 `/skills` 下並以 `$anatomy` 執行；若未出現請重新啟動 Codex。MiniMax Code 會顯示為 `/anatomy`；若未出現請重新啟動 `mcode`。

<details>
<summary><b>Codex：若瀏覽器檢查被阻攔</b></summary>

<br>

skill 會啟動無頭 Chrome 來檢查自己的圖形，Chrome 會寫入暫存設定檔並透過本地埠通訊。Codex 在沙箱中執行指令，沙箱可能阻止 Chrome。圖形仍會被建置；只有檢查會失敗。建議順序如下：

1. 當 Codex 詢問是否在沙箱外執行檢查時，批准該指令。這需要預設的 `approval_policy = "on-request"`。
2. 或在 `~/.codex/config.toml` 中允許一次：

   ```toml
   approval_policy = "on-request"
   sandbox_mode = "workspace-write"

   [sandbox_workspace_write]
   network_access = true
   writable_roots = ["/tmp"]
   ```

   較新的 Codex 版本可能使用不同設定名稱；請參考你版本的設定文件。
3. 或在一般終端自行執行檢查，例如 `node scripts/capture.mjs page.html --out shots/page.png`。

以 `--sandbox danger-full-access` 啟動 Codex 也可行，但會解除該工作階段的所有限制，僅建議用於你信任的專案。

</details>

## 使用方式

輸入 `/anatomy`（在 Codex 中為 `$anatomy`）並說明圖形應解釋什麼：

```text
/anatomy explain how a token bucket rate limiter works, interactive
```

你不一定要明確命名 skill。當你要求等角插圖、文件說明圖、部落格或落地頁的解釋圖、或互動式說明時，Claude 也會載入它。Antigravity、OpenCode、Codex 與 MiniMax Code 同樣如此。

<details>
<summary><b>更多提示</b>，來自 skill 的 <a href="evals/evals.json">evals</a></summary>

<br>

```text
/anatomy a figure for our Next.js docs on database connection pooling: a pool of 10 connections, requests borrow one and give it back, and when all 10 are busy new requests wait in a queue. A React component plus a static HTML preview, dark theme.
```

```text
/anatomy an isometric SVG explaining how a CDN edge cache works, cache hit vs miss, TTL of 60 s, for a dark landing page. Just the SVG file and a PNG preview.
```

```text
/anatomy a Bunsen burner on a lab bench: opening the air collar turns the lazy yellow flame into a roaring blue cone. WebGL for the flame, one HTML file, dark theme.
```

```text
/anatomy a heat-exchanger espresso machine with the side panel off: boiler, heat-exchanger tube, group head, pump, steam wand and gauge. Show the water flowing when you pull a shot. Standalone HTML, light theme.
```

</details>

三個習慣能得到最好的圖形：

1. **說出概念，而不是繪圖。** 說明它應解釋什麼，並提供真實數字（尺寸、數量、速率、閾值）。Anatomy 會發明物件；這是大部分工作，且它比描述方塊與箭頭做得更好。
2. **或直接說出物件。** 如果你已經知道想要的機器（義式咖啡機、本生燈、鎖），就說出來，並說明什麼應該移動。
3. **說明它將存在於哪裡。** 獨立 HTML 頁面、單獨 SVG 檔，或 React/Next.js 元件；淺色或深色。建置方式會因此不同。

圖形會以你擁有的原始碼形式交付：一個 Node 建置腳本與它寫出的頁面，或（對於 React）幾何模組、靜態藝術的伺服器元件與一個運動的客戶端元件。工具包會一併提供。

## 範例

每個無框架範例都有 Node 建置腳本，會在自身旁邊寫出獨立頁面。加上 `--light` 可使用淺色主題。

| 範例 | 展示內容 | 建置 |
|---|---|---|
| [`dial-indicator`](examples/dial-indicator) | 支架上的千分表，下方為量塊托架。最小範例，約 300 行。 | `node examples/dial-indicator/build.mjs` |
| [`desk-computer`](examples/desk-computer) | 1984 風格桌面電腦，可打字的鍵盤。打出的字會出現在機殼正面平面上繪製的 CRT，關閉時畫面會塌縮成一條線與一個點。約 85 個實體。 | `node examples/desk-computer/build.mjs` |
| [`arcade-cabinet`](examples/arcade-cabinet) | 直立式街機機台，側板打開。投入一枚硬幣：它會沿投幣滑道滾過投幣開關線進入錢箱，脈衝沿纜線傳至電路板，CRT 暖機進入在傾斜螢幕平面上繪製的吸引模式。約 240 個實體與 15 條纜線。 | `node examples/arcade-cabinet/build.mjs` |
| [`raptor-engine`](examples/raptor-engine) | 測試台上的 Raptor 2 引擎。可拆解成 11 個組件，WebGL 羽流、激波、飛濱與蒸汽在後 SVG 與前 SVG 之間渲染。密集管路、平滑陰影、淡出與審計的參考範例。建置需數分鐘。 | `node examples/raptor-engine/build.mjs` |
| [`ripple-tank`](examples/ripple-tank) | 高腳學校波動水槽，上方為紙幕，從 44° 仰角觀看。兩層 WebGL 註冊到等角平面，由 `model.mjs` 中的純模型驅動。 | `node examples/ripple-tank/build.mjs` |
| [`test-rig`](examples/test-rig) | 來自 React/Next.js 網站的正式圖形：彈簧安裝托架上的玻璃按鈕、軌道上的手指探針，以及讀取傾斜的千分表。53 個實體。無建置腳本：複製到 React 應用即可。 | 無 |
| [`spot-plate`](examples/spot-plate) | 來自同一網站的第二個圖形：點板上一對對玻璃滴，隨著一扇量規葉片打開而匯合成一塊玻璃。每對由一個距離場繪製。無建置腳本：複製到 React 應用即可。 | 無 |
| [`turning-dial`](examples/turning-dial) | 3D 模式：真正 3D 轉動的密碼轉盤，上面有小機器人手、三鉐鏈可抬起的手指，以及作為自由體斷裂的艙體。`stress.mjs` 是雜亂工作室中 380 個零件的手，用於效能測量。 | `node examples/turning-dial/build.mjs` |

Raptor 與街機機台也可列印。`node scripts/print.mjs examples/raptor-engine/sheet.mjs --format all` 會從已建置的淺色頁面寫出三份 A4 PDF：單頁海報、單頁技術圖與雙頁詳細說明。要求任何圖形的可列印版本時，Anatomy 會寫出其 `sheet.mjs`；詳見 [`references/print.md`](references/print.md)。

`node examples/raptor-engine/build.mjs --audit`、`node examples/arcade-cabinet/build.mjs --audit` 與 `node examples/turning-dial/build.mjs --light --audit` 也會執行幾何審計。3D 審計較慢；詳見 [`references/3d.md`](references/3d.md)。

## 運作原理

- **[`SKILL.md`](SKILL.md)** 是 Claude 讀取的內容。它設定工作流程：先收集真實數字、發明物件、寫零件清單、規劃世界、用工具包一次建置幾何、由後往前繪製、加上框架、使其活起來，然後像評論者一樣驗證。它也以簡短形式保存工藝規則。
- **[`kit/`](kit)** 是圖形建置所使用的繪圖庫：等角相機、實體與零件庫（`iso-kit`）、任意軸上的圓形零件（`lathe.mjs`）、管路與纜線（`tube.mjs`）、WebGL 層（`gl.mjs`）、3D 執行環境（`turn*.mjs`），以及 React 元件（`react/`）。除了那些元件所需的 React 外，沒有其他依賴。
- **[`references/`](references)** 是 Claude 需要時會開啟的長篇指南：工藝、工具包 API、運動、React、驗證、WebGL、設計逐步說明與 3D 模式。
- **驗證。** [`kit/audit.mjs`](kit/audit.mjs) 證明幾何正確：沒有東西穿過任何東西、每個端點都位於安裝點上、每個重疊都以深度順序繪製（`node build.mjs --audit`）。在無頭 Chrome 中，[`scripts/capture.mjs`](scripts/capture.mjs) 與 [`scripts/drive.mjs`](scripts/drive.mjs) 擷取截圖、特寫與放慢的接觸表，[`scripts/lines.mjs`](scripts/lines.mjs) 會讓任何在空中結束的線條失敗，[`scripts/turn-check.mjs`](scripts/turn-check.mjs) 檢查 3D 圖形。skill 會指示 Claude 讀取它產生的每一張 PNG。

<details>
<summary><b>儲存庫結構</b></summary>

<br>

```text
anatomy/
├── SKILL.md                  skill：工作流程、設定與工藝規則
├── kit/                      繪圖庫
│   ├── iso-kit.ts            核心：相機、實體、零件、SVG 渲染器、卡片與頁面、CSS
│   ├── iso-kit.mjs           相同核心的純 ESM 版本，供 Node 建置腳本使用
│   ├── iso.css               工具包的 CSS，兩種主題
│   ├── react/                draw.tsx（伺服器安全元件）、live.tsx（客戶端 hooks）
│   ├── lathe.mjs             任意軸上的圓形零件
│   ├── tube.mjs              管路、管子與纜線
│   ├── audit.mjs             幾何審計
│   ├── gl.mjs                繪圖內部著色器的 WebGL 層
│   ├── turn.mjs              3D 執行環境（beta）
│   ├── turn-build.mjs        3D 建置器
│   ├── turn-audit.mjs        3D 軌道審計
│   └── turn-fixed.mjs, canvas-painter.mjs, gl-shared.mjs
│                             實驗性變體，尚未文件化或被範例使用
├── references/               Claude 需要時讀取的長篇指南
│   ├── craft.md  kit.md  motion.md  react.md
│   └── verify.md  webgl.md  walkthrough.md  3d.md
├── scripts/                  無頭 Chrome 檢查與建置輔助
│   ├── capture.mjs           截圖與特寫
│   ├── drive.mjs             腳本化工作階段與接觸表
│   ├── lines.mjs             線條端點檢查（搭配 line-ends.mjs）
│   ├── inline-kit.mjs        作為原始碼的工具包，可內嵌到獨立頁面
│   ├── turn-check.mjs        瀏覽器中的 3D 檢查（搭配 turn-fidelity.mjs）
│   └── turn-bench.mjs        Node 中的 3D 計時
├── examples/                 八個完整圖形，已建置頁面已提交
├── evals/evals.json          測試提示與良好答案應包含的內容
└── .github/                  issue 表單、PR 範本、CI、README 圖片
```

</details>

## 需求

| | 用途 | 備註 |
|---|---|---|
| **[Claude Code](https://code.claude.com/docs/en/overview)**，或 [Antigravity](https://antigravity.google)、[OpenCode](https://opencode.ai/docs/skills/)、[Codex](https://developers.openai.com/codex/skills) 或 [MiniMax Code](https://github.com/MiniMax-AI/minimax-code) | 一切 | skill 為 Claude Code 撰寫並遵循開放 Agent Skills 格式，因此 Antigravity、OpenCode、Codex 與 MiniMax Code 也能載入。在 Codex 中，瀏覽器檢查會啟動 Chrome；若沙箱阻攔，請為那些指令允許。 |
| **Node.js 20.10+** | 建置、工具包、檢查 | 僅內建模組：無需 `npm install`。範例已在 Node 20.19 與 22.11 上逐位元組重建。在 Node 20 上，瀏覽器腳本會以 `--experimental-websocket` 重新啟動自身。 |
| **Chrome 或 Chromium** | 檢查 | `capture.mjs`、`drive.mjs`、`lines.mjs` 與 `turn-check.mjs` 會在 macOS、Linux 與 Windows 的常見位置以及 Playwright 快取中尋找。其他二進位請設定 `CHROME_PATH`。它們以無頭模式執行並啟用 WebGL。 |
| **React 18+** | 僅 React 輸出 | `kit/react/`、`examples/test-rig/` 與 `examples/spot-plate/`。 |

## 限制

- **它不是圖表庫。** 沒有座標軸、系列或資料繪圖。數字以模型驅動的即時讀數出現，以及零件的真實尺寸與數量。
- **它繪製機器、儀器、工具與家具。** 不是人物或精確地圖。沒有可建造機制的概念會輸出較弱的結果。
- **它刻意緩慢。** 一張圖需要長時間工作階段：零件清單、幾何、審計，以及兩種主題中每個接頭的特寫。Raptor 的建置需數分鐘，完整 3D 軌道審計對 30 個零件需 15 到 20 分鐘。
- **著色器需要 WebGL。** 沒有它時 SVG 仍可閱讀，在減少動態偏好下每張圖都會靜止。

> [!NOTE]
> **3D 模式為 beta。** 它已在其範例與一個測試圖形上驗證，尚未在正式圖形上驗證。小型 3D 圖形以 60 fps 執行；380 零件的壓力手在 1440 px 寬度約 20 fps，在節流手機設定檔的重負載機器上為 13 到 15 fps。

## 分享圖形

做出好東西了嗎？請你的 agent「將這張圖發佈到 Anatomy 社群圖庫」。它會詢問標題與你的 GitHub 名稱，顯示將傳送的內容，在你同意後會在 [anatomy-community](https://github.com/wheresryan22/anatomy-community) 開啟 pull request：無需手動 git 或 fork。或自行執行 `scripts/publish.mjs --submit`。沒有終端時，可使用圖庫的 **Submit a figure** 表單搭配 GitHub Gist。

## 貢獻

歡迎 issue 與 pull request。請先閱讀 [CONTRIBUTING.md](CONTRIBUTING.md)：它涵蓋建置範例、檢查，以及變更必須遵守的規則（其中包括程式碼中沒有註解，以及工具包變更必須讓每個現有範例逐位元組相同）。請遵守 [行為準則](CODE_OF_CONDUCT.md)，並依 [SECURITY.md](SECURITY.md) 所述回報安全問題。

- [回報錯誤](https://github.com/wheresryan22/anatomy/issues/new?template=bug_report.yml)
- [請求圖形](https://github.com/wheresryan22/anatomy/issues/new?template=figure_request.yml)
- [變更日誌](CHANGELOG.md)

## 授權

[MIT](LICENSE) © 2026 Ryan · [@wheresryan22](https://x.com/wheresryan22)

<p align="center"><sub>如果 Anatomy 為你畫出有用的東西，一個 ⭐ 能幫助其他人找到它。</sub></p>
