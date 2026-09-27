# United States Construction Cost Database (USCCDB) v1.0

DOI of this version: https://doi.org/10.5281/zenodo.22979157
Author: Toshikatsu Oga (ORCID 0009-0000-9180-903X), The HORIZONs Co., Ltd.
Licence: CC BY 4.0 for the compilation. Values from U.S. federal sources are in the public domain (17 U.S.C. 105); city open data keep their own terms, quoted in each ledger.

USCCDB is the U.S. companion of the Japan Construction Cost Database (JCCDB, https://doi.org/10.5281/zenodo.22127751). It uses the same columns.

## What is in this record

2,849,829 rows (2,743,751 with a value) from 2,375 U.S. public sources, one row per observation: an item, in a region, at a point in time, with the value or the reason no public value exists, the unit, the source page, the evidence URL and the licence.

- `usccdb-v1-observations-part1of9.zip` to `usccdb-v1-observations-part9of9.zip`: 115 CSV files in 9 zips, split so that each upload stays small; unzip them into the same folder. Large sources are split into several files.
- `usccdb-v1-sources.zip`: 2377 source ledgers (URL, retrieval date, SHA-256 of the original, licence and its text quoted verbatim, how it was read).
- `usccdb-v1-observations-manifest.csv`: rows and SHA-256 of every CSV inside the zips.
- `usccdb-v1-schema.md` (English) and `usccdb-v1-schema.ja.md` (Japanese): columns and price statuses.
- `usccdb-v1-reports.zip`: the ingestion and checking reports (Japanese).

Sources include Davis-Bacon general wage determinations, BLS wages (OEWS, QCEW, ECI), producer price and construction cost indexes (BLS PPI, FHWA NHCCI, Census CQPI, USACE CWCCIS), DoD area cost factors, USACE and FEMA equipment rates, Census building permits, value put in place and the 2022 Economic Census, HUD total development cost limits, FHWA and state DOT bid prices, and city permit data.

## Counts

| layer | rows |
|---|---:|
| bid_item | 12,442 |
| cost_limit | 23,296 |
| cost_sqft | 2,066 |
| equipment | 95,985 |
| house_price | 1,056 |
| index | 80,558 |
| labor | 133,962 |
| spending | 1,470,090 |
| wage | 1,026,002 |
| work | 4,372 |

| price_status | rows |
|---|---:|
| not_set | 104,586 |
| public_domain | 2,727,809 |
| publication_based_not_public | 1,492 |
| published_open_terms | 15,942 |

| licence | rows |
|---|---:|
| OPEN-TERMS | 16,389 |
| US-PD-17USC105 | 2,833,440 |

## What is not included, and why

- Rows from sources whose terms limit reuse to personal or informational use (the South Dakota and Montana DOT item lists, 3,616 rows) are not included. Texas DOT and Florida DOT data were not ingested at all.
- Davis-Bacon determinations cover the states retrieved before automated retrieval was stopped under the SAM.gov terms of use; the remaining states are not included.
- No values from commercial cost books.
- The distribution-chain estimates served by the HORIZON SHIELD MCP server (landed import cost, wholesale, retail, contractor, trade margins, contract discounts) are computed on request and are not part of this dataset.

## What these values are not

Prevailing wages are minimums for federally funded work, permit valuations are declared by applicants, and public unit prices and indexes are reference data. None of them is a renovation quote or a verdict on a quote.

## How to cite

Oga, T. (2026). United States Construction Cost Database (USCCDB) v1.0 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22979157

## Related

- JCCDB (Japan): https://doi.org/10.5281/zenodo.22127751
- Live access for AI agents: the HORIZON SHIELD MCP server, https://mcp.horizonshield.dev/mcp (get_us_construction_prices, get_us_prevailing_wage, get_us_permits, get_us_area_factor, get_jccdb_observations, get_jccdb_index_series, get_jccdb_coverage).
- Source repository: https://github.com/ogasurfproject-jpg/horizon-shield/tree/main/data/jccdb-obs-v2

## 日本語の要約

USCCDB は米国の公的な資料から取った建設費の観測 2,849,829 行(値のある行 2,743,751)を、JCCDB と同じ列で持つ。各行に出典の URL と利用条件が付く。個人・情報目的に限る条件の出典(South Dakota と Montana の DOT)の行は入れていない。流通の各段の推計(輸入の陸揚げ原価・卸・小売・元請)は MCP サーバーが問われたときに計算して返すもので、このデータセットには入らない。
