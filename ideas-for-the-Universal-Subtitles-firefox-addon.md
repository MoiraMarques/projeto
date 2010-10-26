I was thinking that it should be possible to create a firefox addon that when you go to youtube and go to watch a video it automatically adds the US (Universal Subtitles) button below it.  it would be much nicer then having to go to the universal subtitles site and past the address in to see if it has subs.

So far I have an idea for the start of the code. 

<code>$('#movie_player').after('<a href="#" class="mirosubs-subtitleMeLink"><img src="http://s3.www.universalsubtitles.org/images/small_logo.png" alt="small logo"><span class="mirosubs-tabTextchoose">Original Language</span></a><a style="display: none;" href="#"><span class="mirosubs-tabTextfinish">NUDGE TEXT</span></a>');</code>

that should add the universal subtitles button to all youtube videos.

but that is jQuery which -should- work in a firefox extension. (dunno)

you would need the addon to have all of the universal subtitles javascript files and css files inside of it then an addition javascript which would look kind of like this:

///////////script start
//things written with these"//" infront of them aren't code but instead are comments on my code that will not affect the code.
<code>
function LoadUS(){
  $('#movie_player').after('<a href="#" class="mirosubs-subtitleMeLink"><img src="http://s3.www.universalsubtitles.org/images/small_logo.png" alt="small logo"><span class="mirosubs-tabTextchoose">Original Language</span></a><a style="display: none;" href="#"><span class="mirosubs-tabTextfinish">NUDGE TEXT</span></a>');
}
//#movie_player is the object that youtube creates that the youtube video runs inside.

function onloadhookcustom() {
  LoadUS();
}


if (window.addEventListener){window.addEventListener("load",onloadhookcustom,false);}
else if (window.attachEvent) {window.attachEvent("onload",onloadhookcustom);}
//these two lines just check to see when a webpage is loaded then triggers the "onloadhookcustom()" function.
</code>
/////////script end

that should work as far as making the subtitles button appear, then after that a the normal US javascript/css files should kick in and function as normal.  that is my presumption anyway. 

comments? I'd love to hear from people that know a bit more than me about programming.