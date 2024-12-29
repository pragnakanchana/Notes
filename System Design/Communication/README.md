# Communication
- what are diff kinds of techiniques to communicate with backend from frontend.

## Short Polling
![image](https://github.com/user-attachments/assets/c71e6ac8-3c11-4d9d-8d83-cc4712f65f23)
- short live connection
- no persistent connection
- less resource utility
- problem with scale
- examples
  - cricket info
  - analytics
  - 
```javascript
const endpointUrl = 'https://example.com/api/updates';
const pollingInterval = 5000; // 5 secs

async function pollServer() {
    try {
        const response = await fetch(endpointUrl);
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        const data = await response.json();
        console.log('Update received:', data);
    } catch (error) {
        console.error('Error fetching updates:', error);
    }
}
// Set up the interval to poll the server
setInterval(pollServer, pollingInterval);
pollServer();
```


## Long Polling
- ![image](https://github.com/user-attachments/assets/9e4abbfe-5da6-4c78-a186-5d7ac475498c)
- Single long live connection, connection might get timedout.
- reduces number of calls than short polling
- Cons:
  - large number of connections, so scaling BE is a problem.
 
- Usecases:
  - real time connections
 

# Web socket
- full duplex communication.
- ![image](https://github.com/user-attachments/assets/2a86f409-72e6-472e-9383-6e18813a750c)
- single long live on TCP connection.
- continuous bi-directional communication
- usecases:
  - trading dashboards
  - online gaming
  - Collab - like google sheets, docs.
 
- Challanges:
  - Hardware - resources - as users increases, number of connections increases.
  - sticky sessions - to handle the case where load balancer should send the request from a client to the same server
  - Scaling
  - Testing and Debugging.
  - resource cleanup - once connection is ended, cleanup resources otherwise it keeps consuming.


## Server Side Events:
- ![image](https://github.com/user-attachments/assets/dbbf031a-68c9-4bb1-af41-cf3aa24e8f2d)
- Long live unidirectional communication
- single HTTP Connection
- use cases: Feeds, notifications, monitoring dashboards.
- Connection is of : keep-live type
- each event comprises of data and id.
- https://developer.mozilla.org/en-US/docs/Web/API/EventSource
- Challanges:
  - browser compatibility
  - connection timeout - handle seperately
  - resource utilisation
  - sticky connection
  - Testing
  - Broadcasting
 

## Web Hooks
- 





