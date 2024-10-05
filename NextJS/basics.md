# Routing
### Folder Structure:

- .next folder is generated when dev or build is run, it's from this folder, Next JS application is served.
- a folder can be made private and exclude from routing - by adding prefix of _ to folder name
- otherwise, have normal name and donot have page as component file name
- route groups - groups all the route folders into one and rename folder enclosing with ().
	- helpful when we want to have same layout - header and footer etc to a set of routes. - by nesting this folder structure.
- Layouts
- routing metaData - helps with Search Engine Optimisation
	- export constant if it's static 
	- export generateMetaData if it's dynamic - can be async also
- programatically navigation - like on click of button
	- useRouter hook returns router and by just pushing page into nav stack when can open
- layouts
	- re-renders the only changed part and common components keeps it same.
	- if we want to re-render the common components or create a seperate instance, then use **templates** instead of layouts <img width="925" alt="Screenshot 2024-10-01 at 5 46 54 PM" src="https://github.com/user-attachments/assets/6b06b903-3e5f-4802-b162-d69da8a1e441">
 	- filename : template.tsx
- loading
	- speacial file - to show loader to user
- error.tsx
	- special file - client side component that renders error view when we throw an error.
   	- same as Error Boundary - any unhandled exception would render Error.tsx
   	- only the affected part of page is shown error screen and can be recovered easily.
   	- recovering
   	  	- by sending reset callback to error component and onclick triggering it.
   	- handling errors at layout level : have one error.tsx at the parent of layout.tsx 

### Special Files
- page.tsx
- layout.tsx
- template.tsx
- not-found.tsx
- loading.tsx
- error.tsx
- default.tsx - for unmatched routes
<img width="845" alt="Screenshot 2024-10-01 at 5 55 52 PM" src="https://github.com/user-attachments/assets/23189804-b58d-4c7c-961a-c6c121582c9f">

### Parallel Routes
- are created using names @slots - folder name convention - prefix @
- each section (route) can have it's own loading and error screens.
- easy to maintain
- can navigate to specific routes of a section
- **Un-matched Routes:**
	- have default.tsx file


### Intercepting Routes
- for scenarios like, opening login modal by changing route.

### Route Handlers
<img width="919" alt="Screenshot 2024-10-02 at 12 06 15 AM" src="https://github.com/user-attachments/assets/054f9694-9757-4827-bab3-b0d77ffdd3b2">

- route.ts - naming convention - export GET method and return response using Response()
- GET and POST Requests etc - export methods
- query parameters can be extracted with request object
- redirects - when route is not found - using redirect('')
- headers - can be read from Request Object

#### Caching with Route Handlers
- by default, on prod build - caching is on.
- Segment Config Option - to opt out caching

### Middleware
- to add , match or modify requests or response.

# Rendering
- CSR:
- <img width="839" alt="Screenshot 2024-10-02 at 1 23 48 AM" src="https://github.com/user-attachments/assets/cbb6f4c2-19aa-4ee0-bd6f-190d725e1921">
- Drawbacks:
	- SEO Optimisation
	- Performance - client heavy
- SSR:
	- SEO Optimised
	- Hydration - (static html page which is served initially is brought to live by downloading JS files).<img width="1338" alt="Screenshot 2024-10-02 at 1 28 38 AM" src="https://github.com/user-attachments/assets/d9b8ee6c-a249-496d-9b79-af4a07ed2162">
	- SSR can be categorized into two solutions:
		- SSG - Static Site Generation
		- SSR - Server Side Rendering<img width="1320" alt="Screenshot 2024-10-02 at 1 30 37 AM" src="https://github.com/user-attachments/assets/8a044bcd-5e79-4e2e-9904-17b342bb9b09"> <img width="1339" alt="Screenshot 2024-10-02 at 1 31 06 AM" src="https://github.com/user-attachments/assets/9a256ef8-d99b-42aa-bd54-dfa9735557c8">
  <img width="851" alt="Screenshot 2024-10-02 at 1 31 56 AM" src="https://github.com/user-attachments/assets/e87a954c-e053-413c-a660-e1b9c3785b01"> 
