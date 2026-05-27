# Bachelor Format

## About
これは卒論用のフォーマットです．
千葉工業大学2024年度修士の高橋さんと高島さんが作成してくださった卒論用のフォーマットを千葉工業大学2025年度2231015が __LuaLaTeX__ で書き出せるように修正し，いらないものを追加したので，適宜修正して使用してください．

__/Bachelor/documents/Manual.texによく目を通すこと．__

追加したものは，Manual.texのLaTeXで遊んでみたにある程度は書きました．

## 1. LaTeXの環境構築をしよう
[Qiita]
[LaTeX完全導入ガイド](https://qiita.com/passive-radio/items/623c9a35e86b6666b89e#2-vscode-%E3%81%AE%E8%A8%AD%E5%AE%9A)

## 2. settings.jsonの変更
### "latex-workshop.latex.tools"の変更
```diff
// latexmk を利用した lualatex によるビルドコマンド
{
    "name": "Latexmk (LuaLaTeX)",
    "command": "latexmk",
    "args": [
        "-f",
        "-gg",
-       "-pv",
+       "-pv-",
        "-lualatex",
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
+       "-outdir=%OUTDIR%",
        "%DOC%"
    ]
},
```
* `-pv-`：`.latexmkrc`の`$pdf_previewer`を起動しないようにする．\
VSCodeのLaTeX WorkshopでのPDF表示で十分．
* `-outdir=%OUTDIR%`：出力先のディレクトリを指定する．\
これを追加しないと出力先用のoutディレクトリだけ生成されて補助ファイルが散らかるので階層関係がおかしなことになる．

ビルドすることで，outフォルダにpdfファイルが生成されます．

## 3. ビルドエラーするとき
* インストール後はとりあえず再起動
* フォントが存在しない
* LuaLaTeX用の定義になっていない
* パッケージの依存関係
