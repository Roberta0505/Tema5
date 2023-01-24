
Starting with the flights information in the flights.json file (taken from https://gist.github.com/tdreyno/4278655)
Add them to your js file like this:
```javascript
let flights = // flights.json data here
```
Under the `head` tag in your html page add:
```css
p {
    display: inline-block;
}
```
this will display all paragraphs in your page on a single line

1. Create a class called FlightsManager. This class is responsible for displaying flights with a load more functionality, meaning that there should be a button that when clicked, more elements of the array are displayed to the screen. Flights manager will have the folowing properties:
Members (all private):
- current_index - the last index in the array that was displayed (used to load additional data)
- elements_per_page - the number of elements that should be loaded when the load more button is clicked
- container - a html div that will be used to append all elements that we need

Member functions:
- a constructor taking container and elements_per_page as parameters. the constructor will set container and elements_per_page with the parameters and current_index to 0. In the constructor we also want to add the Load More button. Create a button element, set its innerHTML to `Load More` and the onclick to an arrow (Warning!! arrow not normal, its very important so we can capture this as a FlightsManager object inside the function) function that only calls this.on_button_click (see the next point). Append the button to the container.
- on_button_click a function that will get called on every click of the load more button that will currently only print and increment current_index

2. In the html create a div element with a custom id. Back in the js file, in the `window.onload` construct a FlightManager object. Load the index.html in the browser, you should see a load more button that when clicked will console.log a new number.

3. Now the hard part. On every click of the button display obejcts_per_page new objects from the flights array as in the example:
```
code:AAA
lat:-17.3595
lon:-145.494
name:Anaa Airport
city:Anaa
state:Tuamotu-Gambier
country:French Polynesia
woeid:12512819
tz:Pacific/Midway
phone:
type:Airports
email:
url:
runway_length:4921
elev:7
icao:NTGA
direct_flights:2
carriers:1
```

To do so, iterate over the flights in the interval [current_position, current_position + elements_per_page) (careful not to go over flights.length). Check lesson 1 for examples on iterating arrays. now, for each element in this iteration iterate over its keys. if you cant remember how to iterate over an object keys, here is an example:
```javascript
// iterate over keys and values in the object `obj`
for (let k in obj) {
    console.log(k + ":" + obj[k]);
}
```
For each `key: value` pair in an object, create two paragraphs and a div. for the paragraphs, set the innerHTML for one of them to the key + ":" and for the other to the value. Append the two paragraphs to the div.
Now we need a way to go to the next line. There is a special HTML tag that i didnt tell you about. It is called `br`. its only purpuse is to break the current line (kinda like a `\n`). Create a `br` element and append it to the line.

Finally, append the div to the container.

Now solve all the bugs created in the process and try not to hate me too much :D 