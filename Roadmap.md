_In progress. Last updated 7 November 2011_

## By 11 Nov 2011

### Team management
- ~~Can create new team~~ (`/teams/create/` — must be super user)
- Can adjust/save basic settings
- Can create projects
- Can edit projects
- Can remove projects

### Team videos
- ~~Can view videos~~ (`/teams/:slug/`)
- ~~Can add single video to team~~ (`/teams/add/video/:slug/`)
- Can add multiple videos to team (awaiting [#282][1])
- ~~Can edit video~~ (`/teams/edit/video/:team_video_id`)
- Can remove videos
- ~~Can filter videos view by project~~ (`/teams/:slug/p/:project_slug`)

### Team members
- ~~Can view members~~ (`/teams/:slug/members/`)
- ~~Can join team~~
- ~~Can apply to team~~
- ~~Can approve applications~~ (`/teams/applications/:slug/`)
- ~~Can leave team~~ 
- ~~Can filter members view by role~~ (`/teams/:slug/members/:role_slug/`)
- Can invite members

### API
- Partner can create users via the API
- Partner can add videos for created users via the API
- Partner can upload subtitles for users via the API

## By 18 Nov 2011

### Team management
- Can adjust permissions
- Can specify workflow options
- Can block languages

### Team members
- Can edit member roles
- Can edit role restrictions
- Can block/remove member

### Team tasks
- Can view tasks
- Can create tasks
- Can view existing tasks
- Can assign tasks
- Can accept/reject tasks
- Can filter tasks by language

### Infrastructure
- Non-public staging server for testing

## By 25 Nov 2011

### Team management
- Can save custom messages and guidelines
- Can adjust notification settings

### Team videos
- Can move videos among projects

## By 2 December

### Team videos
- Can filter videos view by orig language
- Can filter videos view by sub language
- Can search videos view

### Team members
- Can filter members view by language spoken
- Can search members view

### Team activity
- Can filter activity view by type
- Can filter activity view by language
- Can search activity view

### Team tasks
- Can filter tasks by type


[1]: https://unisubs.sifterapp.com/projects/12298/issues/469162/comments