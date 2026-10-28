# POSIM Crisis Datasets

This directory releases the three Sina Weibo online-opinion-crisis datasets used in POSIM, after de-identification.

| Code | Crisis | Period of the crisis |
|---|---|---|
| **LE** | Luxury Earring (天价耳环) | May 2025 |
| **WL** | WHU Library (武大图书馆) | Jul 2025 |
| **XF** | Xibei Prepared Food (西贝预制菜) | Sep 2025 |

Each dataset contains four kinds of data:

- **Event timeline** (`events.jsonl`): the dated public developments of the crisis.
- **Accounts** (`users.jsonl.gz`): the participating accounts and their public profile fields.
- **Full-chain posts** (`posts.jsonl.gz`): the original posts, reposts (with repost chains), and comments (with comment/reply threads) of these accounts.
- **Interaction relations** (`interactions.csv.gz`): the repost, comment, and reply relations extracted from the posts.

The accounts are the ones POSIM initialises its agents from: each account becomes one agent, and its posts provide the agent's history and the real activity that simulations are scored against. The full crawl from which these accounts were selected is much larger. It is described in [FULL_CRAWL.md](FULL_CRAWL.md).

## Directory layout

```
datasets/
├── README.md
├── FULL_CRAWL.md            # the complete crawl (4.52M records) and how to obtain it
├── LE/
│   ├── events.jsonl         # event timeline
│   ├── users.jsonl.gz       # accounts
│   ├── posts.jsonl.gz       # original posts, reposts, comments
│   ├── interactions.csv.gz  # repost / comment / reply relations
│   └── network.csv.gz       # relationship network used as simulation input
├── WL/   (same files)
└── XF/   (same files)
```

All files are UTF-8. `.jsonl` files hold one JSON object per line, and `.gz` files are gzip-compressed.

## Statistics

| | LE | WL | XF | Total |
|---|---:|---:|---:|---:|
| Accounts | 1,530 | 1,843 | 1,987 | 5,360 |
| Original posts | 4,961 | 3,792 | 5,926 | 14,679 |
| Reposts | 19,018 | 17,168 | 12,423 | 48,609 |
| Comments | 81,994 | 64,090 | 11,525 | 157,609 |
| **Posts (all types)** | **105,973** | **85,050** | **29,874** | **220,897** |
| Interaction relations | 101,012 | 81,243 | 23,947 | 206,202 |
| Accounts reached by interactions | 25,024 | 20,210 | 7,909 | — |
| Event timeline entries | 40 | 17 | 18 | 75 |
| First / last post | 2025-05-07 / 2025-07-31 | 2025-06-03 / 2025-09-23 | 2025-09-10 / 2025-09-23 | — |

Notes:

- 190 accounts take part in more than one crisis (177 in two, 13 in all three), so the three datasets together contain 5,157 distinct accounts. Because pseudonyms are consistent across events (see below), these accounts can be linked between datasets.
- Across all files, 57,872 distinct accounts appear (as posters, repost sources, commented-post authors, or reply targets).
- Posts cover the whole collected activity of each account, including activity before and after the simulated window. This is the history that agent initialisation draws on.

## File schemas

### `events.jsonl`: event timeline

| Field | Type | Description |
|---|---|---|
| `event_id` | str | `<CODE>-E<nn>`, in chronological order |
| `time` | str | time the development became public (`YYYY-MM-DDTHH:MM`, UTC+8) |
| `event_type` | str | `external_development` (news, official statement, etc.) or `key_post` (an influential post inside the network) |
| `topic` | str | short title of the development |
| `content` | str | description of the development |
| `influence` | float | relative salience in [0, 1] |
| `storyline` | str | the storyline of the crisis this development belongs to |
| `tags` | list[str] | Weibo hashtags associated with the development |
| `trigger_type` | str \| null | for `key_post`: kind of trigger (e.g. 媒体报道 media report, 意见领袖发声 opinion leader, 官方回应 official response, 爆料 disclosure) |
| `source_user_id` | str \| null | for `key_post`: pseudonymous ID of the posting account |
| `source_post_id` | str \| null | for `key_post`: pseudonymous ID of the post |
| `source_post_time` | str \| null | for `key_post`: publication time of the post |
| `source_post_metrics` | object \| null | for `key_post`: `repost_count`, `comment_count`, `like_count` |

### `users.jsonl.gz`: accounts

| Field | Type | Description |
|---|---|---|
| `user_id` | str | pseudonymous account ID (`U` + 16 hex characters) |
| `screen_name` | str \| null | retained only for institutional accounts (media, government, organisation, enterprise); `null` for individuals |
| `verified_type` | str | Weibo verification type, e.g. 普通用户 (unverified), 个人认证-橙V / 金V (verified individual), 机构认证-媒体 / 政府 / 团体 (verified institution), 企业认证 (enterprise) |
| `role` | str | agent role used in POSIM: `citizen`, `kol`, `media`, or `government` |
| `gender` | str \| null | 男 / 女 as declared on the profile |
| `location` | str \| null | declared region (province level) |
| `register_location` | str \| null | registration region (province level) |
| `register_year` | int \| null | year of registration (the full timestamp is removed) |
| `followers_count`, `following_count`, `posts_count` | int | profile counters at collection time |
| `description` | str \| null | profile description, after text scrubbing |
| `n_original`, `n_repost`, `n_comment` | int | number of posts of each type in `posts.jsonl.gz` |

