# Berries Clothing

A fashion e-commerce storefront built with *Next.js 16 (App Router), **React 19, **TypeScript* and *Tailwind CSS v4*, inspired by the layout of large online fashion retailers. The UI and content are in Romanian.

> Learning project. It is not a real store and is not affiliated with any retailer or brand shown. Brand names, logos and product images are used only for demonstration.

## Features

- *Section pages* for Women, Men, Kids and Home, each with video/image hero banners, product carousels and promo blocks
- *Responsive header*
  - On desktop: help links, category tabs and a mega-menu that opens on hover
  - On mobile: a hamburger menu that opens an overlay panel
- *Context-aware navigation*: links are built from the current URL section (/mens/..., /womens/...), so the same header works on every section
- Product listing with filters: filter by category, brand, color and size. Choices are staged as a draft and applied with an Accept button. Results are computed with useMemo.
- *Search* through the ?query= URL parameter, matched against brand and product name
- *Carousels* (shadcn/ui + Embla) for products and a looping brand-logo slider, with swipe on mobile and arrows on desktop
- *Reusable promo components* (picture, video and double-picture) driven by typed props interfaces
- *Mobile-first styling* with Tailwind breakpoints. The codebase is being migrated from CSS Modules to Tailwind.

## In development

### User accounts

- Sign-up and sign-in screens
- Passwords hashed with bcrypt and never stored in plain text
- JWT-based sessions in httpOnly cookies
- Protected routes for account pages such as the wishlist, cart and order history

### AI styling assistant

A chat assistant that helps shoppers put together outfits:

- Suggests outfits for a specific time of day (morning, evening), occasion or event, such as an office day, a wedding or a night out
- Asks follow-up questions to refine the answer: weather, preferred colors, style, budget, size
- Recommends real products from the store catalog, with links to their pages

## Tech stack

| Area | Tools |
| --- | --- |
| Framework | Next.js 16 (App Router), React 19 |
| Language | TypeScript |
| Styling | Tailwind CSS v4, CSS Modules (being phased out) |
| UI | shadcn/ui, Base UI, Embla Carousel, lucide-react |
| Images | next/image with static imports and responsive sizes |
| Linting | ESLint 9 (flat config, eslint-config-next) |

## Getting started

Requirements: Node.js 20+ and npm.

bash
git clone <repo-url>
cd berries-clothing
npm install
npm run dev


Open [http://localhost:3000](http://localhost:3000). The root URL redirects to /home.

## Scripts

| Command | What it does |
| --- | --- |
| npm run dev | Start the development server |
| npm run build | Production build |
| npm start | Serve the production build |
| npm run lint | Run ESLint |

## Project structure


app/
  layout.tsx                  Root layout: fonts, global CSS, Header and Footer
  home/  mens/  womens/  kids/
    page.tsx                  Section landing pages
    clothing/page.tsx         Product listing with sidebar and filters
  home/shoes/page.tsx         Shoes listing
  components/
    header/                   Desktop and mobile header
    footer/
    shared/
      header-dropdown-search/ Mega-menu, search form, mobile nav links
      brands-slider/          Brand logo carousel
      page-filters/           Filter and search logic
      page-products/          Product grid
      page-sidebar/           Category sidebar
      page-product-look/      Product carousel
      Promos/                 Picture, video and double promo components
      interfaces/             Shared TypeScript prop types
  api/                        Route handlers (products, vendors)
  backend/                    Admin area (work in progress)
components/ui/                shadcn/ui components (button, card, carousel)
lib/utils.ts                  cn() class-name helper
public/
  products.json               Product data used by the listings
  products/  Animations/      Product images, banners, videos, brand logos
styles/globals.css            Tailwind entry point and base layer


## Product data

Products are loaded from public/products.json:

json
{
  "id": 1,
  "imgSrc": "/products/Camasa-HUGO.png",
  "brand": "HUGO Blue",
  "name": "Cămașă pentru bărbați din bumbac Ebaltow",
  "category": "Cămași",
  "price": "498.90",
  "currency": "RON",
  "tag": "Mens",
  "size": ["S", "M"]
}
