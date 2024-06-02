# Keys in Flutter

Keys are used to identify widgets in the widget tree. It gives them the unique identifier.

## When to use Keys

An example: If we have two colored tiles in an app placed in a row side by side and when we click a button the colors of both the tiles should change. In the implementation of this, we have a list of tiles and we swap their position when button is pressed and when finally call setState() to rebuild the screen. In this case, if the tiles are stateless widgets then the output will be as expected but if the tiles are stateful widgets then the colors will not change. So, here we need to pass the keys and then it will work.

So, we need to use the keys when we are trying to modify the order or number of our stateful widgets in a collection. [1]

### Why does this happen?

This happens because the colors or any of the properties are stored in the stateless widget but in case of a stateful widget the properties are stored in the element tree as a state. So, when we pass a key to our stateful widget, flutter checks the keys and realise that they are different and it then again make new connections from element tree to widget tree. NOTE: In the above example, the elements which are having keys should have a same parent meaning if we wrap them around some widget then flutter will not be able to find the key which it is looking for if the state is changed in the element tree level. So, in this case we need to add the keys to the widget which is wrapped around these tiles in this case. For details go the the reference video. [1]

## Types of Keys

### Local Keys

- ValueKey('ABC DEF'): If the items are simple string we can use Value key. For eg. we have a custom widget and it has a argument which can be a model of anything and that model can have an id which can be used a key
- ObjectKey(Model()): If the items are having model or more than one type of arguments, we can use object key.
- UniqueKey(): We use this usually when we dont have any data which we need to pass like in the example of tiles we use a uniqueKey().
- PageStorageKey(scrollLocation): This key stores the page locations and scroll locations.

### Global Keys

- GlobalKey(): These are used when we want to use a same widget at different places in app and maintain its state everywhere.

NOTE: These methods of using keys are not used as there are more robust solutions with the help of state management tools now.

## References

[1]: [When to use keys](https://youtu.be/kn0EOS-ZiIc)
