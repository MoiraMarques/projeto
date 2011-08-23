For 0.9.2 deployment:

* After deployment, remove cron job that runs update_changes.
* Add EMAIL_SUBJECT_PREFIX to settings file.
* Go through and remove videos that have no VideoUrl models. First possibly copy data from these to existing videos.