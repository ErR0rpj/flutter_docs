# Go Router

## Difference between GoRouter.go(), GoRouter.push() and Navigator.push()

- GoRouter.go(): Good for web. Not good for mobile.
  - Replaces the current page with the new page.
  - Doesnt add back button if the URL is not a subdomain of the current URL. Adds if URL is subdomain of current URL.
  - Pressing back in web takes to previous screen
  - Pressing back on mobile exits the app
  - Shows corrent URL in web.

- GoRouter.push(): Good for mobile. Ok for web
  - Puts a new page in stack over the previous page
  - Back button is added by default.
  - Pressing back or back button in browser takes back to previous page
  - Pressing back in mobile takes back to previous page
  - Doesnt show URL in web. To show URL: <https://stackoverflow.com/questions/76730901/flutter-go-router-push-vs-go-and-web-url-changes>

- Navigator.push(): Good for mobile. Not good for web
  - Puts a new page in stack over the previous page
  - No back button added by default.
  - Pressing back button takes back to previous screen but pressing back in browser take to previous URL
  - Pressing back in mobile takes back to previous page
  - Doesnt show URL in web.
