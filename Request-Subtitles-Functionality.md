Functionality providing interface to users for publishing requirements of
subtitles.

Google summer of code project of [Rohan Jain]
(http://www.google-melange.com/gsoc/project/google/gsoc2011/crodjer/10001)

#Functionality Required
(Discussion: <http://piratepad.net/tVDSnTpZ0W>)

##User sees

[Video]  
[Subtitle me][**Request Subtitles**][Share]

Other possible texts:

 - I want subtitles
 - Request subs

##On click, user

 - Logs in, if not
 - Selects languages to be reqested from the dropdowns
 - Writes a description: "Why do you want subtitles?" (Not necessary to
   be filled)
 - Checkbox (checked by default) saying "Notify me about edits/updates to
   this video" or "Keep me posted about this video."

##Notifying potential volunteers

 - Any time user recieves any notification, **footer of notification**
   email tells them other videos they can work on.
 - Asking multi lingual users if they want to be notified for subtitle
   requests in their languages.
 - If there is a very low number of users ( < 100) who speak a language,
   then notify all: "You are one of just 25 users on our site who speak
   LANGUAGE.  
   We wanted to let you know that USERNAME requested subitltes for LANGUAGE
   subtitles for VIDEO TITLE"
 - Some users are **heavy helpers**, send high notifications to users with
   high response rates/large amounts of lines contributed.

##Places where requests display on the site

 - Video homepage.
 - Request text: Commen on video info page (or pseudo comment that displays
   like a comment, not a comment)
 - Page listing requested videos by sort: **Volunteer Page**

##Volunteer Page

 - Multiple Sort by "most requested", known languages
 - Partially done stuff first
 - Has language filters like: http://dev.universalsubtitles.org/en/search/,
   these are "from / into my languages" by default
 - List of featured videos at the top (should these be filtered?) admins
   would be able to flag videos as featured using the admin site.
 - User can choose to follow a language for requests ("Show me all language
   requests for Catalan") and let them choose "My languages", let  them
   follow all requests.

##Notifying the requesters

 - When somebody starts on a request you made
 - When somebody completes a request you made, also ask to work on further
   translation.
 - Requester follows:

    - video?
    - all languages (even ones that don't exist)
    - for further subtitling requests
 - They can unfollow specific languages that don't matter to them.
 - Unbatched emails are okay for this.

##Admin settings:

 - > N requests sends out N notifications
 - Send users N notifications per week, with requests batched OR top
   request.


#Technical Design

##A `Requset` (Model)

 - Users
 - Video
 - Language

##Request-User M2M

 - Time
 - User
 - Request
