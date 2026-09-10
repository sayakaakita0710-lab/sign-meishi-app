# 名刺台帳 — 配信用

サインコサインの社内ツール「名刺台帳」の**画面だけ**を GitHub Pages で配信するためのリポジトリ。

**アプリURL**: https://sayakaakita0710-lab.github.io/sign-meishi-app/

## ここに入っているもの / いないもの

- 入っている: ブラウザで動く画面のコード（HTML/CSS/JS 1ファイル）と、Supabase の URL・anon キー。
  anon キーは公開前提の識別子で、これ単体では何も読めない。
- 入っていない: 名刺データ、名刺画像、APIキー。これらは非公開の Supabase プロジェクト側にあり、
  許可メールアドレスのアカウント以外は1行も読めない（RLSで強制）。

## 更新のしかた

このリポジトリのファイルは自動生成物なので直接編集しない。
編集はソース側（プライベートリポジトリ `sayakaakita0710-lab/-` の `meishi/`）で行う。

```bash
cd meishi
# web/index.html か web/app.js を編集
SUPABASE_URL=... SUPABASE_ANON_KEY=... node scripts/build.mjs
# 出来た dist/index.html と dist/404.html をこのリポジトリにコピーして push
```

push すると GitHub Pages に自動反映される（1〜2分）。

## Pages の設定

Settings → Pages → Source を **Deploy from a branch** にし、Branch を `main` / `/ (root)` にしてある。
ワークフローは使っていない（このリポジトリのファイルがそのまま配信される）。
