Keep a metadata table called VideoLanguagePairs that has each language pair for every video, along with percent_complete. So for k languages and n videos we have nk(k-1) rows. This table is indexed on video_id, team_id, language_0, language_1, and (language_0, language_1) pair.

Whenever someone requests the team detail page k:

    NUM_VIDEOS = 20
    video_list = []
    for sublist_type in sublist_types:
        for language_pair in my_language_pairs:
            video_list.extend(_get_videos(sublist_type, team_id, language_pair, k))
            if len(video_list) >= NUM_VIDEOS:
                break
        if len(video_list) >= NUM_VIDEOS:
            break
    # now do whatever work on video_list before displaying it.
    # maybe save video_list in cache

Note this runs in `O(log(n))` time.

To keep the metadata table fresh:

1. Whenever a new Video is added or a Video is associated with a Team, queue an asynchronous job to add it to the VideoLanguagePairs table.
2. Whenever a new language is added to settings.py, queue an asynchronous job to add it to the VideoLanguagePairs table for every video.
3. Whenever a SubtitleLanguage is saved, queue an asynchronous job to update the 2k-1 VideoLanguagePairs rows for that language/video combination.

Remember, the metadata table doesn't have to be totally up-to-date all the time. Worst-case scenario is that it's a minute or two out-of-date.