## HTML 5 Videos

Example:

    <script type="text/javascript" src="http://s3.www.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.mysite.com/link_to_video.ogg"
      })
    </script>

For HTML 5 videos you can include any attributes for the `video` element using the `video_config` parameter. The `video_config` parameter can also include the property `click_to_play`:

    <script type="text/javascript" src="http://s3.www.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.mysite.com/link_to_video.ogg",
           video_config: {
               poster: "http://www.mysite.com/link_to_poster.jpg",
               click_to_play: true
           }
      })
    </script>

## Youtube Videos

The youtube video embed code should include the video url. The optional video_config parameter can include any of the [[YouTube Embedded Player Parameters|http://code.google.com/apis/youtube/player_parameters.html]], as well as width and height:

    <script type="text/javascript" src="http://s3.www.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.youtube.com/watch?v=I6Rg1i743o4",
           video_config: {
               color1: FF0000,
               width: 640,
               height: 480
           }
      })
    </script>

## FLV Files

For raw FLV files, the widget uses [[FlowPlayer|http://flowplayer.org/]]. The optional video_config parameter can include any of the [[FlowPlayer plugins|http://flowplayer.org/documentation/configuration/plugins.html]], as well as width and height:

    <script type="text/javascript" src="http://s3.www.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.youtube.com/watch?v=I6Rg1i743o4",
           video_config: {
               width: 640,
               height: 480,
               content: {
                   url: 'flowplayer.content-3.2.0.swf',
                   height: 220,
                   padding:30,
                   backgroundColor: '#112233',
                   opacity: 0.7,
                   backgroundGradient: [0.1, 0.1, 1.0],
                   html: '<p>This big overlay is a content plugin</p>',
                   style: {p: {fontSize: 40}}			
               }
           }
      })
    </script>

## Adding alternate video URLs

The embed code can include alternate video URLs. The widget will choose the URL that is "most preferred" for the browser, where ogg > h264 > flash.

    <script type="text/javascript" src="http://s3.www.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.youtube.com/watch?v=I6Rg1i743o4",
           alternate_video_urls: ["http://example.com/examplevideo.ogg", "http://example.com/examplevideo.mp4"]
      })
    </script>

You can also add appropriate video_config parameters to the alternate video URLs:

    <script type="text/javascript" src="http://s3.www.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.youtube.com/watch?v=I6Rg1i743o4",
           alternate_video_urls: [
              { url: "http://example.com/examplevideo.ogg", 
                config: {poster: "http://www.mysite.com/link_to_poster.jpg"}}, 
              "http://example.com/examplevideo.mp4"]
      })
    </script>

