# SpotifyPlayer
project 3
Documentation
Spotipy's full documentation is online at Spotipy Documentation.

Installation
pip install spotipy
alternatively, for Windows users

py -m pip install spotipy
or upgrade

pip install spotipy --upgrade
Quick Start
A full set of examples can be found in the online documentation and in the Spotipy examples directory.

To get started, install spotipy and create an app on https://developers.spotify.com/. Add your new ID and SECRET to your environment:

Without user authentication
import spotipy
from spotipy.oauth2 import SpotifyClientCredentials

sp = spotipy.Spotify(auth_manager=SpotifyClientCredentials(client_id="YOUR_APP_CLIENT_ID",
                                                           client_secret="YOUR_APP_CLIENT_SECRET"))

results = sp.search(q='weezer', limit=20)
for idx, track in enumerate(results['tracks']['items']):
    print(idx, track['name'])
With user authentication
A redirect URI must be added to your application at My Dashboard to access user authenticated features.

import spotipy
from spotipy.oauth2 import SpotifyOAuth

sp = spotipy.Spotify(auth_manager=SpotifyOAuth(client_id="YOUR_APP_CLIENT_ID",
                                               client_secret="YOUR_APP_CLIENT_SECRET",
                                               redirect_uri="YOUR_APP_REDIRECT_URI",
                                               scope="user-library-read"))

results = sp.current_user_saved_tracks()
for idx, item in enumerate(results['items']):
    track = item['track']
    print(idx, track['artists'][0]['name'], " – ", track['name'])