### `posts.jsonl.gz`: full-chain posts

Fields shared by all post types:

| Field | Type | Description |
|---|---|---|
| `post_id` | str | pseudonymous ID: `P…` for original posts and reposts, `C…` for comments |
| `user_id` | str | pseudonymous ID of the author |
| `type` | str | `original`, `repost`, or `comment` |
| `time` | str | publication time (`YYYY-MM-DD HH:MM:SS`, UTC+8) |
| `content` | str | text, after text scrubbing; for reposts, the reposter's own comment |
| `platform_emotion` | str \| null | emotion label provided by the data platform (e.g. 中性, 愤怒) |
| `matched_keywords` | list[str] | crisis keywords the post matched during collection |

Additional fields by type:

| Type | Field | Description |
|---|---|---|
| `original` | `like_count`, `repost_count`, `comment_count` | engagement counters |
| `repost` | `root_post_id` | ID of the root original post, when it is also in this file (otherwise `null`) |
| | `root_user_id`, `root_time`, `root_content` | author, time, and text of the root post |
| | `repost_chain` | the intermediate reposts from the root to this repost: list of `{user_id, content, level}`, with level 0 the root |
| `comment` | `level` | 1 = comment on the post; 2 and above = reply within the comment thread |
| | `parent_post_id`, `parent_user_id`, `parent_content` | the commented post (`parent_post_id` uses the same ID scheme as `post_id`) |
| | `replied_to_user_id`, `replied_to_content` | for replies: the account and comment being replied to |

### `interactions.csv.gz`: interaction relations

| Column | Description |
|---|---|
| `source_user_id` | the acting account |
| `target_user_id` | the account acted on |
| `interaction_type` | `repost` (source reposted a post by target), `comment` (source commented on a post by target), or `reply` (source replied to target's comment) |
| `time` | time of the interaction |
| `post_id` | the repost or comment that carries the interaction (joins to `posts.jsonl.gz`) |

Self-relations (an account reposting or commenting on its own post) are kept as observed.

### `network.csv.gz`: simulation input network

The directed relationship network among the accounts, which defines the relationship exposure channel of the simulation (`source_user_id` receives posts of `target_user_id`). It is generated from account attributes as described in the paper (Section 5.1), and is provided so that runs can be reproduced.

## De-identification

All data come from public Sina Weibo posts and profiles. Before release we applied the following:

1. **Account pseudonymisation.** Platform account IDs and screen names are replaced by keyed-hash pseudonyms (HMAC-SHA256 with a secret key that is not released). The same account receives the same pseudonym in every file and every crisis, so the interaction structure is preserved. Accounts known only by screen name, such as authors of root posts outside the collected set, receive an `N…` pseudonym derived in the same way.
2. **Screen names.** Screen names of individual accounts are removed. Screen names are retained only for institutional accounts (media, government, organisations, enterprises), whose identity is part of the public record of the crisis.
3. **Post identifiers.** Post URLs, which embed account IDs and post IDs, are removed and replaced by keyed-hash post IDs.
4. **Text scrubbing.** In every text field (post content, root/parent content, repost chains, profile descriptions, event descriptions):
   - `@mentions` of individual accounts → `@用户`;
   - URLs and short links → `[链接]`;
   - mobile phone numbers → `[电话]`, and 18-digit ID numbers → `[证件号]`;
   - individual screen names written out in the text → `[用户]`, and an account's own screen name in its description → `[昵称]`;
   - platform account IDs written out in the text → `[ID]`.
5. **Profile coarsening.** Registration time is reduced to year. Location fields are at province level. Profile descriptions are kept after scrubbing.

Names of public figures and organisations that are the subject of a crisis are left in the text, because the discussion cannot be understood without them.

## Loading example

```python
import gzip, json
import pandas as pd

event = "XF"
users = pd.read_json(f"datasets/{event}/users.jsonl.gz", lines=True)
posts = pd.read_json(f"datasets/{event}/posts.jsonl.gz", lines=True)
events = pd.read_json(f"datasets/{event}/events.jsonl", lines=True)
edges = pd.read_csv(f"datasets/{event}/interactions.csv.gz")

print(posts["type"].value_counts())
```

## Terms of use

The datasets are released for non-commercial academic research only. By using them, you agree:

- not to attempt to re-identify any individual, including by searching post texts on the platform;
- not to redistribute the data outside these terms;
- to use the data in accordance with the Sina Weibo terms of service and applicable personal-information protection law.

If you use the datasets, please cite the POSIM paper. Requests to remove specific content can be sent to the authors through the issue tracker of this repository.
