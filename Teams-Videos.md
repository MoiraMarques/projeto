[[← All Specs|Teams-Spec]]

## Video listing

* **Displays:**
    * list of videos (`ul.listing.videos`)
    * items sorted from newest to oldest by date added to team
    * 10 items per page
* **Visible to:** everyone (public, users, and team members)

### Use Cases

* WHEN there are no video results
    * `ul.listing.videos` is not displayed
    * `p.empty` displayed containing the text "Sorry, no videos here..."


## Project filtering

* **Displays:** linked list of team's projects in right sidebar (`div.controls`)
* **Visible to:** everyone
* **Behavior:** clicking the name of a project filters the list of videos so that only videos in that project are shown

### Use cases

* WHEN a team has only one project (see [#298][1])
    * `ul` contains only one item
        * WHEN the default project has not been renamed, the item reads "All videos"
        * WHEN the default project has been renamed, the item shows the project name
    * WHEN user is admin or owner
        * Message is displayed below menu: "Projects allow you to organize your team's videos. [View/create projects](#)."


## Filter by language

* **Displays:** dropdown of languages above the video listing
* **Visible to:** everyone
* **Behavior:** selecting a language filters the list of videos so that only videos with subtitles in that language are shown

### Use cases

* WHEN user is logged in AND has specified language preferences
    * preferred languages should be at top of list


## Manage videos

* **Displays:** an admin menu (`ul.admin-controls`)
* **Visible to:** role specified in team settings
* **Behavior:** appears when hovering over a video listing

### Use cases

* WHEN team member has 'add/remove videos' privileges
    * admin menu displays 'Edit' and Remove' buttons
* WHEN team member has 'assign tasks' privileges
    * admin menu displays 'Create Task' button (see below)


## Add videos

* **Displays:** an 'add videos' button above the video listing
* **Visible to:** role specified in team settings
* **Behavior:** clicking loads the [[Add Video]] form

### Use cases

* WHEN team member does not have 'add/remove' videos privileges
    * button is not displayed


## Create a task

* **Displays:** 'New Task' button in the admin menu
* **Visible to:** role specified in team settings
* **Behavior:** clicking loads the [[Create Task]] form

### Use cases

* WHEN team member does not have 'assign tasks' videos privileges
    * button is not displayed


## Remove a video

* **Displays:** 'Remove' button in the admin menu
* **Visible to:** role specified in team settings
* **Behavior:** clicking prompts user for confirmation; user may confirm or cancel removal

###  Confirmation text

Are you sure you want to remove this video from your team? The video will remain on Universal Subtitles, and existing subtitles will not be affected, but you will no longer be able to manage the video.

### Use cases

* WHEN team member does not have 'add/remove' videos privileges
    * button is not displayed
* WHEN user clicks 'confirm' during confirmation
    * the video is removed from the team
    * all tasks attached to that video are removed
    * user is shown message confirming that video has been removed
* WHEN user click 'cancel' during confirmation
    * confirmation is dismissed, video is not removed


## Manage membership

* **Displays:** A button in the right sidebar allowing user to manage her/his membership
* **Visible to:** everyone

* WHEN user is logged in AND is a team member
    * "Leave team" button is displayed
    * **Behavior:** 
        * clicking button displays confirmation alert
        * clicking "Confirm" removes member from team
        * clicking cancel dismissed the alert
* WHEN user is logged in AND is not a team member
    * WHEN team membership is open
        * "Join this team now!" button is displayed
        * **Behavior:** 
            * clicking button makes user a member of the team
            * user is given the role of contributor
            * page is reloaded
    * WHEN team membership is by application
        * "Apply to join" button is displayed
        * **Behavior:**
            * clicking button loads application form in modal dialog
            * submitting application form creates new application
            * team admins and owners receive site notification (not yet implemented)
    * WHEN team membership is by invitation
        * `p.action-replacement` is displayed containing the text "Membership by invitation only"
* WHEN user is not logged in
    * "Sign in to join team" button is displayed
    * **Behavior:** clicking button loads the sign in page


## Bulk edit videos (incomplete)

* **Displays:** checkbox in the admin menu
* **Visible to:** role specified in team settings
* **Behavior:** 
    * checking selects and deselects videos
    * selecting a video makes the admin menu persist (i.e. doesn't disappear when the item loses hover)
    * once at least one video is selected, a bulk actions menu is displayed (not yet implemented)


## Search videos

Not yet implemented



[1]: https://unisubs.sifterapp.com/projects/12298/issues/482211/comments