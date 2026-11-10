# paws-ms-assets
Stored assets for paws-ms-* projects (the paws.ms site and the Paws Discord bot).

## Layout

```
gms/
  classes/<class>/     one folder per GMS class (config.MAPLESTORY_CLASS_CHOICES on the site)
  class-links.toml     each GMS class's shared buttons: its Discord, class docs, sites
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

Use lowercase file names without spaces too (e.g. `overview.png`). Empty folders hold a `.gitkeep` so git keeps them;
it can be deleted once the folder has a real file.

When a class is added to the site's config, add its folder here.

## Class guides (`/class`)

paws.ms serves this repo at `/assets/` (a rewrite in the site's vercel.json), so a file at
`gms/classes/hero/overview.png` is `https://paws.ms/assets/gms/classes/hero/overview.png`.

The Classes editor on the site's Bot Commands page fills these links in, so adding a file here is usually all it
takes:

| What | File | Link the editor fills in |
|------|------|--------------------------|
| Image | `<class>/overview.png` | `https://paws.ms/assets/gms/classes/hero/overview.png` |
| Any other image, e.g. `hexa.png` | `<class>/<name>.png` / `.gif` / `.jpg` / `.webp` | a button named after the file ("Hexa"; `boss-guide.png` is "Boss Guide"), Origin and Ascent first; with no `overview.png`, `origin.gif` is the image instead |
| Thumbnail (top right of `/class`) | `<class>/avatar.png` | none: always this file, left out until it exists |
| A link button, e.g. "Bossing" | `<class>/<button name>.png` | `https://paws.ms/assets/gms/classes/hero/bossing.png` |
| Shared buttons (Discord, class doc) | `gms/class-links.toml` | none: `/class` adds them itself, first |

Button names become file names the same way class names become folders ("Boss Guide" → `boss-guide.png`).

`class-links.toml` has one section per class, named exactly as the site spells it, with one `Label = "link"` line
per button in the order they show (quote a name with spaces; `#` starts a note):

```toml
["Night Lord"]
# Discord: apply with your Night Lord and wait for manual approval
Discord = "https://discord.gg/AvP8wq4"
"Class Doc" = "https://docs.google.com/document/d/..."
```

The site reads it only when the bot asks for a class guide, keeping it for an hour, so an edit shows up within the
hour, or straight away after "Check paws-ms-assets" on the Classes editor. A mistake in the file (a missing quote, a
class listed twice) stops it loading: `/class` then shows only each guide's saved links until it's fixed.

Replacing a file under the same name updates every embed that uses it (Discord may show the old image for a
while from its cache; a new file name avoids that).

## Credits

Most class infographics (`overview.png`, `hexa.png`, `hexa-<variant>.png`, `culvert.png`, `sequence.png`) and the Origin / Ascent skill
animations (`origin.gif`, `ascent.gif`) come from [Grandis Library](https://grandislibrary.com)
([source](https://github.com/ikasuu/grandislibrary-next)), licensed under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). They are renamed to fit this repo's layout and
otherwise unchanged. Keep this credit if you add more from there. MapleStory and its game art belong to Nexon.
