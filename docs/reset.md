#Mousetrap.reset


```
Mousetrap.bind(['ctrl+s', 'meta+s'], function(e) {
    _saveDraft();
    return false;
});
```

The reset method will remove anything you have bound to mousetrap. This can be useful if you want to change contexts in your application without refreshing the page in your browser. You can ajax in a new page, call reset, and then bind the key events needed for that page.

Internally mousetrap keeps an associative array of all the events to listen for so reset does not actually remove or add event listeners on the document. It just sets the array to be empty.
