# NNL - Luxury Fashion E-Commerce UI

A high-fidelity, pixel-perfect e-commerce frontend built with **Nuxt 3** and **Tailwind CSS**.
This project simulates a premium fashion shopping experience (rebranded as **NNL**), focusing on complex navigation interactions, seamless mobile experiences, and a minimalist luxury aesthetic.

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Nuxt 3](https://img.shields.io/badge/Nuxt-3.x-00DC82?logo=nuxt.js)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38B2AC?logo=tailwind-css)
![Vue 3](https://img.shields.io/badge/Vue-3.x-4FC08D?logo=vue.js)

## ✨ Key Features

### 🖥️ Desktop Experience
- **Smart Header**: Dynamic transparent-to-solid background transitions based on page route and interaction.
- **Mega Menu**: Full-width hover dropdowns showcasing categories, promotional images, and discount cards.
- **Search Overlay**: Elegant, full-width search bar toggle with auto-focus.
- **Region Selector**: Modal popup with high-quality country flags and currency selection.

### 📱 Mobile Optimization (RWD)
- **Multi-Level Drawer**: Smooth slide-out navigation with nested sub-menus (Level 1 & Level 2).
- **Sticky Bottom Elements**: The "Ship To" selector is permanently fixed to the bottom of the drawer for easy access, regardless of screen height.
- **Accordion Menus**: Expandable category lists within the mobile menu.
- **Sticky Promo**: Floating "Get 15% Off" button fixed to the bottom-left corner.
- **Unified Header**: Optimized header layout with accessible search, login, and wishlist actions.

### 📄 Page Layouts
- **Homepage**:
  - Full-screen Hero Banner with video/image background support.
  - "Just In" Product Slider/Grid.
  - Dual-column promotional banners.
- **Login Page**:
  - Custom layout with a full-screen background image.
  - Integrated "Trust Badges" and a simplified footer specific to the login flow.
- **Wishlist**:
  - Minimalist "Empty State" design.
  - Auto-adapting header style (forces black text on white background for visibility).

## 🛠️ Tech Stack

- **Framework**: [Nuxt 3](https://nuxt.com/) (Vue 3)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **State Management**: [Pinia](https://pinia.vuejs.org/)
- **Routing**: Vue Router (Integrated in Nuxt)
- **Icons**: Inline SVGs & FlagCDN
- **Rendering Mode**: SPA (Single Page Application) - Configured via `ssr: false` for stability.

## 📂 Project Structure

The project uses a simplified, flat component structure to ensure easy maintenance and avoid path resolution issues.

```bash
.
├── components/          # All UI components (Header, Footer, Cards, Modals)
│   ├── AppHeader.vue    # Core Navigation & Logic
│   ├── AppFooter.vue    # Footer with conditional props
│   ├── HeroSection.vue  # Homepage Banner
│   ├── ProductCard.vue  # Reusable Product Grid Item
│   └── RegionModal.vue  # Country/Currency Selector
├── layouts/
│   └── default.vue      # Main App Layout
├── pages/
│   ├── index.vue        # Homepage
│   ├── login.vue        # Login / Sign Up
│   └── wishlist.vue     # Wishlist Page
├── public/              # Static Assets
├── nuxt.config.ts       # Nuxt Configuration
└── tailwind.config.js   # Tailwind Theme Config
```

## 🚀 Getting Started

### **Prerequistes**

- Node.js(v16.0.0 or later)
- npm or yarn

### **Installation**

1. Clone the repository
```bash
git clone [https://github.com/your-username/nnl-fashion-store.git](https://github.com/your-username/nnl-fashion-store.git)
cd nnl-fashion-store
```

2. Install dependencies
```bash
npm install
```

3. Start the development server
```bash
npm run dev
```

### **Building for Production**

To create a production-ready build : 
```bash
npm run build
# or
npm run generate # for static hosting
```

## 🎨 Design System

### **Typography**
- Headings: Playfair Display (Serif) - Adds a luxury feel.
- Body/UI: Inter (Sans-serif) - Ensures readability.

### **Colors**
- Primary: Black (#000000)
- Secondary: White (#FFFFFF)
- Accent: Sale Red (#D32F2F)
- Background: Off-White (#F9F9F9)

## 📝 Notes

- SPA Configuration: This project is set to ssr: false in nuxt.config.ts to prevent hydration mismatches and simplify deployment on static hosting services (like GitHub Pages or Vercel Static).
- Clean Install: If you encounter any issues, try deleting node_modules and .nuxt folder and run npm install again.

© 2025 NNL Clone. All Rights Reserved.
