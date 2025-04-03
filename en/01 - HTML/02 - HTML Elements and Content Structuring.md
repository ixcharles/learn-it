
# **HTML Elements and Content Structuring**  

## Introduction  
HTML elements define the structure and content of a webpage. This course covers essential elements such as headings, paragraphs, lists, links, multimedia, tables, and forms for effective content organization.  

## Table of Contents  
- [Headings, Paragraphs, and Lists](#headings-paragraphs-and-lists)  
- [Links, Anchor Tags, and Navigation](#links-anchor-tags-and-navigation)  
- [Images and Multimedia Elements](#images-and-multimedia-elements)  
- [Tables: Structure, Accessibility, and Best Practices](#tables-structure-accessibility-and-best-practices)  
- [Forms: Input Elements, Labels, and Form Validation](#forms-input-elements-labels-and-form-validation)  
- [Conclusion and Practical Exercise](#conclusion-and-practical-exercise)  

---  

## **Headings, Paragraphs, and Lists**  
### Definition  
Headings define document structure, paragraphs hold text, and lists organize content.  

### Example  
```html
<h1>Main Title</h1>
<p>This is a paragraph with important content.</p>
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
</ul>
<ol>
    <li>First step</li>
    <li>Second step</li>
</ol>
```  
### Explanation  
Use headings (`<h1>`-`<h6>`) to establish hierarchy, paragraphs (`<p>`) for readable text, and lists (`<ul>`, `<ol>`) for organization.  

---  

## **Links, Anchor Tags, and Navigation**  
### Definition  
Links connect pages, anchor tags enable navigation, and nav elements define menus.  

### Example  
```html
<a href="https://example.com">Visit Example</a>
<nav>
    <ul>
        <li><a href="home.html">Home</a></li>
        <li><a href="about.html">About</a></li>
    </ul>
</nav>
```  
### Explanation  
Use `<a>` for hyperlinks and `<nav>` for navigation structures.  

---  

## **Images and Multimedia Elements**  
### Definition  
HTML supports images, audio, and video for rich content.  

### Example  
```html
<img src="image.jpg" alt="Description of image">
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
</audio>
<video controls width="400">
    <source src="video.mp4" type="video/mp4">
</video>
```  
### Explanation  
Use `<img>` for images, `<audio>` for sound, and `<video>` for clips. Always include `alt` for accessibility.  

---  

## **Tables: Structure, Accessibility, and Best Practices**  
### Definition  
Tables organize tabular data using rows and columns.  

### Example  
```html
<table>
    <caption>Product List</caption>
    <tr>
        <th>Product</th>
        <th>Price</th>
    </tr>
    <tr>
        <td>Phone</td>
        <td>$699</td>
    </tr>
</table>
```  
### Explanation  
Use `<table>` with `<tr>` (rows), `<th>` (headers), and `<td>` (data). Add `<caption>` for accessibility.  

---  

## **Forms: Input Elements, Labels, and Form Validation**  
### Definition  
Forms collect user input through fields and buttons.  

### Example  
```html
<form action="submit.php" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
    <input type="submit" value="Submit">
</form>
```  
### Explanation  
Forms use `<form>` to wrap inputs. Labels (`<label>`) improve accessibility, and `required` ensures validation.  

---  

## **Conclusion and Practical Exercise**  

### **Key Takeaways**  
1. Headings and paragraphs structure content.  
2. Links and navigation elements enable page connectivity.  
3. Images and multimedia enhance user experience.  
4. Tables effectively organize tabular data.  
5. Forms collect user data with validation.  

### **Practical Exercise**  
Create a webpage containing:  
- A heading (`<h1>`) and paragraph (`<p>`).  
- A navigation bar (`<nav>`) with three links.  
- An image (`<img>`) with an `alt` attribute.  
- A table (`<table>`) with three rows and two columns.  
- A form (`<form>`) with a text input and a submit button.  

Save as `content.html` and view in a browser.  
