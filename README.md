# mermaid-generic-logic-skill

mermaid で図を書くときの、一般的な判断を持つロジックスキル。
xychart の凡例・色・軸と題、gantt と timeline の色と並び、描けるかの確かめ方について、記法の仕様と、描いて分かった癖とその避け方を答える。

## 必要なもの

- [Claude Code](https://docs.claude.com/en/docs/claude-code/overview)
- 図を描いて確かめるなら、ブラウザと Python（ローカルの HTTP サーバーに使う）

## インストール

```bash
git clone https://github.com/junyatakechi/mermaid-generic-logic-skill.git ~/.claude/skills/mermaid-generic-logic-skill
```

特定のプロジェクトだけで使うなら、`<プロジェクト>/.claude/skills/` の中でクローンする。

## セットアップ

なし。

## 使い方

主に、アプリケーションスキルから呼ばれる。
直接聞くときも、`/mermaid-generic-logic-skill` で名前を指名する。指名しないと、このスキルは読み込まれない。

- 「/mermaid-generic-logic-skill xychart で1本の棒だけ色を変えるには？」
- 「/mermaid-generic-logic-skill 横向きの棒グラフに凡例を出せる？」
- 「/mermaid-generic-logic-skill gantt の背景の色を変えたい」
