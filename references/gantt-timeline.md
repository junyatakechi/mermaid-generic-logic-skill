# gantt と timeline

## 扱うこと

gantt・timeline で描くとき、色と並びをどう指定し、何が出せないか

## 答え方と理由

### 0. 判断全体

なし

### 1. gantt と timeline には、凡例が無い

gantt と timeline は、色の意味を示す凡例を出せない。色を分けたら、意味は図の外で示す。

1. （原因）gantt と timeline で色を分けた図を描いたが、どちらにも凡例は出なかった。（発生日：2026-11-21）

### 2. gantt の色は、`themeVariables` の決まった名前で変える

gantt の棒の色は、図の先頭の設定の `themeVariables` で変える。普通の棒は `taskBkgColor`・`taskBorderColor`、`crit` の棒は `critBkgColor`・`critBorderColor`、`done` の棒は `doneTaskBkgColor`・`doneTaskBorderColor`、`section` の背景は `sectionBkgColor`・`altSectionBkgColor`・`sectionBkgColor2`。指定しないと、既定の紫と黄の背景になる。

1. （原因）`themeVariables` を指定しない gantt は、section の背景が紫と黄になった。指定すると、指定した色になった。（発生日：2026-11-21）

### 3. gantt で、同じ section の棒を1行に並べるには `displayMode: compact` にする

gantt は、棒を1本ずつ別の行に置く。同じ section の、重ならない棒を1行に並べるときは、`gantt` → `displayMode: compact` にする。

1. （原因）`displayMode: compact` にすると、同じ section の、続けて置いた2本の棒が1行に並んだ。（発生日：2026-11-21）

### 4. gantt の軸と左の余白は、設定で整える

月の目盛りは `axisFormat %-m月`（0を詰めない）と `tickInterval 1month` で出す。今日の線は、描くたびに位置が変わるので、残す図では `todayMarker off` にする。section の名前が左で切れるときは、`gantt` → `leftPadding` を広げる。

1. （原因）`axisFormat %m月` では「01月」と0が付いた。section の名前が長いと、既定の左の余白で切れた。（発生日：2026-11-21）

### 5. gantt は、置かれた所の幅で描かれる

gantt は、描くときの置き場所の幅に合わせて描かれる。幅が0の所で描くと、幅0の図になる。

1. （原因）幅を決めていない確かめ用のページで描いたら、gantt だけが幅0になった。幅を決めた所で描くと、正しく描けた。（発生日：2026-11-21）

### 6. timeline の色は、`theme: base` と `cScale0` 〜 で変える

timeline の期間ごとの色は、`theme: base` にし、`themeVariables` の `cScale0`・`cScale1`… で、期間の順に指定する。文字の色は `cScaleLabel0`… で指定する。指定しないと、期間ごとに既定の色が付く。

1. （原因）既定の timeline は期間ごとに色が違い、`theme: base` と `cScale0` 〜 を指定すると、指定した色になった。（発生日：2026-11-21）

## 判断定数

なし

## 未決

なし

## 求める材料

| 材料 | 種類 | 必須 | 形 | 無いとき |
|---|---|---|---|---|
| 描こうとしている gantt か timeline | 対象の値 | ○ | mermaid の記法の文 | 判断できない |

## 計算

なし

## 道具

なし
