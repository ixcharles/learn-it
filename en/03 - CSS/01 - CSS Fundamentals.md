
# CSS Fundamentals

CSS (Cascading Style Sheets) is a stylesheet language used to describe the presentation of a document written in HTML or XML. This course will cover the essential concepts and properties you need to know to start styling websites effectively.

## Table of Contents
- [Introduction to CSS](#introduction-to-css)
- [CSS Syntax and Selectors](#css-syntax-and-selectors)
- [Basic Styling: Colors, Fonts, and Text](#basic-styling-colors-fonts-and-text)
- [The Box Model: Content, Padding, Border, Margin](#the-box-model-content-padding-border-margin)
- [Positioning: Static, Relative, Absolute, Fixed, Sticky](#positioning-static-relative-absolute-fixed-sticky)
- [CSS Display Property: Block, Inline, Inline-Block, Flex, Grid](#css-display-property-block-inline-inline-block-flex-grid)
- [CSS Units: px, em, rem, %, vh, vw, fr, and others](#css-units-px-em-rem-vh-vw-fr-and-others)
- [CSS Specificity and Inheritance](#css-specificity-and-inheritance)
- [Responsive Design Basics](#responsive-design-basics)

---

## Introduction to CSS

CSS is used to control the layout, design, and visual presentation of a website. It separates content (HTML) from presentation, allowing for more flexibility and control over the design.

---

## CSS Syntax and Selectors

**Definition:**  
CSS syntax consists of a selector and a declaration block. The selector targets an HTML element, while the declaration block contains style properties and values.

**Example:**
```css
p {
  color: blue;
  font-size: 16px;
}
```
**Explanation:**  
The `p` selector targets all `<p>` elements, applying the styles within the curly braces.

---

## Basic Styling: Colors, Fonts, and Text

**Definition:**  
CSS allows you to control the colors, fonts, and text properties of an element.

**Example:**
```css
h1 {
  color: #333;
  font-family: Arial, sans-serif;
  text-align: center;
}
```
**Explanation:**  
The `color` property changes the text color, `font-family` specifies the font, and `text-align` centers the text.

---

## The Box Model: Content, Padding, Border, Margin

**Definition:**  
The CSS box model defines the structure of an element's box, consisting of content, padding, border, and margin.

**Example:**
```css
div {
  width: 200px;
  padding: 10px;
  border: 1px solid black;
  margin: 20px;
}
```
**Explanation:**  
The box model adds padding inside the element, a border around it, and margin outside the element, affecting the layout.

---

## Positioning: Static, Relative, Absolute, Fixed, Sticky

**Definition:**  
CSS positioning determines how an element is positioned in the document.

**Example:**
```css
div {
  position: absolute;
  top: 50px;
  left: 100px;
}
```
**Explanation:**  
`absolute` removes the element from the normal flow and positions it relative to the nearest positioned ancestor.

---

## CSS Display Property: Block, Inline, Inline-Block, Flex, Grid

**Definition:**  
The `display` property controls how an element is displayed on the page.

**Example:**
```css
div {
  display: flex;
}
```
**Explanation:**  
Using `flex` enables a flexible layout for the child elements within the container.

---

## CSS Units: px, em, rem, %, vh, vw, fr, and others

**Definition:**  
CSS units define the measurement of properties like size, spacing, and positioning.

**Example:**
```css
p {
  font-size: 1.5em;
  width: 50%;
}
```
**Explanation:**  
`em` is relative to the parent element's font size, while `%` is relative to the parent element's width.

---

## CSS Specificity and Inheritance

**Definition:**  
Specificity determines which styles apply when multiple styles target the same element. Inheritance allows properties to be passed down to child elements.

**Example:**
```css
div p {
  color: red;
}
```
**Explanation:**  
This rule has higher specificity than just `p` because it is more specific, targeting `p` within a `div`.

---

## Responsive Design Basics

**Definition:**  
Responsive design ensures a website looks good on devices of various sizes by using flexible layouts and media queries.

**Example:**
```css
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```
**Explanation:**  
This media query changes the background color when the viewport width is less than or equal to 600px.

---

## Conclusion

### Key Takeaways:
1. CSS separates content from presentation, providing control over layout and design.
2. The Box Model is essential for understanding element dimensions and spacing.
3. Positioning and display properties are crucial for controlling layout behavior.
4. CSS units provide flexibility in measurement, allowing responsive design.
5. Specificity and inheritance determine how and which styles are applied to elements.

### Practical Exercise:
1. Create a simple webpage with a header, two columns, and a footer.
2. Use the Box Model to style the page, applying padding, borders, and margins.
3. Make the layout responsive using media queries to adjust for different screen sizes.
