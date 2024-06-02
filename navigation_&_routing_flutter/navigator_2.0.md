# Navigator 2.0 [In-Progress]

This notes explains the full navigator 2.0 usage and architecture of navigator 2.0 which introduced router.
Before navigator 2.0 the routes were pushed as stack on one another with either named routes or anonymous routes.

## Anonymous routes

When we use navigator.push() in our code it pushes the new route on the existing route as a anonymous route. This is because it is not named and it does not have any url or endpoint.
![nav_stack](nav_stack.png)

## Named Routes

We can use named routes but the names are predefined and we cannot pass arguments in the route link. We can although arguments to it. For eg, we cannot parse something like: /details/:id. With onGenerateRoute we can define all our routes at the same place and we can handle any arguments that might come while routing in this place.

## References

[1]: [Navigator 2.0](<https://medium.com/flutter/learning-flutters-new-navigation-and-routing-system-7c9068155ade>)
