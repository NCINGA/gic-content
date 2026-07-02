# 4 - JS HTML DOM (3).pdf

## Page 1

University of Kelaniya, Sri Lanka
Ms. Hansi Udapola
B.Sc. (Special) in Computer Science
Lecturer (Probationary)
Department of Software Engineering
Faculty of Computing and Technology.
E-Mail – hansi@kln.ac.lk

## Page 2

Department of Software Engineering, University of Kelaniya, Sri Lanka
CTEC 32033
Web Programming - II
The HTML DOM
Chapter 4

## Page 3

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
• When a web page is loaded, the browser creates a 
Document Object Model of the page.
• The HTML DOM model is constructed as a tree of Objects:
The HTML DOM (Document Object Model)

## Page 4

Department of Software Engineering, University of Kelaniya, Sri Lanka
DOM (Document Object Model)
• With the object model, JavaScript gets all the power it 
needs to create dynamic HTML:
change all the HTML elements in the page
change all the HTML attributes in the page
change all the CSS styles in the page
remove existing HTML elements and attributes
add new HTML elements and attributes
react to all existing HTML events in the page
create new HTML events in the page
The HTML DOM (Document Object Model)

## Page 5

Department of Software Engineering, University of Kelaniya, Sri Lanka
What is the DOM?
• The DOM is a W3C (World Wide Web Consortium) 
standard.
• The DOM defines a standard for accessing documents:
• "The W3C Document Object Model (DOM) is a platform and 
language-neutral interface that allows programs and scripts 
to dynamically access and update the content, structure, 
and style of a document.“ – W3C
• The W3C DOM standard is separated into 3 different parts:
Core DOM - standard model for all document types
XML DOM - standard model for XML documents
HTML DOM - standard model for HTML documents
The HTML DOM (Document Object Model)

## Page 6

Department of Software Engineering, University of Kelaniya, Sri Lanka
What is the HTML DOM?
• The HTML DOM is a standard object model and 
programming interface for HTML. It defines:
HTML elements as objects
properties of all HTML elements
methods to access all HTML elements
events for all HTML elements
• In other words: The HTML DOM is a standard for how to 
get, change, add, or delete HTML elements.
The HTML DOM (Document Object Model)

## Page 7

Department of Software Engineering, University of Kelaniya, Sri Lanka
HTML DOM Methods
• HTML DOM methods are actions you can perform on HTML 
Elements.
• HTML DOM properties are values of HTML Elements that 
you can set or change.
The HTML DOM (Document Object Model)

## Page 8

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
<html>
<body>
<p id="demo"></p>
<script>
document.getElementById("demo").innerHTML = "Hello World!";
</script>
</body>
</html>
In the example above, getElementById is a method, while innerHTML is a property.

## Page 9

Department of Software Engineering, University of Kelaniya, Sri Lanka
Finding HTML Elements
Method
Description
document.getElementById(id)
Find an element by element id
document.getElementsByTagName(name)
Find elements by tag name
document.getElementsByClassName(name)
Find elements by class name
querySelectorAll(selector)
Find elements by selector name
Ex: document.querySelectorAll("p.intro");
The HTML DOM (Document Object Model)

## Page 10

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
.c1{
color:orange;
font-family:courier;}

## Page 11

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
function fun1(){
document.getElementById("id1").innerHTML = "Changed the heading with id1";
}

## Page 12

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
function fun2(){
for (let x of document.getElementsByTagName("h1")) {
x.innerHTML = "Changed All headings";
}
}

## Page 13

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
function fun3(){
elemList = document.getElementsByClassName("c1");
for (let i=0; i<elemList.length; i++) {
elemList[i].innerHTML = "Changed All elements with c1 class";
}
}

## Page 14

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
function fun4(){
Array.from(document.querySelectorAll("h1.c1")).forEach(function(elem){
elem.innerHTML = "Changed only headings &lt;h1&gt; with C1 class";
});
}

## Page 15

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
function fun5(){
Array.from(document.querySelectorAll("h1.c1, h2.c1")).forEach(function(elem){
elem.innerHTML = "Changed all headings and sub headings with C1 class";
});
}

## Page 16

