This small bit of javascript can be added to the <header> of your template and then every YouTube or html5 video on the site will have the subtitle tab attached below.

**To use it:** add the following code at the end of the \<body\> (i.e.just above \</body\> tag) in your CMS template.

`<script type="text/javascript" src="http://s3.www.universalsubtitles.org/js/mirosubs-widgetizer.js"></script>`

**Demo:** http://universalsubtitles.org/widget/widgetize_demo.html

**Important note I** the widgetizer only works with YouTube and html5 videos. We'll be adding support for more formats and services in the very near future

**Important note II** IE visitors will require youtube videos be direct descendants of the `<body/>` tag. We're looking for a workaround to this issue.

*Caveat: certain formats that we support must use the flowplayer skin, in order to give us necessary timing data so that we can sync the subtitles to the video.*