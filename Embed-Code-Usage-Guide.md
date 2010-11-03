h2. HTML 5 Videos

Example:

    <script type="text/javascript" src="http://www.s3.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.mysite.com/link_to_video.ogg"
      })
    </script>

For HTML 5 videos you can include any attributes for the `video` element using the `video_config` parameter. The `video_config` parameter can also include the property `click_to_play`:

    <script type="text/javascript" src="http://www.s3.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.mysite.com/link_to_video.ogg",
           video_config: {
               poster: "http://www.mysite.com/link_to_poster.jpg",
               click_to_play: true
           }
      })
    </script>

h2. Youtube Videos

The youtube video embed code should include the video url. The optional video_config parameter can include any of the [[YouTube Embedded Player Parameters|http://code.google.com/apis/youtube/player_parameters.html]], as well as width and height:

    <script type="text/javascript" src="http://www.s3.universalsubtitles.org/embed.js">
      ({
           video_url: "http://www.youtube.com/watch?v=I6Rg1i743o4",
           video_config: {
               color1: FF0000,
               width: 640,
               height: 480
           }
      })
    </script>
