#### Make the new editor the primary editor, and use the new embedder on amara.org
*(while maintaining the beta editor for fallback.)*

- **Saving issues**
  - [#1147](https://github.com/pculture/unisubs/issues/1147) Refactor saving things
  - [#1138](https://github.com/pculture/unisubs/issues/1138), saving a backup copy each minute
  - [#751](https://github.com/pculture/unisubs/issues/751), save local copy on server save failure, Filesaver.js

- **Help**
  - [#514](https://github.com/pculture/unisubs/issues/514) Implement the new instructions design

- **Support for various embeds**
  - Brightcove [#1125](https://github.com/pculture/unisubs/issues/1125) (almost done)
  - support flv videos, [#1171](https://github.com/pculture/unisubs/issues/1171)
  - Dailymotion
  - Wistia
  - Handling for embeds not supported in new editor [#548](https://github.com/pculture/unisubs/issues/548)

- **Implement existing functionality from Old Editor**
  - [#785](https://github.com/pculture/unisubs/issues/785) Shift-tab key for skip back
  - [#1043](https://github.com/pculture/unisubs/issues/1043) Reset button (to clear subtitles, or timings)
  - [#784](https://github.com/pculture/unisubs/issues/784)  Auto-pause options (typing modes)

- **Update all the dialogs that open the Old editor**
 - Video page links
 - Video language page links
 - Teams pages:
    - Dashboard tasks
    - Tasks page tasks
 - Widget embed menu (**Skipable, but see Embedder-specific notes below)
 - Upload subtitles dialog (*I think it relies on old widget menus*) We should implement [#993](https://github.com/pculture/unisubs/issues/993) Upload versions directly to the new editor.

- **Create new dialogs for setting the Primary Audio Language and choose language to Translate**
  - [#723](https://github.com/pculture/unisubs/issues/723) Selecting the initial reference language
  - [#807](https://github.com/pculture/unisubs/issues/807) base-language argument ignored when opening new editor

- **Other bugs**
  - [#995](https://github.com/pculture/unisubs/issues/995), timestamp rounding error
  - [#1141](https://github.com/pculture/unisubs/issues/1141), subs freezing in safari on osx

- **Embedder-specific changes needed**
  - Currently the *Improve these subtitles* menu item points to the video page. Could either change default to opening the subtitle editor, or have an amara-specific default setting.
  - Change the default embed code on the Video and video language pages
  - Verify existing embeds using the old widget are not broken.

