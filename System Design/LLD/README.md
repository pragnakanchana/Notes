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







