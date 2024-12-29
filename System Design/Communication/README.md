# Communication
- what are diff kinds of techiniques to communicate with backend from frontend.

# Short Polling
- ![image](https://github.com/user-attachments/assets/c71e6ac8-3c11-4d9d-8d83-cc4712f65f23)
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

