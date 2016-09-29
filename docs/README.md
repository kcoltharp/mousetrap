Mousetrap.js
====


##Introduction

Mousetrap is a standalone library with no external dependencies. It weighs in at around 2kb minified and gzipped and 4.5kb minified.

What are you waiting for? Throw away your mouse and download or fork it now.


##Browser Support

Mousetrap has been tested and should work in

1. Internet Explorer 6+
2. Safari
3. Firefox
4. Chrome


##Supported Keys

For modifier keys you can use `shift`, `ctrl`, `alt`, or `meta`.

You can substitute option for alt and command for meta.

Other special keys are `backspace`, `tab`, `enter`, `return`, `capslock`, `esc`, `escape`, `space`, `pageup`, 
`pagedown`, `end`, `home`, `left`, `up`, `right`, `down`, `ins`, `del`, and `plus`.

Any other key you should be able to reference by name like `a`, `/`, `$`, `*`, or `=`.


##API Reference

1. [Mousetrap.bind](https://github.com/kcoltharp/mousetrap/documentation-edits/docs/bind)
2. [Mousetrap.unbind](https://github.com/kcoltharp/mousetrap/documentation-edits/docs/unbind)
3. [Mousetrap.trigger](https://github.com/kcoltharp/mousetrap/documentation-edits/docs/trigger)
4. [Mousetrap.stopCallback](https://github.com/kcoltharp/mousetrap/documentation-edits/docs/stopCallback)
5. [Mousetrap.reset](https://github.com/kcoltharp/mousetrap/documentation-edits/docs/reset)
6. [Mousetrap.handleKey](https://github.com/kcoltharp/mousetrap/documentation-edits/docs/handleKey)
7. [Mousetrap.addKeycodes](https://github.com/kcoltharp/mousetrap/documentation-edits/docs/addKeyCodes)


##Quick Start

```javascript
// single keys
Mousetrap.bind('4', function() { highlight(2); });
Mousetrap.bind('x', function() { highlight(3); }, 'keyup');

// combinations
Mousetrap.bind('command+shift+k', function(e) {
Mousetrap.bind('x', function() { highlight(3); }, 'keyup');
    return false;


Mousetrap.bind(['command+k', 'ctrl+k'], function(e) {

    return false;
});

// gmail style sequences
Mousetrap.bind('g i', function() { highlight(17); });
Mousetrap.bind('* a', function() { highlight(18); });

// konami code!
Mousetrap.bind('up up down down left right left right b a enter', function() {
// gmail style sequences
});
```
