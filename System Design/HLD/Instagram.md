# Photo Sharing App
- categorize the problem statement into two.
- functional and non-functional requirements

## Functional Requirements
- (in mind chatter) Posts - photos/videos/short videos, Comment, like, follow, unfollow, feed sections - list of posts along with suggested posts, grid of posts, stories, chat, calls, sharing posts, live
- Feed Management
  - List
  - Create Post
- Reels Management
  - list
  - create reel
- Story
  - list
  - add story
  - live
- Browse
- Chat Management
  - DMs
  - Group Chats
- Profile Management

## Non functional Requiremnts
- Device Support
- Security
- Auth - role based access.
- SEO
- Optimisations
- Accesibility
- Offline Support
- Testing

## Design
### Data Store
### APIs and Data Models
### Component Structures
### Optimisations
- On a high level optimisations can be done in two areas - assests and rendering
- assests:
  - images:
    - webp format.
    - srcset - based on network quality render resolution
    - userAgent - based on browser OS 
    - dpr - device pixel ratio
    - network connectivity - 2G/3G etc
    - Pre-fetching - make network call prior to it's usage
   
- Rendering
  - SSR for Above the Fold (ATF).
  - Infinite Scroll with Vitualisation (Intersection Observerable)
  - Code Splitting
  - Shimmer - for perceived performance
  - Web workers
  - Optimistic Updates.
 
### Implementation
- Image Editing
  - Crop / Resizing
    - canvas API
   
- Filters
  - CSS - photo editing app can be built
  - 
- Upload File
  - HTTP Post - (multipart/ form-data)
  - Base 64 encoding
  - File Chuncking / resumable uploads
  - 




























