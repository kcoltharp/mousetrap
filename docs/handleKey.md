#Mousetrap.handleKey


Mousetrap.handleKey is a method that is called every time a key is pressed. If you do not know what you are doing it is really not a good idea to override this function, but it allows you to do custom handling that wouldn't be possible with mousetrap natively.

It gets passed three arguments:

* character - the actual character that was pressed
* modifiers - an array of modifiers that were held down when the key was pressed
* e - key event that triggered this callback
