
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
    "rank": 1,
    "appearances": 3934,
    "score": 100.0,
    "author_first": "William",
    "author_middle": "A.",
    "author_last": "Strunk",
  },
  {
    "title": "Biology",
    "pub_year": 1987,
    "rank": 2,
    "appearances": 3057,
    "score": 97.2,
    "author_first": "Neil",
    "author_middle": null,
    "author_last": "Cambell",
  },
  {
    "title": "Frankenstein",
    "pub_year": 1818,
    "rank": 3,
    "appearances": 2320,
    "score": 95.0,
    "author_first": "Mary",
    "author_middle": "Wollstonecraft",
    "author_last": "Shelley",
  },
]
```

### `/api/authors`

This endpoint provides lists of authors, ranked by the number of times their texts are assigned in the corpus.

### Parameters

- `institution` (int) - Match authors that were assigned in syllabi at a given institution, identified by ID.
  - `/api/authors?institution=1`
  - `/api/authors?institution=1&institution=2`

- `field` (int) - Match authors that were assigned in syllabi in a given institution, identified by ID.
  - `/api/authors?field=1`
  - `/api/authors?field=1&field=2`

- `country` (int) - Match authors that were assigned at institutions in a given country, identified by 3-letter ISO 3166-1 codes.
  - `/api/authors?country=USA`
  - `/api/authors?country=USA&country=ARG`

- `query` (str) - A free-text search query, which gets looked up against the index of author names.
  - `/api/authors?query=Hemingway`

### Format

```json
[
  {
    "name_first": "Mark",
    "name_middle": null,
    "name_last": "Twain",
    "rank": 1,
    "appearances": 4400,
    "text_count": 20,
  },
  {
    "name_first": "Mary",
    "name_middle": "Wollstonecraft",
    "name_last": "Shelley",
    "rank": 2,
    "appearances": 2000,
    "text_count": 13,
  },
  {
    "name_first": "William",
    "name_middle": "A.",
    "name_last": "Strunk",
    "rank": 3,
    "appearances": 1000,
    "text_count": 10,
  },
]
```

### `/api/institutions`

This endpoint provides lists of institutions, ranked by number of syllabi.

### Parameters

- `field` (int) - Match institutions with syllabi in one or more fields, identified by ID.
  - `/api/institutions?field=1`
  - `/api/institutions?field=1&field=2`

- `country` (int) - Match institutions in a given country, identified by 3-letter ISO 3166-1 codes.
  - `/api/institutions?country=USA`
  - `/api/institutions?country=USA&country=ARG`

- `query` (str) - A free-text search query, which gets looked up against the index of institution names.
  - `/api/institutions?query=Yale`

### Format

```json
[
  {
    "name": "Yale University",
    "country": "USA",
    "rank": 1,
    "syllabus_count": 20000,
  },
  {
    "name": "Stanford University",
    "country": "USA",
    "rank": 2,
    "syllabus_count": 19000,
  },
  {
    "name": "Harvard University",
    "country": "USA",
    "rank": 3,
    "syllabus_count": 18000,
  },
]
```

### `/api/publishers`

This endpoint provides lists of publishers, ranked by the number of times their books / articles are assigned in syllabi.

### Parameters

- `field` (int) - Match publishers with texts assigned in syllabi in one or more fields, identified by ID.
  - `/api/publishers?field=1`
  - `/api/publishers?field=1&field=2`

- `country` (int) - Match publishers in a given country, identified by 3-letter ISO 3166-1 codes.
  - `/api/publishers?country=USA`
  - `/api/publishers?country=USA&country=ARG`

- `query` (str) - A free-text search query, which gets looked up against the index of publisher names.
  - `/api/publishers?query=Cengage`

- `pub_year_start` (int) - Match publishers with texts that were published during or after the provided year.
  - `/api/publishers?pub_year_start=1900`

- `pub_year_end` (int) - Match publishers with texts that were published during or before the provided year.
  - `/api/publishers?pub_year_end=2000`

- `class_year_start` (int) - Match publishters texts that were assigned in classes during or after the provided year.
  - `/api/publishers?class_year_start=2000`

- `class_year_start` (int) - Match publishers with texts that were assigned in classes during or after the provided year.
  - `/api/publishers?class_year_end=2005`

### Format

```json
[
  {
    "name": "Elsevier",
    "rank": 1,
    "assignment_count": 125000,
    "text_count": 4500,
  },
  {
    "name": "Cengage",
    "rank": 2,
    "assignment_count": 110000,
    "text_count": 3000,
  },
  {
    "name": "MacMillan",
    "rank": 3,
    "assignment_count": 100000,
    "text_count": 2000,
  },
]
```

### `/api/fields`

This endpoint provides lists of fields, ranked by number of syllabi.

### Parameters

- `country` (int) - Match fields with syllabi assigned in a given country, identified by 3-letter ISO 3166-1 codes.
  - `/api/fields?country=USA`
  - `/api/fields?country=USA&country=ARG`

- `query` (str) - A free-text search query, which gets looked up against the index of field names.
  - `/api/institutions?query=English`

### Format

```json
[
  {
    "name": "History",
    "rank": 1,
    "syllabus_count": 20000,
  },
  {
    "name": "English",
    "rank": 2,
    "syllabus_count": 19000,
  },
  {
    "name": "Computer Science",
    "rank": 3,
    "syllabus_count": 18000,
  },
]
```
