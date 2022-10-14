# Seasonal Collections

The `seasonal` Default Metadata File is used to dynamically create seasonal collections based on holidays .

**This file only works with Movie Libraries.**

![](../images/seasonal.png)

## Collections Section 00

| Collection                   |      Key       | Description                                                                 |
|:-----------------------------|:--------------:|:----------------------------------------------------------------------------|
| `Seasonal Collections`       |  `separator`   | [Separator Collection](../separators) to denote the Section of Collections. |
| `🎊 New Year's Day Movies`   |    `years`     | Collection of Movies related to New Year's Day.                             |
| `💘 Valentine's Day Movies`  |  `valentine`   | Collection of Movies related to Valentine's Day.                            |
| `☘ St. Patrick's Day Movies` |   `patrick`    | Collection of Movies related to St. Patrick's Day.                          |
| `🐰 Easter Movies`           |    `easter`    | Collection of Movies related to Easter.                                     |
| `🤱 Mother's Day Movies`     |    `mother`    | Collection of Movies related to Mother's Day.                               |
| `🪖 Memorial Day Movies`     |   `memorial`   | Collection of Movies related to Memorial Day.                               |
| `👨 Father's Day Movies`     |    `father`    | Collection of Movies related to Father's Day.                               |
| `🎆 Independence Day Movies` | `independence` | Collection of Movies related to Independence Day.                           |
| `⚒ Labor Day Movies`         |    `labor`     | Collection of Movies related to Labor Day.                                  |
| `🎃 Halloween Movies`        |  `halloween`   | Collection of Movies related to Halloween.                                  |
| `🦃 Thanksgiving Movies`     | `thanksgiving` | Collection of Movies related to Thanksgiving.                               |
| `🎅 Christmas Movies`        |  `christmas`   | Collection of Movies related to Christmas.                                  |

## Config

The below YAML in your config.yml will create the collections:

```yaml
libraries:
  Movies:
    metadata_path:
      - pmm: seasonal
```

## Template Variables

Template Variables can be used to manipulate the file in various ways to slightly change how it works without having to make your own local copy.

Note that the `templates_variables:` section only needs to be used if you do want to actually change how the defaults work. Any value not specified is its default value if it has one if not it's just ignored.

All [Shared Variables](../variables) are available as well as the additional Variables below which can be used to customize the file.

