
# Tailwind Fundamentals

Tailwind CSS is a utility-first CSS framework that enables rapid UI development by composing styles directly in your markup. This course covers the foundational concepts necessary to effectively use and customize Tailwind.

---

## Table of Contents

- [Introduction to Utility-First CSS](#introduction-to-utility-first-css)
- [Installing and Setting Up Tailwind](#installing-and-setting-up-tailwind)
- [Tailwind Configuration File (tailwindconfigjs)](#tailwind-configuration-file-tailwindconfigjs)
- [Using the CLI and PostCSS](#using-the-cli-and-postcss)
- [Purging Unused Styles for Production](#purging-unused-styles-for-production)
- [Understanding Responsive Design in Tailwind](#understanding-responsive-design-in-tailwind)
- [The Basics of Utility Classes](#the-basics-of-utility-classes)
  - [Layout Utilities](#layout-utilities)
  - [Spacing Utilities](#spacing-utilities)
  - [Typography Utilities](#typography-utilities)
  - [Background and Border Utilities](#background-and-border-utilities)
- [Customizing Design Tokens (Colors, Fonts, Spacing)](#customizing-design-tokens-colors-fonts-spacing)
- [Conclusion](#conclusion)

---

## Introduction to Utility-First CSS

**Definition**: A utility-first approach involves using small, single-purpose classes to build complex designs directly in HTML.

**Example**:
```html
<div class="bg-blue-500 text-white p-4 rounded">Hello Tailwind</div>
```

Tailwind avoids custom CSS by providing a comprehensive set of utility classes.

---

## Installing and Setting Up Tailwind

**Definition**: Tailwind can be installed via npm and integrated into your build process.

**Example**:
```bash
npm install -D tailwindcss
npx tailwindcss init
```

Then include Tailwind in your CSS:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## Tailwind Configuration File (tailwind.config.js)

**Definition**: This file controls your project's theme, variants, and plugins.

**Example**:
```js
module.exports = {
  content: ['./src/**/*.{html,js}'],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Use it to customize Tailwind to fit your design system.

---

## Using the CLI and PostCSS

**Definition**: Tailwind provides a CLI to compile your CSS and works with PostCSS to automate transformations.

**Example**:
```bash
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

Use PostCSS for autoprefixing and other CSS transformations.

---

## Purging Unused Styles for Production

**Definition**: Tailwind removes unused styles via the `content` field in `tailwind.config.js`.

**Example**:
```js
content: ['./public/**/*.html', './src/**/*.{js,jsx,ts,tsx}'],
```

This ensures your final CSS bundle is small and optimized.

---

## Understanding Responsive Design in Tailwind

**Definition**: Tailwind uses mobile-first breakpoints to apply styles responsively.

**Example**:
```html
<div class="text-sm md:text-lg lg:text-xl">Responsive Text</div>
```

Prefixes like `md:` and `lg:` apply styles at specific screen widths.

---

## The Basics of Utility Classes

### Layout Utilities

**Definition**: Control element layout using flex, grid, display, and more.

**Example**:
```html
<div class="flex justify-between items-center">...</div>
```

---

### Spacing Utilities

**Definition**: Manage margin and padding using `m-`, `p-`, and directional shorthands.

**Example**:
```html
<div class="p-4 mt-2 mb-6">Spaced Content</div>
```

---

### Typography Utilities

**Definition**: Adjust font size, weight, alignment, and line height.

**Example**:
```html
<p class="text-lg font-semibold leading-relaxed text-center">Typography</p>
```

---

### Background and Border Utilities

**Definition**: Style backgrounds and borders with colors, radius, and widths.

**Example**:
```html
<div class="bg-gray-100 border border-gray-400 rounded-lg">Card</div>
```

---

## Customizing Design Tokens (Colors, Fonts, Spacing)

**Definition**: Modify Tailwind’s default design system via the `theme.extend` section.

**Example**:
```js
theme: {
  extend: {
    colors: {
      primary: '#1E40AF',
    },
    fontFamily: {
      sans: ['Inter', 'sans-serif'],
    },
  },
}
```

This allows you to align Tailwind with your brand or project design system.

---

## Conclusion

### Key Takeaways

- Tailwind uses utility-first classes to build UIs rapidly.
- Installation is straightforward with CLI or PostCSS integration.
- The `tailwind.config.js` file is essential for customization.
- Responsive design is built-in and mobile-first.
- Utility classes cover layout, spacing, typography, and more.

---

### Practical Exercise

Create a responsive card component using Tailwind that includes:
- A container with padding and a shadow
- An image on top
- A title and description
- A button with hover state
