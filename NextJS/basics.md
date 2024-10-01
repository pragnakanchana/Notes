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

### Special Files
- page.tsx
- layout.tsx
- template.tsx
- not-found.tsx
- loading.tsx
- error.tsx
