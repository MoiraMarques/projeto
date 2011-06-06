The overall goal of this project is to revise the current [Watch page](http://www.universalsubtitles.org/videos/) and [Search Results page](http://dev.universalsubtitles.org/en/search/) (currently in development) in the Universal Subtitles product. The revision should facilitate the discovery, watching and subtitling of videos.

Matt is working on HTML buildout of the project and should have the Watch page finished by WednesdayThursday, June 8/9. The Search Results page will be finished by Friday, June 10.

Here is the current visual documentation of the project:

### Wireframes
[Most Recent Wireframes](http://dl.dropbox.com/u/583499/Browsing-Videos-WIREFRAMES-v0.2.pdf)  

 * Page 1, 2 and 3 cover the same page. They are the top, bottom and advanced search functionality respectively  
 * Page 4 and 5 are the Search Results page, with Page 5 just showing that there will be an advanced search options hide/show.  
 * If this link stops working, ask Sunil for the file.

### Concepts
[Watch Page Concept](http://d.pr/bEgA)  
[Watch Page Concept](http://d.pr/gQWv) (with Advanced Search Options opened)  
[Search Results](http://d.pr/wU1R)

Please [email Sunil](mailto:sunil@doshimedia.com) if you have any questions.

### Instructions for Dmitriy

Dmitriy, this should be a fun task. You're going to create this page using Solr with Haystack. The "Advanced Search" will be done using Faceting, which is built into Solr and Haystack.

We're going to add a bunch of fields to the Video SearchIndex to support the spec. Here are the fields I think we should add:

`featured_date = DateTimeField(indexed=True)` -- this is not filled in yet. but we'll create an admin page for interns to make videos "featured". The top part of the Browse Videos page will be sorted in descending order by this date.

`daily_views = IntegerField(indexed=True)`  
`weekly_views = IntegerField(indexed=True)`  
`monthly_views = IntegerField(indexed=True)`  
`yearly_views = IntegerField(indexed=True)`  

`daily_views`, `weekly_views`, `monthly_views`, and `yearly_views` are filled in by the same process that moves redis views data to mysql.

`latest_subtitle_date = DateTimeField(indexed=True)` -- This should be the latest SubtitleVersion date for the video.

`language_count = IntegerField(indexed=True)` -- this is the number of SubtitleLanguages with is_complete_and_synced() == True

`activity_score` -- I'm not sure how we'll compute this yet, but we'll probably have to update it with a daily cron job.

We need to be able to facet and search on "Subtitled into" and "Team" (See the final page in wireframes). I'm not sure how to do this yet. Let's discuss it. It might be best to use a MultiValueField, but I don't know.