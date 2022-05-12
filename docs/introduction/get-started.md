## Prerequisites
### Sign Up for Earth Engine Account

## Earth Engine JavaScript Playground
The Code Editor is an interactive environment for developing Earth Engine applications (Figure 1). The center panel provides a JavaScript code editor. Above the editor are buttons to save the current script, run it, and clear the map. The Get Link button generates a unique URL for the script in the address bar. The map in the bottom panel contains the layers added by the script. At the top is a search box for datasets and places. The left panel contains code examples, your saved scripts, a searchable API reference and an asset manager for private data. The right panel has an inspector for querying the map, an output console, and a manager for long-running tasks. The help button help in the upper right contains links to this Guide and other resources for getting help. Learn more from the Code Editor guide and the Get Help guide.

### Basic Javascript Syntax
This is an example of javascript code snippet on markdown

```js
// Line comments start with two forward slashes. Like this line.

/* Multi line comments start with a forward slash and a star,
and end with a star and a forward slash. */

// Variables are used to store objects, and are defined using the keyword var.
var the_answer = 42;

// String objects start and end with a single quote.
var my_variable = "I am a string";

// String objects can also start and end with double quotes.
// But don't mix and match them.
var my_other_variable = "I am also a string";

// Statements should end in a semi-colon, or the editor complains.
var test = "I feel incomplete...";

// Parentheses are used to pass parameters to functions.
print("This string will print in the Console tab.");

// Square brackets are used for selecting items within a list.
// The zero index refers to the first item in the list.
var my_list = ["eggplant", "apple", "wheat"];
print(my_list[0]);

// Curly brackets (or braces) can be used to define dictionaries (key:value pairs)
var my_dict = { food: "bread", color: "red", number: 42 };
// Square brackets can be used to access dictionary items by key.
print(my_dict["color"]);
// Or you can use the dot notation to get the same result.
print(my_dict.color);

// Functions can be defined as a way to reuse code and make it easier to read
var my_hello_function = function (string) {
  return "Hello " + string + "!";
};
print(my_hello_function("world"));
```
### Add data to the Map


### Earth Engine data structures

