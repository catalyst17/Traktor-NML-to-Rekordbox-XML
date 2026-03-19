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
- [x] **Custom loop length for Traktor** ✨ NEW

### To be added

- [ ] Custom map for Cues and Tracks colors

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

## ✨ Custom Loop Lengths (NEW)

Transform loop lengths during Rekordbox → Traktor conversion!

### Quick Start

```bash
# Default (no transformation)
python rekord_to_nml.py collection.xml

# With custom loop config (when enabled in loop_config.json)
# Just place loop_config.json in the same directory
```

### Configuration

Edit `loop_config.json` and set `"enabled": true`:

#### Double All Loops
```json
{
  "loopLengthMappings": {
    "enabled": true,
    "customRules": {
      "multiplyAll": 2
    }
  }
}
```

#### Specific Bar Mappings
```json
{
  "loopLengthMappings": {
    "enabled": true,
    "barMappings": {
      "mappings": {
        "4": 8,
        "8": 16
      }
    }
  }
}
```

#### Beat-Based Precision
```json
{
  "loopLengthMappings": {
    "enabled": true,
    "beatMappings": {
      "mappings": {
        "16": 32,
        "32": 64
      }
    }
  }
}
```

### Features
- **Bar mappings**: Transform by musical bars (4→8, 8→16)
- **Beat mappings**: Precise beat-level control
- **Global rules**: Double or halve ALL loops
- **BPM-aware**: Automatically calculates based on track tempo
- **Disabled by default**: No changes unless you enable it

See `loop_config.json` for full documentation and examples.

## Links
- [Traktor NML utils library](https://pypi.org/project/traktor-nml-utils/)
- [Rekordbox XML schema](https://cdn.rekordbox.com/files/20200410160904/xml_format_list.pdf)
- [TraktorBox library](https://github.com/nonodesbois42/TraktorBox/tree/main)
