# 複数リポジトリを束ねて作業する

各プロジェクトは独立リポジトリにし、VS Code の Multi-root Workspace で1つのウィンドウに束ねて開く。

## なぜ

- **公開単位はリポジトリ単位で揃えたい**: aozora-reading-compass は単独で star されたい
- **でも横断原則(handbook)を参照しながら書きたい**: ADR から handbook を引用する場面が頻繁にある
- **AIエージェントに両方のコンテキストを持たせたい**: 「handbook の grounding 原則を参照して、このプロジェクト用のADRを書いて」が成立する

これを満たすには「物理的には別、作業時は1つ」が要る。

## どうする

### 1. ディレクトリは並べる

```
~/Documents/dev/
  aozora-reading-compass/    # 別リポジトリ
  hagishun-handbook/         # 別リポジトリ
  hagishun.code-workspace    # 両方を束ねる定義ファイル
```

### 2. workspace ファイルを置く

```json
{
  "folders": [
    { "path": "aozora-reading-compass" },
    { "path": "hagishun-handbook" }
  ]
}
```

`code ~/Documents/dev/hagishun.code-workspace` で開くと、サイドバーに両方のリポジトリが並ぶ。

### 3. AIエージェントに横断参照を許可する

各プロジェクトの `.github/copilot-instructions.md` に書く:

```markdown
## 関連ナレッジ
- 横断原則は `../hagishun-handbook/principles/` を参照
  （workspace に同居している場合のみ）
```

workspace に handbook が無ければこの指示は無視される。プロジェクト単独で clone した人が困らない設計。

## 効果

- Cmd+Shift+F の横断検索が両リポジトリ一発
- Source Control ビューが**リポジトリ別セクション**で表示される（コミット混入事故が起きない）
- Copilot/Claude が handbook を context に入れて回答する
- いつでも片方だけ単独で開ける（公開リポジトリの独立性は崩れない）

## やらない選択肢と却下理由

| 案 | なぜ却下 |
|---|---|
| Git Submodule で埋め込む | 運用が複雑、submodule初心者の事故率が高い |
| Monorepo に統合 | 公開単位がごちゃつく、単独 star が取れない |
| 別ウィンドウで2つ開く | 横断検索ができない、ウィンドウ往復が面倒 |

## いつこの構成にするか

- **2つ目のリポジトリができた瞬間**から効く。1リポジトリのうちは workspace ファイル不要
- handbook は「2回目に同じことを書きたくなった瞬間」に作ればいい

## 改訂履歴

- 2026-05-04: 初版。handbook を新設したタイミングで抽出
