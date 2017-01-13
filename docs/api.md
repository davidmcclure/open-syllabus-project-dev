
# JSON API Spec

### `/api/texts`

This endpoint provides lists of texts, ranked the number of times they are assigned in the corpus and cropped down by various filters.

### Parameters

- `pub_year_start` (int) - Match texts that were published during or after the provided year.
  - `/api/texts?pub_year_start=1900`

- `pub_year_end` (int) - Match texts that were published during or before the provided year.
  - `/api/texts?pub_year_end=2000`

- `class_year_start` (int) - Match texts that were assigned in classes during or after the provided year.
  - `/api/texts?class_year_start=2000`

- `class_year_start` (int) - Match texts that were assigned in classes during or after the provided year.
  - `/api/texts?class_year_end=2005`

- `open_access` (bool) - If this parameter is included, just return OA texts. This is just a boolean flag, so no value needs to be provided.
  - `/api/texts?open_access`

- `us_state` (bool) - Match texts that were assigned at US institutions in the provided state, using two-letter postal abbreviations.
  - `/api/texts?us_state=CA`

- `inst_type` (bool) - Match texts that were assigned at institutions of a particular type (eg, "Liberal Arts College"). The types will be identified by integer IDs, which correspond to identifiers on US government datasets.
  - `/api/texts?inst_type=5`

### Format

```json
[
  {
    "title": "The Elements of Style",
    "pub_year": 1920,
    "appearances": 3934,
    "score": 100.0,
    "rank": 1,
    "author_first": "William",
    "author_middle": "A.",
    "author_last": "Strunk",
  },
  {
    "title": "Biology",
    "pub_year": 1987,
    "appearances": 3057,
    "score": 97.2,
    "rank": 2,
    "author_first": "Neil",
    "author_middle": null,
    "author_last": "Cambell",
  },
  {
    "title": "Frankenstein",
    "pub_year": 1818,
    "appearances": 2320,
    "score": 95.0,
    "rank": 3,
    "author_first": "Mary",
    "author_middle": "Wollstonecraft",
    "author_last": "Shelley",
  },
]
```
