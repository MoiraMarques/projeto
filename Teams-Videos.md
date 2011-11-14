[[← All Specs|Teams-Spec]]

* **Access:** Visible to all (public, users, and team members)
* Page displays a paginated list of a team's videos, optionally filtered by project and/or language.
* Videos are sorted reverse-chronologically by date added, from most to least recent
* Each page displays 10 videos

## Functionality

### Filter by project

* **Access:** Available to all
* **Description:** Clicking the name of a project in the right sidebar (`div.controls`) filters the list of videos so that only videos in that project are shown.

**Use Cases**

* **WHEN** projects are not enabled
    * `ul` should not exist in (`div.controls`)
* **WHEN** 

#### Filter by language

**Access:** Available to all

### Create a task

**Access:** Available to managers and above

### Remove a video

**Access:** Available to role specified in settings

### Bulk edit videos (incomplete)

**Access:** Available to role specified in settings