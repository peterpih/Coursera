#Coffee is the rails lightweight version of javascript
#JQuery
File extension is **.js** since it is ***javascript***
Used for making effects (ie animations)  
https://pragmaticstudio.com/blog/2015/3/18/rails-jquery-ajax  

```
// This is a comment

"cake".length  #=> 4
```

```
<div id='green'>      # in HTML
<div class='red'>

#green {              # in .css
}
.red{
}

$("#green")           # in .js, '#' is for id's, '.' is for class
$('.red')
```
###Generalized jQuery setup
```
$(document).ready(function() {
    $('thingToTouch').event(function() {
        $('thingToAffect').effect();
    });
});

where:
document is the entire document (focus)
"thing to touch" is the HTML element you'll click on, hover over, or otherwise interact with
"thing to affect" is the HTML element that fades away, changes size, or undergoes some other transformation
```
###jQuery events
```
$('element').click();
	.dblclick();
	.hover();
	.keydown();
	.fadeTo('speed', delay);
	.animate({action}, time);
	.mouseover();
	.mouseenter();
	.mouseleave();
	
$(this).addClass('active');
	.hide();
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
###Example of getting keyboard input
**html**
```
<!DOCTYPE html>
<html>
    <head>
    	<title>Super Mario!</title>
        <link rel='stylesheet' type='text/css' href='stylesheet.css'/>
		<script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <img src="http://i1061.photobucket.com/albums/t480/ericqweinstein/mario.jpg"/>
	</body>
</html>
```
**stylesheet.css**
```
img {
    position: relative;
    left: 0;
    top: 0;
}
```
**script.js**
```
$(document).ready(function() {
    $(document).keydown(function(key) {
        switch(parseInt(key.which,10)) {
			// Left arrow key pressed
			case 37:
				$('img').animate({left: "-=10px"}, 'fast');
				break;
			// Up Arrow Pressed
			case 38:
				$('img').animate({top:"-=10px"}, 'fast');
				break;
			// Right Arrow Pressed
			case 39:
				$('img').animate({left:"+=10px"},'fast');
				break;
			// Down Arrow Pressed
			case 40:
				$('img').animate({top:"+=10px"},'fast');
				break;
		}
	});
});
```
