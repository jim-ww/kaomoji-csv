# kaomoji

96,225 kaomoji, tagged in English and Japanese/romaji, for use with rofi
or any picker reading a flat `character<space>tags` file.

## Format

```
<kaomoji> <tag1,tag2,...>
```

Spaces inside a kaomoji are encoded as U+00A0 (non-breaking space) to keep
the field boundary unambiguous.

## Sources

- [kaomoji-collection](https://github.com/kaomojiya-collection/kaomoji-collection)
  (~36k, MIT) — from kaomojiya.org, romaji category tags
- [emoticon_kaomoji_dataset](https://github.com/ekohrt/emoticon_kaomoji_dataset)
  (~62k, MIT) — English tags

## How it was built

- Translated all 535 kaomoji-collection romaji categories to English by hand
- Merged both datasets, unioning tags on exact kaomoji matches
- Backfilled romaji tags onto English-only entries where a tag matched a
  known translation
- Fixed unescaped HTML entities (`&gt;` → `>` etc.) left over from scraping

## Usage

```sh
rofi -dmenu -i -p kaomoji < kaomoji.csv | awk '{print $1}' | sed 's/\xc2\xa0/ /g' | xargs -0 wtype --
```
