# Contribution: Custom Loop Length & Color Mapping

## Features Added

### 1. Custom Loop Length for Traktor
Allows users to specify custom loop lengths when converting from Rekordbox to Traktor.

### 2. Custom Color Mapping Configuration
Provides a user-configurable color mapping system for both tracks and cue points.

## Implementation Plan

### Feature 1: Custom Loop Lengths
- Add `--loop-length` CLI parameter to `rekord_to_nml.py`
- Support common loop sizes: 1/32, 1/16, 1/8, 1/4, 1/2, 1, 2, 4, 8, 16, 32 bars
- Allow multiple loop lengths to be converted (e.g., all 4-bar loops in Rekordbox → 8-bar loops in Traktor)
- Preserve loop names during conversion

### Feature 2: Custom Color Mapping
- Create `color_config.json` for user-defined mappings
- Support both track colors and cue point colors
- Add validation for RGB values
- Provide example configurations for common DJ workflows
- Add CLI parameter `--color-config` to load custom mappings

## Files to Modify

1. `consts.py` - Add default loop length mappings
2. `rekord_to_nml.py` - Add loop length parameter handling
3. `utils.py` - Add color config loading functions
4. `color_config.json` (new) - Example color mapping configuration
5. `README.md` - Document new features

## Testing Approach

- Test with various loop lengths (edge cases)
- Verify color mappings work with custom RGB values
- Ensure backwards compatibility (no breaking changes)
- Test with real Traktor/Rekordbox collections

---

**Author**: Arseny (ctlst) + OpenClaw AI Assistant
**Date**: March 19, 2026
