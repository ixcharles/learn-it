
# **Foundations of HTML**  

## Introduction  
HTML (HyperText Markup Language) is the foundation of web development, defining the structure and content of web pages. This course covers essential HTML concepts, from basic tags to semantic structuring.  

## Table of Contents  
- [Introduction to HTML and Its Role in Web Development](#introduction-to-html-and-its-role-in-web-development)  
- [Setting Up a Development Environment](#setting-up-a-development-environment)  
- [Understanding HTML Document Structure](#understanding-html-document-structure)  
- [Essential HTML Tags and Their Usage](#essential-html-tags-and-their-usage)  
- [Text Formatting and Semantic HTML](#text-formatting-and-semantic-html)  
- [Conclusion and Practical Exercise](#conclusion-and-practical-exercise)  

---  

## **Introduction to HTML and Its Role in Web Development**  
### Definition  
HTML is the standard markup language used to structure web content. It defines elements such as text, images, and links for browsers to render.  

### Example  
```html
<!DOCTYPE html>
<html>
<head>
    <title>My First Web Page</title>
</head>
<body>
    <h1>Welcome to HTML</h1>
    <p>This is a simple web page.</p>
</body>
</html>
```  
### Explanation  
Every webpage starts with HTML. It works with CSS for styling and JavaScript for interactivity.  

---  

## **Setting Up a Development Environment**  
### Definition  
To write HTML, you need a text editor and a web browser. Popular editors include VS Code, Sublime Text, and Notepad++.  

### Example  
1. Install [VS Code](https://code.visualstudio.com/).  
2. Create an `index.html` file.  
3. Open it in a browser.  

### Explanation  
A good editor provides syntax highlighting, auto-completion, and extensions for better workflow.  

---  

## **Understanding HTML Document Structure**  
### Definition  
An HTML document consists of elements that define its structure, including the `DOCTYPE`, `html`, `head`, and `body` tags.  

### Example  
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Page Structure</title>
</head>
<body>
    <h1>Document Structure Example</h1>
</body>
</html>
```  
### Explanation  
The `head` contains metadata, while the `body` contains visible content.  

---  

## **Essential HTML Tags and Their Usage**  
### Definition  
HTML elements define content types such as headings, paragraphs, links, images, and lists.  

### Example  
```html
<h1>Main Heading</h1>
<p>This is a paragraph.</p>
<a href="https://example.com">Visit Example</a>
<img src="image.jpg" alt="Sample Image">
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
</ul>
```  
### Explanation  
Use appropriate tags to organize content effectively.  

---  

## **Text Formatting and Semantic HTML**  
### Definition  
Semantic HTML enhances readability and accessibility by using meaningful tags like `<article>`, `<section>`, and `<aside>`.  

### Example  
```html
<article>
    <h2>HTML Semantics</h2>
    <p>Using semantic elements improves SEO and accessibility.</p>
</article>
<section>
    <h2>Example Section</h2>
    <p>Content inside sections is structured logically.</p>
</section>
```  
### Explanation  
Semantic elements describe the meaning of content, helping search engines and assistive technologies interpret pages.  

---  

## **Conclusion and Practical Exercise**  

### **Key Takeaways**  
1. HTML is the backbone of web development.  
2. A proper development environment improves efficiency.  
3. HTML documents follow a structured format.  
4. Essential tags define content layout and elements.  
5. Semantic HTML improves accessibility and SEO.  

### **Practical Exercise**  
Create a simple webpage using the following requirements:  
- A `title` and a `meta charset="UTF-8"` in the `<head>`.  
- A heading (`<h1>`) and a paragraph (`<p>`).  
- A link (`<a>`), an image (`<img>`), and a list (`<ul>`).  
- Use semantic elements like `<section>` and `<article>`.  

Save the file as `index.html` and open it in a browser.  
