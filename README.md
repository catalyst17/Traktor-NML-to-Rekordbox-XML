# Traktor-NML-to-Rekordbox-XML

> ## Access the [online tool](https://segolene-albouy.github.io/Traktor-NML-to-Rekordbox-XML/) 🌍

Python script to convert your playlists from Traktor NML to Rekordbox XML and vice versa.
It keeps:

- [x] Hot Cues (with names)
- [x] Saved loops (with names)
- [x] Track color
- [x] Playtime
- [x] Genre / Artist / Title / Music tonality / etc.
- [x] Pad order of Hots Cues and Loops
- [x] Flexible beatgrid
- [x] Rekordbox XML <=> Traktor NML
- [x] Playlist tree-structure
- [x] Tracklist cue point analysis
- [x] **Custom map for Cues and Tracks colors** ✨ NEW
- [x] **Configurable color mappings via JSON** ✨ NEW

### To be added

- [ ] Custom loop length for Traktor

## How to

### Traktor to Rekordbox
1. Export your playlist in Traktor in NML (Right-click on the playlist > Export Playlist > NML)
2. `python nml_to_rekord.py <path/to/your/collection>.nml`
3. Open Rekordbox > Preferences > View > Layout > Tree View > Check rekordbox xml
4. Preferences > Advanced > Database > rekordbox xml > Imported Library > Select `<outputed_collection>.rekordbox.xml`
5. In the sidebar of Rekordbox should appear a `rekordbox xml` section > All tracks
6. Tada! 🎉

### Rekordbox to Traktor
1. In Rekordbox, export your collection: File > Export Collection in xml format > Pick any location
2. `python rekord_to_nml.py <path/to/your/collection>.xml`
3. Open Traktor > Right-click on the Playlists > Import Playlist > Choose the `<outputed_collection>.nml` file
4. Tada! 🥳

## ✨ Custom Color Mappings (NEW)

You can now customize how colors are mapped between Traktor and Rekordbox!

### Quick Start

```bash
# Use default colors (automatic)
python nml_to_rekord.py collection.nml

# Use custom color config
python nml_to_rekord.py collection.nml --color-config my_colors.json
```

### Creating Custom Color Mappings

1. Copy `color_config.json` to `my_colors.json`
2. Edit the `_customMappings` section:

```json
{
  "_customMappings": {
    "example_trackColors": {
      "8": "0x808080",
      "9": "0x000000"
    },
    "example_cueColors": {
      "mycolor": { "R": 128, "G": 128, "B": 128 }
    }
  }
}
```

3. Use your config: `python nml_to_rekord.py collection.nml -c my_colors.json`

### What You Can Customize

- **Track Colors**: RGB hex values for Traktor color numbers
- **Cue Point Colors**: Named color palette (pink, blue, green, etc.)
- **Semantic Mappings**: Map cue names like "intro", "drop", "outro" to colors
- **RGB to Cue Type**: Map specific RGB values to Traktor cue types

See `color_config.json` for full documentation and examples.

## Links
- [Traktor NML utils library](https://pypi.org/project/traktor-nml-utils/)
- [Rekordbox XML schema](https://cdn.rekordbox.com/files/20200410160904/xml_format_list.pdf)
- [TraktorBox library](https://github.com/nonodesbois42/TraktorBox/tree/main)
