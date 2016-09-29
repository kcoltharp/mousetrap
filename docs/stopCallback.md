#Mousetrap.stopCallback


Mousetrap.stopCallback is a method that is called to see if the keyboard event should fire based on if you are inside a form input field.

It gets passed three arguments:

* e - key event that triggered this callback
* element - reference to the target element for the event
* combo - the specific keyboard combination that is triggering the event

If true is returned then it stops the callback from firing, if false it fires it.

The default implementation is:

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
