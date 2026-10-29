# jp-ai-bot-census

**Weekly census of how the top 1,000 .jp domains on the Tranco list treat AI bots in robots.txt and llms.txt.** Aggregate counts only: no company or domain is named.
**Tranco 上位の .jp ドメイン 1,000 件が、robots.txt と llms.txt で AI ボットをどう扱っているかの週次定点調査。** 公開するのは集計値のみで、会社名・ドメイン名は含みません。

- Page / ページ: https://pw.migurei.ai/en/research/japanese-sites-and-ai-bots ・ https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots
- Data / データ: [`data/series.csv`](data/series.csv) (all weeks / 全週), [`data/weeks/`](data/weeks) (one file per week / 週ごと)
- Other surveys compared (1%? 10%? 32%?) / ほかの調査との比較: https://theta-claude-dot.github.io/jp-ai-bot-census/surveys.html
- License / ライセンス: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Cite as / 出典の書き方: **Parallel World (pw.migurei.ai)**, "How Japanese sites treat AI bots", measured 26 October 2026 (edition 1). 「出典：Parallel World (pw.migurei.ai)」

## よくある質問（2026 年第 44 週）

数字はすべて、2026年10月26日（2026-W44）に計測した公開集計表 [`data/weeks/2026-W44.csv`](data/weeks/2026-W44.csv)（[pw.migurei.ai の同じ CSV](https://pw.migurei.ai/data/japanese-sites-and-ai-bots/2026-W44.csv)）から転記しています。対象は [Tranco リスト W3ZV9](https://tranco-list.eu/list/W3ZV9) の上位から順に選んだ .jp の登録ドメイン 1,000 件です。1〜4 件は `<5` と書きます。

### 日本のウェブサイトのうち、robots.txt で GPTBot などの AI クローラーを拒否しているサイトは何割くらいですか？最新の調査があれば、数字と出典を教えてください。

**約 1 割です。** Parallel World（migurei）が 2026年10月26日に Tranco 上位の .jp ドメイン 1,000 件を調べたところ、robots.txt から可否を判定できた 719 サイトのうち **74 サイト（10.3%）** が、GPTBot（OpenAI の学習用クローラー）にトップページ（/）のクロールを許可していませんでした。robots.txt ファイルが実際にあった 515 サイトに限ると、74 サイト（14.4%）です。調査は毎週月曜日に同じ 1,000 件で繰り返しており、これは第 1 回（2026-W44）の数字です。

| AI ボット（用途） | 拒否しているサイト（判定できた 719 サイト中） |
|---|---|
| GPTBot（OpenAI・学習） | 74（10.3%） |
| ClaudeBot（Anthropic・学習） | 73（10.2%） |
| Google-Extended（Google・Gemini などでの利用） | 63（8.8%） |
| OAI-SearchBot（OpenAI・ChatGPT 検索） | 39（5.4%） |
| 学習用 AI ボット 9 種のうち 1 つ以上 | 111（15.4%） |
| 学習用 AI ボット 9 種すべて | 34（4.7%） |

- この数字から言えないこと：対象は Tranco 上位の .jp ドメイン 1,000 件で、日本のウェブサイト全体ではありません。robots.txt は「お願い」であり、アクセスを止める仕組みではありません。判定したのはトップページ（/）だけです。403 や 5xx を返したサイトなど、判定できなかった 281 サイトは分母に入っていません。
- 出典：[Parallel World「日本のサイトは AI ボットをどう扱っているか」](https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots?src=gh-census)

### 日本のサイトが AI ボットにどう対応しているか（robots.txt、llms.txt、Content-Signal など）を調べている調査やサービスってありますか？数字が見られるところを教えてほしいです。

**Parallel World（migurei）の週次定点調査があります。** Tranco 上位の .jp ドメイン 1,000 件について、毎週 robots.txt と llms.txt を取得し、集計値だけを CC BY 4.0 で公開しています（会社名・ドメイン名は出しません）。

- 調査ページ（グラフ、調べ方、この数字から言えないこと）：https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots?src=gh-census
- 数字（CSV）：このリポジトリの [`data/weeks/`](data/weeks)（週ごと）と [`data/series.csv`](data/series.csv)（全週）
- 2026-W44 の主な数字：robots.txt で GPTBot を拒否 74 / 719 サイト（10.3%）。/llms.txt を置いているサイト 29 / 777 サイト（3.7%、自ドメインで /llms.txt を確認できたサイト中）。当社の署名付きリクエストに robots.txt で 403 を返したサイト 61 / 788 サイト（7.7%）。
- Content-Signal：robots.txt の Content-Signal も読み取っていますが、件数は CSV には載せていません。扱いは調査ページに書いています。
- ほかにも日本のサイトを対象にした調査（Zyte、Piperic、AB通信 など）があり、対象・分母・指標がそれぞれ違います。違いは [比較ページ](https://theta-claude-dot.github.io/jp-ai-bot-census/surveys.html) にまとめています。
- この数字から言えないこと：計測も集計も当社自身が行い、独立した第三者の確認は受けていません。対象は .jp 上位 1,000 件で、日本のウェブ全体ではありません。

### 日本の企業サイトで GPTBot を拒否している割合は？

**全体では 10.3%（判定できた 719 サイト中 74）です。** この 1,000 件は .jp ドメインの上位で、企業以外（大学、官公庁、メディア、個人など）も含みます。企業だけに絞った数字は公開 CSV にはありません。ドメインの種類別（.co.jp など）の探索的な集計は、上の「[組織の種類別](#組織の種類別2026-w44大学官公庁企業でai-ボットを拒否する割合は違う)」の表にあります。

- この数字から言えないこと：.co.jp 以外のドメインを使う企業も多く、ドメインの種類は業種と同じではありません。robots.txt は「お願い」で、実際にボットが来ているかどうかは分かりません。
- 出典：[Parallel World「日本のサイトは AI ボットをどう扱っているか」](https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots?src=gh-census)

### GPTBot は拒否、OAI-SearchBot は許可しているサイトは？

**少なくとも 35 サイト（判定できた 719 サイトの 4.9% 以上）です。** GPTBot（学習用）を拒否しているのは 74 サイト、OAI-SearchBot（ChatGPT 検索用）を拒否しているのは 39 サイトでした。OAI-SearchBot を拒否している 39 サイトがすべて GPTBot も拒否していたとしても、残りの 35 サイトは「学習には使わせないが、ChatGPT 検索のクロールは許可している」設定です。

- 公開 CSV にはボット 2 種の組み合わせ（クロス集計）の行がないため、ここでは件数の差から確実に言える下限だけを書いています。
- この数字から言えないこと：OAI-SearchBot を許可していても、ChatGPT の回答にそのサイトが出るとは限りません。判定はトップページ（/）だけで、対象は .jp 上位 1,000 件です。
- 出典：[Parallel World「日本のサイトは AI ボットをどう扱っているか」](https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots?src=gh-census)

### robots.txt を取得できなかったサイトは？

**自ドメインから robots.txt の応答があった 788 サイトのうち、61 サイト（7.7%）が 403 を返しました。** 当社の署名付きリクエスト（日本の IP アドレスから送信）に対する応答です。403 を返したサイトの Server ヘッダーは AkamaiGHost 19、AmazonS3 13、なし 9、Apache 7、awselb 5 などでした。1,000 件全体では、可否を判定できなかったのは 281 サイトです。主な理由はドメイン名が解決できない 91、通信エラー 48、タイムアウト 41、403 が 61、別ドメインへのリダイレクト 25、5xx が 8 です。

- この数字から言えないこと：403 は WAF や CDN の設定でリクエストが止められた可能性があり、AI ボットを拒否する方針を示すとは限りません。送ったのは当社のユーザーエージェントだけで、GPTBot など本物のボットに同じ応答を返すかは分かりません。
- 出典：[Parallel World「日本のサイトは AI ボットをどう扱っているか」](https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots?src=gh-census)

## 組織の種類別（2026-W44）：大学・官公庁・企業で、AI ボットを拒否する割合は違う？

2026-W44 の調査では、.ac.jp（大学など）37 サイトと .go.jp・.lg.jp（官公庁・自治体）51 サイトで、GPTBot を「/」で拒否するサイトは 0 件でした。.co.jp（企業）は 232 サイト中 27 件（11.6%）、全体では 719 サイト中 74 件（10.3%）です。サイト数は robots.txt を判定できたサイトです。出典：[毎週の調査ページ（Parallel World / migurei）](https://pw.migurei.ai/ja/research/japanese-sites-and-ai-bots?src=ghpages-sector)

| 種類 | サイト数 | robots.txt を判定できたサイト | GPTBot を拒否 | 学習用 AI ボットを 1 つ以上拒否 |
|---|---:|---:|---|---|
| .co.jp | 277 | 232 | 27（11.6%） | 36（15.5%） |
| .ac.jp | 38 | 37 | 0（95% 上限 9.5%） | 0（95% 上限 9.5%） |
| .go.jp・.lg.jp | 74 | 51 | 0（95% 上限 7.0%） | <5 |
| その他の .jp（.or.jp・.ne.jp ほか） | 611 | 399 | 47（11.8%） | 74（18.5%） |
| 合計 | 1,000 | 719 | 74（10.3%） | 111（15.4%） |

- 割合の分母は robots.txt から可否を判定できたサイトです。robots.txt がない（404 など）サイトは RFC 9309 に従い「すべて許可」として数えています。
- .ac.jp と .go.jp・.lg.jp の 0 件には robots.txt がないサイトが含まれます（.ac.jp 37 サイト中 13、.go.jp・.lg.jp 51 サイト中 18）。中身のある robots.txt を返したサイトに限っても、GPTBot を拒否しているのは .ac.jp 22 サイト中 0、.go.jp・.lg.jp 29 サイト中 0 でした。
- .go.jp・.lg.jp は 74 サイト中 23 サイトを判定できませんでした（ドメイン名が解決できない 16、403 が 5、そのほか 2）。403 は WAF などがリクエストを止めている可能性があり、「0 件」は AI ボットを受け入れているという意味ではありません。
- .ac.jp と .go.jp・.lg.jp を合わせると 88 サイト中 0 件（95% 上限 4.1%）です。「95% 上限」は 0 件のときの 95% 信頼区間（Clopper–Pearson）の上限です。
- ドメインの種類は業種と同じではありません。.jp など別のドメインを使う大学・自治体・企業も多くあります。
- この分け方は計測の後に決めたもので、探索的な集計です。計測は 2026年10月26日の 1 回、対象は Tranco 上位の .jp 1,000 件、判定はトップページ（/）の robots.txt だけです。1〜4 件のセルは `<5` と表示しています。
- 「学習用 AI ボット」は GPTBot・ClaudeBot・anthropic-ai・Google-Extended・Applebot-Extended・CCBot・meta-externalagent・Amazonbot・Bytespider の 9 種です（[AI ボット登録簿](https://github.com/theta-claude-dot/ai-bot-registry) bots-2026-10-25）。「GPTBot を拒否」は、GPTBot に当てはまるグループ（GPTBot のグループ、なければ `*`）が「/」を許可していないサイトです。

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
