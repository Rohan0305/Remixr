
# ![remixr](https://github.com/rtkg12/remixr/blob/master/client/public/logo.png)  
  
  
### Description
Remixr is a smart playlist generator for Spotify that helps users discover new music based on their existing preferences. By leveraging Spotify's powerful API, Remixr allows users to generate personalized playlists from their favorite tracks, artists, or playlists, while fine-tuning parameters like mood, energy, and popularity.
  
### Features - Spotify login  
- Generate playlists based on artist, track or playlist seeds  
- Generate playlists based on personal playlist as a seed  
- Tune parameters like popularity, mood, energy, etc. to further customize the playlist  

## Algorithm to generate similar playlists

 - Feature range calculation
	 1. Get all tracks in the playlist from the Spotify API
	 2. Query Spotify for different track features
	 3. Calculate the 0.1 and 0.9 quantile range for each feature
	 4. Use these as min and max targets for each feature
- Extract most relevant artists and tracks as seeds
	1. Find the frequency of artists and tracks in:
		- Playlist
		- User profile / listening history: short, medium, long term
	2. Select most frequently appearing artists and tracks that exist in the playlist
- Query Spotify API with the calculated seeds and parameter values
  
## Installation  
  
### Clone  
  
	 git clone https://github.com/rtkg12/remixr.git  

### Pre-requisites  
  
1. Make a developer account at https://developer.spotify.com and obtain the `Client ID` and `Client Secret`  

2. Update `client/.env` and `server/app.env` accordingly.

|Property| Description  |
|--|--|
| REACT_APP_API_URL | Use `/api` for default configuration. Replace with backend server address for custom deployment |
|REACT_APP_TRACKING_ID|`optional` Google Analytics Tracking Id |
|CLIENT_URL|Address of the client application|
|REDIRECT_URI|Callback endpoint for Spotify authentication. `Note` Make sure this matches the Redirect URL in the Spotify API console|

3. Go to the Node.js website and download the latest LTS version (which is the most stable). Node.js is required to run the JavaScript server and manage project dependencies.
After installing, run the following command to ensure Node.js is installed:

    node -v

4. Download/Install Yarn: Yarn is a package manager used to install and manage dependencies. Install it globally by running:

    npm install -g yarn

Check Installation: After installation, run the following command to verify Yarn is installed:

    yarn -v

You should see the Yarn version printed (e.g., 1.x.x or 3.x.x).

### Installation

	yarn install

### Building and developing locally

#### Configuration
 
 |Environment variable| Value  |
|--|--|
| REACT_APP_API_URL | `http://localhost:8080/api` |
|CLIENT_URL|`http://localhost:3000`|
|REDIRECT_URI|`http://localhost:8080/api/callback`|

#### Running the project	
	yarn develop

The React app should start running in port `3000` and the Node.js app will be running in `8080`

### Deploying to Production

#### Configuration
 
 |Environment variable| Value  |
|--|--|
| REACT_APP_API_URL | `/api` |
|CLIENT_URL|`http://PUBLIC_URL`|
|REDIRECT_URI|`http://PUBLIC_URL/api/callback`|

#### Deploying
	yarn deploy

This will build the React app and serve the build folder from Express. Express should be running in port `8080`

## Future Areas of Improvement

- Add support for greater than five seeds using random sampling from generated playlists
- Functionality to add individual songs to library directly from the app
- Regenerate, re-order and edit the playlist dynamically before saving
- Session-wide playlist building. Add songs from multiple queries, save in the end
- Algorithm improvements - different statistical measures, collaborative filtering

## Contribute

Please feel free to open an issue/pull request if you wish to work on any of the above features, or if you have any other suggestions for improvement.



