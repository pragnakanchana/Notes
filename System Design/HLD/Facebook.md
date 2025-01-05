# News Feed

## Requirements
### Functional Requirements
- `< same like instagram >`
### Non-Functional Requirements
- `< same like instagram >`
### System Architecture
- `< same like instagram >`
### Data Models

### Implementation Details
#### Rendering & Optimisation
- SSR - for first page
- CSR - for next pages or after scrolls
- **Ininite Scroll (Pagination)**
  - Cursor Pagination is preffered. `{ cursor, size }`
- In case if user comes back to a stale page, 2 options can be done
  1. give user an option to refresh like a floating icon
  2. refresh automatically.
- **Infinite Loading**
  - when to fetch next page, diff ways can be implemented
  - ScrollEvent - above 50px or 100px above
  - Intersection Observer API
  - 
- **Virtualisation**
  -   less browser painting
  -   Virtual DOM Reconciliation is faster
  -   light-weighted real DOM.
- Shimmer - for better perceived performance
- Preserving scroll postition
- **Mentions & HashTags**
  - Input or TextArea - doesn't work
  - insted a div with [contentEditable](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/contenteditable) is better
  - use WYSIWYG editor libraries are better - like draft.js
  - hashtags - parser and customRendering
  - mention - userId and mention name can be mapped - can be stored in data store
 
- **Optimistic Updates**
  - when we click on post, it doesn't wait for server to get back and then show to user.
  - instead on local,  create a temporary id and make a requestId corresponding to this temporary id.
  - improving perceived performance
  - libraries like reactQuery, apollo client are supporting optimistic updates
 
- **TimeStamp Updates**
  -  Relative Times - on slack/facebook - we show "1min ago" or "1hr ago" - to show this network call doesn't happen in intervals, Instead computation is done on client with the cached data.
 
- **Icon/Image rendering**
  - SVG
  - `<read more>`
- **Comments**
  - cursor based pagination
  - optimisitic update
  - lazy loading
  - recursion for rendering

