API documentation v. 1.0

## SubtitleHandler
**Name:** read(GET)

**Signature:** no parameters
***
Return subtitles for video.

Send in request:

**video url:** video_url

**video id:** video_id

**language:** language of video

**revision:** revision of subtitles

**sformat: **format of subtitles(srt, ass, ssa, ttml, sbv)

By default format of response is 'plain', so you get raw subtitles content in response.

If 'sformat' exists in request - format will be 'plain'.

If 'callback' exists in request - format will be 'json'.

    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -d 'callback=callback' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -d 'sformat=srt' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -d 'sformat=srt' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_id=7Myc2QAeBco9' -G
***

**Name:** create(POST)

**Signature: **no parameters
***
Add subtitles for video.

Send in request:

**video:** video_id

**video_language:** language of video

**language:** language of subtitles

**format:** format of subtitles(srt, ass, ssa, ttml, sbv)

**subtitles:** subtitles(max size 256kB. Can be less, not tested with big content)

    curl "http://127.0.0.1:8000/api/1.0/subtitles/?username=admin&password=admin" -d 'video=0zaZ2GPv3o9m' -d 'video_language=en' -d 'language=ru' -d 'format=srt' -d 'subtitles=1%0A00:00:01,46 --> 00:00:03,05%0Atest'

***

## AnonymousSubtitleHandler
**Name:** read(GET)

**Signature: **no parameters

***
Return subtitles for video.

Send in request:

**video url:** video_url

**video id:** video_id

**language:** language of video

**revision:** revision of subtitles

**sformat:** format of subtitles(srt, ass, ssa, ttml, sbv)

By default format of response is 'plain', so you get raw subtitles content in response.

If 'sformat' exists in request - format will be 'plain'.

If 'callback' exists in request - format will be 'json'.

    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -d 'callback=callback' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -d 'sformat=srt' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_url=http://www.youtube.com/watch?v=YMBdMtbth0o' -d 'sformat=srt' -G
    curl http://127.0.0.1:8000/api/1.0/subtitles/ -d 'video_id=7Myc2QAeBco9' -G

***

**Name: **create(POST)

**Signature:** no parameters

***

Add subtitles for video.

Send in request:

**video:** video_id

**video_language:** language of video

**language:** language of subtitles

**format:** format of subtitles(srt, ass, ssa, ttml, sbv)

**subtitles:** subtitles(max size 256kB. Can be less, not tested with big content)

    curl "http://127.0.0.1:8000/api/1.0/subtitles/?username=admin&password=admin" -d 'video=0zaZ2GPv3o9m' -d 'video_language=en' -d 'language=ru' -d 'format=srt' -d 'subtitles=1%0A00:00:01,46 --> 00:00:03,05%0Atest'

***

## AnonymousSubtitleLanguages
**Name:** read(GET)

**Signature:** no parameters

***

Return inforamiton about avilable subtitles languages.

Send in request:

**video url: **video_url

**video id:** video_id

    curl http://127.0.0.1:8000/api/1.0/subtitles/languages/ -d 'video_id=7Myc2QAeBco9' -G

    [
        {
            "code": "it", 
            "name": "Italian", 
            "is_original": true
        }
    ]

## SubtitleLanguagesHandler
**Name:** read(GET)

**Signature:** no parameters

***

Return information about available subtitles languages.

Send in request:

**video url:** video_url
**video id:** video_id

    curl http://127.0.0.1:8000/api/1.0/subtitles/languages/ -d 'video_id=7Myc2QAeBco9' -G

    [
        {
            "code": "it", 
            "name": "Italian", 
            "is_original": true
        }
    ]

***


## VideoHandler

**Name:** read(GET)

**Signature:** video_id=<optional>

***
Get video by video_id(JVoMAa3kaWzq)
    curl "http://127.0.0.1:8000/api/1.0/video/JVoMAa3kaWzq/"

Get video by url. It will be created if does not exist. Authentication is not required. 

If video does not exist and you are authenticated, you will be saved as creator for this video.
    curl "http://127.0.0.1:8000/api/1.0/video/?username=admin&password=admin" -d 'video_url=http://www.youtube.com/watch?v=oOOve811tMY' -G

Response format is JSON by default. 

You can set format with "format" parameter in URL, like 

'http://127.0.0.1:8000/api/1.0/video/JVoMAa3kaWzq/?format=xml' 

or 'http://127.0.0.1:8000/api/1.0/video/JVoMAa3kaWzq/?format=yaml'

***


## AnonymousVideoHandler
**Name: **read(GET)

**Signature:** video_id=<optional>

***

Get video by video_id(JVoMAa3kaWzq)
    curl "http://127.0.0.1:8000/api/1.0/video/JVoMAa3kaWzq/"

Get video by url. It will be created if does not exist. 

Authentication is not required. If video does not exist and you are 

authenticated, you will be saved as creator for this video.
    curl "http://127.0.0.1:8000/api/1.0/video/?username=admin&password=admin" -d 'video_url=http://www.youtube.com/watch?v=oOOve811tMY' -G

Response format is JSON by default. You can set format with "format" parameter in URL, 

like 'http://127.0.0.1:8000/api/1.0/video/JVoMAa3kaWzq/?format=xml' 

or 'http://127.0.0.1:8000/api/1.0/video/JVoMAa3kaWzq/?format=yaml'
