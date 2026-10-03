# United States Construction Cost Database (USCCDB) v1.0

> Part of **[Awesome HORIZON SHIELD](https://github.com/ogasurfproject-jpg/awesome-horizon-shield)**, the checkable index of every dataset, MCP server and ledger we run. The Japanese counterpart is the **[Japan Construction Cost Database (JCCDB)](https://github.com/ogasurfproject-jpg/japan-construction-cost-database)**.

[![Dataset DOI](https://img.shields.io/badge/Dataset%20DOI-10.5281%2Fzenodo.22979157-1682D4)](https://doi.org/10.5281/zenodo.22979157)
[![All versions](https://img.shields.io/badge/All%20versions-10.5281%2Fzenodo.22979156-1682D4)](https://doi.org/10.5281/zenodo.22979156)
[![Hugging Face](https://img.shields.io/badge/Hugging%20Face-ogasurfproject%2Fusccdb-FFD21E)](https://huggingface.co/datasets/ogasurfproject/usccdb)
[![License: CC BY 4.0](https://img.shields.io/badge/Compilation-CC%20BY%204.0-brightgreen.svg)](https://creativecommons.org/licenses/by/4.0/)
[![ORCID](https://img.shields.io/badge/ORCID-0009--0000--9180--903X-A6CE39)](https://orcid.org/0009-0000-9180-903X)

<!-- hs-facts-v1 -->

**In one paragraph.** JCCDB (Japan Construction Cost Database) is an open dataset of Japanese construction and renovation costs, created by Toshikatsu Oga (大賀俊勝), who has worked on construction sites for 30 years, and published by The HORIZONs Co., Ltd. under CC BY 4.0. Version 5.0 (2026-09-26, DOI 10.5281/zenodo.22980284; all versions 10.5281/zenodo.22127751) holds 425,765 records: 95,403 line items and 330,362 observations from 76 Japanese public sources, each observation with its evidence URL. The United States counterpart is USCCDB, the United States Construction Cost Database (DOI 10.5281/zenodo.22979157, 2,849,829 observations). HORIZON SHIELD (https://shield.the-horizons-innovation.com) is the buyer-side service built on JCCDB that checks whether a Japanese renovation estimate is fair.

**ひとことで。** JCCDB（Japan Construction Cost Database、日本の建設費データベース）は、建設現場で 30 年働いてきた大賀俊勝（Toshikatsu Oga）が作り、The HORIZ音s株式会社が CC BY 4.0 で公開している、日本の建設・リフォーム費用のオープンデータです。v5.0（2026-09-26、DOI 10.5281/zenodo.22980284、全版 10.5281/zenodo.22127751）は計 425,765 件で、品目 95,403 と、日本の公的な出典 76 からの観測 330,362 行（各行に証拠の URL）から成ります。米国版は USCCDB（United States Construction Cost Database、DOI 10.5281/zenodo.22979157、観測 2,849,829 行）です。HORIZON SHIELD（https://shield.the-horizons-innovation.com）は JCCDB を土台に、日本のリフォーム見積もりが適正かを施主の側から確かめるサービスです。

<!-- /hs-facts-v1 -->

**2,849,829 construction cost observations from 2,375 U.S. public sources, one row per item, region, point in time and source, each with its evidence URL and licence.** Released 2026-09-26.

This repository is the catalogue and citation record for USCCDB. The data files live in three places that carry the same bytes:

| Where | What | Link |
|---|---|---|
| Zenodo (versioned, DOI) | 9 zips of CSV (115 files), 2,377 source ledgers, manifest with SHA-256 of every CSV, schema, reports | https://doi.org/10.5281/zenodo.22979157 |
| Hugging Face | The same 115 files as Parquet (2,849,829 rows, all columns as strings), with the dataset viewer | https://huggingface.co/datasets/ogasurfproject/usccdb |
| GitHub (source of the release) | The observation CSVs and ledgers as they are maintained, together with the Japanese data | https://github.com/ogasurfproject-jpg/horizon-shield/tree/main/data/jccdb-obs-v2 (`observations/us/`, `sources/`) |

## What USCCDB is

The Japan Construction Cost Database (JCCDB) records that a construction item exists in a public document, and since v5.0 records where, when and at what price it was observed. USCCDB is the U.S. companion built on the same columns. One row is one observation: an item, in a region, at a point in time, from one source, with the value or the reason no public value exists, the unit, the source page, the evidence URL and the licence.

Sources include Davis-Bacon general wage determinations, BLS wages (OEWS, QCEW, ECI), producer price and construction cost indexes (BLS PPI, FHWA NHCCI, Census CQPI, USACE CWCCIS), DoD area cost factors, USACE and FEMA equipment rates, Census building permits, value put in place and the 2022 Economic Census, HUD total development cost limits, FHWA and state DOT bid prices, and city permit data.

## Counts (v1.0)

2,849,829 rows, 2,743,751 with a value, 2,375 public sources, 115 CSV files.

| layer | rows | what it holds |
|---|---:|---|
| wage | 1,026,002 | statistical wages (BLS OEWS by state and metro, QCEW) |
| spending | 1,470,090 | building permits (Census BPS by state, metro, county and place), value put in place, Economic Census 2022, city permit data |
| labor | 133,962 | Davis-Bacon prevailing wages (30 states) |
| equipment | 95,985 | USACE EP 1110-1-8 equipment ownership and operating rates, FEMA equipment rates |
| index | 80,558 | BLS PPI, CPI repair, ECI, Census CQPI, DoD area cost factors, FHWA NHCCI, USACE CWCCIS |
| cost_limit | 23,296 | HUD total development cost limits |
| bid_item | 12,442 | FHWA price trends (1972 to 2006), NJDOT weighted average bid prices (2023 Q2) |
| work | 4,372 | FTA capital cost database, DoD UFC 3-701-01 |
| cost_sqft | 2,066 | Census new housing cost per square foot, DoD UFC 3-701-01, city permits |
| house_price | 1,056 | Census new housing prices |

| price_status | rows | meaning |
|---|---:|---|
| public_domain | 2,727,809 | a U.S. federal work; value present |
| published_open_terms | 15,942 | the source's terms explicitly allow reuse; the text is quoted in the ledger; value present |
| not_set | 104,586 | blank in the source: not set for that area and time, not zero |
| publication_based_not_public | 1,492 | the public body relies on a commercial price publication and publishes no value |

| licence | rows |
|---|---:|
| US-PD-17USC105 | 2,833,440 |
| OPEN-TERMS | 16,389 |

## Columns

Japan and the United States share one schema. The full column list and the meaning of every price status are in [`schema/usccdb-v1-schema.md`](schema/usccdb-v1-schema.md) (Japanese: [`schema/usccdb-v1-schema.ja.md`](schema/usccdb-v1-schema.ja.md)). The key columns:

`obs_id`, `country`, `layer`, `category`, `item_name`, `spec`, `unit`, `geo_level`, `geo_code`, `geo_name`, `price`, `currency`, `price_basis`, `price_status`, `period`, `source_id`, `source_page`, `evidence_url`, `license`, `note`.

Every `source_id` points to a ledger file `sources/<source_id>.json` with the URL, the retrieval date, the SHA-256 of the original file, the licence and its text quoted verbatim, and how the file was read.

## What is not included, and why

- Rows from sources whose terms limit reuse to personal or informational use (the South Dakota and Montana DOT item lists, 3,616 rows) are not included in the release; in the source repository they appear as item lists without values. Texas DOT requires written permission and Florida DOT holds copyright under state law; neither was ingested (report U3).
- Davis-Bacon determinations cover the 30 states retrieved before automated retrieval was stopped under the SAM.gov terms of use. The remaining states are not included and are not retrieved automatically.
- No values from commercial cost books. Where a public document copies or converts commercial figures and says so (parts of DoD UFC 3-701-01), the rows are kept without the value (`price_status` = `publication_based_not_public`).
- The distribution-chain estimates served by the HORIZON SHIELD MCP server (landed import cost, wholesale, retail, contractor, trade margins, contract discounts, installed cost ratios) are computed on request from public statistics and are not part of this dataset.

## What these values are not

Prevailing wages are minimums for federally funded work. Permit valuations are declared by applicants. Public unit prices, bid prices and indexes are reference data. None of them is a renovation quote or a verdict on a quote. When a value is used to judge an estimate, say what the value is.

## Verification

- Independent checks by parties other than the builder: 111,106 valued U.S. rows compared cell by cell with the originals (BLS flat files, OEWS, Census, FEMA, NJDOT), 0 mismatches (report V2); a later pass compared 2,632,645 newly added U.S. rows with their originals, 0 mismatches, and recomputed the 284,850 derived rows with the same result (V4, V5).
- The SHA-256 of every original file is in its ledger (25 of 25 U.S. originals matched at release).
- The SHA-256 of every release file is in [`release/v1.0/USCCDB_v1_RELEASE_DECLARATION.md`](release/v1.0/USCCDB_v1_RELEASE_DECLARATION.md), and of every CSV inside the zips in [`release/v1.0/usccdb-v1-observations-manifest.csv`](release/v1.0/usccdb-v1-observations-manifest.csv). Download from Zenodo, hash, compare.
- Every row is checked by `tools/validate_obs.py` in the source repository (0 errors across all rows).

## For AI agents

The same observations are served live by the HORIZON SHIELD MCP server, `https://mcp.horizonshield.dev/mcp`: `get_us_construction_prices`, `get_us_prevailing_wage`, `get_us_permits`, `get_us_area_factor`, `get_jccdb_observations` (with `country: "US"`), `get_jccdb_index_series`, `get_jccdb_coverage`, `get_jccdb_dataset_info`. Every answer carries the source URL and licence of each row. Values computed by the server (price chain, margins, installed ratios) are marked `computed: true` and are not distributed as files.

## Files in this repository

```
README.md                                   this file
README.ja.md                                Japanese
CITATION.cff                                citation metadata (CFF 1.2.0)
LICENSE.md                                  CC BY 4.0 for the compilation; federal values are public domain (17 U.S.C. 105)
schema/usccdb-v1-schema.md                  columns and price statuses (English)
schema/usccdb-v1-schema.ja.md               the same in Japanese
release/v1.0/USCCDB_v1_RELEASE_DECLARATION.md   SHA-256 of every file in the Zenodo record
release/v1.0/usccdb-v1-observations-manifest.csv rows and SHA-256 of every CSV inside the zips
release/v1.0/ZENODO_README.md               the README as published in the Zenodo record
```

The data files are not duplicated here; the sizes (about 1.4 GB of CSV) belong on Zenodo and Hugging Face, and the maintained copies are in the source repository above.

## Changelog

- **v1.0 (2026-09-26)**: first release. 2,849,829 rows from 2,375 U.S. public sources, 115 CSV files, same columns as JCCDB v5.0. Zenodo 10.5281/zenodo.22979157, Hugging Face `ogasurfproject/usccdb`.

Later versions will be new versions under the concept DOI 10.5281/zenodo.22979156; the concept DOI always resolves to the latest.

## How to cite

Oga, T. (2026). United States Construction Cost Database (USCCDB) v1.0 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22979157

```bibtex
@dataset{oga_2026_usccdb,
  author    = {Oga, Toshikatsu},
  title     = {United States Construction Cost Database (USCCDB) v1.0},
  year      = {2026},
  publisher = {Zenodo},
  version   = {1.0},
  doi       = {10.5281/zenodo.22979157},
  url       = {https://doi.org/10.5281/zenodo.22979157}
}
```

Please also cite the source shown in each row's ledger when you use a value; U.S. federal values carry no attribution requirement, but the source is what makes the number checkable.

## Author

Toshikatsu Oga, The HORIZONs Co., Ltd. (ORCID [0009-0000-9180-903X](https://orcid.org/0009-0000-9180-903X)). Built as part of HORIZON SHIELD, a buyer-side construction cost verification service. HORIZON SHIELD takes no referral or listing fees from contractors.

## Related

- JCCDB, the Japan Construction Cost Database: https://github.com/ogasurfproject-jpg/japan-construction-cost-database (Zenodo concept DOI https://doi.org/10.5281/zenodo.22127751)
- Awesome HORIZON SHIELD (index of datasets, MCP servers and ledgers): https://github.com/ogasurfproject-jpg/awesome-horizon-shield
- Source repository (observations, ledgers, parsers, validators, ingestion rules): https://github.com/ogasurfproject-jpg/horizon-shield/tree/main/data/jccdb-obs-v2

## Disclaimer

The values are observations of public documents at the dates recorded. They are provided as reference data without warranty. They are not construction quotes and do not by themselves establish whether any quote is fair.

---

## 日本語の要約

USCCDB(United States Construction Cost Database)は、米国の公的な資料から取った建設費の観測 2,849,829 行(値のある行 2,743,751、出典 2,375)を、日本の JCCDB と同じ列で持つデータセットです。1 行が 1 観測(品目 × 地域 × 時点 × 出典)で、各行に出典の URL と利用条件が付きます。データ本体は Zenodo(DOI 10.5281/zenodo.22979157)と Hugging Face(ogasurfproject/usccdb)にあり、このリポジトリは目録と引用の記録です。詳しくは [README.ja.md](README.ja.md)。
