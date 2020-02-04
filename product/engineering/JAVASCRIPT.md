# Javascript Best Practices

# jQuery

While we won't normally use jQuery for a new project at Countable, several older projects do use it. jQuery has been unpopular for large software projects due to maintainability issues, and thsoe concerns are founded. However, taking some care in how you use the library helps keep jQuery projects maintainable.

Most of the problems maintaining jQuery apps come from [DOM Manipulation](https://api.jquery.com/category/manipulation/) which leads to needlessly complex state. To minimize this, here are some guidelines to use where possible.

Where possible, just `.hide()` and `.show()` different pieces of pre-defined content instead of creating it on the fly. ie)

```
// bad
$(".some-selector").append("<a id='abc_error_message' class='error hidden'>error message here</a>")

// better
// <a id='abc_error_message' class='error hidden'>error message here</a> <!--already in index.html-->
$("#abc_error_message").show()
```

If you must dynamically generate HTML, `.html` and `.text` for setting a large block of generated information, with ES6 strings.
```
$("#parent_id").html(`<b> here is a dynamic fragment. ${variable} ${variable}</b>`)
```

To make small changes to how something looks, animate it, open/close, etc. use `addClass` and `removeClass`.

```
// bad
$("#accordion").css('height', '25px')

// better
// define the actual CSS in the .open-accordion class.
$("#accordion").addClass('open-accordion')
```

Use ID instead of class for selecting items in jQuery:
```
// bad
$(".next")

// better
$("#main-modal-next-button")
```

When manipulating the DOM, as in `https://api.jquery.com/category/manipulation/`, prefer:

  * `.hide()`, `.show()`, `.addClass()`, `.removeClass()`, `.toggleClass()`, `.val()`

if needed, use:
  * `.text()`, `.html()`

avoid:

  * `.after()`, `.append()`, `.attr()`, `.before()`, `.clone()`, `.css()`, `.remove()`, and everything else.

### When traversing the DOM many times, load one into memory first!

```
<div id="one">
  <div id="two">
    <div id="three">
      <div id="four">
      <div>
    <div>
  <div>
<div>
```

It is better to query the DOM once, cache it then use the `find` method to grab elements. See cache.find performance test here: https://jsperf.com/selector-vs-find-again/11
```
// BAD
const one = $("#one");
const two = $("#two");
const three = $("#three");
const four = $("#four");

// GOOD
const one = $("#one);
const two = one.find("#two");
const three = one.find("#three");
const four = one.find("#four");

```

### You can do PubSub with jQuery

```
// not ideal
$('#myButton').on('click', update_ui())
$('#myButton').on('click', update_ui2()) // elsewhere in code
$('#myButton').on('click', get_new_data()) // in another component

// It's better to use this method to trigger and listen to custom events, than to have many primary event handlers. This way, updates can be centralized.
$('#myButton').on('click', function() {
  $(document).trigger('testEvent', 'Hello World');
});
$(document).on('testEvent', function(e, data) { 
    update_ui()
});
$(document).on('testEvent', update_ui());
$(document).on('testEvent', function(e, data) { 
    get_new_data()
});
```

### Prefer Event Delegation in jQuery

Event delegation means you'll never have bugs with event handlers being created too late or being lost due to dom updates.

```
// It's bad to do this, particularly if #confirm_popup_button might not exist.
$('#confirm_popup_btn').click(function () {...})

// Better to use event delegation, because it will work even if #confirm_popup_btn is created later.
$('body').on('click', '#confirm_popup_btn', function () {...})
```
