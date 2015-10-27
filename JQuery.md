#JQuery
File extension is **.js**  
```
// This is a comment
```
```
"cake".length  #=> 4
```

```
<div id="green">      # in HTML

#green {              # in .css
}

$("#green")           # in JS
```
###jQuery events
```
$('element').mouseover();
$('element').click();
$('element').mouseenter();

```
###Example of form input
**html**
```
<!DOCTYPE html>
<html>
    <head>
    	<title>To Do</title>
        <link rel="stylesheet" type="text/css" href="stylesheet.css"/>
        <script type="text/javascript" src="script.js"></script>
	</head>
	<body>
		<h2>To Do</h2>
		<form name="checkListForm">
			<input type="text" name="checkListItem"/>
		</form>
		<div id="button">Add!</div>
		<br/>
		<div class="list"></div>
	</body>
</html>
```
**stylesheet.css**
```
h2 {
    font-family:arial;
}

form {
    display: inline-block;
}

#button{
    display: inline-block;
    height:20px;
	width:70px;
	background-color:#cc0000;
	font-family:arial;
	font-weight:bold;
	color:#ffffff;
	border-radius: 5px;
	text-align:center;
	margin-top:2px;
}

.list {
	font-family:garamond;
	color:#cc0000;
}
```
**script.js**  
```
$(document).ready(function(){
    $('#button').click(function(){
        var toAdd = $('input[name=checkListItem]').val();
        $(".list").append('<div class="item">'+ toAdd + '</div>');
    });
    $(document).on('click', '.item', function(){
        $(this).remove();
    });
});
```
###Generalized jQuery setup
```
$(document).ready(function() {
    $('thingToTouch').event(function() {
        $('thingToAffect').effect();
    });
});

where:
"thing to touch" is the HTML element you'll click on, hover over, or otherwise interact with
"thing to affect" is the HTML element that fades away, changes size, or undergoes some other transformation
```
