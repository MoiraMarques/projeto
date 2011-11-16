[[← All Specs|Teams-Spec]]

## Member listing

* **Displays:**
    * list of members (`ul.listing.members`)
    * members sorted from oldest to newest by date added to team
    * 10 members per page
* **Visible to:** everyone (public, users, and team members)


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

* **Displays:** an 'add videos' button above the video listing
* **Visible to:** role specified in team settings
* **Behavior:** clicking loads the [[Add Video]] form

### Use cases

* WHEN team member does not have 'add/remove' videos privileges
    * button is not displayed





## Manage membership

See description on [[Videos|Team-Videos]] spec