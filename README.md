# jp-ai-bot-census

**Weekly census of how the top 1,000 .jp domains on the Tranco list treat AI bots in robots.txt and llms.txt.** Aggregate counts only: no company or domain is named.
**Tranco 上位の .jp ドメイン 1,000 件が、robots.txt と llms.txt で AI ボットをどう扱っているかの週次定点調査。** 公開するのは集計値のみで、会社名・ドメイン名は含みません。

- Page / ページ: https://pw.migurei.ai/en/research/japanese-sites-and-ai-bots ・ https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots
- Data / データ: [`data/series.csv`](data/series.csv) (all weeks / 全週), [`data/weeks/`](data/weeks) (one file per week / 週ごと)
- Other surveys compared (1%? 10%? 32%?) / ほかの調査との比較: https://theta-claude-dot.github.io/jp-ai-bot-census/surveys.html
- License / ライセンス: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Cite as / 出典の書き方: **Parallel World (pw.migurei.ai)**, "How Japanese sites treat AI bots", measured 26 October 2026 (edition 1). 「出典：Parallel World (pw.migurei.ai)」

## English

### What it is
Every Monday we fetch `/robots.txt` and `/llms.txt` from the same frozen list of 1,000 domains: the first 1,000 `.jp` registrable domains, in rank order, of [Tranco list W3ZV9](https://tranco-list.eu/list/W3ZV9) (25 October 2026). The list does not change from week to week, so a difference between weeks is a change on the sites (or in whether we could reach them). For each of the 39 bots in our [AI bot registry](https://github.com/theta-claude-dot/ai-bot-registry) we count the sites whose robots.txt does not allow the top page `/`.

The first edition was measured on 26 October 2026 (2026-W44). The latest numbers, the method and what the numbers do not prove are on the page above.

### Method in short
- One GET for `robots.txt` per site over https, up to 3 redirects, one retry on the `www` host after a network failure. `/llms.txt` once, only where robots.txt does not disallow our user agent.
- User agent `migurei-ParallelWeb/0.1 (+https://migurei.ai/ja/scanner; research@migurei.ai)`, every request signed with Web Bot Auth, sent from a Japanese IP address. Read-only: no form, no login, no purchase.
- Verdicts follow RFC 9309 (Robots Exclusion Protocol) for the path `/`. A `/version` suffix in a User-agent line is ignored, as in Google's open-source parser. A missing robots.txt (404 and similar) means everything is allowed. A site whose robots.txt redirected to another registrable domain is left out of the per-bot denominators.
- Every row says what it is divided by (`denominator_definition`); there is no total score.

### Files
| File | Content |
|---|---|
| `data/weeks/<week>.csv` | The public aggregate table of one week: `metric, numerator, denominator, percent, denominator_definition` |
| `data/series.csv` | The rows of every week in one file, with `week_id, week_start, tranco_list_id, registry_version, code_sha` |

Counts under 5 are written `<5` with an empty percent. The Content-Signal count is not published. "Minus our own and excluded sites" in `denominator_definition` is the selection rule; in edition 1, 0 sites were excluded.

### What it does not prove
robots.txt is a request, not a barrier: this says nothing about which bots actually visit. Sites that answered 403 or 5xx have no per-bot verdict and are outside the shares. The sample is 1,000 `.jp` domains of one day's Tranco list, not "the Japanese web". We sent only our own user agent. Only the top page `/` is evaluated. We measured and counted it ourselves; no independent party has checked it.

## 日本語

### 概要
毎週月曜日に、同じ 1,000 ドメインの固定リストから `/robots.txt` と `/llms.txt` を取得します。リストは [Tranco リスト W3ZV9](https://tranco-list.eu/list/W3ZV9)（2026年10月25日版）の上位から順に選んだ .jp の登録ドメイン 1,000 件で、毎週入れ替えません。そのため週ごとの差は、サイト側の設定の変化（または到達できたかどうかの変化）を表します。[AI ボット登録簿](https://github.com/theta-claude-dot/ai-bot-registry)の 39 ボットそれぞれについて、robots.txt がトップページ（/）を許可していないサイトを数えています。

第 1 回は 2026年10月26日（2026-W44）の計測です。最新の数字、調べ方、この数字から言えないことは上のページにあります。

### 調べ方（要約）
- 各サイトに robots.txt の GET を 1 回（https、リダイレクトは 3 回まで、通信エラーのときだけ www 付きで 1 回再試行）。/llms.txt は、robots.txt が当社のユーザーエージェントを拒否していないサイトにだけ 1 回。
- ユーザーエージェントは `migurei-ParallelWeb/0.1 (+https://migurei.ai/ja/scanner; research@migurei.ai)`。すべてのリクエストに Web Bot Auth の署名を付け、日本の IP アドレスから送信。読み取りだけで、フォーム送信・ログイン・購入はしません。
- 判定は RFC 9309（Robots Exclusion Protocol）に従い、パス `/` について行います。User-agent 行の `/version` は、Google の公開パーサーと同じく無視します。robots.txt がない（404 など）場合は「すべて許可」です。別の登録ドメインにリダイレクトされたサイトは、ボット別の分母から除きます。
- 各行に分母の定義（`denominator_definition`）があり、合計点はありません。

### ファイル
| ファイル | 内容 |
|---|---|
| `data/weeks/<週>.csv` | 1 週間分の公開用集計表：`metric, numerator, denominator, percent, denominator_definition` |
| `data/series.csv` | 全週の行を 1 ファイルにまとめたもの（`week_id, week_start, tranco_list_id, registry_version, code_sha` 付き） |

5 件未満のセルは `<5` と表示し、割合は空欄です。Content-Signal の件数は公開していません。`denominator_definition` の「当社のサイトと除外したサイトを除く」は選定の規則で、第 1 回に除外したサイトは 0 件でした。

### この数字から言えないこと
robots.txt は「お願い」であり、アクセスを止める仕組みではありません。実際にどのボットが訪れているかは分かりません。403 や 5xx を返したサイトはボット別の判定ができず、割合に入っていません。対象はある日の Tranco リストの .jp ドメイン 1,000 件で、「日本のウェブ全体」ではありません。取得は当社のユーザーエージェントだけで、判定したのはトップページ（/）だけです。計測も集計も当社自身が行い、独立した第三者の確認は受けていません。

## License / ライセンス
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Credit "Parallel World (pw.migurei.ai)". / 出典に「Parallel World (pw.migurei.ai)」と記載してください。
