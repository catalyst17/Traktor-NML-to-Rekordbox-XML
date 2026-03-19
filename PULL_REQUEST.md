# Pull Request: Custom Color Mapping System

## Summary

Added a flexible custom color mapping system that allows users to configure how colors are converted between Traktor and Rekordbox.

## What's New

### ✅ Feature: Custom Color Configuration

- **New File**: `color_config.json` - Comprehensive color mapping configuration
- **CLI Parameter**: `--color-config` / `-c` to load custom configs
- **Automatic Loading**: Uses `color_config.json` if present in script directory
- **Fully Backwards Compatible**: Works with defaults if no config provided

### 🎨 What Can Be Customized

1. **Track Colors** - RGB hex values for Traktor color numbers (1-7+)
2. **Cue Point Colors** - Named palette (pink, blue, cyan, etc.)
3. **Semantic Mappings** - Map cue names ("intro", "drop", "outro") to colors
4. **RGB to Cue Type** - Map specific RGB values to Traktor cue types (hotcue, loop, etc.)

## Technical Details

### Files Modified

1. **`utils.py`**
   - Added `load_custom_color_config()` - Loads and caches JSON config
   - Added `get_custom_track_color_map()` - Merges custom track colors
   - Added `get_custom_cue_colors()` - Merges custom cue palette
   - Added `get_custom_rgb_to_cue_type()` - Custom RGB→type mappings
   - Added `get_custom_semantic_mapping()` - Custom name→color mappings
   - Updated color functions to use custom configs

2. **`nml_to_rekord.py`**
   - Added argparse CLI with `--color-config` parameter
   - Improved error handling and user feedback
   - Better help text and examples

3. **`README.md`**
   - Documented custom color mapping feature
   - Added usage examples
   - Updated feature checklist

### Files Added

1. **`color_config.json`** - Example configuration with:
   - Full default color mappings
   - Documentation for each section
   - Example custom mappings section
   - JSON schema-style structure

2. **`CONTRIBUTION.md`** - Implementation notes and testing approach

## Usage Examples

```bash
# Default behavior (unchanged)
python nml_to_rekord.py collection.nml

# Use custom colors
python nml_to_rekord.py collection.nml --color-config my_colors.json

# Short form
python nml_to_rekord.py collection.nml -c my_colors.json
```

## Example Custom Config

```json
{
  "_customMappings": {
    "example_trackColors": {
      "8": "0xFFFFFF",
      "9": "0x000000"
    },
    "example_cueColors": {
      "custom": { "R": 100, "G": 200, "B": 150 }
    }
  }
}
```

## Benefits

1. **DJ Workflow Flexibility** - Each DJ can map colors to match their style
2. **Extended Color Palette** - Support colors beyond default 7
3. **Semantic Mapping** - Consistent color coding across libraries ("drop" always pink, etc.)
4. **Future-Proof** - Easy to add new color mappings without code changes
5. **No Breaking Changes** - Fully backwards compatible

## Testing

- ✅ Tested with default config (backwards compatible)
- ✅ Tested with custom track colors
- ✅ Tested with custom cue colors
- ✅ Verified CLI parameter handling
- ✅ Tested semantic cue name mappings
- ✅ Verified RGB distance calculation for closest color matching

## Next Steps

If accepted, the next feature to implement would be:
- **Custom Loop Lengths** - Allow users to specify loop length transformations (e.g., 4-bar → 8-bar)

## Credits

- **Original Repo**: Segolene-Albouy/Traktor-NML-to-Rekordbox-XML
- **Contributors**: Arseny (@ctlst) + OpenClaw AI Assistant
- **Date**: March 19, 2026

---

## Installation & Testing

```bash
# Clone the fork
git clone <your-fork-url>
cd Traktor-NML-to-Rekordbox-XML

# Test with defaults
python nml_to_rekord.py test_playlist.nml

# Test with custom colors
python nml_to_rekord.py test_playlist.nml -c color_config.json
```

## Questions?

Feel free to ask about implementation details, design decisions, or future enhancements!
