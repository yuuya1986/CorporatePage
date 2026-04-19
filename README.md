# CorporatePage — 株式会社エフルム コーポレートサイト

株式会社エフルム（eFLM, Inc.）の公式コーポレートサイトです。

## 公開URL

- **GitHub Pages**: https://yuuya1986.github.io/CorporatePage/
- 独自ドメイン設定後はそちらに切り替わります。

## サイト構成

| ファイル | 内容 |
|---|---|
| `index.html` | トップページ（Hero / 事業 / 代表 / 会社概要 / お問い合わせ） |
| `privacy.html` | プライバシーポリシー |
| `tokushoho.html` | 特定商取引法に基づく表記 |
| `assets/css/tokens.css` | デザイントークン（色・余白・タイポグラフィ） |
| `assets/css/site.css` | サイト固有スタイル |
| `assets/css/recipes/` | jp-ui-contracts の日本語組版CSSレシピ |
| `assets/img/favicon.svg` | ファビコン |
| `DESIGN.md` | 日本語UI設計契約（jp-ui-contracts base テンプレートをカスタマイズ） |

## 技術スタック

- 素の HTML / CSS（フレームワーク・ビルドツール不使用）
- ホスティング: GitHub Pages（main ブランチ / ルート）
- 日本語組版: [jp-ui-contracts](https://github.com/hirokaji/jp-ui-contracts)（MIT）

## 設計契約

[`DESIGN.md`](DESIGN.md) に日本語UI向けの設計契約を記載しています。
[jp-ui-contracts](https://github.com/hirokaji/jp-ui-contracts) の `base` テンプレートを土台に、このプロジェクト固有のタイポグラフィ・カラー・コンポーネント方針を定義しています。

## サードパーティ表記

[`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md) を参照してください。
ライセンス全文は [`LICENSES/`](LICENSES/) に格納しています。
