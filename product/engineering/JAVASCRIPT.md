# Javascript Best Practices

# jQuery

While we won't normally use jQuery for a new project at Countable, several older projects do use it. jQuery has been unpopular for large software projects due to maintainability issues, and thsoe concerns are founded. However, taking some care in how you use the library helps keep jQuery projects maintainable.

Most of the problems maintaining jQuery apps come from [DOM Manipulation](https://api.jquery.com/category/manipulation/) which leads to needlessly complex state. To minimize this:

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
$("#parent_id").html(`<b> here is a dynamic fragment. ${varaible} ${variable}</b>`)
```

When manipulating the DOM, as in `https://api.jquery.com/category/manipulation/`, prefer:

  * `.hide()`, `.show()`, `.addClass()`, `.removeClass()`, `.toggleClass()`, `.val()`

if needed, use:
  * `.text()`, `.html()`

avoid:

  * `.after()`, `.append()`, `.attr()`, `.before()`, `.clone()`, `.css()`, `.remove()`, and everything else.


