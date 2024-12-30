## Component Design
- we want the design to be
  - MODULAR
  - READABLE
  - REUSABLE
  - TESTABLE
- SOLID Principles
  - S - Single Responsibility Principle - applicable for components - keep componnets as simple as possible.
 
- Higher Order Components
  - takes in a component and returns a component.
 
- Lazy load components

## Config Driven UI
- UI is built in a way that It's mostly driven by BE.
- Config holds the layout
- Dynamic UI - same code - multiple UI looks.
- flexible
- without deployment - UI changes


## Shimmer UI
- Improves perceived performance
- shows dummy cards

## Routing
- Routes impact SEO, SEO tracks pages with Routes.
- donot change/migrate routes to one another - x/z to x/y/z etc - cause people might have already bookmarked the pages. - to handle this redirection is not a go to approach.
- keep routes as simple as possible
- Protected Routes - How to handle
  - naive way - have a isAuthenticated bool at parent level and have checks to render.
  - donot have authentication checks or logic where routes reside.
  - rather, have a wrapper - and add outlet only when user is authenticated, outlet is the place where children is rendered.
  ```javascript
  <BrowserRouter>
        <Routes>
          <Route path="/" element={<Body />}></Route>
          <Route element={<ProtectedRoute />}>
            <Route path="/team" element={<Team />}></Route>
          </Route>
          <Route path="/about" element={<About lang={lang} />}></Route>
        </Routes>
      </BrowserRouter>
  ```

  ```javascript
  import { Outlet, Navigate } from "react-router-dom";

  const ProtectedRoute = () => {
    // Write Authentication Logic
    // Make login APi call, ceck if token valid
    const isAuthenticated = false;
  
    return isAuthenticated ? <Outlet /> : <Navigate to="/login" />;
  };
  export default ProtectedRoute;
  ```


## State Management
- FE application has 2 layers
- presentation layer - UI - it is controlled by data layer
- Data layer -
- why do we need state management library


## Infinite Scroll
- window.scrollY + body.innerHeight >= document.body.scrollHeight
- if the above condition is true, trigger API calls to get next page data.

## Reddit Nested Comments
```
type Comments {
  userName: string,
  displayText: string,
  replies: Comments[] | null,
}

type data {
  comments Comments[]
}
```
- render in a recursive fashion

## Slider
- setInterval for auto scroll
- for left and right clicks - write diff functions which will update activeIndex state.

## Pagination
- pagination vs infinite scroll
- pagination is choosen
  - when footer is there
  - friction is more
  - (by pagination it's about having page numbers at the bottom etc)
 
- Infinite scroll is choosen
  - when data is real time - social media
  - addictive - instagram
  - Bad for SEO

- Frontend Pagination vs Server side Pagination
  - frontend pagination
    - fetch all data at once.
    - keep the data in local store or redux - somewhere
    - show 10 per page
    - pros:
      - changing page - no network lag, better user experience. - page change is faster.
    - Cons:
      - initial load time is high.
      - data is huge, can make browser slow.
      - not recommended for huge amounts of data.
      - no on-demand fetching.
   
  - Server side pagination
    - make api call per page
    - Pros;
      - works good on large data.
      - initial load time - less
      - on-demand fetching
      - doesn't hit performance when implemented properly.
    - Cons:
      - more num of API calls on each page call.
      - make API calls for sorting, filtering etc.
      - backend dependency is huge.
    - Technique: - Offset pagination
      - pageNumber and count can be sent - so that backend knows how many products it should send.
     
- Cursor Pagination
  - issues with offset pagination
    - if the ordering of data chagnes very frequenctly, there is a chance of skipping some data, or duplicaiton or missing.
  - cursor pagination:
    - from facebook
    - good for Real time - dynamic data
    - no skipped/missing entries
    - faster than offset pagination
   
    - 
     



