Department of Software Engineering, University of Kelaniya, Sri Lanka
Changing HTML Elements
Property
Description
element.innerHTML = new html content
Change the inner HTML of an element
element.style.property = new style
Change the style of an HTML element
Method
Description
element.setAttribute(attribute, value)
Change the attribute value of an HTML element
The HTML DOM (Document Object Model)

## Page 17

Department of Software Engineering, University of Kelaniya, Sri Lanka
function fun1(){
document.getElementById("id1").innerHTML = "Changed the heading with id1";
document.getElementById("id1").style.backgroundColor = "#000";
document.getElementById("id1").setAttribute("class", "c1");
//document.getElementById("id1").style.display = "none";
}

## Page 18

Department of Software Engineering, University of Kelaniya, Sri Lanka
Adding and Deleting Elements
Method
Description
document.createElement(element)
Create an HTML element
document.removeChild(element)
Remove an HTML element
document.appendChild(element)
Add an HTML element
document.replaceChild(new, old)
Replace an HTML element
document.write(text)
Write into the HTML output stream
The HTML DOM (Document Object Model)

## Page 19

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
.c1{
color:orange;
font-family:courier;
}

## Page 20

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)

## Page 21

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)

## Page 22

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)

## Page 23

Department of Software Engineering, University of Kelaniya, Sri Lanka
Finding HTML Objects
• The first HTML DOM Level 1 (1998), defined 11 HTML 
objects, object collections, and properties. These are still 
valid in HTML5.
• Later, in HTML DOM Level 3, more objects, collections, and 
properties were added.
The HTML DOM (Document Object Model)

## Page 24

Department of Software Engineering, University of Kelaniya, Sri Lanka
Property
Description
DOM
document.anchors
Returns all <a> elements that have a name attribute
1
document.baseURI
Returns the absolute base URI of the document
3
document.body
Returns the <body> element
1
document.cookie
Returns the document's cookie
1
document.doctype
Returns the document's doctype
3
document.documentElement
Returns the <html> element
3
document.documentMode
Returns the mode used by the browser
3
document.documentURI
Returns the URI of the document
3
document.domain
Returns the domain name of the document server
1
document.embeds
Returns all <embed> elements
3
document.forms
Returns all <form> elements
1
document.head
Returns the <head> element
3
document.images
Returns all <img> elements
1
The HTML DOM (Document Object Model)

## Page 25

Department of Software Engineering, University of Kelaniya, Sri Lanka
Property
Description
DOM
document.implementation
Returns the DOM implementation
3
document.inputEncoding
Returns the document's encoding (character set)
3
document.lastModified
Returns the date and time the document was updated
3
document.links
Returns all <area> and <a> elements that have a href 
attribute
1
document.readyState
Returns the (loading) status of the document
3
document.referrer
Returns the URI of the referrer (the linking document)
1
document.scripts
Returns all <script> elements
3
document.strictErrorChecking
Returns if error checking is enforced
3
document.title
Returns the <title> element
1
document.URL
Returns the complete URL of the document
1
The HTML DOM (Document Object Model)

## Page 26

Department of Software Engineering, University of Kelaniya, Sri Lanka
Finding HTML Elements by HTML Object Collections
The HTML DOM (Document Object Model)
<form id="frm1" action="/action_page.php">
First name: <input type="text" name="fname" value=“Nimal"><br>
Last name: <input type="text" name="lname" value=“Perera"><br><br>
<input type="submit" value="Submit">
</form> 
<button onclick="myFunction()">Try it</button>
<p id="demo"></p>
<script>
function myFunction() {
var x = document.forms["frm1"];
var text = ""; var i;
for (i = 0; i < x.length ;i++) {
text += x.elements[i].value + "<br>";
}
document.getElementById("demo").innerHTML = text;
}
</script>
In the forms collection, and 
displays all element values

## Page 27

Department of Software Engineering, University of Kelaniya, Sri Lanka
Changing HTML
• Changing the HTML Output Stream
• JavaScript can create dynamic HTML content. In JavaScript, 
document.write() can be used to write directly to the HTML 
output stream.
• Changing HTML Content
• The easiest way to modify the content of an HTML element is by 
using the innerHTML property.
• Changing the Value of an Attribute
• To change the value of an HTML attribute, use this syntax:
document.getElementById(id).attribute = new value;
Ex: document.getElementById("myImage").src = "landscape.jpg";
The HTML DOM (Document Object Model)

