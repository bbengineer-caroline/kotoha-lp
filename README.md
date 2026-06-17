# 言の葉 kotoha — Landing Page

事前登録（プレローンチ）用の静的ランディングページ。`app/` の Flutter 本体とは別リポジトリ・別デプロイ。

## 構成
- `index.html` — LP 本体（レイアウトCSS・JSはインライン）
- `styles.css` — デザイントークン（フォント／色）。出典: `brand-guidelines/brand.css`
- `favicon.svg` — 藤色の葉

ビルド不要の純静的サイト。

## ローカルで見る
```sh
python3 -m http.server 4321 --directory .
# → http://localhost:4321
```

## デプロイ（Vercel）
1. GitHub に新規リポジトリを作成（例: `kotoha-lp`）。
2. このフォルダを push:
   ```sh
   git remote add origin https://github.com/<you>/kotoha-lp.git
   git push -u origin main
   ```
3. Vercel で「Add New… → Project」→ そのリポジトリを Import。
   - Framework Preset: **Other**（ビルドコマンド・出力ディレクトリは空のまま）
   - Deploy を押すだけ。`https://<project>.vercel.app` で公開される。
4. 以後は `main` に push するたび自動デプロイ。PR ごとにプレビューURLも出る。

## ローンチ段階の切り替え
公開版は事前登録（prelaunch）固定。`<body data-phase="...">` を変えると表示が変わる:
`teaser`（種まき）/ `prelaunch`（事前登録）/ `live`（公開後・App Storeボタン）/ `atelier`（課金訴求）。

## 公開前の TODO
- [ ] **事前登録フォームのバックエンド配線** — 現状はダミー（送信してもメールは保存されない）。
      Vercel Functions か Firestore（既存の kotoha-a8619）か フォームサービスに接続する。
- [ ] **フッターのリンク先** — プライバシーポリシー／利用規約 が `#` のまま。
      （メール収集をするなら、プライバシーポリシーの掲示は必須／APPI）
- [ ] **OG画像**（1200×630 PNG）と `og:url` / `canonical` — ドメイン確定後に追加。
      現状は画像なしの `twitter:card=summary`。
- [ ] **独自ドメイン** — まずは `*.vercel.app`。後でドメインを当てる。
