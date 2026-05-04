# Copilot Instructions

このリポジトリで Copilot / Claude などのAIエージェントが作業するときの指針。

## このプロジェクトの目的

<1〜2文で書く。READMEから抜粋でよい>

## 設計判断 (ADR)

- 設計判断は `docs/adr/` に格納している
- 実装前に関連ADRを確認すること
- ADRに反する実装をする場合は、先にADRのステータスを更新すること
- ADR一覧は `docs/adr/INDEX.md` を参照

## 関連ナレッジ (handbook)

- 横断原則は `../hagishun-handbook/principles/` を参照
  （VS Code Multi-root Workspace に同居している場合のみ）
- handbook を参照したADRは、その原則に従う

## このプロジェクト特有のルール

<例>
- 青空文庫の本文は自前ホスティングしない。リンクのみ
- 推薦は実在リストでgroundingする (ADR-0001)
- 著作権保護期間が満了した作品のみを扱う

## 書くべきでないコード

<例>
- 青空文庫からのスクレイピング
- 本文の要約・再配布

## トーン

<例>
- READMEは技術者にも文学好きにも読めるトーン
- 押しつけがましくない、実験としての謙虚さ
