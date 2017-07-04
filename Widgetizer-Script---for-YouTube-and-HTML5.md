## Enterprise Services

If you are interested in API integration, privacy controls, quality control processes, professional services, and building a volunteer community, please see our [enterprise services](http://www.universalsubtitles.org/en/enterprise/).


The widgetizer is deprecated, please use the embedder instead.

## Widgetizer for YouTube and HTML5

This small bit of javascript can be added to your html and then every YouTube (it's compatible with the old style YouTube `<object>` embeds only, NOT the newer `<iframe>` embeds) or html5 video on the site will have the subtitle tab attached below.  There are a few ways to add the widgetizer script:

### To the `<head/>` element

Just add the following bit of javascript to the `<head/>` element of your page:

`<script type="text/javascript" src="http://s3.www.universalsubtitles.org/js/unisubs-widgetizer.js"></script>`

**Demo:** http://www.universalsubtitles.org/widget/widgetize_demo/youtube_js

### At the bottom of the `<body/>` element

If you're concerned with the widgetizer script load slowing down your page, then place it at the bottom of your page's `body` element:


        <script type="text/javascript" src="http://s3.www.universalsubtitles.org/js/unisubs-widgetizer.js"></script>
    </body>

However, for youtube videos, you'll need a very tiny bit of javascript in the `head`:

`http://s3.www.universalsubtitles.org/js/widgetizer/widgetizerprimer.js`

(or you can just include the same script inline in the page).

**Important note** The widgetizer only works with YouTube and html5 videos. We'll be adding support for more formats and services in the very near future.