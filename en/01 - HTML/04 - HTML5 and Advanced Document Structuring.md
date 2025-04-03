
# **HTML5 and Advanced Document Structuring**  

## Introduction  
HTML5 introduced new semantic elements, multimedia support, and APIs for advanced document structuring. This course covers semantic HTML, multimedia, the Canvas API, and embedding external content.  

## Table of Contents  
- [Semantic HTML5 Elements and Their Importance](#semantic-html5-elements-and-their-importance)  
- [Articles, Sections, and Document Flow](#articles-sections-and-document-flow)  
- [HTML5 Multimedia: Audio and Video Elements](#html5-multimedia-audio-and-video-elements)  
- [Canvas API for Graphics and Animations](#canvas-api-for-graphics-and-animations)  
- [Embedding External Content (iFrames, SVG, Object)](#embedding-external-content-iframes-svg-object)  
- [Conclusion and Practical Exercise](#conclusion-and-practical-exercise)  

---  

## **Semantic HTML5 Elements and Their Importance**  
### Definition  
Semantic elements describe the meaning of content, improving SEO and accessibility.  

### Example  
```html
<header>
    <h1>Website Title</h1>
</header>
<nav>
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
    </ul>
</nav>
<main>
    <article>
        <h2>Article Title</h2>
        <p>Content of the article...</p>
    </article>
</main>
<footer>
    <p>&copy; 2025 My Website</p>
</footer>
```  
### Explanation  
Elements like `<header>`, `<nav>`, `<article>`, and `<footer>` enhance document clarity and accessibility.  

---  

## **Articles, Sections, and Document Flow**  
### Definition  
HTML5 introduces `<article>` and `<section>` for better content organization.  

### Example  
```html
<section>
    <h2>Latest News</h2>
    <article>
        <h3>Breaking News</h3>
        <p>Details about the news...</p>
    </article>
</section>
```  
### Explanation  
Use `<section>` for content grouping and `<article>` for standalone content.  

---  

## **HTML5 Multimedia: Audio and Video Elements**  
### Definition  
HTML5 supports native audio and video playback without external plugins.  

### Example  
```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
</audio>

<video controls width="400">
    <source src="video.mp4" type="video/mp4">
</video>
```  
### Explanation  
The `<audio>` and `<video>` elements support multiple formats and controls.  

---  

## **Canvas API for Graphics and Animations**  
### Definition  
The `<canvas>` element allows dynamic rendering of graphics via JavaScript.  

### Example  
```html
<canvas id="myCanvas" width="200" height="100"></canvas>
<script>
    const canvas = document.getElementById("myCanvas");
    const ctx = canvas.getContext("2d");
    ctx.fillStyle = "blue";
    ctx.fillRect(20, 20, 150, 50);
</script>
```  
### Explanation  
Use the `<canvas>` API for custom drawings and animations.  

---  

## **Embedding External Content (iFrames, SVG, Object)**  
### Definition  
HTML5 allows embedding other web pages, scalable graphics, and external content.  

### Example  
```html
<iframe src="https://example.com" width="600" height="400"></iframe>

<svg width="100" height="100">
    <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
</svg>

<object data="file.pdf" type="application/pdf" width="600" height="400"></object>
```  
### Explanation  
Use `<iframe>` for embedding pages, `<svg>` for vector graphics, and `<object>` for external files.  

---  

## **Conclusion and Practical Exercise**  

### **Key Takeaways**  
1. Semantic elements improve SEO and accessibility.  
2. `<section>` and `<article>` organize content meaningfully.  
3. HTML5 supports native audio and video playback.  
4. The `<canvas>` API allows dynamic graphics.  
5. `<iframe>`, `<svg>`, and `<object>` embed external content.  

### **Practical Exercise**  
Create a webpage that includes:  
- **A semantic structure** with `<header>`, `<nav>`, `<main>`, and `<footer>`.  
- **An article section** with headings and paragraphs.  
- **An embedded video** using the `<video>` element.  
- **A simple drawing** using the `<canvas>` API.  
- **An embedded SVG graphic** for vector rendering.  

Save as `advanced.html` and open in a browser.  
