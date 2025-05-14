# Video Streaming Apps - Netflix/Youtube

## Functional Requiremtns
**think from both supply and demand povs**
**Supply**
  - Video upload
  - Analytics
  - Meta Info
  - Tagging
    
**Demand**
*Module Level*
- Multi Porfile Model
- Account management
- Auth Model
- Subscription Model
- Videos Catalogue
- Detail Page
- Watch list

*Feature Level*
- Home
  - Lang choice
  - sign in /sign up
  - configuration UI
- Multi User Management
  - switching between profiles
  - Parental Control
- Catalog
  - Search
  - Card Preview
  - Banner Preview
  - Mini VDP
  - Video Page
- Browse Videos
- Autoplaying hero banner
- Video Playing
  - play/pause
  - forward
  - timestamps
  - playback rate
- Audio
  - mute/umute
  - reduce or increase volume
  - changing language
- Subtitle
  - turn on/off
  - language specific
 
## Non Functional Requiremtns
- Video Optimisation
  - supporting multiple resolutions
  - Network based resolutions - auto shifts while playing
  - Fast Video startup
- Resource Hinting
- Open Graph Tags
- Deep links
- Page Performance
- Device Support - Mobile & Desktop
  - Protocols would change depending on OS
- Auth
- Security
- Caching
- Offline Support
- A/B Testing
- Responsive behaviour
- User Demographics
- 2 way pagination
- Config driven UI
- Internationalisation/localisation

## Tech Choices
- React JS
- RxJS
- TypeScript.js
- Restify instead of express js
- Falcor GraphQL
- Build tools - webpack
- Dependencies
  - image blobs / Sprite / SVGs
  - Video Tags - HTML5 / Media Sources
  - HTTP1.1/2/3
- Streaming

## Video Streaming Terminologies
- **Streaming**
  - download chuncks instead of entire video at once - smaller chuncks are consumable
- **Buffer**
  - getting future chuncks ahead
- **Bitrate**
  - the amount of data that can be transferred within a sec
  - when it's 2G - low bitrate and for 4G - its higher
  - higher the birate - higher the resolution
- **Frame Rate**
  - need higher frame rate
  - more the framerate - less jerky experience
- **Resolution**
  - user can set resolution - 480, 1080, 1440p etc
- **Codec**
  - audio and videos are encoding and decoding while transferring
- **Bandwidth**
  - 100mbps, etc - how many MBs or GBs of data can be downlaoded per sec.
- **Poster**
  - Thumnails
- **Closed/Open Caption**
- **Playback Controls**
  - controls - play/pause/mute/resollution set/
- **Seeking**
  - click on any part of the video
- **Scrubbing**
  - dragging the control of the video
- **Manifest File**
  - Metadata related to the chunk
  - the chunk packets are independent
  - timestamps from and to the chunk serves
- **SubTitle File**
  - SRT - Transcript with timestamps.
  - TTML - time text markup language
  - SCC - Closed Captions
  - WebVTT 


 ## Architecture
 - **Views**
   - Hero Section
   - Video Player
   - Video List
 - **Controller**
   - Video Player
     - take care of understanding Bandwidth etc.
   - Video Recommendation
 - **Services**
   - Video Player
   - Video Recommendation
 - **Data Storage**
 - **CDN on Backend**

## Implementation
- Hero Section
  - one fetched, cache it
  - netflix uses GraphQL - apollo client
- Video Players
- Netflix has both vertical and horizontal Scrolls
  - two way pagination
- Video Player
  - HTML `<video>` tag
  - mediaSource API
  - libraries - chrome MediaPlayer, VideoJS, Shaka Player (open source)
  - 
 
## Data models
```
Recommendation{
   VideoSectionList[], offset based pagiantion (data doesn't change frequently) {pagenum, limit} 
}

VideoSectionList{
  category
  Videos[], offset based pagiantion (data doesn't change frequently) {pagenum, limit} - horizontal pagination
}

Videos{
  thumbnail
  id
  title
  videoPreviewUrl
}
```

