<img width="900" alt="Screenshot 2024-10-02 at 1 32 28 AM" src="https://github.com/user-attachments/assets/47b12db4-2c33-495d-b018-6a2ffee21402">
	- Drawbacks:
 		- having to load data for the entire page.
     		- having to load entire JS for the page.
         	- having to hydrate entire page
          - these lead to "All or Nothing" waterfall problem.
- Suspense SSR:
	- helps with selective hydration when we don't want entier page to load only when entire hydration happens. instead, we can add selective hydration by wrapper few components in suspense and giving a fallback component until that hydration piece is done.
 	- Suspense along with code splitting works better - downloading JS bundling in parts
  	- traditional problems with SSR are addressed with Suspense SSR.
  	- Drawbacks with Suspense SSR:
  		- Does users really have to download lot of data (JS) ?? - perf on low end browsers.
  	   	- Should all the components be hydrated even those who doesn't need interactivity ?
  	 
- Server Components:
	- dual-component model: - client components & server components
	- Client Components:
 		- rendered on client side. but can also be sent from server as html to improve perceived performance.
		- have access to client environment like cookies, local storage, useState, useEffect etc so that you can build components for specific usecases.
    	- Server Components:
		- code resides on server and is never downloaded to browser.
		- Benefits:
  			- Reduced Bundled Sizes.
       			- benefits users with low network, not having the need to download, parse and execute JS.
            		- removes hydration step.
                	- efficient with data fetching as server side has access to databases or file systems.
                   	- leveraging computation power of servers.
                   	- security with API keys
                   	- enables caching on server side, reduces costs, speeds up delivery of content.
                   	- Initial Page load and FCP are significantly improved with server components.
                   	- Improved SEO - fully accesible by search ENgine bots.
                   	- users starts seeing partial parts of page.
- RSC Loading Sequence:
  	- <img width="1300" alt="Screenshot 2024-10-03 at 12 50 19 AM" src="https://github.com/user-attachments/assets/31f6c1e3-661b-4e16-ac20-7eaa354b9faa">

## Rendering Strategies
- rendering strategies
	- static rendering
	- dynamic rendering
	- streaming

 #### Static rendering
 - html is generate while build phase, cached and served by cdn.
 - default rendering strategy

### Dynamic Rendering
- by using cookies(), header() etc - we can make a route dynamic
- <img width="1369" alt="Screenshot 2024-10-05 at 6 14 19 PM" src="https://github.com/user-attachments/assets/ceff752f-893a-49db-bc59-888838dce50c">

### Streaming
- progressive UI rendering from server
- work is divided into chunks and delivered to client so that parts can be rendered without having to wait for entire page
- significantly improves initial page load performance
- important and can be great with async components.

## Server and Client Composition Patterns
- server components:
	- Fetching data
   	- Directly accessing backend resources
   	- security for APi keys etc
   	- heavy pieces helps reduce client side javascript
- client components:
	- interactivity
   	- handling event listeners
   	- accessign hooks - browser side things
   	- browser APIs
   	- custom hooks
   	- react class components

### Server only code:
- to avoid server only code to get bundled with client side js when called from client component - we can use server-only package

### Context Provider:
- have a component for provider - client component and render children in it

### Client-only Code:
- interactivity
- interation with DOM
- by including client-only package, we ensure during build time it throws an error if by mistakely included in server components. 
- Third party libraries which are using client things, can be used with "use client" tag and called from server components.

### Client Component Placement
-  when a component is created as server component, by default all of it's children in that subtree becomes client component. so it's advisable to have client components at the leaves.

# Data Fetching
- components can be written as async components
- next js automatically- by default caches fetch result - data cache
- opting out of data cache - cache - "no-store". If a request is mentioned as no-store cache, it doesn't cache the later fetch requests in the components.
- nextjs doesnot cache any fetch request which is mentioned later dynamic functions (cookies(), searchParams())

## Request Memoization
- eliminates duplication of same network calls
- <img width="1065" alt="Screenshot 2024-10-06 at 4 07 38 AM" src="https://github.com/user-attachments/assets/9de3a7f6-4b45-487f-b55f-673ff74a429f"><img width="1330" alt="Screenshot 2024-10-06 at 4 09 43 AM" src="https://github.com/user-attachments/assets/576c4e6d-323d-4349-87f7-81f8238fb905">
- cache timing can be set by revalidate
- 