## Page 28

Department of Software Engineering, University of Kelaniya, Sri Lanka
Changing HTML (Cont.)
• Changing HTML Style
• To change the style of an HTML element, use this syntax:
document.getElementById(id).style.property = new style
Ex: document.getElementById("p2").style.color = "blue";
• Using Events
• The HTML DOM allows you to execute code when an event occurs.E
vents are generated by the browser when "things happen" to HTML 
elements:
An element is clicked on
The page has loaded
Input fields are changed
Ex: <button type="button“ onclick="document.getElementById('id1').style.color = 'red'">
Click Me!</button>
The HTML DOM (Document Object Model)

## Page 29

Department of Software Engineering, University of Kelaniya, Sri Lanka
HTML DOM Animation
• JavaScript animations are done by programming gradual 
changes in an element's style.
• The changes are called by a timer. When the timer interval 
is small, the animation looks continuous.
The HTML DOM (Document Object Model)

## Page 30

Department of Software Engineering, University of Kelaniya, Sri Lanka
Let’s add simple animation on an image
The HTML DOM (Document Object Model)

## Page 31

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)

## Page 32

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)

## Page 33

Department of Software Engineering, University of Kelaniya, Sri Lanka
HTML DOM Events
• A JavaScript can be executed when an event occurs, like when a user 
clicks on an HTML element.
• To execute code when a user clicks on an element, add JavaScript code to 
an HTML event attribute.
• Examples of HTML events:
When a user clicks the mouse Ex: <h1 onclick="this.innerHTML = 'Ooops!'">Click on this text!</h1>
When a web page has loaded
When an image has been loaded
When the mouse moves over an element
When an input field is changed
When an HTML form is submitted
When a user strokes a key
The HTML DOM (Document Object Model)
onclick=JavaScript

## Page 34

Department of Software Engineering, University of Kelaniya, Sri Lanka
• HTML Event Attributes
• To assign events to HTML elements you can use event attributes.
• Assign Events Using the HTML DOM
• The HTML DOM allows you to assign events to HTML elements using 
JavaScript:
The HTML DOM (Document Object Model)
<button onclick="displayDate()">The time is?</button>
<script>
function displayDate() {
document.getElementById("demo").innerHTML = Date();
}
</script>
<button id="myBtn">Try it</button>
<p id="demo"></p>
<script>
document.getElementById("myBtn").onclick = displayDate;
function displayDate() {
document.getElementById("demo").innerHTML = Date();
}
</script>

## Page 35

Department of Software Engineering, University of Kelaniya, Sri Lanka
HTML DOM EventListener
• The addEventListener() method attaches an event handler to the specified element.
• The addEventListener() method attaches an event handler to an element without 
overwriting existing event handlers.
• You can add many event handlers to one element.
• You can add many event handlers of the same type to one element, i.e two "click" 
events.
• You can add event listeners to any DOM object not only HTML elements. i.e the 
window object.
• The addEventListener() method makes it easier to control how the event reacts to 
bubbling.
• When using the addEventListener() method, the JavaScript is separated from the 
HTML markup, for better readability and allows you to add event listeners even 
when you do not control the HTML markup.
• You can easily remove an event listener by using the removeEventListener() 
method. Ex: element.removeEventListener("mousemove", myFunction);
The HTML DOM (Document Object Model)

## Page 36

Department of Software Engineering, University of Kelaniya, Sri Lanka
Syntax
• The first parameter is the type of the event (like "click" or "mousedown" or 
any other HTML DOM Event.)
• The second parameter is the function we want to call when the event 
occurs.
• The third parameter is a boolean value specifying whether to use event 
bubbling or event capturing. This parameter is optional.
• Bubbling the inner most element's event is handled first and then the 
outer.(default)
• Capturing the outer most element's event is handled first and then the inner.
The HTML DOM (Document Object Model)
element.addEventListener(event, function, useCapture);

## Page 37

