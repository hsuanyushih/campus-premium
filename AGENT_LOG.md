# Agent log

Add a dated entry each time you work with your AI coding agent, with the newest entry at the bottom. Each entry records what you asked the agent, what it produced, and what you checked or changed. Paste your key prompts in exactly as you typed them. Include at least one time the agent got something wrong, and how you caught it.

Copy this outline for each entry:

```markdown
## YYYY-MM-DD: What you worked on

- **Asked:** "Paste your prompt here."
- **Agent produced:** What it made or changed.
- **Checked or changed:** How you checked it, and what you fixed.
```

## 2026-11-11: First version of the Campus Premium page

- **Asked:** "Read AGENTS.md and docs/data_description_sheet.md first. Then replace the placeholder index.html with a page titled “Campus Premium” that shows the median sale price for each of the 11 universities as a bar chart, computed from data/college_town_home_sales.csv. Exclude sales under $10,000 and state that rule on the page. Round prices to whole dollars. Use plain HTML, CSS and JavaScript. Do not edit any files in data/."
- **Agent produced:** An `index.html` that reads the CSV in the browser, excludes sales under $10,000, states that rule on the page, and draws a sorted bar chart of medians.
- **Checked or changed:** I compared all 11 medians with a separate Python calculation, and they matched. I also tested the page in a headless browser: no errors, and no horizontal scroll at phone width. No file in `data/` was changed.

## 2026-11-11: Dropdown, scatter plot, number cards and budget slider

- **Asked:** I approved the agent's plan, then asked for this layout:
  - "上方放下拉選單或按鈕，可以切換 11 所大學，預設停在 UIUC"
  - "主圖是散點圖或地圖，橫軸是離校距離，縱軸是價格"
  - "旁邊放幾個數字卡片，顯示這所大學的中位數房價、坪價和平均幾天賣掉"
  - "最下面放一個預算滑桿：「用 $300K 在這裡大概能買到什麼」類似這樣的互動"
- **Agent produced:** A university dropdown (default UIUC), a scatter plot of distance against price with a median line and hover details, three number cards, and a budget slider from $100,000 to $1,000,000. Each part was added in its own pull request or commit.
- **Checked or changed:** I checked the figures for UIUC, Davis and Florida against a separate Python calculation. I also reviewed the chart screenshots the agent sent me.
- **What the agent got wrong:** The agent used 坪, a Taiwanese unit, in the number card and the budget text without asking. I caught it because the page is in English, and I wrote: "不是不能有中文字啊，為什麼有「坪」？？？". I chose option A, which switched the figures to "sq ft" in a later pull request.

## 2026-11-12: Restyling the page and the title

- **Asked:** "好，照計畫做，從大學下拉選單開始。" and later "我覺得這邊的設計可以再更像title一點，然後我要滑鼠滑過去有陰影". I also asked for "美化風格我要溫暖配色，我想呈現有舒卷氣息的感覺，有哈佛的那種感覺", and then "下方一條細金線 不要細金線，其他照舊".
- **Agent produced:** A warm cream and crimson palette, a serif title, side-by-side number cards, a hover shadow on the cards, and a title with rules above and below it. I made four title options as images, and you chose option 2. Then you asked for EB Garamond, which I used.
- **Checked or changed:** I tested the layout at desktop and phone widths. I also confirmed the hover shadow and that every figure still matched the earlier numbers.

## 2026-11-13: README and cleanup

- **Asked:** "可以幫我寫readme的部分嗎", then "幫我改" for the template sections, and "自己一個人做的" when asked about "Who did what".
- **Agent produced:** The README's purpose, live link, data notes (including the $10,000 rule and how each figure is defined), and tools used. I also removed the template sections "Start here" and "Who did what".
- **Checked or changed:** I checked the README figures against the code and the earlier numbers. I did not verify the README on the GitHub homepage myself, so that is still on your list.
- **What the agent got wrong:** The agent pushed the README to a new branch, `claude/readme-campus-premium`, instead of the designated branch. I caught it when I asked "我不懂為什麼分支不對". The agent then moved the commit to the correct branch after I gave permission, and I deleted the stray branch on GitHub.
