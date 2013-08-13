# MPD Album Art

Python module to query current MPD song, and find an album art match from local filesystem or LastFM.

## Install
```sh
$ pip install mpd-album-art
```

## Example Usage
#### Play some jams
Start up your MPD session as normal, e.g.
```sh
$ mpd
```
Take note of which port it's running on (normally `localhost:6600`).

### With the commandline script (the easy way)
```sh
$ mpd_album_art.py -n localhost -p 6600 -m ~/music/ -a ~/.covers -l current
```

### With the Python module (the manual way)
#### Hook up to the MPD server
```python
import mpd_album_art, mpd
# Open an MPD client
mpd_client = MPDClient()
# Connect to MPD session
mpd_client.connect("localhost", 6600)
# ...
```
#### Find what's making those groovy vibes
```python
# ...
song = mpd_client.currentsong()
# ...
```
#### Grab some art
Artwork is saved to `save_dir`
`library_dir` should be where your music files are (this is used in `Grabber.get_local_art`)
```python
# ...
grabber = mpd_album_art.Grabber(
    save_dir="/home/jamie/.conky/scripts/album_art",
    library_dir="/home/jamie/Music/Library"
    )
grabber.get_art(song)
```
Now, if the album isn't too *obscurely titled*, you should have its artwork in `save_dir`
saved as something like `"Artist_Name_Album_Name_h4sh.png"`.
And a symlink should exist in there saved as `"current"` pointing to it.

You can also check your local filesystem for artwork in the music directory:
```python
grabber.get_local_art(song)
```
This will create a symlink called `"current"` in `save_dir` pointing to the largest image file in the directory

Issuing these commands when there's no **music pumping** will remove the symlink.
