# Widget rendering and trees

Based on: [How Flutter renders widgets](<https://youtu.be/996ZgFRENMs>)

## How flutter renders widgets

Everything is a widget in flutter and widgets are immutable (meaning they cannot be changed). And an app has a tree containing the widgets. If widgets are immutable then how UI can be changed? The thing is widgets are instantiated with the help of element. An element instantiate a widget and it also has the location of the widget in the widget tree. It manages the lifecycle of the widget. Then a renderobject layouts, sizes and paints the actual UI.

### Widget trees

Flutter has three trees: Widget tree (Configure), Element tree (Lifecycle) & RenderObject tree (Painting). These all the three trees are responsible for rendering the widgets.

- Widget Tree (Configure): It has all the properties of the widgets which we create and form the widget tree. It calls the particular widget and its element.
- Element Tree (Lifecycle): It maintains the child parent relationships and has a place where the widget actually is present in the UI. It manages the lifecycle of the widgets.
- RenderObject Tree (Painting): Size and paint the actual UI. Layout the childers and gives them constraints.

If we update a widget what happens to the tree? It first checks the new widget with the older one and see if the older one can be reused in the widget tree. If yes it just calls the on update method and then reuses the widget tree how much it can. Then it sees the element tree for any updates, if not required it then calls render object tree to update the new UI with the changes. Here, flutter reuses the element and thus it leads to performance improvements. NOTE: Here, the render object instance ids doesnt changes they update the values inside. Also, if we change the widget altogether then the instance id for the render object changes because it will destroy the element and renderobject for the older one and will create a new one. We can see these live in DevTools.

### Why three trees?

So, the reason mainly lies in the amount of work that would be require if there was only one tree and if we update the UI. In most cases there would be a need to update all the things. But with three trees doing only there specific tasks, we are diving the work load and thus when we update the UI, there are much more reuses. For eg. We have a text widget with text "Hello world!" then we update the text to "Hello universe!" in this case changes will be required in widget tree and the render object tree and not the element tree as the location and other things would be same. So, reusing the widgets become much easier with three trees.

## Buildcontext

All the stateless and stateful widgets have this called build context it it. Although explicitly no widget knows where it lies in the widget tree. If we go into the implementation of the stateless and stateful widgets we will see they both are extended from Widget class. So, at the end stateful and stateless widgets are also widgets which all other widgets like Text, Cloumn get extended from. A widget class has a function called createElement(). This function creates the widget and it has all the data like parent, children, size, etc for that widget which helps to track where the widget lies in the widget tree. And an element is a build context from its core. So, whenever we use a .of(context) it specifies where the widget belongs to meaning which context it belongs to. [1](URL <https://www.youtube.com/watch?v=rIaaH87z1-g>)
