#Mousetrap.trigger
=================

```
Mousetrap.trigger('esc');
```

Any keyboard event that has been bound can be triggered by passing in the string you used when you bound it originally. Note that this is not actually triggering a key event in the browser. It is simply firing the event you bound to that key within mousetrap. This method also accepts an optional argument for what type of event to trigger
