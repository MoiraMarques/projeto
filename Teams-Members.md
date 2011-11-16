[[← All Specs|Teams-Spec]]

## Member listing

* **Displays:**
    * list of members (`ul.listing.members`)
    * members sorted from oldest to newest by date added to team
    * 10 members per page
* **Visible to:** everyone (public, users, and team members)

### Items

Each item displays:

* User avatar
    * WHEN user has not uploaded an avatar
        * Default gravatar image shown
* User name
    * WHEN user shown  in logged-in user
        * "(You)" appended to user name
* User languages in `span.descriptor` elements in the `h3`
* User role
    * WHEN user has role restrictions
        * role retrictions appended after role
* Actions menu (`ul.actions`) with one item:
    * Send message
        * **Behavior:** when clicked, loads the send message page (or opens a modal... unsure yet)


## Role filtering

* **Displays:** linked list of roles in right sidebar (`div.controls`)
* **Visible to:** everyone
* **Behavior:** clicking the name of a role filters the list of members so that only members with that role are shown


## Filter by language

* **Displays:** dropdown of languages above the member listing
* **Visible to:** everyone
* **Behavior:** selecting a language filters the list of members so that only members proficient in that language are shown

### Use cases

* WHEN user is logged in AND has specified language preferences
    * preferred languages should be at top of list


## Manage members

* **Displays:** an admin menu (`ul.admin-controls`)
* **Visible to:** admins and owner
* **Behavior:**
    * appears when hovering over a member listing
    * displays 'Edit' and Remove' buttons


## Edit member

* **Displays:** an 'Edit' button in the admin menu
* **Visible to:** role specified in team settings
* **Behavior:** clicking loads a popover form...

### Form

* Role
* Project restriction
* Language restriction


## Manage membership

See description on [[Videos|Teams-Videos]] spec


## Bulk edit members (incomplete)

* **Displays:** checkbox in the admin menu
* **Visible to:** role specified in team settings
* **Behavior:** 
    * checking selects and deselects videos
    * selecting a video makes the admin menu persist (i.e. doesn't disappear when the item loses hover)
    * once at least one video is selected, the edit member popover is displayed (not yet implemented)


## Search members

Not yet implemented