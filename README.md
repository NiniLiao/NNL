# NNL - Luxury Fashion E-Commerce UI

A high-fidelity, pixel-perfect e-commerce frontend built with **Nuxt 3** and **Tailwind CSS**.  
This project features a minimalist aesthetic inspired by high-end fashion brands (rebranded as **NNL**), focusing on complex navigation interactions and a seamless mobile experience.

## ⚡ Tech Stack

- **Framework**: [Nuxt 3](https://nuxt.com/) (Vue 3)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **State Management**: [Pinia](https://pinia.vuejs.org/)
- **Icons**: SVG Icons & FlagCDN
- **Rendering**: Client-Side Rendering (SPA mode)

## ✨ Key Features

### 🖥️ Desktop Experience
- **Smart Header**: Transparent-to-solid transition effects.
- **Mega Menu**: Full-width hover dropdowns with promotional images.
- **Search Overlay**: Elegant, full-width search bar toggle.
- **Region Selector**: Modal popup with country flags and currency selection.

### 📱 Mobile Optimization (RWD)
- **Multi-Level Drawer**: Smooth slide-out navigation with nested sub-menus.
- **Sticky Bottom Elements**: The "Ship To" selector is permanently fixed to the bottom of the drawer.
- **Sticky Promo**: Floating "Get 15% Off" button fixed to the bottom-left.
- **Accordion Menus**: Expandable category lists.

### 📄 Page Layouts
- **Homepage**: Hero Banner, Product Grids, and Dual-column Banners.
- **Login**: Custom full-screen background layout with integrated trust badges.
- **Wishlist**: Minimalist "Empty State" design with auto-adapting header.

## 🚀 Getting Started

### Prerequisites
- Node.js (v16.0.0 or later)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone [https://github.com/your-username/nnl-fashion-store.git](https://github.com/your-username/nnl-fashion-store.git)
   cd nnl-fashion-store

2. **Install dependencies**
   ```bash
   npm Install
   
3. **Start the development server**
   ```bash
   npm run dev
   Open http://localhost:3000 in your browser to view the project.
   
### Building for Production
   ```bash
   npm run build
   # or
   npm run generate # for static hosting


## 🎨 Design System

- **Typography**:
  - Headings: Playfair Display (Serif) - Adds a luxury feel.
  - Body/UI: Inter (Sans-serif) - Ensures readability.

- **Colors**:
  - Primary: Black (#000000)
  - Secondary: White (#FFFFFF)
  - Accent: Sale Red (#D32F2F)
  - Background: Off-White (#F9F9F9)
  
  
## 📝 Notes

- SPA Configuration: This project is set to ssr: false in nuxt.config.ts to prevent hydration mismatches and simplify deployment on static hosting services (like GitHub Pages or Vercel Static).

- Clean Install: If you encounter any issues, try deleting node_modules and .nuxt folder and run npm install again.