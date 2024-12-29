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
  - 
- Data persistence - each cookie will have definite expiry or when browser is closed(in case of session cookie)
- Data Structure - key, value pair - value is always  a string
- Security - better to configure expiry, 
- when to use - majorily used for authorization, or any data that we want to flow to server.
- When not to use - large dataset (takes a perf hit), no sensitive information,


- on logout, when you want to delete all the info in cookies, and other storages - a header can be used -  Clear-Site-Data

