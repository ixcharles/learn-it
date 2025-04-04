
# Layout Systems in Tailwind

Tailwind CSS provides a complete suite of utility classes for building complex layouts using modern CSS techniques like Flexbox, Grid, and container queries. This course dives into Tailwind's layout systems for responsive and structured design.

---

## Table of Contents

- [Flexbox Utilities](#flexbox-utilities)
  - [Alignment, Justify, and Flex Direction](#alignment-justify-and-flex-direction)
- [Grid Utilities](#grid-utilities)
  - [Template Columns and Rows](#template-columns-and-rows)
  - [Grid Gap and Auto Placement](#grid-gap-and-auto-placement)
- [Positioning Utilities](#positioning-utilities)
  - [Relative, Absolute, Fixed, Sticky](#relative-absolute-fixed-sticky)
- [Z-Index and Stacking Context](#z-index-and-stacking-context)
- [Aspect Ratio and Object Fit Utilities](#aspect-ratio-and-object-fit-utilities)
- [Container Queries (Tailwind v3.2+)](#container-queries-tailwind-v32)
- [Conclusion](#conclusion)

---

## Flexbox Utilities

### Alignment, Justify, and Flex Direction

**Definition**: Tailwind makes it easy to manage layout flow and alignment using Flexbox classes.

**Example**:
```html
<div class="flex flex-col md:flex-row justify-between items-center">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

Use `flex`, `justify-*`, and `items-*` to align children flexibly.

---

## Grid Utilities

### Template Columns and Rows

**Definition**: Create multi-column layouts with `grid-cols-*` and `grid-rows-*`.

**Example**:
```html
<div class="grid grid-cols-2 md:grid-cols-4 gap-4">
  <div class="bg-gray-200 p-4">Item</div>
</div>
```

Define rows with `grid-rows-*` similarly.

---

### Grid Gap and Auto Placement

**Definition**: Use `gap-*` utilities to manage spacing and let grid auto-place items.

**Example**:
```html
<div class="grid grid-cols-3 gap-6">
  <div>1</div>
  <div>2</div>
  <div>3</div>
</div>
```

Auto-placement uses the default grid behavior without explicitly naming rows/columns.

---

## Positioning Utilities

### Relative, Absolute, Fixed, Sticky

**Definition**: Tailwind offers positioning utilities that mirror CSS position values.

**Example**:
```html
<div class="relative">
  <div class="absolute top-0 right-0 bg-red-500">Badge</div>
</div>
```

Use `top-*, left-*, right-*` in combination with position classes.

---

## Z-Index and Stacking Context

**Definition**: Control element layering with `z-*` classes.

**Example**:
```html
<div class="relative z-10">On top</div>
<div class="relative z-0">Behind</div>
```

Z-index values range from `z-0` to `z-50` or custom via config.

---

## Aspect Ratio and Object Fit Utilities

**Definition**: Maintain fixed width-to-height ratios with `aspect-*` and scale content with `object-*`.

**Example**:
```html
<div class="aspect-w-16 aspect-h-9">
  <iframe src="..."></iframe>
</div>
<img src="img.jpg" class="object-cover w-full h-48" />
```

Aspect utilities keep media proportional across devices.

---

## Container Queries (Tailwind v3.2+)

**Definition**: Container queries apply styles based on the size of a parent container, not the viewport.

**Example**:
```html
<div class="container md:container-lg">
  <div class="@container">
    <div class="text-base @lg:text-xl">Scales by container</div>
  </div>
</div>
```

Enable in config:
```js
plugins: [require('@tailwindcss/container-queries')],
```

---

## Conclusion

### Key Takeaways

- Use Flexbox utilities for directional flow and alignment.
- Grid utilities allow for responsive, column-based structures.
- Positioning classes handle layer placement and layout control.
- Z-index, aspect ratios, and object-fit utilities enhance control and consistency.
- Container queries allow style control based on parent dimensions.

---

### Practical Exercise

Build a responsive card grid with:
- 1 column on mobile, 2 on medium, 3 on large screens
- Each card has an image (16:9), title, and description
- Add a floating button using absolute positioning