Department of Software Engineering, University of Kelaniya, Sri Lanka
Example
The HTML DOM (Document Object Model)
<button id="myBtn">Try it</button>
<script>
document.getElementById("myBtn").addEventListener("click", myFunction);
function myFunction() {
alert ("Hello World!");
}

## Page 38

Department of Software Engineering, University of Kelaniya, Sri Lanka
DOM Nodes
• According to the W3C HTML DOM standard, everything in an 
HTML document is a node:
The entire document is a document node
Every HTML element is an element node
The text inside HTML elements are text nodes
Every HTML attribute is an attribute node (deprecated)
All comments are comment nodes
• With the HTML DOM, all nodes in the node tree can be accessed 
by JavaScript.
• New nodes can be created, and all nodes can be modified or 
deleted.
The HTML DOM (Document Object Model)

## Page 39

Department of Software Engineering, University of Kelaniya, Sri Lanka
DOM Node
The HTML DOM (Document Object Model)

## Page 40

Department of Software Engineering, University of Kelaniya, Sri Lanka
Node Relationships
• The nodes in the node tree have a hierarchical relationship 
to each other.
• The terms parent, child, and sibling are used to describe the 
relationships.
In a node tree, the top node is called the root (or root node)
Every node has exactly one parent, except the root (which has no 
parent)
A node can have a number of children
Siblings (brothers or sisters) are nodes with the same parent
The HTML DOM (Document Object Model)

## Page 41

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
<html>
<head>
<title>DOM Tutorial</title>
</head>
<body>
<h1>DOM Lesson one</h1>
<p>Hello world!</p>
</body>
</html>

## Page 42

Department of Software Engineering, University of Kelaniya, Sri Lanka
Navigating Between Nodes
• You can use the following node properties to navigate 
between nodes with JavaScript:
parentNode
childNodes[nodenumber]
firstChild
lastChild
nextSibling
previousSibling
The HTML DOM (Document Object Model)

## Page 43

Department of Software Engineering, University of Kelaniya, Sri Lanka
Creating New HTML Elements (Nodes)
• To add a new element to the HTML DOM, you must create 
the element (element node) first, and then append it to an 
existing element.
The HTML DOM (Document Object Model)
<div id="div1">
<p id="p1">This is a paragraph.</p>
<p id="p2">This is another paragraph.</p>
</div>
<script>
var para = document.createElement("p");
var node = document.createTextNode("This is new.");
para.appendChild(node);
var element = document.getElementById("div1");
element.appendChild(para);
</script>

## Page 44

Department of Software Engineering, University of Kelaniya, Sri Lanka
Creating new HTML Elements - insertBefore()
• The appendChild() method in the previous slide, appended 
the new element as the last child of the parent.
• If you don't want that you can use the insertBefore() 
method:
The HTML DOM (Document Object Model)

## Page 45

Department of Software Engineering, University of Kelaniya, Sri Lanka
The HTML DOM (Document Object Model)
<div id="div1">
<p id="p1">This is a paragraph.</p>
<p id="p2">This is another paragraph.</p>
</div>
<script>
var para = document.createElement("p");
var node = document.createTextNode("This is new.");
para.appendChild(node);
//para.innerHTML = "This is new"
var element = document.getElementById("div1");
var child = document.getElementById("p1");
element.insertBefore(para,child);
</script>

## Page 46

Department of Software Engineering, University of Kelaniya, Sri Lanka
Removing Existing HTML Elements
• To remove an HTML element, use the remove() method.
The HTML DOM (Document Object Model)
<div>
<p id="p1">This is a paragraph.</p>
<p id="p2">This is another paragraph.</p>
</div>
<button onclick="myFunction()">Remove Element</button>
<script>
function myFunction() {
var elmnt = document.getElementById("p1");
elmnt.remove();
}
</script>

## Page 47

Department of Software Engineering, University of Kelaniya, Sri Lanka
In Class Activity
• Write a function to read name and age through a simple form. There is button 
called add. When you click on that button, you should display data in a table by 
adding each row into the table programmatically. (Hint: Use insertCell, and 
insertRow to append rows and cells into your table.)
The HTML DOM (Document Object Model)
