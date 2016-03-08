# To embed a video from Amara:

Step 1: paste this in your document somewhere (closest to the closing body tag is preferable):

```
<script type="text/javascript" src='https://amara.org/embedder-iframe'>
</script>
```
Step 2: paste this inside your HTML body where you want to include the videos, with the video URL, height, and width of your choosing:

```
<div class="amara-embed" data-height="480px" data-width="854px" data-url="http://www.youtube.com/watch?v=5CKwCfLUwj4">
</div>
```

You can set the following options:

* Hide the menu item to order subtitles by adding **data-hide-order="true"** in the previous tag.
* Set the initial active subtitle language by adding **data-initial-language="language"** in the previous tag, where language is the language code, such as "en" for English.
* Display the subtitles by default by adding **data-show-subtitles-default="true"** in the previous tag.
* Display the transcript by default by adding **data-show-transcript-default="true"** in the previous tag.

The subtitles and transcript will display as they do on the Amara video pages and in the [amara embedder example](http://amara.org/embedder-offsite)

![](https://dl.dropboxusercontent.com/u/12459347/amara-imgs/embedder-example-screenshot.png)
