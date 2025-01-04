# Ecommerce

1. Config driven UI
2. Browse and Purchase

# Browse and Purchase
## Functional Requirements
- Browse Product
  - Search
  - Filters
  - PLP
  - PDP
- Add to Cart flow
  - Cart page
  - change quantity
  - price summary
  - Coupons
- Purchase
  - Address Info - delivery promise
  - Bank Offers 
  - Payment Gateway
  - Order confirmation
  - Orders Page
 
## Non-Functional Requirements
- Device Compatibility
- Auth - roled based access - like login to wishlist etc
- i18n
- SEO
- Optimisation
- Security - payment is involved
- Accesibility
- Deployment
- Offline Support

## Architectural Decisions
### View Layer
- PLP
- PDP
- Cart
- Checkout
- in view layer - we can cover design system

### Controllers
- Filter 
- Cart - add, remove, price summary
- Checkout
  - Address
  - Coupons
  - Bank offers
  - 

### Services
- Wrappers which knows which API to call when
- Browse
- PDP
- Cart
- Address
- Checkout
  
### Data Storage
- Redux
- caching - service worker
- indexedDb
- Browser Storage

### Data models
- Product
- Cart
  - CartItem
- Address
- Payment
- Coupon
  etc etc...

### Component Architecture
- first think of reusable components - like rating component, wishlist, ATC,
- always break down into smaller pieces - to make them more modular and reusable - seperation of concerns.

### API Design
- Search/Filters
- product info
- Cart Listing
- Add to Cart
- Place Order
- Payment Gateway API


## Optimisation
- Code splitting
- Lazy loading  - Virtualisation
- ATF
  - defer/async
  - pre-fetch
- Image
  - webp
  - image priority
  - [adaptive loading](https://web.dev/articles/adaptive-loading-cds-2019) - depending on network quality - resolution of images can be set.
 

## SEO
- title, meta tags - with right set of keywords
- sitemap.xml - all the links we want to index to search engine
  - [flipkart](https://flipkart.com/sitemap)
- robots.txt
  - [amazon](https://www.amazon.in/robots.txt)
- canonical tags
- Semantics
- better page speed - better indexing
- SSR is better for SEO
- SSG - Static Site Generation
- CSR is not good but there is a technique ![image](https://github.com/user-attachments/assets/ff6fbbcc-39f5-4965-9d67-159679da240c)
- Shareable Links
  - search/Filters has to be a part of Urls
- Human Readble Urls


## [Internationalization/Localization](https://web.dev/learn/design/internationalization)
- diff countries has timezones, currencies
- in html tag, we can give lang
- RTL
  - direction of reading
  - CSS take care
- Capbility to change language
- showing times - take care of time zones
- 
























