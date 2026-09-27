# Observation layer: columns and price statuses

One row is one observation: an item, in a region, at a point in time, from one source. Japan and the United States use the same columns.

| Column | Meaning |
|---|---|
| obs_id | 16 hex digits, derived from the source id and the values that identify the row; the same input gives the same id |
| country | JP or US |
| layer | material, labor, work (combined unit prices), equipment, index, spending, cost_sqft, cost_limit, bid_item, house_price, wage |
| category | chapter or class in the source, in the source's words |
| item_name | item, trade, work item or series name, in the source's words |
| spec | specification, size or condition, as printed |
| unit | unit as printed in the source |
| geo_level | national, bureau_area, pref, pref_area, city, census_region, state, metro, county, district, place |
| geo_code | JP or US for national; JIS two digits for prefectures; FIPS for states and counties; CBSA for metros |
| geo_name | name of geo_code |
| area_label, area_code, area_members | the source's own area label, code and member municipalities |
| price | the value, only when the source licence allows redistribution; a plain number |
| currency | JPY or USD; empty for indexes |
| price_basis | what the value is, for example design_unit_price_ex_tax, labor_wage_8h, index_value, wage_hourly_mean, bid_weighted_avg |
| price_status | see below |
| ref_value, ref_note | a reference value and what it is |
| period | point in time: YYYY, YYYY-MM, YYYY-MM-DD, YYYYQn, FYYYYY or YYYYHn |
| effective_from | effective date when known |
| source_id | the ledger file sources/<source_id>.json |
| source_page | page in the source |
| evidence_url | URL of the source |
| license | licence of the source for this row |
| jccdb_v4_item_id | the JCCDB v4 item id when the row could be linked |
| note | reading notes |

| price_status | value present | meaning |
|---|---|---|
| published_pdl | yes | published by the source and redistributable under PDL1.0 |
| published_cc_by | yes | Japanese Government Standard Terms of Use 2.0 or CC BY 4.0 |
| public_domain | yes | a U.S. federal work or other public-domain value |
| published_open_terms | yes | the source's terms explicitly allow reuse; the text is quoted in the ledger |
| publication_based_not_public | no | the public body uses commercial price publications and publishes no value |
| not_set | no | blank, "-", or 0 in a unit price table: not set for that area and time, not zero |

Counts and amounts of 0 in statistics are values (price 0). The ledger for each source (sources/<source_id>.json) records the URL, retrieval date, sha256 of the original, the licence and its text quoted verbatim, and how the source was read.
