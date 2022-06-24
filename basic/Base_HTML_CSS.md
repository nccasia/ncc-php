# Chapter 01: Necessary Knowledge Base

These are the basic knowledge required to be able to get started with PHP.
This series focuses on PHP, so this knowledge only stops at the level of listing and introduction.

Table of contents

1. [Basic Html](#1-basic-html) <br>
1-1 [What is Html](#1-1-what-is-html)<br>
1-2 [Html syntax structure](#1-2-html-syntax-structure)<br>
1-3 [Tags in Html](#1-3-tags-in-html)<br>
2. [Css](#2-css)<br>
2-1 [What is Css](#2-1-what-is-css)<br>
1-2 [Css syntax structure](#2-2-css-syntax-structure)<br>
1-3 [How to embed Css in Html](#2-3-how-to-embed-css-in-html)<br>
3. [Web service](#3-web-service)

---

## 1. Basic Html
### 1-1. What is Html?
HTML stands for HyperText Markup Language (translated as HyperText Markup Language) used to create a web page.
A website can contain many pages and each page is referred to as an HTML document.
Think that if the website is a complete body, the HTML is the skeleton of that body.

**More information**

Website has two main types:
- Static web (website/web tĩnh) - Là trang web chỉ bao gồm HTML có sẵn, do trình duyệt tải về từ máy chủ và hiển thị cho người dùng. Website không cho phép người dùng tương tác với nó.
- Dynamic website (web app) - Một trang web sẽ giao tiếp với máy chủ để gửi và nhận dữ liệu, dữ liệu sẽ được gửi đến dưới dạng văn bản HTML và trình duyệt sẽ hiển thị nó.
Để một trang web có thể giao tiếp với máy chủ web, nó sẽ sử dụng một số ngôn ngữ lập trình phía máy chủ như PHP, ASP.NET, Ruby,… để thực hiện. Ví dụ, một trang web làm bằng WordPress là một trang web động.

### 1-2. Html Syntax Structure
Below is an example of one of the simplest examples of an HTML document.
```html
<!DOCTYPE html>
<html>
<head>
<title>This is Title Tag</title>
</head>
<body>
<h1>This is H1 Tag</h1>
<p>This is P Tag</p>
</body>
</html>
```
### 1-3. Tags in HTML

HTML is tag language and uses different tags to format the content. These tags are contained within two parentheses <tag name>.
Except for a few tags, most tags have their corresponding closing tags. For example, the tag `<html>` has a close tag of `</html>`, and the `<body>` tag has a corresponding close tag of `</body>`...

**Basic html tags need to know:**
- HTML Headings
- HTML Paragraphs
- HTML Attributes
- HTML Colors
- HTML Links
- HTML Images
- HTML Tables
- HTML Lists
- HTML JavaScript
- HTML Responsive Web Design
- HTML Forms

To learn more about the other tags and their meanings, you can find out at the following link:

[https://www.w3schools.com/html](https://www.w3schools.com/html/)

## 2. Css
### 2-1. What is Css?
Css là ngôn ngữ nhằm mục đích trang trí cho trang web (viết tắt của Cascading Style Sheet) viết bằng ngôn ngữ mark up (ở đây là HTML)
### 2-2. Css syntax structure
Here is an example of one of the simplest Css templates.
```css
body {
    background-color: black;
    color: #fff;
}
```

The above Css will define all the html elements in the body tag, the background image will be black and the text is white.

### 2-3. How to embed CSS in HTML

**Inline: CSS code written in the style attribute of the HTML element**
```html
<p style="color:white; background-color:red;"></p>
```
**Internal: the CSS code in the HTML document itself, inside the tag block `<style>`**
```html
<style>
    h1 {
        color: #000;
    }   
</style>
```
**External: CSS code in a separate file then loaded into HTML with the element `<link>`**
```html
<html>
   <head>
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" />
   </head>
   <body>
      <p class="display-1 text-success">Hello CSS</p>
   </body>
</html>

```
### 2-4. Css specific syntax

![Alt text](images/css-declaration-small.png?raw=true "Css")
1. Selector
The HTML element name at the beginning of the rule set. It selects the styled element (s) (p element in this case). To style another element, simply change the selector.
Declaration
A single rule like: color: red; specifies which element properties you want to style.

2. Properties
Ways you can style an HTML element.
(In this case, color is an attribute of the `<p>` element.) In CSS, you choose which property you want to affect in your rule.

3. Attribute value
To the right of the property after the colon (:), we have the property value, which chooses one out of as many possible occurrences for a particular property (color has a lot of values ​​beyond red).

**Basic CSS need to know:**
- CSS Colors
- CSS Backgrounds
- CSS Borders
- CSS Margins
- CSS Padding
- CSS Height and Width
- CSS Dropdowns
- CSS Forms
- CSS Transitions
- CSS Animation
- CSS Buttons
- CSS Pagination
- CSS Responsive

To learn more about other properties of CSS, learn more at the following link:

[https://www.w3schools.com/css](https://www.w3schools.com/css/)

## 3. Web service

Here are some basic components of a web service

![Basic web service](images/basic_web_service.png?raw=true "Css")

When you download a web browser, you get HTML, CSS, and JavaScript, but you do not get PHP. PHP scripts—which you’ll soon be writing—have to be interpreted by the PHP interpreter program, called php. And, you can’t just add a PHP interpreter to your browser. It doesn’t know what to do with scripts and isn’t built to interpret PHP.

Instead, you need PHP on a web server. It’s the web server — not the web browser — that can interact with a PHP interpreter. Your browser can handle HTML on its own, but it has to make a request to a web server to deal with PHP scripts. That server can take your PHP scripts and run them, and then take the response and send it back to your browser. Your browser can then understand and handle the response.

![PHP and HTML](images/php_html.png?raw=true "Css")

Here’s the basic process:
1. A web browser makes a request for some page. That page might be a URL on a remote web server, or a local file on your computer.
2. The web server returns HTML (and CSS and JavaScript) or, in the case of PHP, passes the PHP request on to the PHP interpreter.
3. The PHP interpreter interprets, or runs, the PHP. The result of that should be something that a browser can understand, like HTML, JSON string. It passes this result, or response, back to the web server and later the web browser.

