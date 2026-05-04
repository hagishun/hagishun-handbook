# hagishun-handbook

萩平の横断ナレッジ。プロジェクトをまたいで効く**原則**と、各リポジトリで使う**テンプレ**を置く場所。

## 何のためにあるか

- 同じ判断を毎回ゼロから考えない
- AIエージェントに「萩平の流儀」を一度に渡す
- 各プロジェクトのADRから引用される一次資料

## 何を置くか / 置かないか

| 置く | 置かない |
|---|---|
| プロジェクトをまたいで効く原則 | 特定プロジェクトのADR（各リポジトリの `docs/adr/` へ） |
| 自分が驚いた・ハマった経験から得た教訓 | ググって5分で出る一般知識 |
| 各リポジトリにコピペするひな形 | 一度設定したら忘れていい設定手順 |

判断基準は3つ:

1. 次に同じ場面が来たとき、思い出したいか？
2. ググっても**自分の文脈の答え**は出ない内容か？
3. 自分にとって「驚き」があったか？

3つすべて Yes なら書く。

## 構成

```
hagishun-handbook/
  README.md                          # このファイル（索引）
  principles/                        # 横断原則
    llm-grounding.md
    working-across-multiple-repos.md
  templates/                         # 各リポジトリに配る雛形
    adr-template.md
    copilot-instructions-template.md
```

## 使い方

### 個人プロジェクトから参照する

各プロジェクトと同じ親ディレクトリに clone し、VS Code の Multi-root Workspace で束ねる。詳しくは [principles/working-across-multiple-repos.md](principles/working-across-multiple-repos.md)。

### 各リポジトリのADRから引用する

```markdown
## Context
LLMによる推薦は[handbookのLLM grounding原則](https://github.com/hagishun/hagishun-handbook/blob/main/principles/llm-grounding.md)に従う。
本プロジェクトでは具体的に以下の方法で実装する……
```

handbook が**原則**を持ち、ADRが**そのプロジェクトでの具体的な適用**を持つ、という分担。

## ステータス

`seed`. ここから育てていく。
