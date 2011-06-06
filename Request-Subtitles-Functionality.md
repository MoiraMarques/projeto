Functionality providing interface to users for publishing requirements of
subtitles.

Google summer of code project of [Rohan Jain](http://www.google-melange.com/gsoc/project/google/gsoc2011/crodjer/10001)

#Functionality Required
(Discussion: <http://piratepad.net/tVDSnTpZ0W>)

##User sees
(If video does not has at least one subtitle language created)

[Video]  
[Subtitle me][**Request Subtitles**][Share]

Other possible texts:

 - I want subtitles
 - Request subs

Wireframe: <https://cacoo.com/diagrams/n8OuAAItVnbzm70K>

##On click, user

 - Logs in, if not
 - Selects languages to be reqested from the dropdowns
 - Writes a description: "Why do you want subtitles?" (Not necessary to
   be filled)
 - Checkbox (checked by default) saying "Notify me about edits/updates to
   this video" or "Keep me posted about this video."

##Notifying potential volunteers

 - Any time user recieves any notification, **footer of notification
   email** tells them other videos they can work on.
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

 I

 - When somebody starts on a request you made (Include bullets: • View existing work (may not be visible yet) • Send USERNAME a personal message • Leave an encouraging comment)   
 - When somebody completes a request you made (this asks them to proofread the subtitles, and translate them into another language.  Include in bullets: "Now its your turn: • Say "Thanks" in the comments • Review these subtitles for spelling and grammar errors • Translate them into other languages") 
 - Unbatched emails are okay for this.

##Admin settings:

 - > N requests sends out N notifications
 - Send users N notifications per week, with requests batched OR top
   request.


#Technical Design

###Requesting interface
(<https://cacoo.com/diagrams/n8OuAAItVnbzm70K>)

 - If a video does not have at least one subtitle language already created
   the *Request Subtitles* button will be rendered.
 - A click pops up the language selection dialogue with user known
   languages already selected.
 - Ajax (rpc?) based submission. For each language the requesting user is
   appended to the getted or newly created requests for the language.

###Notifications

As soon as a request is created select users to be notified in these ways:

 - Provide user an option to set the list of languages for which they 
   follow the requests.
   All the users who have language list containing the request languages.  
   Set the above option `True` for users who are *heavy contributors*, the
   ones who have contributed more than a specific amount of *subtitles* and
   also for all the users who speak a language with low popularity
   ( < 100)  
 - Users who are following a video for requests filtered based on their
   known language.

Other notification ways:

 - From any random three requests for footer of the notification emails.
 - Video page bottom like action rendering.
 - A volunteer page, with the haystack search implemented here and sticky
   pagination (for featured videos).

##Notifying requesters

 - For subtitling start: Cron based, as for instantaneous every action will
   have to be checked for being a possible response.
 - For end: Notify right away.
 - As soon as the request form is submitted, user follows the requested
   languages + all other ones if the *keep me posted* option is checked.

#Definitions

##Models

###Requset

 - Users (M2M through Request-User below)
 - Video
 - Language
 - Subtitle Responses
   This can be based on `Action` (`ADD_VERSION`) or `Subtitle` (Doesn't
   have a datetime field).  
   Maybe a denormalized M2M or just a method.

###Request-User M2M

 - Time
 - User
 - Request
 - Description

**OR**

###Existing Action model
(Alternative to the above)

 - Add another type: `Request`

**OR**

###A combination of both above

###User Profile

 - A list of languages to follow requests.

###Video

 - Featured boolean.

##Forms

###Request Form

 - A language selection formset (for multiple lanuages) + a form for the
   general fields.

###Follow Request Language form
 
 - A language selection formset.