# kidoku-cdn

KIDOKU の **一時的な公開アセット**を置くためのリポジトリ。

## 用途

外部サービス（主に Meta / Instagram Graph API）が画像を fetch する際に、HTTPS の公開 URL を要求するため、その「fetch されるための一時置き場」として使う。

例：
```
https://raw.githubusercontent.com/HAL-kidoku/kidoku-cdn/main/ig/2026/04/post-001.jpg
```

## 運用ポリシー

1. **投稿後に削除する**：Meta 側で CDN にキャッシュ取り終えたら、当該ファイルは git rm で削除する。Instagram 投稿そのものは残る（Meta の CDN コピーがあるため）。
2. **このリポジトリには機密情報を入れない**：投稿用画像のみ。社内資料・契約書・PII は絶対に置かない。
3. **コミット履歴は残る**：削除しても git の履歴からは復元可能。事故時のリスクを忘れずに。
4. **命名は中立**：投稿内容・クライアント名がリポ名から推測できないようにする。

## ディレクトリ構造

```
ig/
  YYYY/
    MM/
      post-NNN.jpg
note/
  ...
```

## 関連
- 投稿パイプライン: [HAL-kidoku/kidoku-company-os](https://github.com/HAL-kidoku/kidoku-company-os)（`apps/content-autopublish/`）
