---
project: sketch2html
stars: 36
description: |-
    Convert a Hand-drawn Sketch to HTML/CSS code
url: https://github.com/iSysLab/sketch2html
---

# Sketch2HTML
* Demonstration video
>[![sketch2html](http://img.youtube.com/vi/uLR1RNqJ1Mw/0.jpg)](https://youtu.be/At2FMvgjaSc) 

* Demo web application for converting a hand-drawn sketch 2 html code
* The converting module is now actively being developed.

* Left: Sketch, Right: Auto-generated Web page
 
![](demo.jpg)

* Auto-generated HTML code

```html
<html>
<head>
<link rel=stylesheet type=text/css href="sketch2html_result_1523510698424.css" /></head>
<body>
	<div id="div0">
	text
	<input type="text" id="editText3"/>
	<input type="button" id="button3" value="button"/>
	<input type="button" id="button2" value="button"/>
	</div>
	<div id="div1">
		<div id="div2">
		<input type="checkbox" id="checkBox3"/><label> check
		<br>
		<input type="checkbox" id="checkBox2"/><label> check
		<br>
		<input type="checkbox" id="checkBox1"/><label> check
		<br>
		<input type="checkbox" id="checkBox0"/><label> check
		<br>
		<input type="button" id="button1" value="button"/>
		</div>
		<div id="div3">
		<input type="text" id="editText2"/>
		<br>
		<input type="text" id="editText1"/>
		<br>
		<input type="text" id="editText0"/>
		<br>
		<input type="button" id="button0" value="button"/>
		</div>
	</div>
	<div id="div4">
	text
	</div>

</body>
</html>
```

# How to run
* $ pip install -r requirements.txt
* $ python app.py
* Open http://127.0.0.1:5000 in your web browser

# Model's Weights
* You need the model's weights file to run
* To train the model, run
* $ model model_frcnn
* [Pre-trained model file](https://drive.google.com/open?id=1aP4nfyW7Xu_XAVJn_JsT6Hpzp9zFTUt4) ( > 100MB)


