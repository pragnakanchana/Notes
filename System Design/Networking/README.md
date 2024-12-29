# Networking

## How web works
- DNS - Domain name server - which gives ip for a domain.
- ![image](https://github.com/user-attachments/assets/4e0324d9-ea42-4b64-b594-e674ba3f15d8)
- ![image](https://github.com/user-attachments/assets/11a6e5e5-b89c-4548-ac56-287048c5aa71)
- how do we connect with servers which are very far
        - can be done through satellite communication
        - wired connections - optical fibres - ![image](https://github.com/user-attachments/assets/18450fe5-d140-4de7-a99b-fba6d6efa323)
        - ![image](https://github.com/user-attachments/assets/f23862e4-8bfc-4687-a3f2-e5525fe6725a)
- while making network calls, browsers can make x number of requests, all requests other than x are stored in a queue and processed.
- Browser rendering:
  ![image](https://github.com/user-attachments/assets/ddb71c3b-7b46-4301-93b8-14bbf376b8a3)
- ![image](https://github.com/user-attachments/assets/e9bb82aa-c9b5-475d-b70f-ca953333bd03)
- [learn here](https://web.dev/articles/howbrowserswork)

## Communication Protocols
### HTTP - Hypertext transfer protocol
- first it makes tcp connection
- req
- response
- ![image](https://github.com/user-attachments/assets/d0479553-8882-4a22-bebc-393c31440b97)

### HTTP3 
- youtube uses
- with udp connection
- faster, improves performance
- has header compression
- better network congestion
- 

### TCP
- three way handshake
- ![image](https://github.com/user-attachments/assets/1bba2782-4852-4dcb-b6fe-fdd7bb604f44)
- makes sure non of the data packages are missing

### UDP
- for faster communication
- useful for Video conferencing

### HTTPS
- ![image](https://github.com/user-attachments/assets/26bad7af-9d9a-4e04-a406-22c80c737504)

### Web socket
- full duplex connection

### SMTP
- to send and receive emails.

## REST APIs
API - application programming interface
- internally rest uses HTTP protocol
- Benefits
  - ease of use.
  - Stateless -
  - Scalability
  - Flexibility with Data
  - Uniform Interface - to read data from URL (HTTP's )
  - Caching - HTTP
  - Seperation of concerns
  - Interoperability - lang agnostic
  - ease of testing
  - security
 
- Building Blocks
  - structure of request and response
  - request:
    - HTTP request line (url)
      - Schema - HTTPS/HTTP/HTTP3
      - ![image](https://github.com/user-attachments/assets/692df212-315c-45a2-a359-7015162425a2)
      - fragment doesnt get sent from client to server.
    - request headers
      - host - target host
      - origin -
      - referrer - indicates the prev web page which is making request
      - user-agent - client info - browser/os.
      - accept - response content type
      - Accept-language - response content language.
      - accept-encoding - encoding algorithm
      - connecton - to keep the tcp connection open - to eliminate hand shake for further requests. values - keep alive/close.
      - authorization - send credentials
      - cookies -
      - if-modified-since
      - cache-control - http caching 
    - request body
  - response:
    - response status line
    - response headers
      - date - on which response is generated.
      - server - may be lead security risks - so donot disclose
      - content-type - type of response
      - content-length - response length
      - set-cookie - cookie that needs to be stored for future - eg: in case of signup.
      - content-encoding - response content encoding
      - if-modified-since
      - cache-control - http caching
      - eTag
    - response body
  - Status Codes:
    - https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
    - ![image](https://github.com/user-attachments/assets/a5f58bd9-c156-4c35-b5cc-30f3a253f422)


## GraphQL
- ![image](https://github.com/user-attachments/assets/01fa0455-2c0f-4da5-be51-1ae762d47f4b)
- Graph Query Language
- At its simplest, GraphQL is about asking for specific fields on objects.
- Benefits
  - avoids over fetching
  - avoids under fetching
  - better mobile performance
 
- Http concepts remains same
- REST vs GraphQL:
  - <img width="737" alt="Screenshot 2024-12-29 at 2 18 09 AM" src="https://github.com/user-attachments/assets/ca2daf45-ec30-4029-bcd1-74cddf858e49" />
  - In a system like REST, you can only pass a single set of arguments—the query parameters and URL segments in your request. But in GraphQL, every field and nested object can get its own set of arguments, making GraphQL a complete replacement for making multiple API fetches.

- Building Blocks
  - Schema/Types:
    - schema is like types in typescript. - also known as schema definition language.
    - data types:
      - two types: scalar and custom
      - scalar
        - ID, String, Int, Boolean
      - custom:
        - eg: Comments, POsts, Countries etc - custom defined ones.
       
  - Query/Mutation:
    - Query: to get the data.
    - Mutation: to update the data.
   
  - REsolvers:
    - functions which resolves the query.
   
- Official Docs is very clear


## GRPC:
- Google remote procedure call.
- uses HTTP2
- data that is transfered needs to be serialized using protocol serialization technique.
- Bi-directional streaming. ![image](https://github.com/user-attachments/assets/95bd61a3-f5e2-46f8-8062-7efa40fd3077)

- one tcp connection and bi-directional streaming can be done with that one connection.
- Protocol Buffer (ProtoBuff) - (by google)
  - it's an IDL - Interface Definition Language.
  - hanldes serialisation/deserialisation.
  - binary support - data is transeferred in a binary way - making it faster.
  - extension - .proto (proto3)
 
- Benefits:
  - using proto buf, since it's binary data - uses less  CPU resources.
  - faster.
 
- Compared to REST
  - it handles serialization, and it's language agnostic.
  - it's efficient - 10x faster than REST.
  - more secure.
  - 



  





     
  



