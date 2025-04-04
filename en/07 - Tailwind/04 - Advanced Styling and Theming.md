
# Advanced Styling and Theming

Tailwind CSS offers robust tools for deep customization, allowing you to extend and tailor its utilities to fit your project’s branding and design system. This course covers advanced configuration, custom utilities, and theme-based design.

---

## Table of Contents

- [Advanced Customization via Configuration File](#advanced-customization-via-configuration-file)
  - [Extending vs Overriding Defaults](#extending-vs-overriding-defaults)
- [Creating Custom Utility Classes and Plugins](#creating-custom-utility-classes-and-plugins)
- [Dark Mode Strategies](#dark-mode-strategies)
  - [Class vs Media Strategy](#class-vs-media-strategy)
  - [Dark Mode Theming](#dark-mode-theming)
- [Theme Customization for Branding](#theme-customization-for-branding)
  - [Colors, Fonts, Spacing, Shadows](#colors-fonts-spacing-shadows)
- [Using @apply for Component Styles](#using-apply-for-component-styles)
- [Conclusion](#conclusion)

---

## Advanced Customization via Configuration File

### Extending vs Overriding Defaults

**Definition**: You can extend Tailwind's default configuration by adding custom values, or override it entirely to meet your design needs.

**Example**:
```js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: '#1F2937',
      },
    },
  },
}
```

Use `extend` to add new values without losing defaults, or directly modify the `theme` to replace them.

---

## Creating Custom Utility Classes and Plugins

**Definition**: Tailwind allows you to create your own utility classes and plugins for reusable components or complex designs.

**Example**:
```js
const plugin = require('tailwindcss/plugin');

module.exports = {
  plugins: [
    plugin(function({ addUtilities }) {
      addUtilities({
        '.rotate-15': {
          transform: 'rotate(15deg)',
        },
      });
    }),
  ],
}
```

Create custom classes like `.rotate-15` for specific styles that aren’t part of Tailwind's default set.

---

## Dark Mode Strategies

### Class vs Media Strategy

**Definition**: Tailwind offers two strategies for dark mode: using a class or the `prefers-color-scheme` media query.

**Example (Class Strategy)**:
```html
<div class="dark:bg-gray-800 dark:text-white">
  Dark mode content
</div>
```
```js
module.exports = {
  darkMode: 'class', // Enable class-based dark mode
}
```

**Example (Media Strategy)**:
```js
module.exports = {
  darkMode: 'media', // Use prefers-color-scheme
}
```

Class-based strategy gives more control, while media automatically applies based on user preferences.

### Dark Mode Theming

**Definition**: Tailwind supports dark mode styling by applying classes based on the strategy chosen (class or media).

**Example**:
```html
<div class="bg-white dark:bg-gray-800 text-black dark:text-white">
  Dark mode example
</div>
```

You can customize dark mode styles in your configuration file, allowing different color schemes and effects.

---

## Theme Customization for Branding

### Colors, Fonts, Spacing, Shadows

**Definition**: Customize Tailwind's default theme to align with your project's branding (colors, fonts, spacing, etc.).

**Example**:
```js
module.exports = {
  theme: {
    extend: {
      colors: {
        brand: '#FF5722',
      },
      fontFamily: {
        sans: ['Poppins', 'sans-serif'],
      },
      spacing: {
        128: '32rem',
      },
      boxShadow: {
        custom: '0 4px 6px rgba(0, 0, 0, 0.1)',
      },
    },
  },
}
```

Tailor the core design system to match your brand’s colors, typography, and spacing conventions.

---

## Using @apply for Component Styles

**Definition**: The `@apply` directive allows you to compose Tailwind utilities into reusable component styles.

**Example**:
```css
.btn {
  @apply bg-blue-500 text-white p-2 rounded-md shadow-md;
}
```

Use `@apply` in your CSS files to combine multiple utilities for a consistent, reusable design.

---

## Conclusion

### Key Takeaways

- Extending `tailwind.config.js` adds custom values, while overriding replaces default settings.
- Tailwind plugins and custom utilities extend its functionality for project-specific needs.
- Tailwind offers two strategies for dark mode: class-based and media-query based.
- Theme customization allows you to align Tailwind with your branding (colors, fonts, etc.).
- Use `@apply` to consolidate utility classes into reusable, maintainable components.

---

### Practical Exercise

Create a custom button component with:
- A background color based on the brand’s primary color
- A hover effect using `@apply` for reusable button styles
- Support for both light and dark modes
