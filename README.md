# paws-ms-assets
Stored assets for paws-ms-* projects (the paws.ms site and the Paws Discord bot).

## Layout

```
gms/
  classes/<class>/     one folder per GMS class (config.MAPLESTORY_CLASS_CHOICES on the site)
  bosses/
classic/
  classes/<class>/     MapleStory Classic, 3rd job classes only (no Pirates in Classic yet)
challenger/
  bosses/
```

Class folders are flat, not split by faction or archetype: faction groupings change over time and some classes
span two archetypes, and a flat path keeps every image URL stable.

## Naming

Folder names are the class name in lowercase, spaces become `-`, and `/`, `(` and `)` are dropped:

| Class | Folder |
|-------|--------|
| Hero | `hero` |
| Angelic Buster | `angelic-buster` |
| Arch Mage (F/P) | `arch-mage-fp` |
| F/P Mage (Classic) | `fp-mage` |

Use lowercase file names without spaces too (e.g. `guide.png`). Empty folders hold a `.gitkeep` so git keeps them;
it can be deleted once the folder has a real file.

When a class is added to the site's config, add its folder here.

## Using an image

The repo is public, so Discord can load files straight from GitHub. For a `/class` guide, paste the raw URL into
the class's Image URL on the site's Bot Commands page:

```
https://raw.githubusercontent.com/mirandonguyen/paws-ms-assets/main/gms/classes/hero/guide.png
```

Replacing a file under the same name updates every embed that uses it (Discord may show the old image for a
while from its cache; a new file name avoids that).
