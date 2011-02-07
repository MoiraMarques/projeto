## Fetching subtitle languages for a video url

The url for fetching subtitles is `http://universalsubtitles.org/en/api/subtitle_existence/?video_url=<VIDEO_URL>`, where `<VIDEO_URL>` is the url for the video.

## Fetching subtitles for a video url

The url for fetching subtitles is `http://universalsubtitles.org/en/api/subtitles/`. Query string parameters are:

<table>
  <tr>
    <td>video_url</td>
    <td>URL for the video</td>
    <td>Required</td>
  </tr>
  <tr>
    <td>language</td>
    <td>Language code</td>
    <td>Optional: defaults to original</td>
  </tr>
  <tr>
    <td>format</td>
    <td>Return text format. Valid values are "json", "srt", "sbv", "ssa", and "xml"</td>
    <td>Optional: defaults to json</td>
  </tr>
  <tr>
    <td>callback</td>
    <td>Callback function name, for use with jsonp.</td>
    <td>Optional: only for use with jsonp.</td>
  </tr>
</table>