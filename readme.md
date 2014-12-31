Crystal.js
---
##### Version v0.1.4
##### See it in action at http://cojomojo.github.io/Crystal.js/

## A lightweight Javascript inline/live form validator
+ 4KB minified 
+ No JQuery.

## Getting Started
1. Download or clone Crystal.js and include it in your HTML markup.
    
    ```html
    <script type='text/javascript' src='/path/to/crystal.min.js'></script>
    ```

2. Add the necessary HTML markup to input and textarea elements you want to apply Crystal to. You'll just have to add a data attribute `data-crystal` with the value begin the kind of field it is (e.g. a name field, email, etc.). You'll be creating validation rules using this value later on.
    
    ```html
    <input data-crystal="name" type="text">
    ```

3. Add the CSS

    ```css
    .crystal-invalid {
        border: 2px solid #f15b22 !important;
    }
    ```

4. Instantiate Crystal. The constructor takes one parameter, the parent node for all forms you want to apply Crystal to. By default this is `document`. 

    ```javascript
    var crystal = new Crystal();
    // OR somethiing like this
    var crystal = new Crystal(document.getElementById("demo1"));
    ```

## Creating Validation Rules
The flexibility of Crystal.js is because it allows for you to define the validation rules. It is very simple, just use the method `setFieldConfig`.

```javascript
/**
 * Sets the configurable parts of the 
 * @param {int | int array | "all"} [id] the "data-crystal-id"(s) of the element(s) to set the config for
 * @param {string} the "data-crystal" value you want to create validation for
 * @param {config} an object with the following params
 * @param {regex literal} [regex] Regex literal to test input value agains. You want this to match valid input
 * @param {input|blur} [trigger] Event that determines when fields are checked for validity. Defaults to "input".
 */
crystal.setFieldConfig("all", "name", {
    regex: /^(?!\s*$).+/,
});
```

Check out [these](https://github.com/cojomojo/Crystal.js/blob/master/validation-examples/common.js) awesome validation configurations for some common fields like name, email, and message. 

## Using the Event Emitter
The next thing you will want to do is decide what will happen if a user submits a form when fields are valid or invalid. Crystal.js proivdes an event emitter to make handling this easy. Check out this example (setup for the Crystal.js [home page](http://cojomojo.github.io/Crystal.js/)):

```js
crystal.ee.on("valid", function(el){
    alert("Message Sent");
})
    
crystal.ee.on("invalid", function(el){
    document.getElementById("not-valid").style.display = "block";
})
```

*Note that when a form's submit button is pressed, and a field is invalid, `preventDefault()`is applied.*

## Going Further
Crystal.js can be very powerful. Check out the [GitHub Wiki](https://github.com/cojomojo/crystal.js/wiki) for the complete and in depth documentation.

## Contributing
The goal of crystal.js is to be a lightweight boilerplate for simple inline form validation. Thus, when contributing keep this in mind. Fork, and send a pull request. All contributors will be added to a list of contributors.

## License
MIT
