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
- `media` is a file in the same folder (PNG/JPG under 5 MB, MP4 under 20 MB) or null. `youtube` only with a video.
- Arabic first. Facebook gets both languages in one post; X gets Arabic (≤ 280 characters: keep `text.ar` short or add `"x": "..."`).
- Red lines (enforced in code by the publisher, social/src/redlines.js in jana1234149/matrix-exchange): no profit promises,
  no price talk or buy/sell advice (MTIX included), no wallet addresses, no requests for passwords/codes/keys, no links
  or @accounts except matrixcex.com, info@matrixgroups.net, @MatrixCex_bot and the official pages. Facts only from
  social/kb/kb.md in jana1234149/matrix-exchange: never invent dates, prizes, fees, partners or features.
- Every contest post ends with: «المسابقة تعليمية تجريبية وليست نصيحة استثمارية» / "An educational demo contest, not investment advice."
- `published-cloud.json` records what Claude published to X and YouTube: `{ "<folder>": { "x": "<url or error>", "youtube": "..." } }`.
- Never delete or rewrite a post whose time has passed.
