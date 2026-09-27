# United States Construction Cost Database(USCCDB)v1.0

英語版が正本です: [README.md](README.md)

米国の公的な資料から取った建設費の観測 **2,849,829 行**(値のある行 2,743,751、出典 2,375)。1 行が 1 観測(品目 × 地域 × 時点 × 出典)で、各行に出典の URL と利用条件が付きます。日本の [JCCDB(Japan Construction Cost Database)](https://github.com/ogasurfproject-jpg/japan-construction-cost-database)と同じ列で持ちます。公開 2026-09-26。

このリポジトリは目録と引用の記録です。データ本体は次の 3 か所にあり、中身は同じです。

| 場所 | 中身 | リンク |
|---|---|---|
| Zenodo(版ごとの DOI) | CSV 115 本を 9 本の zip に、出典の台帳 2,377 本、各 CSV の SHA-256 の一覧、列の定義、検査の報告 | https://doi.org/10.5281/zenodo.22979157 |
| Hugging Face | 同じ 115 本を Parquet で(2,849,829 行、全列文字列)、閲覧つき | https://huggingface.co/datasets/ogasurfproject/usccdb |
| GitHub(公開の元) | 保守している観測の CSV と台帳(日本の分と同じ場所) | https://github.com/ogasurfproject-jpg/horizon-shield/tree/main/data/jccdb-obs-v2(`observations/us/`、`sources/`) |

## 何のデータか

JCCDB は「品目が公的資料に実在する」を 1 行 1 品目で持ち、v5.0 から「どの地域・どの時点で・いくらで観測されたか」も持つようになりました。USCCDB はその米国版で、同じ列で作っています。1 行は 1 観測: 品目、地域、時点、出典、値(または値が公開されていない理由)、単位、出典の頁、証拠の URL、利用条件。

出典は Davis-Bacon の賃金決定、BLS の賃金統計(OEWS、QCEW、ECI)、生産者物価指数と建設費指数(BLS PPI、FHWA NHCCI、Census CQPI、USACE CWCCIS)、DoD の地域係数、USACE と FEMA の機械の単価、Census の建築許可・出来高・2022 年経済センサス、HUD の総開発費上限、FHWA と州 DOT の入札単価、市の建築許可データです。

## 件数(v1.0)

| layer(系統) | 行 | 中身 |
|---|---:|---|
| wage(統計上の賃金) | 1,026,002 | BLS OEWS(州・都市圏)、QCEW |
| spending(支出・許可の統計) | 1,470,090 | Census の建築許可(州・都市圏・郡・地方自治体)、出来高、経済センサス 2022、市の許可データ |
| labor(公的に定めた労務単価) | 133,962 | Davis-Bacon の賃金決定(30 州) |
| equipment(機械) | 95,985 | USACE EP 1110-1-8 の機械の所有・運転単価、FEMA の機械単価 |
| index(指数) | 80,558 | BLS PPI、CPI(修繕)、ECI、Census CQPI、DoD 地域係数、FHWA NHCCI、USACE CWCCIS |
| cost_limit(費用の上限) | 23,296 | HUD の総開発費上限 |
| bid_item(入札単価) | 12,442 | FHWA の価格動向(1972〜2006)、NJDOT の加重平均入札単価(2023 Q2) |
| work(工事の単価) | 4,372 | FTA の資本費データベース、DoD UFC 3-701-01 |
| cost_sqft(面積あたり費用) | 2,066 | Census の新築住宅の面積あたり費用、DoD UFC 3-701-01、市の許可データ |
| house_price(住宅価格) | 1,056 | Census の新築住宅価格 |

| price_status(値の状態) | 行 | 意味 |
|---|---:|---|
| public_domain | 2,727,809 | 米連邦政府の著作物(公有)。値あり |
| published_open_terms | 15,942 | 出典の利用条件が再利用を明示的に許す(条文を台帳に写している)。値あり |
| not_set | 104,586 | 原本で空欄。その地域・時点で設定なし(0 ではない) |
| publication_based_not_public | 1,492 | 公的機関が市販の物価資料に依っていて値を公開していない |

## 列

日本と米国で同じ列です。列の一覧と値の状態の意味は [`schema/usccdb-v1-schema.ja.md`](schema/usccdb-v1-schema.ja.md)(英語: [`schema/usccdb-v1-schema.md`](schema/usccdb-v1-schema.md))。`source_id` は台帳 `sources/<source_id>.json`(URL、取得日、原本の SHA-256、利用条件とその条文、読み方)を指します。

## 入れていないもの

- 利用条件が「個人・情報目的」までの出典(South Dakota と Montana の DOT の品目一覧、3,616 行)は公開の版に入れていません(公開の元のリポには値なしの品目一覧として残しています)。Texas DOT は書面の許可が要り、Florida DOT は州法で著作権を持つため、どちらも取り込んでいません。
- Davis-Bacon は SAM.gov の利用規約が自動取得を禁じると分かった時点で取得を止め、取れていた 30 州だけです。残りは自動取得しません。
- 市販の物価資料の値はどこからも入れていません。公的な文書が市販の値を写した・換算したと明記する行は値なしで残しています。
- HORIZON SHIELD の MCP サーバーが返す流通の各段の推計(輸入の陸揚げ原価、卸、小売、元請、マージン、契約の値引き、施工込みの比)は問われたときに公的な統計から計算するもので、このデータセットには入りません。

## この値は何ではないか

Davis-Bacon の賃金は連邦の補助事業の最低賃金、建築許可の金額は申請者の申告、公共の単価・入札単価・指数は参考値です。どれもリフォームの見積単価ではなく、見積の当否の判定でもありません。見積の判断に使うときは、何の値かを添えてください。

## 確かめ方

- 作った担当とは別の者による全行の機械照合: 値のある米国の 111,106 行が原本のセルと一致(不一致 0、報告 V2)。その後に足した 2,632,645 行も原本と一致、計算した 284,850 行も作り直した値と一致(V4・V5)。
- 原本の SHA-256 は各台帳に(公開時 25/25 一致)。
- 公開した各ファイルの SHA-256 は [`release/v1.0/USCCDB_v1_RELEASE_DECLARATION.md`](release/v1.0/USCCDB_v1_RELEASE_DECLARATION.md)、zip の中の各 CSV の SHA-256 は [`release/v1.0/usccdb-v1-observations-manifest.csv`](release/v1.0/usccdb-v1-observations-manifest.csv)。Zenodo から落として hash を取り、突き合わせてください。
- 全行を検査器 `tools/validate_obs.py`(公開の元のリポ)に通し、誤り 0。

## AI エージェントから

同じ観測を HORIZON SHIELD の MCP サーバー `https://mcp.horizonshield.dev/mcp` が返します: `get_us_construction_prices`、`get_us_prevailing_wage`、`get_us_permits`、`get_us_area_factor`、`get_jccdb_observations`(`country: "US"`)、`get_jccdb_index_series`、`get_jccdb_coverage`、`get_jccdb_dataset_info`。各行に出典の URL と利用条件が付きます。サーバーが計算する値(価格の連鎖、マージン、施工込みの比)は `computed: true` の印つきで、ファイルとしては配りません。

## 引用

Oga, T. (2026). United States Construction Cost Database (USCCDB) v1.0 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22979157

版が変わっても concept DOI https://doi.org/10.5281/zenodo.22979156 は最新の版を指します。

## 作者

大賀俊勝(The HORIZ音s株式会社、ORCID [0009-0000-9180-903X](https://orcid.org/0009-0000-9180-903X))。施主側の建設費の検証サービス HORIZON SHIELD の一部として作りました。HORIZON SHIELD は業者から紹介料・掲載料を受け取りません。

## 関連

- JCCDB(日本): https://github.com/ogasurfproject-jpg/japan-construction-cost-database(Zenodo concept DOI https://doi.org/10.5281/zenodo.22127751)
- Awesome HORIZON SHIELD(データセット・MCP サーバー・台帳の索引): https://github.com/ogasurfproject-jpg/awesome-horizon-shield
- 公開の元のリポ(観測、台帳、parser、検査器、取り込みの掟): https://github.com/ogasurfproject-jpg/horizon-shield/tree/main/data/jccdb-obs-v2

## 免責

値は記録した日付の公的な資料の観測で、保証なしの参考値です。工事の見積ではなく、それだけで見積の当否を決めるものでもありません。
