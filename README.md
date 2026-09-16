# wordquiz-frontend-dist

WordQuiz の **OTA バンドル配信先** (GitHub Pages)。

- 中身は `wordquiz-frontend` (private) の CI が自動生成して push する。**手で編集しない。**
- 配布物は Ed25519 で署名されており、アプリ側は署名検証に通ったバンドルしか適用しない。

Base URL: `https://pad01g.github.io/wordquiz-frontend-dist/`

```
dist/version_info-<x.y>.json   最新版のポインタ {"version": "...", "url": "..."}
dist/<x.y.z>/<x.y.z>.zip       ビルド成果物 (dist/ を zip 化したもの)
dist/<x.y.z>/<x.y.z>.zip.sig   上記の Ed25519 署名 (raw, 64 bytes)
```

アプリは起動時に自分のバージョンの `x.y` から `version_info-<x.y>.json` を引き、
同じ `x.y` かつ `z` が異なる場合のみ更新する。
