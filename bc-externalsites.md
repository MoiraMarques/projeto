# Brightcove integration

### Currently:  
 - have support for brightcove player in new editor
 - Able to import individual bc urls
 - Able to add bc simple mrss feeds

### Want: 
 - To simplify the process for user:
  - easy configuration
  - no manually adding of videos
  - no requirement from them to generate feeds for ingest
 - To be able sync captions back to the user's bc account

### Requires from us:
 - User has enterprise level or better bc account
 - Creates a compatible 'amara-player' in bc (chromeless player with javascript enabled)
 - Configures syncing on amara team with:
   - publisher id
   - player id
   - api write token
   - tags (optional) otherwise we default to new

### From brightcove:
  If they could add a default 'amara-player' for users, it would save the users about 5 steps of the config process in the brightcove management console.

### Approach:

1. via ExternalSites configuration tab configure:
 - publisher id
 - player id 
 - write token
 - tags (optional)


2. Amara generates a simple mrss feed and pulls in videos based on tag / player / publisher info
ex: 
```
http://link.brightcove.com/services/mrss/player<player id>/<publisher id>/tags/tag 1/tag 2/...
```
or 
```
http://link.brightcove.com/services/mrss/player<player id>/<publisher id>/new (for all videos added in)
```

We'd need to grab the video id for each entry: bc:title id and store it for syncing later.

3. Once videos are ingested (based on team type, if on-demand, then tasks should be automatically created.

4. When language is completed - captions are synced be to bc using the bc media write api.]
  - ref: [http://docs.brightcove.com/en/video-cloud/media/reference.html#Captioning
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