| Variable                  | Description & Values                                                                                                                                                                                                             |
|:--------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `use_separator`           | **Description:** Turn the [Separator Collection](../separators) off.<br>**Values:** `true` to turn on the collection                                                                                                             |
| `sep_style`               | **Description:** Choose the [Separator Style](../separators.md#separator-styles).<br>**Default:** `orig`<br>**Values:** `orig`, `red`, `blue`, `green`, `gray`, `purple`, or `stb`                                               |
| `tmdb_collection_<<key>>` | **Description:** Adds the TMDb Collection IDs given to the specified key's collection. Overrides the [default tmdb_collection](#default-tmdb_collection) for that collection if used.<br>**Values:** List of TMDb Collection IDs |
| `tmdb_movie_<<key>>`      | **Description:** Adds the TMDb Movie IDs given to the specified key's collection. Overrides the [default tmdb_movie](#default-tmdb_movie) for that collection if used.<br>**Values:** List of TMDb Movie IDs                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `imdb_list_<<key>>`       | **Description:** Adds the Movies in the IMDb List to the specified key's collection. Overrides the [default imdb_list](#default-imdb_list) for that collection if used.<br>**Values:** List of IMDb List URLs                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `trakt_list_<<key>>`      | **Description:** Adds the Movies in the Trakt List to the specified key's collection.<br>**Values:** List of Trakt List URLs                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `emoji`                   | **Description:** Controls the Emoji Prefix for all Collections. Set to `""` to remove all emojis.<br>**Values:** Any String                                                                                                      |
| `emoji_<<key>>`           | **Description:** Controls the Emoji Prefix for the specified key's collection.<br>**Values:** Any String                                                                                                                         |
| `limit`                   | **Description:** Changes the Builder Limit for all collections in this file.<br>**Values:** Number Greater then 0                                                                                                                |
| `limit_<<key>>`           | **Description:** Changes the Builder Limit of the specified key's collection.<br>**Default:** `limit`<br>**Values:** Number Greater then 0                                                                                       |
| `sort_by`                 | **Description:** Changes the Smart Filter Sort for all collections in this file.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../metadata/builders/smart.md#sort-options)                   |
| `sort_by_<<key>>`         | **Description:** Changes the Smart Filter Sort of the specified key's collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../metadata/builders/smart.md#sort-options)                       |
| `schedule`                | **Description:** Changes the Schedule for all collections in this file. Use `daily` to have all collections show.<br>**Values:** [Any Schedule Option](../../metadata/details/schedule)                                          |
| `schedule_<<key>>`        | **Description:** Changes the Schedule of the specified key's collection. Overrides the [default schedule](#default-schedule) for that collection if used.<br>**Values:** [Any Schedule Option](../../metadata/details/schedule)  |
| `data`                    | **Description:** Overrides the [default data dictionary](#default-data). Defines the data that the custom dynamic collection processes.<br>**Values:** Dictionary List of keys/names                                             |
| `append_data`             | **Description:** Appends to the [default data dictionary](#default-data).<br>**Values:** Dictionary List of keys/names                                                                                                           |
| `exclude`                 | **Description:** Exclude these Seasons from creating a Dynamic Collection.<br>**Values:** List of Seasons Keys                                                                                                                   |
| `seasonal_name`           | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>> <<library_translationU>>s`<br>**Values:** Any string with `<<key_name>>` in it.                                              |
| `seasonal_summary`        | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `A collection of <<key_name>> <<library_translation>>s that may relate to the season.`<br>**Values:** Any string.                        |

The below is an example config.yml extract with some Template Variables added in to change how the file works.

```yaml
libraries:
  Movies:
    metadata_path:
      - pmm: seasonal
        template_variables:
          use_separator: true
          sep_style: stb
          use_independence: false
          schedule_thanksgiving: range(10/01-10/30)
          sort_by: random
          # Add a custom holiday
          append_data:
            veteran: Veteran's Day
          schedule_veteran: range(11/01-11/30)
          imdb_list_veteran: https://www.imdb.com/list/ls002014923/
          emoji_veteran: "🪖 "
```

## Default `data`

```yaml
data:
  years: New Year's Day
  valentine: Valentine's Day
  patrick: St. Patrick's Day
  easter: Easter
  mother: Mother's Day
  memorial: Memorial Day
  father: Father's Day
  independence: Independence Day
  labor: Labor Day
  halloween: Halloween
  thanksgiving: Thanksgiving
  christmas: Christmas
```

## Default `tmdb_collection`

```yaml
tmdb_collection:
  halloween:
    - 185103    # Hotel Transylvania
    - 11716     # Addams Family
    - 750822    # Addams Family Animated
    - 313086    # Conjuring
    - 91361     # Halloween Collection
    - 8581      # A Nightmare on Elm Street Collection
    - 1733      # The Mummy Collection
    - 8091      # Alien Collection
    - 2980      # Ghostbusters
    - 751156    # Hocus Pocus
```

## Default `tmdb_movie`

```yaml
tmdb_movie:
  halloween:
    - 23437    # A Nightmare on Elm Street (2010)
```

## Default `imdb_list`

```yaml
imdb_list:
  years: https://www.imdb.com/list/ls066838460/
  valentine:
    - https://www.imdb.com/list/ls000094398/
    - https://www.imdb.com/list/ls057783436/
    - https://www.imdb.com/list/ls064427905/
  patrick: https://www.imdb.com/list/ls063934595/
  easter:
    - https://www.imdb.com/list/ls062665509/
    - https://www.imdb.com/list/ls051733651/
  mother: https://www.imdb.com/list/ls072551197/
  memorial: https://www.imdb.com/list/ls002014923/
  father: https://www.imdb.com/list/ls020471057/
  independence:
    - https://www.imdb.com/list/ls068664510/
    - https://www.imdb.com/list/ls080925875/
  labor: https://www.imdb.com/list/ls002014923/
  halloween:
    - https://www.imdb.com/list/ls023118929/
    - https://www.imdb.com/list/ls000099714/
  thanksgiving:
    - https://www.imdb.com/list/ls000835734/
    - https://www.imdb.com/list/ls091597850/
  christmas: https://www.imdb.com/list/ls000096828/
```

## Default `schedule`

```yaml
schedule:
  years: range(12/26-01/04)
  valentine: range(02/01-02/29)
  patrick: range(03/01-03/18)
  easter: range(03/20-04/30)
  mother: range(05/05-05/10)
  memorial: range(5/18-6/7)
  father: range(06/15-06/20)
  independence: range(06/23-07/11)
  labor: range(09/01-09/10)
  halloween: range(10/01-10/31)
  thanksgiving: range(11/01-11/30)
  christmas: range(12/01-12/31)
```