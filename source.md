# How to Make a Simple Digital Clock In JavaScript
## Digital clock in javascript

In today’s tutorial, we will create a digital clock in javaScript. That will show us the current time, day, date, month, and year. it will also have a nice dark light mode feature. This digital clock in javascript can be an excellent project for a beginner to understand the basic concepts of JavaScript. Creating this will help you know about accessing the DOM, adding activity to them, and much more. By the end of this tutorial, you’ll be familiar with working with the Javascript Date object, and also you’ll have a minimal understanding of asynchronous code execution and the setInterval.

## Contents

You can see the Demo Here [Build a Simple Digital Clock In JavaScript](https://digital-clock-in-javascript.netlify.app/)

## What should you know before you start?
- HTML
- CSS
- JavaScript
  
## What will we learn?
- Understand Javascript’s built-in setInterval function
- Know how to use the JavaScript Date class
- Know how to create a function
- Know how to invoke or call a function
- Know what variable scope is
- Understand how ternary operators work

## Implementation Digital Clock in JavaScript

To implement the clock, first, we need to create a folder (Digital Clock in JavaScript) for our HTML, CSS, and JavaScript files with their respective extensions (.html, .css, .js). You could use any editor you wish but for this tutorial, I’d prefer you use vs code.

## Create index.html

  Here we are making an attractive UI of Digital clock in javascript

![image](https://user-images.githubusercontent.com/91061592/205450963-69395035-329e-46c9-94e8-37f7094a36b7.png)

Create your HTML file, name it index.html. The code snippet below shows the HTML file structure. Here we can use font awesome icons.
  
```  
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Digital Clock using HTML CSS and JavaScript</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css"
    />
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <section>
      <div class="container">
        <div class="date">12 Jun 2021</div>
        <div class="icons">
          <i class="fas fa-moon"></i>
          <i class="fas fa-sun"></i>
        </div>
        <div class="time">
          <div class="time-colon">
            <div class="time-text">
              <span class="num hour_num">08</span>
              <span class="text">Hours</span>
            </div>
            <span class="colon">:</span>
          </div>
          <div class="time-colon">
            <div class="time-text">
              <span class="num min_num">45</span>
              <span class="text">Minutes</span>
            </div>
            <span class="colon">:</span>
          </div>
          <div class="time-colon">
            <div class="time-text">
              <span class="num sec_num">06</span>
              <span class="text">Seconds</span>
            </div>
            <span class="am_pm">AM</span>
          </div>
        </div>
      </div>
    </section>
    <script src="index.js"></script>
  </body>
</html>
  
```  
To link our JavaScript and CSS files in the HTML file, the script and link tags are used as shown above. Though there are other ways of adding JavaScript and CSS to HTML in this article, I choose to use the external file source.

## create style.css
  
```
/* Google fonts import link */
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700&display=swap');
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Orbitron', sans-serif;
  transition: all 0.4s ease;
}
section{
  min-height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #F0F8FF;
  padding: 0 20px;
}
section.dark{
  background: #24292D;
}
section .container{
  display: flex;
  align-items :center;
  justify-content: center;
  height: 220px;
  max-width: 560px;
  width: 100%;
  background: #fff;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  border-radius: 12px;
  position: relative;
}
section.dark .container{
  background: #323840;
}
section .container .icons i{
  position: absolute;
  right: 17px;
  top: 17px;
  height: 30px;
  width: 30px;
  background: #24292D;
  color: #fff;
  text-align: center;
  line-height: 30px;
  border-radius: 50%;
  font-size: 14px;
  cursor: pointer;
}
section.dark .container .icons i{
  background: #fff;
  color: #323840;
}
.container .icons i.fa-sun{
  opacity: 0;
  pointer-events: none;
}
section.dark .container .icons i.fa-sun{
  opacity: 1;
  pointer-events: auto;
  font-size: 16px;
}
section .container .time{
  display: flex;
  align-items: center;
}
.container .time .time-colon{
  display: flex;
  align-items: center;
  position: relative;
}
.time .time-colon .am_pm{
  position: absolute;
  top: 0;
  right: -50px;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 1px;
}
section.dark .time .time-colon .am_pm{
  color: #fff;
}
.time .time-colon .time-text{
  height: 100px;
  width: 100px;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background: #F0F8FF;
  border-radius: 6px;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
section.dark .time .time-colon .time-text{
  background: #24292D;
}
.time .time-colon .time-text,
.time .time-colon .colon{
  font-size: 35px;
  font-weight: 600;
}
section.dark .time .time-text .num,
section.dark .time .colon{
  color: #fff;
}
.time .time-colon .colon{
  font-size: 40px;
  margin: 0 10px;
}
.time .time-colon .time-text .text{
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 2px;
}
section.dark  .time .time-colon .text{
  color: #fff;
}
section.dark .date{
    color: white;
}
.date{
    position: absolute;
    font-family: sans-serif;
    top: 16px;
    height: 30px;
    width: 100%;
    color: black;
    text-align: center;
    font-size: 15px;
    font-weight: 700;
    letter-spacing: 2px;
}
```  
💡 **Now It’s time For Javascript Code** 😎.

## Create index.js File
### JavaScript Code:
For JavaScript, follow the below-given steps.

- Step 1: Create a function updateClock.
- Step 2: Create an instance of the Date object.
- Step 3: Using the methods of Date object get “hours”, “minute”, “day”, “month”, “year” and “seconds”.
- Step 4: Set AM/PM depending on the hour value. The Date object works on 24-hour format so we change hour back to 1 when it get’s larger than 12. The AM/PM also changes according to that.
- Step 5: Now make a string using the same HH:MM:SS format changing the hour, minute, and second value with the values, we get from Date object methods.
- Step 6: Now replace the string variable in the html element using innerText property.
- Step 7: To call the function every second use setInterval() method and set time-interval as 1000ms which is equal to 1s.
- Step 8: Add Light and Dark Theme

  create a function **updateClock.** In this function, declare a variable **date** and assign the JavaScript date object to it.

A function in JavaScript is a set of statements or code that performs an action.

```  
//function declaration
function updateClock(){
 //variable
 let date = new Date();
}
```
  
All we need to build our digital clock will be in the function block apart from the setInterval method.

setInterval, is a method in JavaScript that takes two parameters, a function and the time it will take before the function executes.


Here is the syntax on how to represent setInterval:

**setInterval(updateClock, 1000);**
The code above means that the function updateClock will keep executing after every 1000 milliseconds.

Now that we’ve got this out of the way, let’s go on to declare other variables. These will take the hour of day, minutes, seconds, days of the week, months, year, and period of the day.

```  
  let hour = date.getHours();
  let min = date.getMinutes();
  let sec = date.getSeconds();
  let day = date.getDay();
  let month = date.getMonth();
  let dateNum = date.getDate();
  let year = date.getFullYear();
  const months = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December",
  ];
  const week = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
  ];
  
```  
You will notice that we’re using the date variable to access the various methods in the JavaScript ***date*** class. We declared it up above in our function block.

- Hours, minutes, and seconds are assigned to the hour, min, and sec variables.
- The week variable contains an array of days of the week.
- The months variable contains an array of month name.
- The year variable gets the year from the getFullYear() method.
- The month variable gets the month using getMonth() but it is the number representation that will be printed using this method.
- The dateNum variable gets the today date
- The day variable gets the day using getDay() but it is the number representation.
  
Our next step would be to couple all of these variables in the function, here is how:

```  
function updateClock(){
  let date = new Date();
  let hour = date.getHours();
  let min = date.getMinutes();
  let sec = date.getSeconds();
  let day = date.getDay();
  let month= date.getMonth();
  let dateNum= date.getDate();
  let year= date.getFullYear();
  const months = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December",
  ];
  const week = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
  ];
}
```
  
Set AM/PM depending on the hour value. The Date object works on 24-hour format so we change the hour back to 1 when it gets larger than 12. The AM/PM also changes according to that.

```  
let d;
  d = hour < 12 ? "AM" : "PM"; //if hour is smaller than 12, than its value will be AM else its value will be pm
  hour = hour > 12 ? hour - 12 : hour; //if hour value is greater than 12 than 12 will subtracted ( by doing this we will get value till 12 not 13,14 or 24 )
  hour = hour == 0 ? (hour = 12) : hour; // if hour value is  0 than it value will be 12
```
  
The next step is to set our clock display pattern.

In our HTML file, we set our clock to display 2 digits for hour of day, seconds, and minutes (00:00:00). We need to write a program to conform to that pattern. In doing that, we will use ternary operator, represented as ?.

The ternary operator is a conditional operator that takes three operands. The first is condition followed by a question mark (?). The second is an expression to execute if the condition is true, followed by a colon (:). Finally, the third operand is another expression to execute if the condition is false. It is a simpler way to write an if-else statement.

```
// adding 0 to the front of all the value if they will less than 10
  hour = hour < 10 ? "0" + hour : hour;
  min = min < 10 ? "0" + min : min;
  sec = sec < 10 ? "0" + sec : sec;
```
                
Our next task is to display our clock on the web page and to do this, we need our JavaScript to manipulate our HTML. This is where the knowledge of the Document Object Model (DOM) comes in handy.

There are various document methods but in this tutorial, we’ll be using document.querySelector. With this, we’ll be able to access an HTML element.

```                
  document.querySelector(".hour_num").innerText = hour;
  document.querySelector(".min_num").innerText = min;
  document.querySelector(".sec_num").innerText = sec;
  document.querySelector(".am_pm").innerText = d;
  document.querySelector(".date").innerText = `${week[day]}, ${months[month]} ${dateNum}, ${year}`;
```
                
The **innerText** property of the [HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement) the interface represents the “rendered” text content of a node and its descendants.

Now add dark mode. first, we need sections and icons. when we get icons then add onclick like
                
```                
let section = document.querySelector("section"),
  icons = document.querySelector(".icons");

icons.onclick = () => {
  section.classList.toggle("dark");
};
```
  
The last thing is a function call or invocation. After our function has been declared, given a function body, it will still not work unless it is invoked or called. 

This is how our final code will look:

```  
let section = document.querySelector("section"),
  icons = document.querySelector(".icons");

icons.onclick = () => {
  section.classList.toggle("dark");
};

// creating a function and calling it in every seconds
setInterval(updateClock,1000); // 1000 milliseconds = 1s

function updateClock(){
  let date = new Date();
  let hour = date.getHours();
  let min = date.getMinutes();
  let sec = date.getSeconds();
  let day = date.getDay();
  let month= date.getMonth();
  let dateNum= date.getDate();
  let year= date.getFullYear();
  const months = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December",
  ];
  const week = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
  ];

  let d;
  d = hour < 12 ? "AM" : "PM"; //if hour is smaller than 12, than its value will be AM else its value will be pm
  hour = hour > 12 ? hour - 12 : hour; //if hour value is greater than 12 than 12 will subtracted ( by doing this we will get value till 12 not 13,14 or 24 )
  hour = hour == 0 ? (hour = 12) : hour; // if hour value is  0 than it value will be 12

  // adding 0 to the front of all the value if they will less than 10
  hour = hour < 10 ? "0" + hour : hour;
  min = min < 10 ? "0" + min : min;
  sec = sec < 10 ? "0" + sec : sec;

  document.querySelector(".hour_num").innerText = hour;
  document.querySelector(".min_num").innerText = min;
  document.querySelector(".sec_num").innerText = sec;
  document.querySelector(".am_pm").innerText = d;
  document.querySelector(".date").innerText = `${week[day]}, ${months[month]} ${dateNum}, ${year}`;
}
```
                
## Conclusion
So this is how you can create a digital clock in javaScript in a beginner-friendly way. we have learned about function declaration and function calls. We’ve also learned about the ternary operator and JavaScript date class.

Full source code: [Build a Simple Digital Clock In JavaScript](https://github.com/patelrohan750/Javascript-projects/tree/master/Dynamic%20Digital%20Clock%20in%20HTML%20CSS%20and%20JavaScript)
