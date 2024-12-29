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



