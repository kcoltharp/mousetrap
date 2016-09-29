#Mousetrap.bind
=================

The bind method is the main call you will be making. This will bind a specified keyboard command to a callback method.

###Single key###

```
Mousetrap.bind('/', _focusSearch);
```
There is a third argument you can use to specify the type of event to listen for. It can be keypress, keydown or keyup.

It is recommended that you leave this argument out if you are unsure. Mousetrap will look at the keys you are binding and determine whether it should default to keypress or keydown.

###Combination of keys###
```
Mousetrap.bind('ctrl+s', function(e) {
    _saveDraft();
});
```
If you want to bind multiple key commands to the same callback you can pass in an array for the first argument:
```
Mousetrap.bind(['ctrl+s', 'command+s'], function(e) {
    _saveDraft();
});
```
Mousetrap 1.4 introduced a generic mod helper which lets you set cross platform shortcuts.
```
Mousetrap.bind('mod+s', _saveDraft);
```
On Mac this ends up mapping to command+s whereas on Windows and Linux it maps to ctrl+s.

This differs from the array example above because there both ctrl+s and command+s will trigger save on Mac whereas with the mod helper only command+s will.

###Sequence of keys###
```
Mousetrap.bind('* a', _selectAll, 'keydown');
```
This feature was inspired by Gmail. Any keys separated by a space will be considered a sequence. If you type each key in order the final one in the sequence will trigger the callback. If you type a key not in the sequence or wait too long the sequence will reset.

You can also make a sequence that includes key combinations within it.
```
Mousetrap.bind('g o command+enter', function() { /* do something */ });
```
Any key events that would normally fire for keys within a sequence will not fire if they are pressed within the context of that sequence.

For example if you have a keydown listener for the o key and you press o as part of the sequence above, the event for o on its own will not fire. As soon as the sequence is broken it will fire again.

It is important to note that Mousetrap can get very confused if you have a single key handler that uses the same key that a sequence starts with. This is because it can't tell if you are starting the sequence or if you are pressing that key on its own.

###Shift key###
```
Mousetrap.bind(['ctrl+s', 'command+s'], function(e) {
    _saveDraft();
});
```
Keys that require shift are handled magically for you. They should just work. With keypress events they will try to match the character and for keyup and keydown there is a mapping to allow them to work.

Note that keypress is the most reliable for non US keyboards

###Text fields###

By default all keyboard events will not fire if you are inside of a textarea, input, or select to prevent undesirable things from happening.

If you want them to fire you can add the class mousetrap to the element.
```
Mousetrap.bind(['ctrl+s', 'command+s'], function(e) {
    _saveDraft();
});
```
You can also customize this functionality by overwriting Mousetrap.stopCallback. See below

###Overwriting a specific event###

If you bind the same key event later on in your script it should overwrite the original callback you had specified.

###Checking keyboard combination from callback###

As of version 1.2 the callback will be passed a second argument with a string of the keyboard combination that triggered the event.
```
Mousetrap.bind('ctrl+shift+up', function(e, combo) {
    console.log(combo); // logs 'ctrl+shift+up'
});
```
This example is a bit contrived because you obviously know the shortcut. If, however, you want to do something like use the same callback function for a bunch of combinations and then check which one triggered the event this allows you to do that

###Stopping the default behavior###

This is not usually a good practice, but sometimes you may want to overwrite the default behavior of a keyboard combination in the browser.

For example let's say you want to focus a form input without typing that key into it or you have a text input that you want to save when the user presses ctrl+s. You have a couple ways you can achieve this.

You can explicitly prevent the default behavior:
```
Mousetrap.bind(['ctrl+s', 'meta+s'], function(e) {
    if (e.preventDefault) {
        e.preventDefault();
    } else {
        // internet explorer
        e.returnValue = false;
    }
    _saveDraft();
});
```
You can see here that the callback function gets passed the original key event that triggered it.

As a convenience you can also return false in your callback:
```
Mousetrap.bind(['ctrl+s', 'meta+s'], function(e) {
    _saveDraft();
    return false;
});
```
Returning false here works the same way as jQuery's return false. It prevents the default action and stops the event from bubbling up.
