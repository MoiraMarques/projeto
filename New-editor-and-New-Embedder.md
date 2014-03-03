#### Make the new editor the primary editor, and use the new embedder on amara.org
*(while maintaining the beta editor for fallback.)*

- **Saving issues** (Ben)
  - ~~[#1138](https://github.com/pculture/unisubs/issues/1138), saving a backup copy each minute~~
  - ~~[#751](https://github.com/pculture/unisubs/issues/751), save local copy on server save failure, Filesaver.js~~

- **Help** (Sylvain)
  - ~~[#514](https://github.com/pculture/unisubs/issues/514) Implement the new instructions design~~
  - ~~[#780](https://github.com/pculture/unisubs/issues/780) (Don't need all the shortcuts implemented now, but the Keyboard shortcuts section display changes)~~

- **Support for various embeds** (Sylvain)
  - ~~Brightcove [#1125](https://github.com/pculture/unisubs/issues/1125)~~
  - ~~support flv videos, [#1171](https://github.com/pculture/unisubs/issues/1171)~~
  - ~~mp3~~ (works)
  - ~~html5 video~~ (ogg, ogv, webm, mp4) (works)
  - Handling for embeds not supported in new editor [#548](https://github.com/pculture/unisubs/issues/548)
    -   - Dailymotion [#1241](https://github.com/pculture/unisubs/issues/1241) moving it down here, there's currently no support in popcorn player, so well want to direct users to the old editor for now.
    - Wistia - not critical if hard, there's an easy way to get mp4 urls for wistia vidoes.

- **Implement existing functionality from Old Editor** (Sylvain)
  - ~~[#785](https://github.com/pculture/unisubs/issues/785) Shift-tab key for skip back~~ in gh-780 branch.
  - [#1043](https://github.com/pculture/unisubs/issues/1043) Reset button (to clear subtitles, or timings)
  - [#1274](https://github.com/pculture/unisubs/issues/1274)  - Team Guidelines display

- **Update all the dialogs that open the Old editor** [#1121](https://github.com/pculture/unisubs/issues/1121) Refactor open edit dialog code (Ben) *This is mostly done, but a few tickets in the other bugs sections are also related to this branch.  This is the last thing we want to merge to do the switchover*
 - ~~Video page links~~
 - ~~Video language page links~~
 - Teams pages:
    - ~~Dashboard tasks~~
    - ~~Tasks page tasks~~
 - ~~Widget embed menu~~
 - ~~site and email task notifications (perform task link)~~
 - ~~[#807](https://github.com/pculture/unisubs/issues/807) base-language argument ignored when opening new editor~~ (Ben)

- **Other bugs**
  - [#1198](https://github.com/pculture/unisubs/issues/1198) - All lines are synced message (Ben: partially in gh-1121 branch).
  - ~~[#1195](https://github.com/pculture/unisubs/issues/1195) quotes, apostrophes etc. get escaped (Ben)~~
  - [#1239](https://github.com/pculture/unisubs/issues/1239) Making dialog text and buttons consistent with each other.
  - ~~[#1256](https://github.com/pculture/unisubs/issues/1256) Possible to Approve incomplete subtitles~~
  - ~~[#1255](https://github.com/pculture/unisubs/issues/1255) Update wording for the guided step 2 in new~~ editor

- **Embedder-specific changes needed** (Sylvain)
  - ~~[#1208](https://github.com/pculture/unisubs/issues/1208) - playback issues when same html5 video open in embedder and new editor.~~

- **Nice to haves**
  - [#784](https://github.com/pculture/unisubs/issues/784)  Auto-pause options (typing modes)
  - [#779](https://github.com/pculture/unisubs/issues/779) working / reference alignment with long lines.
  - [#995](https://github.com/pculture/unisubs/issues/995), timestamp rounding error (Sylvain)
  - [#1273](https://github.com/pculture/unisubs/issues/1273) - More shortcuts links for complete list.
  

- **Post New-editor switchover**
  - Change the default embed code on the Video and video language pages
  - Verify existing embeds using the old widget are not broken.
