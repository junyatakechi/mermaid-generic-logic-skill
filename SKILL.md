---
name: mermaid-generic-logic-skill
description: "文脈: mermaid の図の記法。種類: 一般的な業務知識。使う場面: 名前で指名されたときだけ使い、会話の内容からは選ばない。"
metadata:
  version: "0.1.3"
  repository: "https://github.com/junyatakechi/mermaid-generic-logic-skill"
  design: "人の判断を切り出すAgent Skillsの設計_v4.0.0"
  design-url: "https://app.notion.com/p/3eaf2fd6925e8102b86fee3b6b3dd5a3"
---

# 索引

| 判断名 | 扱うこと | ファイル | 依存する判断 | 計算 |
|---|---|---|---|---|
| xychart の凡例 | xychart で色の意味を凡例で示すとき、どう書き、どの形や版では凡例が出ないか | [xychart-legend.md](references/xychart-legend.md) | `xychart-axes.md` | — |
| xychart の色 | xychart で系列の色を指定するとき、どう書き、1本の棒だけ色を変えるにはどうするか | [xychart-colors.md](references/xychart-colors.md) | — | — |
| xychart の軸と題 | xychart で軸と題を書くとき、何が置けて、何が重なったり切れたりするか | [xychart-axes.md](references/xychart-axes.md) | — | — |
| gantt と timeline | gantt・timeline で描くとき、色と並びをどう指定し、何が出せないか | [gantt-timeline.md](references/gantt-timeline.md) | — | — |
| 描けるかの確かめ方 | mermaid の図を書いたあと、正しく描けるかをどう確かめるか | [render-check.md](references/render-check.md) | — | — |

# 手続きに使う道具

なし

# このスキルの設計上の決まりごと

1. このスキルは判断を答えるだけで、判断の対象もデータも持たない。対象の値は、材料の写しとして受け取る。データを取りに行かず、保存もせず、IDも受け取らない。
2. 答える範囲は、聞きたい事を索引の「扱うこと」と照らして決める。索引の「依存する判断」にある判断を、先に出す。
3. 判断ファイルの「求める材料」がそろわなければ答えない。計算がある判断は、`uv run <skill-dir>/scripts/judge.py <判断> <材料.json>` で計算する。<判断> は `references/` のファイル名。依存する判断の材料も、一緒に渡す。
4. 答えは、指定された形にそろえ、理由と組にして返す。
5. 中核判断は、判断ファイルで答えられなければ、一般論で答えず「判断が無い」と返す。「未決」に当たったら、未決であることと、決めるまでの暫定の扱いを含める。一般的な業務知識は、判断ファイルに無いことを一般知識で補ってよい。
6. 読み込まれたら、索引の「扱うこと」に当たる作業で、その判断ファイルに従う。どの道具をどう呼ぶかは、判断ファイルの「道具」が示す。手続きは代わりに行わず、呼び出し側が道具を呼ぶ。操作する対象のIDは、材料ではなく、道具の引数で渡す。
