# Widget rendering and trees

This page contains how flutter render the widgets, how to create custom render object and about semantics in Flutter.

## How flutter renders widgets

Everything is a widget in flutter and widgets are immutable (meaning they cannot be changed). And an app has a tree containing the widgets. If widgets are immutable then how UI can be changed? The thing is widgets are instantiated with the help of element. An element instantiate a widget and it also has the location of the widget in the widget tree. It manages the lifecycle of the widget. Then a renderobject layouts, sizes and paints the actual UI. [2]

### Widget trees

Flutter has three trees: Widget tree (Configure), Element tree (Lifecycle) & RenderObject tree (Painting). These all the three trees are responsible for rendering the widgets.

- Widget Tree (Configure): It has all the properties of the widgets which we create and form the widget tree. It calls the particular widget and its element.
- Element Tree (Lifecycle): It maintains the child parent relationships and has a place where the widget actually is present in the UI. It manages the lifecycle of the widgets.
- RenderObject Tree (Painting): Size and paint the actual UI. Layout the childers and gives them constraints.

If we update a widget what happens to the tree? It first checks the new widget with the older one and see if the older one can be reused in the widget tree. If yes it just calls the on update method and then reuses the widget tree how much it can. Then it sees the element tree for any updates, if not required it then calls render object tree to update the new UI with the changes. Here, flutter reuses the element and thus it leads to performance improvements. NOTE: Here, the render object instance ids doesnt changes they update the values inside. Also, if we change the widget altogether then the instance id for the render object changes because it will destroy the element and renderobject for the older one and will create a new one. We can see these live in DevTools. [2]

### Why three trees?

So, the reason mainly lies in the amount of work that would be require if there was only one tree and if we update the UI. In most cases there would be a need to update all the things. But with three trees doing only there specific tasks, we are diving the work load and thus when we update the UI, there are much more reuses. For eg. We have a text widget with text "Hello world!" then we update the text to "Hello universe!" in this case changes will be required in widget tree and the render object tree and not the element tree as the location and other things would be same. So, reusing the widgets become much easier with three trees. [2]

## Building RenderObjects

First when a widget is created it calls createRenderObject function where it does the three things:

1. performLayout: It get the size of the widget. If it has children, then it calls the children's renderobject to give its size and finfally determines size of all the widgets.
2. paint: It calls the paint method on all the widgets and combine size information and other information and make graphic calls.
3. describeSemanticsConfiguration: It then creates the semantic tree which helps in the accessibility.

When we call the setState the updateRenderOBject method is called and it again goes to the above three process to render the object but this time is might not go to all the three steps above. It can get the cached data which can be reused to build the widget. But the default widgets are immutable and if we need some advance widget, we need to create the renderobject. For eg. go to the reference: [3].

### When and why we need to create our own renderobject?

When we want to create a widget which is mutable or when Flutter single pass algorithm couldn't handle then we need to create our own renderobject.

### Different types of render objects widget

RenderObjects types:

1. LeafRenderObjectWidget: If a widget has zero number of children.
2. SingleChildRenderObjectWidget: If a widget has only one child.
3. MultiChildRenderObjectWidget: If a widget has more than one child.

### How to create a render object

We need to create a class for our widget which extends the renderobjectwidget from any of the above three types. This class has overidden createRenderObject and updateRenderObject methods. Then we need to create another class which extends the render object usually it is a RenderBox. Then here we specify all the properties which we need to paint to the wiget. The widgets are immutable classes and they get destroyed and rebuilt when we change their properties but in case of a renderobject they can change their properties without rebuilding itself. See the code in the reference. [4]

## marksNeedslayout, marksNeedPaint, markNeedsSemanticsUpdate

## Semantics

### Semantics Tree

## Flutter Single Pass Algorithm

## Buildcontext

All the stateless and stateful widgets have this called build context it it. Although explicitly no widget knows where it lies in the widget tree. If we go into the implementation of the stateless and stateful widgets we will see they both are extended from Widget class. So, at the end stateful and stateless widgets are also widgets which all other widgets like Text, Cloumn get extended from. A widget class has a function called createElement(). This function creates the widget and it has all the data like parent, children, size, etc for that widget which helps to track where the widget lies in the widget tree. And an element is a build context from its core. So, whenever we use a .of(context) it specifies where the widget belongs to meaning which context it belongs to. [1]

## References

[1]: [Decode Flutter YouTube](<https://www.youtube.com/watch?v=rIaaH87z1-g>)
[2]: [How Flutter renders widgets](<https://youtu.be/996ZgFRENMs>)
[3]: [How to build RenderObjects](<https://youtu.be/cq34RWXegM8>)
[4]: [Code for Custom Render Object](<https://gist.github.com/craiglabenz/c6fc52e3e61f66c51f7a858115bfce51>)
