###General HTML layout
Always starts with `<!DOCTYPE html>`  
Always has `<html>...</html>` as first and last tags  
Always has `<head>...</head>`, and `<body>...</body>` go inside `<html>..</html>`  

Example:  
```
<!DOCTYPE html>
<html>
  <head>
    <title>
    </title>
    <h1>This is a big heading</h1>
  <head>
  <body style="background-color:red">
    <p>This is a paragraph</p>
    <ol>
      <li style="color:blue">first item in ordered list</li>
      <li style="font-size:20px">second item in ordered list</li>
      <li style="font-family:Arial">third item in ordered list</li>
      <li style="font-size=30px; color:orange; font-family:Verdina">fourth item in ordered list</li>
    </ol>
    <ul>
      <li>first item in unordered list</li>
      <li>second item in unordered list</li>
    </ul>
  </body>
</html>
```
**Include a link**
```
<a href="put url here">"some label here"</a>

In the .css can format the link:
a {
  text-decoration: none   <!-- will not show the underline -->
  color: red              <!-- change the color of the text -->
}
```
**Include an image**
```
<img src="image url here">
```
**Text Alignment**
```
style="text-align:center"
style="text-align:right"
stype="text-align:left"
```
**Bold**
```
<strong>
</strong>
```
**Italics**
```
<em>
</em>
```
**Tables**  
table header area `<theader>...</theader>`  
table header `<th>...</th>`  
table rows `<tr>...</tr>`  
table data `<td>...</td>`  
```
<table>
  <theader>
    <tr>
      <th colspan="3">Title across 3 columns</th>
    </tr>
  </theader>
    <tr>
      <td>creates column 1</td>
      <td>creates column 2</td>
      <td>creates column 3</td>
    </tr>
    </tr>
    
</table>
```
```
<table style="border-collapse:collapse>

table { <!-- in css -->
  border: 1px dashed blue;
}
```
###CSS  
`selector`s are any HTML element  
```
selector {
  property: value;
}
```
**Include CSS stylesheets**  
```
<link type="text/css" rel="stylesheet" href="stylesheet.css"/>
```

###Making a Button
```
div {
    height: 50px;
    width: 120px;
    border-color: #6495ed;
    background-color: #bcd2ee;
    border-style: dashed;
    border-width: 2px;
    border-radius: 5px;
    margin: auto;
    text-align: center;
}
```
#Choose All Elements
```
* {
}
```
**Nesting Elements**  
```
body ul li{
}
body ul li p {
}
```

###id=
Use for when **one** element needs a certain styling  
```
<body id="myid">...</body>
<p id="myid">...</p>

<!--- in the .css --->
#myid {
  selector: property;
}
```

###class=
Use when several different elements have the same styling  
```
<body class="mystyle">...</body>
<p class="mystyle">...</p>

<!--- in the .css --->
.mystyle {
  selector: property;
}
```
###pseuo-class selectors for links
`a:link`  
`a:visited`  
`a:hover`  

`p:first-child`  
`p:nth-child(n)`  
