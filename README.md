# three-readme — camo 再生テスト

GitHub の `<img>`（camo 経由）で、headless SVGRenderer が焼いた CSS `steps()` フリップブックが**アニメ再生されるか**を確認するための捨てリポジトリ用 README。

判定基準：下の図がブラウザ（手元）と同じく、GitHub 上でも回っていれば論点2はクリア。静止画で固まっていたら camo / サニタイザがアニメを潰している。

## 1. Markdown 埋め込み（本命）

torus knot / 24フレーム / ~101KB

![torusknot](./torusknot-wire-24f.svg)

icosahedron / 36フレーム / ~37KB

![icosahedron](./ico-wire-36f.svg)

## 2. HTML `<img>` 埋め込み（幅指定の確認）

<p align="center">
  <img src="./torusknot-wire-24f.svg" width="320" alt="torusknot wire">
  <img src="./ico-wire-36f.svg" width="320" alt="icosahedron wire">
</p>

## チェックリスト

- [ ] markdown 埋め込みで再生される
- [ ] HTML `<img>` + width 指定で再生される
- [ ] ダーク／ライト両テーマで視認できる（現状 stroke は固定色 `#4f9cff`）
- [ ] モバイル（GitHub アプリ）でも再生される
- [ ] 透過背景がテーマ背景と干渉しない

## メモ

- 生成物コミット方式（`snk` と同型）。README は `![](path.svg)` 1行のみ。
- camo は積極キャッシュするので、SVG 差し替え後に絵が更新されない場合は URL に `?v=2` 等を付けて確認。
- 再生されなかった場合の切り分け順：① 生 SVG を raw で開く（ファイル自体は正しいか）→ ② CSS animation を `<img>` 文脈が許可しているか → ③ camo がサニタイズで `<style>` を落としていないか。
