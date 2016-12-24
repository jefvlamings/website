---
layout: post
title:  "A clean calendar in CSS3 & jQuery"
date:   2011-11-03 16:47:14
categories: css javascript css3 jquery html5
---
![CSS3 Calendar screenshot]({{ site.url }}/assets/css3-calendar.gif)

Almost a year ago I had the idea to build a calendar app. The project was called LiveCal and was supposed to become a platform where you could share calendars. The whole idea was that calendars would become something you subscribe to. Let me clarify. Let’s say you are subscribed to the calendar stream of your school. One of your teachers plans an event, such as a task or a test and adds it to the calendar stream. From the moment the event is added to the stream, you’ll get a instant notification that a new event is being planned. This means you’ll always walk around with an updated calendar. Due to the complexity of the idea and the lack of knowledge on my side this project never really took off.

Nevertheless I started to make a CSS3 calendar with some jQuery animation while I was working on this project. In this article I will explain, step by step, how to use the calendar.

## How to get it

Visit the Github repo [here](https://github.com/jefvlamings/css3-calendar)

## How to use it

You’re allowed to use the calendar for your own purpose. For those who are interested to learn a bit more about how the calendar is built, I made a short guide about the animated CSS3 calendar.

### Basic HTML structure

The first thing we have to do is add structure to the HTML file. To keep things as simple as possible I used the usual terms you find in a calendar. A day is nested in a week and a week is nested in a month. The div that represents a day is divided in three subdivs:

* **daybar**: the top bar displaying the day’s number of the month
* **dots**: a div containing an unordered list to present dots according to the events of that day.
* **open**: a div containing all events of that day. This div is only visible if it’s slid out.

```html
<div class="week">
    <div class="day">
        <div class="daybar">
            <p>31</p>
        </div>
        <div class="dots">
           <ul>
               <li></li>
           </ul>
        </div>
        <!-- slide open -->
        <div class="open">
           <ul>
               <li></li>
           </ul>
        </div>
        <!-- slide closed -->
    </div>
</div>
```

At the end of this article you can find out how I used jQuery to animate the accordion style calendar.

### CSS Styling

There are three styling elements that are important in the calendar.

* **Color**: add color to the dots and the events
* **Length**: add length to the events. A one hour event should be half the size of a two hour event
* **Padding**: Position each event on the right spot.

#### Colors

For this calendar I made four classes with color names. If you add one of the classes to any div then that div will obtain the background color of that class. For example, if you want to create a green dot, you add the class “green” to the list element.

```html
<div class="dots">
    <ul>
        <li class="red"></li>
        <li class="green"></li>
        <li class="yellow"></li>
        <li class="blue"></li>
    </ul>
</div>
```

* Red
* Green
* Yellow
* Blue

This calendar makes use of 4 different colors. Of course you can add as many colors as you want.

#### Event length

Instead of giving each individual event a specific height or length, I made some pre formatted classes you can use. Just type “lxx” where x is the amount of hours you want the event to be.

* **l1** = 1 hour event
* **l5** = 5 hour event

For example:
```html
<div class="open">
    <ul>
        <li class="yellow l2"><p>2 hour event</p></li>
        <li class="green l10"><p>10 hour event</p></li>
    </ul>
</div>
```
#### Event padding

We now managed to add color and length to the events. To position each event on the row according to the start of the event, we need to add an extra class to each div. I made a preformatted class “ax” where x stands for the amount of hours between the previous event or the beginning of the day if no event took place.

* **a1** = after 1 hour. The event starts at 1 o’clock
* **a12** = after 12 hours. The event starts at 12 o’clock
* Multiple events
    * **a8** = after 8 hours. The first event starts at 8 o’clock
    * **a4** = after 4 hours. The second events starts 4 hours after the previous event, which is at 12 o’clock

For example:
```html
<div class="open">
    <ul>
        <li class="yellow l1 a13"><p>13:00 first event</p></li>
        <li class="yellow l1 a1"><p>15:00 second event</p></li>
        <li class="red l2 a3"><p>19:00 third event</p></li>
    </ul>
</div>
```
Keep in mind you’ll have to take the length of the event into account when you are adding spacing above an event.

### jQuery magic

For the accordion effect used in this calendar I made a customized script based on the Simple jQuery Accordion menu. I tried to simplify the Simple jQuery Accordion script resulting in fewer lines of code. Here is my version.

```js
function initMenu() {
    //create variable named "block" and put class ".day" in it
    var block = $(".day");
    //hide every div with class "open"
    $('.open').hide();
    //when a div with class ".day" is clicked ...
    block.click(
        function() {
            //... find all divs with class "open" and slide them open
            $(this).parents('div:eq(0)').find('.open').slideToggle('fast');
        }
    );}
$(document).ready(function() {initMenu();});
```
Put this piece of code in the header of your HTML file and you should be ready to go!

## Questions?

As I’m no longer using this calendar for the project I thought it could be useful for someone else. I hope my instructions are clear enough for you to figure out how to use it. If you have any problems with the calendar, feel free to ask questions. I’ll try to answer as quickly as possible.