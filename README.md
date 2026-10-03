# german-drill(ドイツ語ドリル)

学習ポータル(hirano-soura.github.io)の「ドイツ語」カードから開くドリルです。
GitHub Pages(`main` / root)から `https://hirano-soura.github.io/german-drill/` として公開しています。
**`main` に push したものがそのまま公開版**です。

## このリポジトリは公開物だけを持つ

出題データの原本と画面のテンプレートは、非公開の場所で管理しています。
ここにあるのは、原本からビルドした**公開用の成果物**です。

| ファイル | 中身 | 手で直すか |
| --- | --- | --- |
| `index.html` / `data.js` | 基礎暗記ドリル(画面 / 出題データ) | **直さない**(ビルドで上書きされる) |
| `3000/index.html` / `3000/data.js` | 練習問題3000題 演習ドリル(画面 / 出題データ) | **直さない**(ビルドで上書きされる) |
| `status.js` | ハブのカードに出す状態 | 直す |
| `manifest.webmanifest` / `icon-*.png` | ホーム画面に追加したときの名前・色・アイコン | 直す |

`data.js` は `window.DRILL_DATA` に素のデータ(文字列と配列だけ)を置きます。
`index.html` は `data.js?v=<データのハッシュ>` を読むので、画面とデータの版が食い違いません。

ハブのカードの文言・リンクは、学習ポータルの `portals.json` が正本です。

## 約束

1. **リポジトリの外を参照しない。** パスはすべて相対で書き、`../` や `/german-drill/` のような絶対パスを使わない
2. **ハブとの接点は `status.js` だけ。** ハブは `webBase + status.js` を読み、`window.__portalStatus({...})` を受け取る。
   `status.js` はリポジトリの直下に置き、`"id": "german"` を変えない
3. **リポジトリ名を変えない。** Pages の URL がリポジトリ名で決まり、ハブの `webBase` もこれを指している
4. **学習記録の localStorage キー(`de-kiso-drill-v1` / `de3000-drill-v1`)と問題 ID を変えない。** 変えると端末に残った記録が読めなくなる

約束 1 の確認(何も出なければよい):

```sh
grep -rnE '\.\./|/german-drill/' . --exclude=README.md --exclude-dir=.git
```
