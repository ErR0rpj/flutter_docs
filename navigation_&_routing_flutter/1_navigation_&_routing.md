# Navigation and Routing in Flutter

For basic navigations in flutter we use Navigator class. For advance deep linking, flutter web and going to pages from any external sources we need routing in flutter, usually done with router. [1]

## Navigator

Navigator pushes the new screen on the top of the older one and takes care of the animation as per the target platform. For more details on the navigator head to navigator_in_detail.md file. [1]

### Named Navigator

Named routes are same as the normal navigator but it can be redirected to a page with the help of a name which can help in deep linking realted navigations. But, this deep linking is not viable for flutter web. Deep down it works same as the navigator.

It is not recommended to use named routes because of below reasons:

- It cannot be customized for routing.
- It does not support flutter web realted navigations.
- It pushes the new navigator on the screen regardless of where the use currently is on the app. [1]

## Router

Router such as Go Router can be used in an app with multiple navigations and deep links and can be used in web apps where we want to have urls for different pages. This is the best approach present in flutter. For more information on this go to router.md file. [1]

### Using router and navigator together

Both are made to be working together. With router when we navigate to a screen it is created with Page and it can be backed on the web, meaning it has a different URL and it can be deeplinked. On the other hand, if we use navigator to navigate to the screen we usually use Push and pop methods which adds the new screen with a pageless route and it cannot be deep linked. [1]

## Reference

[1]: [Flutter Navigation](<https://docs.flutter.dev/ui/navigation>)
