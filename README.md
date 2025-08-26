# Keys Pages（穴埋め→解錠→クイズ導線）

目的: 各セクションの穴埋め語を“鍵”として入力→全一致時にクイズへ遷移する静的HTML群をまとめる。

構成

- sec1.html … §1 正義の役割
- sec2.html … §2 正義の主題（これ以降も同様）
- prompts/prompt-template.md … 生成AIに新規ページを作らせるための定形プロンプト

公開想定

- GitHub Pages（静的サイト）。HTMLはフロント判定のため秘匿性は低い（導線ゲートとして使用）。

---

## 運用フロー

1) Tex/MDから該当セクションの“穴埋め語（鍵）”を抽出
2) 定形プロンプトにURLと鍵を埋めてAIに依頼→HTML生成
3) ローカルで表示確認→`QUIZ_URL` を本番に差替
4) `keys-pages/` に配置→GitHubへpush→Pagesで公開

---

## GitHub公開手順（最短）

1) ルートに `index.html`（または本README）、`keys-pages/` をコミット
2) GitHubの Settings → Pages → Source: Deploy from a branch、Branch: `main`（または `gh-pages`）/root を選択
3) 公開URL例: `https://<user>.github.io/<repo>/keys-pages/sec1.html`

ブランチ分離（任意）

- `gh-pages` ブランチで `keys-pages/` のみ公開する運用も可

---

## 注意

- 鍵の答えはJSに含まれるため、厳密な試験用途には不向き
- 厳密用途はフォーム→サーバレス判定（Apps Script/Workers等）に置換
