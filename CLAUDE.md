# Queue rules (read by every agent that writes here)

Format of `posts/<YYYY-MM-DD-HHMM-slug>/post.json` (the folder name sorts by publishing time, Damascus time):
```json
{ "id": "2026-10-26-1000-registration-open",
  "at": "2026-10-26T10:00:00+03:00",
  "targets": ["telegram:ar", "telegram:en", "facebook", "x", "youtube"],
  "text": { "ar": "...", "en": "..." },
  "media": "card.png",
  "media_type": "photo",
  "pin": false }
```
- Folder name exactly `YYYY-MM-DD-HHMM-slug`, slug in lower-case a-z, 0-9 and `-` only. Anything else is rejected by the publisher.
- `media` is a plain file name in the same folder (letters, digits, `-` or `_`, ending in `.png`, `.jpg`, `.jpeg` or `.mp4`; no `/`, no `..`) or null; PNG/JPG under 5 MB, MP4 under 20 MB; `media_type` must match (`photo` for png/jpg, `video` for mp4). `text` holds only `ar` and `en` strings (each at most 4000 characters), `x` at most 280. `youtube` is postponed by the owner: do not use it.
- Telegram posts go only to channels the owner approved; a long caption (over 1024 characters) is sent as the image followed by the text.
- Arabic first. Facebook gets both languages in one post; X gets Arabic (≤ 280 characters: keep `text.ar` short or add `"x": "..."`).
- Red lines (enforced in code by the publisher, social/src/redlines.js in jana1234149/matrix-exchange): no profit promises,
  no price talk or buy/sell advice (MTIX included), no wallet addresses, no requests for passwords/codes/keys, no links
  or @accounts except matrixcex.com, info@matrixgroups.net, @MatrixCex_bot and the official pages. Facts only from
  social/kb/kb.md in jana1234149/matrix-exchange: never invent dates, prizes, fees, partners or features.
- A sentence that mentions passwords/codes/keys/recovery phrases, any price, or MTIX is published ONLY if it is copied
  word for word from social/kb/answers.md (or kb.md) in jana1234149/matrix-exchange; any new wording on these subjects is
  blocked. Do not write prices at all, and for security notices or MTIX copy the approved sentence (e.g. the SECURITY,
  MTIX and MTIX-SCAM answers).
- A post that mentions passwords/codes/keys, any price, MTIX or buying/selling a coin ANYWHERE must be made ONLY of approved
  sentences (copied word for word) plus emoji and official links (no numbers or money signs on their own lines):
  one new sentence anywhere blocks the whole post. Never put a coin name next to an amount.
- A post that has started publishing is never re-sent after an edit: to correct a published post, make a NEW folder.
  Deleting a started folder cancels whatever it has not sent yet.
- Every contest post ends with: «المسابقة تعليمية تجريبية وليست نصيحة استثمارية» / "An educational demo contest, not investment advice."
- `published-cloud.json` records what Claude published to X and YouTube: `{ "<folder>": { "x": "<url or error>", "youtube": "..." } }`.
- Never delete or rewrite a post whose time has passed.
