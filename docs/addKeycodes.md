#Mousetrap.addKeycodes


This method was added in version 1.6.0. It lets you add custom keycodes to the internal map in Mousetrap without needing to edit the library itself.

It accepts a single argument. You should pass in an object containing key codes that map to key names.

For example, if you wanted to add the numlock key you would do this:

```
Mousetrap.addKeycodes({
    144: 'numlock'
});
```
