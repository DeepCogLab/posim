# Full Crawl of the Three Crises

The datasets in this directory contain the accounts from which POSIM agents are initialised and those accounts' posts. They were selected from a much larger crawl, which is released separately. This file describes the full crawl and how to obtain it.

## Download

Because of its size (about 2.0 GB compressed), the full crawl is hosted outside GitHub:

- **Baidu Netdisk**: <https://pan.baidu.com/s/1Yhu0u-77VFw6sUN3jlqeHg?pwd=sqfg> (extraction code: `sqfg`)

Besides the data files, the package contains per-crisis statistics, a data profile, validation results, and SHA-256 checksums for every file (see [Files](#files)).

## Scope

For each crisis we collected the original posts that carry crisis-related hashtags or keywords, together with their complete repost chains and comment trees, and the public profile fields of every participating account. The crawl covers the whole collection period of each crisis, not only the window simulated in the paper.

| Crisis | Accounts | Original posts | Reposts | Comments | All posts | Interaction relations |
|---|---:|---:|---:|---:|---:|---:|
| LE: Luxury Earring (天价耳环) | 426,881 | 95,379 | 278,863 | 880,221 | 1,254,463 | 1,159,084 |
| WL: WHU Library (武大图书馆) | 416,235 | 41,435 | 678,616 | 695,786 | 1,415,837 | 1,374,132 |
| XF: Xibei Prepared Food (西贝预制菜) | 725,251 | 90,334 | 840,279 | 920,473 | 1,851,086 | 1,760,704 |
| **Total** | **1,568,367** | **227,148** | **1,797,758** | **2,496,480** | **4,521,386** | **4,293,920** |

- The crawl as collected contains 1,568,368 account documents and 4,521,670 records. The released files are the result of the same de-duplication as the datasets in this directory: it merges one duplicated account document and removes 284 records (<0.01%).
- Accounts are counted per crisis. Across the three crises there are 1,388,891 distinct accounts, and 28,021 of them take part in all three.

| Crisis | Unverified | Verified individuals | Institutions | Collection period | Busiest day (posts) |
|---|---:|---:|---:|---|---|
| LE | 372,497 | 52,543 | 1,841 | 2025-05-02 to 2025-07-31 | 2025-05-16 (170,764) |
| WL | 373,616 | 41,200 | 1,419 | 2025-06-01 to 2025-09-23 | 2025-08-01 (264,453) |
| XF | 639,691 | 82,718 | 2,842 | 2025-09-08 to 2025-09-23 | 2025-09-15 (550,689) |

Institutions are accounts verified as media, government, organisations, schools, websites, or enterprises.

## Files

```
full_crawl_release/
├── LE/  users.jsonl.gz  posts.jsonl.gz  interactions.csv.gz
├── WL/  (same files)
├── XF/  (same files)
├── README.md
├── full_crawl_stats.json     # released volumes per crisis
├── DATA_PROFILE.json         # daily activity, account composition, missing values, linkage coverage
├── VALIDATION.json           # integrity and de-identification checks
├── FILES.txt
└── SHA256SUMS.txt
```

| File | LE | WL | XF |
|---|---:|---:|---:|
| `users.jsonl.gz` | 19.9 MiB | 19.9 MiB | 32.6 MiB |
| `posts.jsonl.gz` | 365.2 MiB | 859.4 MiB | 539.7 MiB |
| `interactions.csv.gz` | 29.5 MiB | 33.4 MiB | 42.7 MiB |

The file schemas are the same as for the datasets in this directory (see [README.md](README.md)). The event timelines are identical to the `events.jsonl` files in this repository and are not duplicated. In `posts.jsonl.gz`, posts are stored account by account rather than in time order, so sort or aggregate by `time` for temporal analysis. Comment records do not carry a platform emotion label (`platform_emotion` is `null`).

## De-identification and linkage

The same de-identification procedure and the same keyed-hash pseudonyms are applied as in the datasets in this directory. An account therefore has the same `user_id` (`U…`) in the full crawl as in the datasets here, and the two can be joined directly. A few accounts that the smaller datasets know only by screen name (`N…` pseudonyms) can be resolved to an account ID in the full crawl, where they appear with a `U…` pseudonym instead.

The `role` field is filled only for the accounts that POSIM initialises as agents and is `null` for all other accounts. A `null` role should not be read as `citizen`.

## Terms of use

The terms in [README.md](README.md#terms-of-use) apply: non-commercial academic research only, no attempts at re-identification, and use in accordance with the Sina Weibo terms of service and applicable personal-information protection law.
