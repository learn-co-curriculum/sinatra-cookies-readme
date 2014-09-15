# Cookies in Sinatra

### What exactly are cookies?

Cookies can be a confusing concept to grasp at first. They are simply tiny text files with a unique ID tag, and are stored on your computer's browser directory or application data subfolders. An identical cookie/text file is created in the company's database. A cookie keeps track of your movements within a web application (or website), and helps that web application remember pertinent data about you. For example, it helps them where you have left off, your registered login information, preferences, the last time you signed in, and so on.

### What is contained in a cookie?

Cookies will usually have a URL to the website that generated it, the date on which it was created (and the date on which it expired, if applicable), and other pertinent information that has been requested by the web application (such as remembered login information, user preferences, etc).

### Why are cookies important?

Initially, cookies were used primarily by web applications to "remember" a user's movement through a website, as well as that user's preferences and other data that the web application wanted to keep concurrent with each time the user visited the website.

However, websites have increasingly become sophisticated over the years in their use of cookies. A good example of this increasing sophistication is the marketing industry. As commerce has transitioned from brick-and-mortar stores to e-commerce, marketing entities have started to use cookies in order to track a user's surfing habits. One reason for this is to develop an algorithm that will convince a user to buy a product based on that user's surfing history.

### What kind of cookies are there?

There are two primary kinds of cookies: session and persistent.

Session cookies allow the website to keep track of your movement from page to page for that specific session (from the time you log in to the time you log out/close the browser). Session cookies simply allow you to navigate through a site without repeatedly having to authenticate yourself on every new page you visit within the web application domain. Session cookies expire every time out log out or navigate away from the website.

Let's walk through an example of what would happen without a session cookie. If you were on Amazon, added an item to your shopping cart, and then selected the `Checkout` option, the new page would have no recollection of your prior activity. Your shopping cart would always be empty, even though you explicitly added an item earlier. There would be no record of your activities for that session.

Persistent cookies allow the website to remember your user information and preferences for future visits. This allows for faster page loading, automatic login and user authentication, and access to other potential web application features. Persistent cookies are usually created on the first visit to the page after you have created an account, and typically don't expire unless the web application has a protocol in place for cookie expiration, or the user clears their browser's cookie cache.

What would happen if we didn't have persistent cookies? We would have to go to Facebook's login page and type in our email address and passwords every single time. Our user settings and preferences would not be remembered, and would potentially contribute to a more negative user experience.

### Resources
- [Cookies.org](http://www.allaboutcookies.org/)
