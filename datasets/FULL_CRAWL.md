# Full Crawl of the Three Crises

The datasets in this directory contain the accounts from which POSIM agents are initialised and those accounts' posts. They were selected from a much larger crawl. This file describes the complete crawl and how to obtain it.

## Scope

For each crisis we collected the original posts that carry crisis-related hashtags or keywords, together with their complete repost chains and comment trees, and the public profile fields of every participating account.

| Crisis | Accounts | Records (original posts + reposts + comments) |
|---|---:|---:|
| LE: Luxury Earring (天价耳环) | 426,882 | 1,254,512 |
| WL: WHU Library (武大图书馆) | 416,235 | 1,416,034 |
| XF: Xibei Prepared Food (西贝预制菜) | 725,251 | 1,851,124 |
| **Total** | **1,568,368** | **4,521,670** |

## Download

Because of its size, the full crawl is hosted outside GitHub:

- **Baidu Netdisk**: <https://pan.baidu.com/s/1Yhu0u-77VFw6sUN3jlqeHg?pwd=sqfg> (extraction code: `sqfg`)

## Format and de-identification

The full crawl uses the same per-crisis layout and file schemas as the datasets in this directory (`users.jsonl.gz`, `posts.jsonl.gz`, `interactions.csv.gz`; see [README.md](README.md)). The event timelines are identical to the `events.jsonl` files in this repository and are not duplicated.

The same de-identification procedure is applied, with the same keyed-hash pseudonyms. An account therefore has the same `user_id` in the full crawl as in the datasets here, and the two can be joined directly. In the full crawl, the `role` field is filled only for the accounts that POSIM initialises as agents, and is `null` for all other accounts.

## Terms of use

The terms in [README.md](README.md#terms-of-use) apply: non-commercial academic research only, no attempts at re-identification, and use in accordance with the Sina Weibo terms of service and applicable personal-information protection law.
