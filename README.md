# Flexget-Cookbook
My Flexget Cookbook recipies


1) Filter RSS Feed to different folders
This setup will take a RSS Feed that you want to download everything from. For example, a RSS Feed of your torrent sites Bookmarks/Favorites/… and will filter TV shows, Movies, and other (everything else) into separate locations.

Replace ‘RSS Feed URL’ with your Feeds URL
Change the downloader plugin (used here deluge) to your downloaders plugin, and change the set sections accordingly (may not be possible for all downloaders)
Change the folder locations from ‘D:…’ to your setups.


2)Move to Archive - TV shows and Movies
This will find all your tv shows and movies that are no longer listed in the Deluge torrent client and that were downloaded over a certain amount of days ago and will move the files and their subtitle files to a different folder (Any mounted drive or local cloud folder).

This setup uses Deluge torrent downloader, you can change the collecting task old-deluge according to your input plugins requirements.

Each type (Movies or TV shows) need 2 tasks in order to work:

old-deluge gets the list from the deluge client’s label and creates a list: gotdeluge

old-files gets the files from the filesystem, removes files listed in the gotdeluge list and any that are younger then the 15 days. Remaining media files are moved to the new destination along with subtitle files.

old-deluge Tasks
Replace <deluge config path> with the path to your deluge config folder as explained in the plugin from_deluge.

Change the Deluge label accordingly.

old-files Tasks
Replace <download path> with the path to the location where your files are.

Change age: 15 days to your decided time limit.

Replace <archive path> with the path to the location where your archive is.

Under extensions: you can add other file extension types that if they have the same name will be copied along with the media file.

This setup will move the file types avi|mkv|mp4|m4v change according to your needs.

If the source folder size is under 10mb after copying it will be deleted - change clean_source: from move as wanted. - Be careful

Copying takes time
Do not run these tasks to often - I run once every 24h
May cause a loss of files - Be carful!
I take no responsibility of any damage or anything else anything here may cause - this works on my setup it may not work on yours.
Large number of files may be copied
Large amount of disk size may be moved - Do you have the space?
Large files may be copied
If the file is synced/cloud/… Will your network manage?
The script uses the OS Move - it may fail and cause a loss of data
If you copy to a Null location you may lose your data
Moving files is the same as if you moved them manually - consider how and when to run!


Uses plugins: rss, deluge, no_entries_ok, set, exists_series, tvmaze_lookup, imdb_lookup, template, priority, disable, list_clear, from_deluge, accept_all, list_add, manipulate, seen, filesystem, metainfo_series, list_match, require_field, if, move, metainfo_movie, age
