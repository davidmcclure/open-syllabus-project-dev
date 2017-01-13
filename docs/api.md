
# JSON API Spec

### `/api/texts`

This endpoint provides lists of texts, ranked the number of times they are assigned in the corpus.

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

- `inst_type` (int) - Match texts that were assigned at institutions of a particular type (eg, "Liberal Arts College"). The types will be identified by integer IDs, which correspond to identifiers on US government datasets.
  - `/api/texts?inst_type=1`
  - `/api/texts?inst_type=1&inst_type=2`

- `author` (int) - Match texts that were written by an author, identified by ID.
  - `/api/texts?author=1`
  - `/api/texts?author=1&author=2`

- `institution` (int) - Match texts that were assigned in syllabi at a given institution, identified by ID.
  - `/api/texts?institution=1`
  - `/api/texts?institution=1&institution=2`

- `field` (int) - Match texts that were assigned in syllabi in a given institution, identified by ID.
  - `/api/texts?field=1`
  - `/api/texts?field=1&field=2`

- `country` (int) - Match texts that were assigned at institutions in a given country, identified by 3-letter ISO 3166-1 codes.
  - `/api/texts?country=USA`
  - `/api/texts?country=USA&country=ARG`

- `us_state` (str) - Match texts that were assigned at US institutions in the provided state, using two-letter postal abbreviations.
  - `/api/texts?us_state=CA`
  - `/api/texts?us_state=CA&us_state=MA`

- `query` (str) - A free-text search query, which gets looked up against the index of text titles.
  - `/api/texts?query=Republic`

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

### `/api/authors`

This endpoint provides lists of authors, ranked by the number of times their texts are assigned in the corpus.

### Parameters

- `birth_year_start` (int) - Match authors who were born in or after the provided year.
  - `/api/texts?birth_year_start=1900`

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
]
```
