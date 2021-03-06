Sorting Hat
===========

###Step 0 - In which we set up our Template ###
Open up [sorting_hat.html](https://github.com/hackbrightacademy/Javascript2/blob/master/sorting_hat.html). It's got a basic bootstrap template there for you, so you don't have to look at those ugly default-internet fonts. It doesn't have much else though, so we'll need to add some things.


###Step 1 - In which information is gathered, and events are briefly mentioned###
First, let's take inventory of the things we need:  
- We need to know how many people we'll be sorting, so we can sort them evenly  
- We need the names of the students who are being sorted  
- We need places to put them after having been sorted  

Since we need to gather some information, let's put a form on the page. **_Since this form doesn't have to submit anywhere, we don't want an actual `form` tag_**. If we *did* add a form tag, it would submit the page to itself, instead of activating our cool JS event. We don't want that.  
  
Add a `div` somewhere in the container, give it the `class` of `form`. 

Inside the `div`, put an `input` tag, another (blank) `div`, and a `button`. Give them all IDs.
```html
	<div class="form">
		<input type="number" id="student_count">  
		<button id="set_student_count">Set Student Count</button>  
		<div id="count"></div>
	</div>
```
Next, we're going to practice button-clicking actions that modify the page.

###Step 2 - In which Javascript is written, and certain events transpire ###
To start, we're going to create a `<script>` tag - like this: 
```html
	<script type="text/javascript">
		//Javascript goes here, and runs when the page loads.
	</script>
```

Next, we need a place to store the information we get from the user. Create a globally scoped variable like this, outside of any functions.
```javascript
	var studentCount = 0;
```
Now let's look at what gets put in the input field and add it to the student count. 

To do that, we'll need to make something that responds to a button click, but for that we'll need to **find the button in the DOM**. Good thing we gave it an ID. IDs are supposed to be unique, so we can target single DOM nodes with them.
```javascript
	var button = document.getElementById("set_student_count");
```
And now we can spy on our button, by adding event listeners to it. This is similar to a wiretap, only we don't need a warrant to do it. (Ok so it's exactly like a wiretap apparently.)  
Basically it looks like this:  
```javascript
	button.addEventListener(event, function)
```
The first argument is a string name of an event we want to listen to. It should be "click" (with the quotes).  
The second argument is a function. We can pass it any function by value, or we can write idomatic javascript by declaring a function right then and there.  

Here's a function being declared in place:
  
```javascript
	button.addEventListener('click', function(){})
```

###Step 3 - Events, having transpired, change the nature of the page###
  
Open that function up by dropping a few line breaks within it. Inside that function, let's tell it what to do whenever that button gets clicked.  

Replace each comment with a line of code:  
```javascript
	button.addEventListener('click', function(){
		//get a variable that points to the div that has the count in it by using document.getElementById("count")
		//get value of the input box (document.getElementById("student_count").value) - save it to a variable. If it's blank, set it to 0.
		// add the value to studentCount, the global variable we set up earlier. ( studentCount += some value
		//write the new value of studentCount to the div we found earlier. Use the .innerHTML property of the #student_count div
		//reset the input box( by changing the .value attribute to 0
	})
```
Great! Now we've used a button click to get data out of a form and change the page, without having to use a server at all!

We're going to do that again, but this time we're going to be collecting student names, and sorting them.

We need to add another input field and button, but this time the type will be `text`, and the button will say "Sort!"

Instructions:  
- Take the value from the student name input field  
- Pick a house at random  
- Check to see if the house is "full". Full means that the house has less than the number of students we're sorting divided by the number of houses. Yes, that does mean you'll need to keep track of who is in each house. (Protip: `document.getElementsByClassName()` will help you here )
- If the house is full, make sure you pick a new house, and do the same checks.  
- Put the student into the house you picked, by displaying the student's name inside the house  
- Decrement the count of students from the count div.  
 
Bonus:  
- Show the sorting hat, as well as the student's name, al la: "Stella LeFevre: Gryffindor!!"  
- Turn house names green as they get full  
- Display a random quote from the sorting hat that goes with the house it's saying (or make up hilarious new ones)  
- Once you've sorted all the students, display a gif and get rid of the input field.  
- If we add more students to be sorted, put the input field back.  
