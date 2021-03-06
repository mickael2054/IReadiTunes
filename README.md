# IReadiTunes
Tool to get any information about iTunes tracks and playlists quickly and easily. 

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install IReadiTunes.

```bash
pip install IReadiTunes
```

## Example code

```python
import IReadiTunes as irit

# First of all, init the library
my_lib = irit.lib_init()

# Read iTunes XML file
my_lib.parse(r'path\to\file\iTunes Music Library.xml')

# Get name of playlists
lib_list = my_lib.get_playlist_list()

print("iTunes playlists: ")
for itunes_library in lib_list:
    print("\t" + itunes_library)  # Print name of each playlist

lib_to_analyse = ""
while lib_to_analyse not in lib_list:
    lib_to_analyse = input("Enter name of library you want to analyse: ")  # Prompt the user to enter the name of the playlist to be scanned. 


playlist_with_attributs = my_lib.get_playlist_contents(lib_to_analyse)  # Analyse choosen playlist

print("\n{} playlist content:".format(lib_to_analyse))

# Print attributs of each element stored in the given playlist
nb_of_tracks = len(playlist_with_attributs)
track_ind = 0 
for track in playlist_with_attributs:
    print("Track [{}/{}]:".format(track_ind+1, nb_of_tracks))
    print("\ttrack_id: {}".format(track.track_id))
    print("\tsize: {} Mb".format(irit.get_size(track.size)))
    print("\ttotal_time: {} seconds".format(irit.get_total_time(track.total_time)))
    print("\tdate_modified: {}".format(track.date_modified))
    print("\tdate_added: {}".format(track.date_added))
    print("\tbitrate: {} kbps".format(track.bitrate))
    print("\tsample_rate: {} kHz".format(track.sample_rate))
    print("\tplay_count: {}".format(track.play_count))
    print("\tplay_date: {}".format(track.play_date))
    print("\tplay_date_utc: {}".format(track.play_date_utc))
    print("\tskip_count: {}".format(track.skip_count))
    print("\tskip_date: {}".format(track.skip_date))
    print("\trating: {} stars".format(irit.get_rating(track.rating)))
    print("\talbum_rating: {} stars".format(irit.get_rating(track.album_rating)))
    print("\tpersistent_id: {}".format(track.persistent_id))
    print("\ttrack_type: {}".format(track.track_type))
    print("\tfile_folder_count: {}".format(track.file_folder_count))
    print("\tlibrary_folder_count: {}".format(track.library_folder_count))
    print("\tname: {}".format(track.name))
    print("\tartist: {}".format(track.artist))
    print("\tkind: {}".format(track.kind))
    print("\tlocation: {}".format(irit.get_track_path(track.location)))
    print()
    
    track_ind += 1
```

## Features

 - Fast library decoding
 - Simple, easy to understand code.


## Contributing

All contributions are welcome. Do not hesitate to contact me in case of bugs or ideas for improvement.

## License

[MIT](https://choosealicense.com/licenses/mit/)