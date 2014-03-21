# Brightcove integration

### Summary: 
 - Amara dev work required is to:
  - generate the url of a bc mrss feed using supplied parameters.
  - recognize a feed as coming from bc and store the video id
  - generate dfxp files of all completed languages
  - add brightcove to external sites configuration page
  - implement syncing via the externalsites app and using the bc media write api.


### Currently:  
 - Have support for brightcove player in new editor
 - Able to import individual bc urls
 - Able to add simple mrss feeds
 - Have support for brightcove videos in the embedder / transcript viewer

### Want: 
 - To simplify the process for user:
  - easy configuration
  - no manually adding of videos
  - no requirement from them to generate feeds for ingest
 - To be able sync captions back to the user's bc account

### Required to work:
 - User has enterprise level or better bc account
 - A compatible 'amara-player' in bc (chromeless player with javascript enabled)
 - Brightcove configured as an amara external site:
   - publisher id
   - player id
   - api write token
   - tags (optional) otherwise we default to new

### From brightcove:
  If they could add a default 'amara-player' for users, it would save the users about 5 steps of the config process in the brightcove management console.

### Configuration
- via ExternalSites configuration tab configure:
 - publisher id
 - player id 
 - write token
 - tags (optional)
### Adding videos to amara
 - Amara generates a simple mrss feed and pulls in videos based on tag / player / publisher info
ex: 
```
http://link.brightcove.com/services/mrss/player<player id>/<publisher id>/tags/tag 1/tag 2/...
```
or 
```
http://link.brightcove.com/services/mrss/player<player id>/<publisher id>/new (for all videos added in)
```
```
        <title>Tagged: amara-test</title>
        <link>http://link.brightcove.com/services/mrss/player2911001534001/2903498771001/tags/amara-test</link>
        <description/>
        <copyright>Copyright 2014</copyright>
        <lastBuildDate>Fri, 21 Mar 2014 04:26:00 -0700</lastBuildDate>
        <generator>http://www.brightcove.com/?v=1.0</generator>
        <item>
            <title>Birds_short</title>
            <link>http://link.brightcove.com/services/link/bcpid2911001534001/bctid2915728359001?src=mrss</link>
            <description>Birds_short</description>
            <guid>http://link.brightcove.com/services/link/bcpid2911001534001/bctid2915728359001?src=mrss</guid>
            <pubDate>Mon, 09 Dec 2013 12:30:49 -0800</pubDate>
            <media:player height="270" url="http://link.brightcove.com/services/link/bcpid2911001534001/bctid2915728359001?src=mrss" width="480"/>
            <media:keywords>amara-test,Amara</media:keywords>
            <media:thumbnail height="90" url="http://lds.pd.ak.o.brightcove.com/2903498771001/2903498771001_2915792270001_th-52a62879e4b00f8cb61e95e3-1592194018001.jpg?pubId=2903498771001" width="120"/>
            <media:thumbnail height="360" url="http://lds.pd.ak.o.brightcove.com/2903498771001/2903498771001_2915792269001_vs-52a62879e4b00f8cb61e95e3-1592194018001.jpg?pubId=2903498771001" width="480"/>
            <bc:playerid>2911001534001</bc:playerid>
            <bc:titleid>2915728359001</bc:titleid>
            <bc:duration>37</bc:duration>
            <dcterms:valid/>
            <bc:accountid>2903498771001</bc:accountid>
        </item>
```
We'd need to grab the video id for each entry: **bc:titleid** and store it for syncing later.


### Workflow
 - Based on team configuration

### Syncing
 - When language is completed - captions are synced be to bc using the bc media write api.]
  - ref: [http://docs.brightcove.com/en/video-cloud/media/reference.html#Captioning]
  - for syncing, bc requires all languages in 1 file: so for each langauge synced, we'd have to pull all the captions for all completed languages and generate a file.

```
<tt xmlns="http://www.w3.org/ns/ttml" xmlns:tts="http://www.w3.org/ns/ttml#styling">
  <head>
    <metadata xmlns:ttm="http://www.w3.org/ns/ttml#metadata">
      <ttm:title/>
      <ttm:description/>
      <ttm:copyright/>
    </metadata>
    <styling xmlns:tts="http://www.w3.org/ns/ttml#styling">
      <style xml:id="amara-style" tts:color="white" tts:fontFamily="proportionalSansSerif" tts:fontSize="18px" tts:textAlign="center"/>
    </styling>
    <layout xmlns:tts="http://www.w3.org/ns/ttml#styling">
      <region xml:id="amara-subtitle-area" style="amara-style" tts:extent="560px 62px" tts:padding="5px 3px" tts:backgroundColor="black" tts:displayAlign="after"/>
    </layout>
  </head>
  <body region="amara-subtitle-area">
        <div xml:lang="en">  
                <p begin="00:00:00.000" end="00:00:01.000">Line 1</p>
                <p begin="00:00:02.000" end="00:00:04.500">Line 2</p>
                <p begin="00:00:04.500" end="00:00:06.500">Line 3</p>
                <p begin="00:00:07.000" end="00:00:08.500">Line 4</p>
                <p begin="00:00:09.500" end="00:00:12.500">Line 5</p>
                <p begin="00:00:13.500" end="00:00:20.500">Line 6</p>
        </div>
        <div xml:lang="fr">  
                <p begin="00:00:00.000" end="00:00:01.000">Line 1</p>
                <p begin="00:00:02.000" end="00:00:04.500">Line 2</p>
                <p begin="00:00:04.500" end="00:00:06.500">Line 3</p>
                <p begin="00:00:07.000" end="00:00:08.500">Line 4</p>
                <p begin="00:00:09.500" end="00:00:12.500">Line 5</p>
                <p begin="00:00:13.500" end="00:00:20.500">Line 6</p>
        </div>
        <div xml:lang="pt">
          <div>
            <p begin="00:00:00.000" end="00:00:01.000">This line has <span tts:fontWeight="bold">bold text in it</span></p>
            <p begin="00:00:01.424" end="00:00:02.501">This line has <span tts:fontStyle="italic">multiline<br/>italics</span></p>
          </div>
        <div>
            <p begin="00:00:02.664" end="00:00:04.048">This one has an evil tag</p>
            <p begin="00:00:04.411" end="00:00:05.126">this is an edited line.</p>
        </div>
       </div>
   </body> 
</tt> 
```

### Other concerns
 - Content control on the BC side.
  - BC Users can configure geographic blocks on videos
  - Security concerns, providing us with a write-access token. 
    - if they don't want to give us write access - subs would have to be downloadable so the users could manually upload them.
  - Users with lower level BC accounts don't have access to the BC media api - so they would have to manually upload their subtitles - or choose and alternate method for display (amara embedder, for example)

