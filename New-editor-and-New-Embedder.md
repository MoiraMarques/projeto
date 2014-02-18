#### Make the new editor the primary editor, and use the new embedder on amara.org
*(while maintaining the beta editor for fallback.)*

- **Saving issues** (Ben)
  - [#1138](https://github.com/pculture/unisubs/issues/1138), saving a backup copy each minute
  - ~~[#751](https://github.com/pculture/unisubs/issues/751), save local copy on server save failure, Filesaver.js~~

- **Help** (Sylvain)
  - [#514](https://github.com/pculture/unisubs/issues/514) Implement the new instructions design

- **Support for various embeds** (Sylvain)
  - ~~Brightcove [#1125](https://github.com/pculture/unisubs/issues/1125)~~
  - support flv videos, [#1171](https://github.com/pculture/unisubs/issues/1171)
  - Dailymotion
  - Wistia
  - Kaltura (new feature)
  - ~~mp3~~ (works)
  - ~~html5 video~~ (ogg, ogv, webm, mp4) (works)
  - Handling for embeds not supported in new editor [#548](https://github.com/pculture/unisubs/issues/548)

- **Implement existing functionality from Old Editor** (Sylvain)
  - [#785](https://github.com/pculture/unisubs/issues/785) Shift-tab key for skip back
  - [#1043](https://github.com/pculture/unisubs/issues/1043) Reset button (to clear subtitles, or timings)
  - [#784](https://github.com/pculture/unisubs/issues/784)  Auto-pause options (typing modes)

- **Update all the dialogs that open the Old editor** [#1121](https://github.com/pculture/unisubs/issues/1121) Refactor open edit dialog code (Ben)
 - Video page links
 - Video language page links
 - Teams pages:
    - Dashboard tasks
    - Tasks page tasks
 - Widget embed menu (**Skipable, but see Embedder-specific notes below)
 - site and email task notifications (perform task link)
 
 - [#807](https://github.com/pculture/unisubs/issues/807) base-language argument ignored when opening new editor (Ben)

- **Other bugs**
  - [#1198](https://github.com/pculture/unisubs/issues/1198) - All lines are synced message
  - [#995](https://github.com/pculture/unisubs/issues/995), timestamp rounding error (Sylvain)
  - ~~[#1195](https://github.com/pculture/unisubs/issues/1195) quotes, apostrophes etc. get escaped (Ben)~~
- **Nice to haves**
- [#993](https://github.com/pculture/unisubs/issues/993) Upload versions directly to the new editor.
- **Embedder-specific changes needed** (Sylvain)
  - Change the default embed code on the Video and video language pages
  - Verify existing embeds using the old widget are not broken.

