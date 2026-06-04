# bellmux-slides

[bellmux](https://github.com/Daiius/bellmux)（tmux × coding agents の「入力待ち」を取り次ぐ小さな CLI）を社内向けに紹介する [Marp](https://marp.app/) スライドです。

スライド本体は [`slides.md`](./slides.md) です。

## セットアップ

```sh
pnpm install
```

## ビルド / プレビュー

```sh
pnpm preview     # ブラウザでライブプレビュー（Marp の -p）
pnpm watch       # build/slides.html を変更監視つきで生成
pnpm build       # build/slides.html を生成（画像も build/ にコピー）
pnpm build:pdf   # build/slides.pdf を生成
```

Marp for VS Code 拡張を使う場合は `slides.md` をそのままプレビューできます。

> PDF / 画像出力時に `slides.md` のローカル画像（`images/` 配下）を読み込むため、Marp CLI には `--allow-local-files` を渡しています（`build:pdf` に設定済み）。

## 図（mermaid）について

Marp は標準では mermaid を描画できないため、`diagrams/*.mmd` を [mermaid-cli](https://github.com/mermaid-js/mermaid-cli) で SVG に事前レンダリングして `images/` に置き、スライドからは画像として参照しています。生成済み SVG はリポジトリに含めているので、発表時の `pnpm build` だけなら mermaid-cli は不要です。

図を編集したら再生成します（Chromium が必要。`diagrams/puppeteer.json` の `executablePath` で参照する Chrome を指定しています。環境に合わせて書き換えてください）。

```sh
pnpm diagrams
```

## 画像の出典

`images/` 配下のロゴは簡易発表用に各サイトから引用したものです（商標は各社に帰属）。出典 URL は `slides.md` 冒頭の HTML コメントに記載しています。

- tmux ロゴ / Rust ロゴ … Wikimedia Commons
- Claude アイコン / OpenAI アイコン … Wikimedia Commons
- `bellmux-demo.gif` … 自作（[bellmux](https://github.com/Daiius/bellmux) リポジトリより）
- `overview.svg` / `scenario1.svg` / `scenario2.svg` … `diagrams/*.mmd` から mermaid-cli で生成
