---
layout: notes
title: "HTML Basic"
date: 2016-11-02
categories: notes it
---

## HTML Tags

- Normally come in **pairs**
    - e.g. `<html>` and `</html>`
    - The first is called the **start tag** and the second the **end tag**
- 3 Exceptions
    - `<br />`: a line break
    - `<hr />`: a horizontal ruler
    - `<img />`: an image
    - They are called **empty tags**, ends with a slash `/`

## Tags and Attributes

- A tag can have a set of **attributes**, which provides **additional information** about a tag
- Always specified in the **start tag**
- Attributes are defined as `name="value"`

```html
<a href="http://www.google.com">Google</a>
```

## HTML Page Structure

- Every web page has the `<html>` and the `<body>` tags
- Most of the visible contents is defined within the `<body>` tag

### HTML Tags: Headings

- `<h1>` to `<h6>`

### HTML Tags: Paragraphs

- `<p>`

### HTML Tags: Text Controls

- Defines how the text is displayed
    - Center: `<center>` (Hot supported in HTML5)
    - Bold: `<b>`
    - Italic: `<i>`
    - Underline: `<u>`

### HTML Tags: Links

- `<a>`
    - Some attributes of a link:
        - `href`: where to link to (non-optional)
        - `target`: this window or a new window?
        - `title`: appears when you move your mousse over the link

```html
<a href="http://www.google.com" title="Google" target="_blank">A link to Google</a>
```

### HTML Tags: Images

- `<img>`
- Some attributes of an image
    - `src`: the address of the image (non-optional)
    - `alt`: displays an alternate text if image doesn't show
    - `border`, `height`, `width`: defined in pixels

### HTML Tags: Lists

- Two types of list:
    - **Unordered lists** `<ul>`
    - **Ordered lists** `<ol>`
- `<li>` stands for **list item**

### HTML Tags: Tables

- Tables are used to display tabular data
    - A list of people
    - Online shopping carts
    - Time tables
    - ...
- Defined with:
    - `<table>`: starts and ends a table
    - `<tr>`: **Table Row**: contains `<td>` or `<th>` tags
    - `<th>`: **Table Header**: for the tops of columns
    - `<td>`: **Table Data**: a regular cell in the table

## Tips on HTML

- HTML tags are written in **lowercase**
    - Currently case-insensitive, but newer standards specify lowercase for HTML tags
- HTML **ignores** certain symbols in your code
    - Spaces
        - Multiple spaces are treated as one
        - Use `&nbsp;` to represent an additional space
    - Tabs
    - Line breaks
        - Use `<p></p>` to specify a paragraph
        - Use `<br />` to break a line
- Basic HTML looks **different** on different browsers
