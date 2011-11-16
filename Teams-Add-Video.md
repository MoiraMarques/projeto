[[← All Specs|Teams-Spec]]

## Add video, single

* **Displays:** form for adding a single video to a team
* **Visible to:** role specified in team settings
* **Behavior:** when submitted, video is added to team and user is redirected to video listing

### Fields

* Video URL
* Title
* Description
* Project (only visible when more than one project exists)
* Thumbnail


## Add video, multiple

* **Displays:** form for adding multiple videos to a team
* **Visible to:** role specified in team settings
* **Behavior:** when submitted, videos are added to team and user is redirected to video listing
   * site notice should be displayed informing user that "Videos may take some time to appear"

### Fields

* Youtube usernames
* Youtube page link
* Feed URL
* Save feed


## Toggle mode

* **Displays:** menu in right sidebar (`div.controls`) allowing user to switch between single video and multiple video forms or return to the video listing
* **Visible to:** role specified in team settings