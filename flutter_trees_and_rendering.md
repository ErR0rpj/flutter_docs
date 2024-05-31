# Widget rendering and trees

## Buildcontext

All the stateless and stateful widgets have this called build context it it. Although explicitly no widget knows where it lies in the widget tree. If we go into the implementation of the stateless and stateful widgets we will see they both are extended from Widget class. So, at the end stateful and stateless widgets are also widgets which all other widgets like Text, Cloumn get extended from. A widget class has a function called createElement(). This function creates the widget and it has all the data like parent, children, size, etc for that widget which helps to track where the widget lies in the widget tree. And an element is a build context from its core. So, whenever we use a .of(context) it specifies where the widget belongs to meaning which context it belongs to. [1](URL <https://www.youtube.com/watch?v=rIaaH87z1-g>)
