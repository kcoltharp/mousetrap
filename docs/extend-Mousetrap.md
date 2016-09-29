#Extending Mousetrap


Any of the public methods can be overwritten to extend Mousetrap.

A few example extensions are:
###Global bindings###

[View](https://github.com/kcoltharp/mousetrap/tree/documentation-edits/plugins/global-bind)

This extension allows you to specify keyboard events that will work anywhere including inside textarea/input fields.

Usage looks like:
```
Mousetrap.bindGlobal('ctrl+s', function() {
    _save();
});
```

This means that a keyboard event bound using `Mousetrap.bind` will only work outside of form input fields, but using `Moustrap.bindGlobal` will work in both places.

If you wanted to create keyboard shortcuts that only work when you are inside a specific textarea you can do that too by creating your own extension.
###Bind dictionary###

View or Download

This extension overwrites the default bind behavior and allows you to bind multiple combinations in a single bind call.

Usage looks like:

```
stopCallback: function(e, element, combo) {

    // if the element has the class "mousetrap" then no need to stop
    if ((' ' + element.className + ' ').indexOf(' mousetrap ') > -1) {
        return false;
    }

    // stop for input, select, and textarea
    return 
        element.tagName == 'INPUT' 
        || element.tagName == 'SELECT' 
        || element.tagName == 'TEXTAREA' 
        || (element.contentEditable && element.contentEditable == 'true');
}
```
You can optionally pass in `keypress`, `keydown` or `keyup` as a second argument.

Other bind calls work the same way as they do by default.
###Pause/unpause###

View or Download

This extension allows Mousetrap to be paused and unpaused without having to reset keyboard shortcuts and rebind them.

Usage looks like:

```
// stop Mousetrap events from firing
Mousetrap.pause();

// stop Mousetrap events from firing
Mousetrap.pause();
```

###Record###

View or Download

This extension allows you to record keyboard shortcuts from your application. For example if you wanted to let users specify their own keyboard shortcuts for performing actions on your page you could ask them to enter a shortcut.

Usage looks like:

```
<button onclick="recordSequence()">Record</button>

<script>
    function recordSequence() {
        Mousetrap.record(function(sequence) {
            // sequence is an array like ['ctrl+k', 'c']
            alert('You pressed: ' + sequence.join(' '));
        });
    }
</script>
```

###Using extensions###

To use any of these extensions all you have to do is include the javascript on your page after you include Mousetrap.
