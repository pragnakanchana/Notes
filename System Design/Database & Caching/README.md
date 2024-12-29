# Database & Caching


## Local Storage
- What ? - storage to store data persistently on user device.
- How it works ? - setItem, getItem, removeItem, clear. 
- Size Limit - approx 5MB per domain(irrespective of how many tabs its in).
- Performance - Synchronous
- Data persistence - persists across browser session, and tabs closure.
- Data Structure - key, value pair - value is always  a string
- Security - encryption is needed, CORS, 
- when to use - user preferences - like theme, non sensitive data,
- When not to use - large dataset (takes a perf hit), Auth token, cross profile info(eg netflix -- needs extra handling).

## Session Storage
- What ? - storage to store data persistently
- How it works ? - setItem, getItem, removeItem, clear. 
- Size Limit - approx 5MB per domain(irrespective of how many tabs its in).
- Performance - Synchronous
- Data persistence - cleared when browser session ends - tabs close, window close etc.
- Data Structure - key, value pair - value is always  a string
- Security - encryption is needed, CORS,
- when to use - temporary, sensitive data
- When not to use - large dataset (takes a perf hit), not for any async operation, avoid for data storage for long duration.

## Cookie Storage
- What ? - storage to store data persistently
- How it works ? - data can be set by server or client, can be transfered via HTTP calls.
- Size Limit - 4kb per domain
-  two types of cookies - session cookies
  - session cookie - expires as soon as tab/browser is closed.
  - persistent cookie - we can define cookie expiry, 
- Performance 
  - since cookies are transfered via HTTP calls.
- Data persistence - each cookie will have definite expiry or when browser is closed(in case of session cookie)
- Data Structure - key, value pair - value is always  a string
- Security - better to configure expiry, 
- when to use - majorily used for authorization, or any data that we want to flow to server.
- When not to use - large dataset (takes a perf hit), no sensitive information,


- on logout, when you want to delete all the info in cookies, and other storages - a header can be used -  Clear-Site-Data


## Indexed DB:
- What ? - storage to store data persistently
- How it works ? - asynchronous way, 
- Size Limit - > 100MB, large datasets can be stored.
- Performance 
  - it's asynchronous, non-blocking operation
  - helps create indices to search
- Data persistence - persist across sessions.
- Data Structure - key, value pair - value can be any strucutre, including blobs, files. 
- Security - encryption is required, data has to be cleared on logout.
- when to use - large set, data cache, offline support, lot of history.
- When not to use - secure data, not for small data, any sync operation - avoid indexedDB.
- libraries like duksie can be leverage to use indexdb in a easy/dev friendly way.


# Normalization
- flattening of nested data structures.
- keeping entities seperately.
- have relationships among entities with unique ids.
- Benefits:
  - removes redundancy.
  - Efficiency.
  - complexity of lookup gets optimized.
  - simplifies nested relationships.
  - updations would be easy
 
# Caching

## HTTP Caching
- driven by headers
- Cache-control (p0)
- Expires(p1)
- Last-Modified(P2)
- ETag(P2)


## Service Worker
- proxy between browser and network layer
- ![image](https://github.com/user-attachments/assets/b27b8e18-6686-433f-a968-061ba27b24bc)
- Register service worker
  - installing -> installed -> activating -> activated -> work 
- while installing - add all the urls for which cache has to be enabled.
- register a event while captures all the fetch requests and checks in cache before triggering the network calls.

## API Caching
- ReactQuery - have caching strategies
- SWR
- Apollo Client


## State Management
- In memory store - reloading will erase
- libraries - Redux, Mobx, Context API(React), VueX, NgRx, Zustand(React). 

























