# Sessions and Cookies

## Overview

In this lesson, we'll introduce you to sessions and cookies and how they work together to store information about a particular user's interactions with a website at a given point in time.

## Objectives

1. Define sessions and explain how they store data describing a client's interactions with a website at a given point in time
2. Define cookies and what's contained in them
3. Distinguish between session cookies and persistent cookies

## How do websites recognize individual users?

If you don't explicitly log out every time you leave Facebook's site, you'll find that, upon returning, you're still logged in and will be taken directly to your timeline. If you check your Gmail account, you might see advertisements relating to search terms that you typed into Google earlier that day. When you shop on Amazon, your shopping cart tracks all of the items you place into it until you're ready to checkout. How is this possible? Is your computer spying on you all the time? Well, sort of.

Before we can understand what is so amazing about the kind of persistence and recognition we've come to expect from our web applications, we need to understand something about how the web works. 

> HTTP is a stateless protocol, treating each request as an independent transaction that is unable to use information from any previous requests. This means there is no way within the hypertext transfer protocol to remember a user’s identity from page to page...

What? Then how does Facebook remember me?

> instead, web applications requiring user login must use a session, which is a semi-permanent connection between two computers (such as a client computer running a web browser and a server running Rails).

>–– Michael Hartl, *The Ruby on Rails Tutorial*

Since HTTP is stateless, we must rely on the individual actors involved in an HTTP exchange –– the user's browser and the website's server(s) –– to persist any sort of simple state. On each HTTP request, the server sends information to the browser. Cookies were invented as a means to store that data. A **cookie** is a hash that gets stored in the browser and sent back to the server along with every subsequent request.

There's also an important server-side use case for temporarily persisting data while a user browses the server's website. Enter sessions. Similarly to cookies, a **session** is an object, like a hash, that stores data describing a client's interactions with a website at a given point in time. The session hash lives on the server. Your application can access it via any of your controllers at any point in time.

So, how does a web application know who is interacting with it? By using both **cookies and session data**.

When you send a request to [facebook.com](https://www.facebook.com/), the application on the server will generate and store some data about you. The application will keep that data in a session hash, and it will also place it into a small text snippet called a cookie. The cookie is sent back to you, the client, and is stored in your browser. When a website sets cookies, they persist between pages while you continue to browse the web. Upon any subsequent visits to the setting website, the cookies are sent back to the site's server. When that happens, the client-side cookie data will be compared to the server-side session data to help the application determine what steps to take and what information to send back to you.

## How do cookies work?

Here's the general flow:

1. You visit a webpage, such as [facebook.com](https://www.facebook.com/).
2. Facebook's web application receives the request and creates a cookie with some information about you as a user.
3. Facebook sends that cookie *back to the browser*, where it is stored. Cookies will last until they expire or are  deleted.
4. Every subsequent request you make to [facebook.com](https://www.facebook.com/) sends the cookies *back to the server*, where Facebook can access them, retrieve information, and alter the cookies.

### What is contained in a cookie?

A cookie will usually contain a URL to the generating website, the date on which it was created (and the date on which it is set to expire, if applicable), and other pertinent information that the web application has requested to persist (such as remembered login information, user preferences, etc).

### Session Cookies vs. Persistent Cookies

There are two primary kinds of cookies: session and persistent.

**Session cookies** allow a website to keep track of your movement from page to page for that specific session (from the time you log in to the time you log out or close the browser). Session cookies simply allow you to navigate through a site without repeatedly having to authenticate yourself on every new page you visit within the web application domain. Session cookies expire every time you log out or navigate away from the website.

Let's walk through an example of what would happen without a session cookie. If you added an item to your Amazon shopping cart on one page and then navigated to another to checkout, the newly-loaded page would have no recollection of your prior activity. Your shopping cart would remain empty despite your best efforts to fill it with items. There would be no persistent record of your activities for that session.

**Persistent cookies** allow a website to remember your user information and preferences for *future* visits. A persistent cookie is stored on your computer, while a session cookie is temporarily stored in your web browser. Persistent cookies allow for faster page loading, automatic login and user authentication, and access to other potential web application features. Much of the data that these features require will be hanging out already in a persistent cookie, stored on your computer. This means you can skip the process of sending a web request to a site and waiting to receive data back from the server in order to login, for example. Persistent cookies are usually created on the first visit to a page after you have created an account on the site, and they typically persist unless either the web application has a protocol in place for cookie expiration or the user clears their browser's cache.

What would happen if we didn't have persistent cookies? We would have to go to Facebook's login page and type in our email address and password every single time we wanted to use the site. Our user settings and preferences would not be persisted, and the quality of the user's experience would go way down.

### Cookies and Sessions: Teamwork!

You can think of cookies as the client-side counterpart to sessions. They store information locally and are visible only to the server that created them. Client browsers send cookies to remote servers along with each web request. The web application on the server reads the cookie, associates it with an existing session (if such a session exists), and decides how to respond. For example, if there is no cookie received, the application might show the login page. If a cookie is received that doesn't match the data stored in the server-side session hash, the app might show the login page with the username filled out –– having retrieved that data from the cookie –– but request that the user reauthenticate. If a cookie is received that does match the data in the server-side session hash, the app would respond with that user's data.

Later on, we'll learn how to use cookie and session objects to build apps that allow users to log in and log out!

### Resources
- [Cookies.org](http://www.allaboutcookies.org/)
- [HTTP Cookie] (https://en.wikipedia.org/wiki/HTTP_cookie#Session_cookie)

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/sinatra-cookies-readme'>Sessions and Cookies</a> on Learn.co and start learning to code for free.</p>

<p class='util--hide'>View <a href='https://learn.co/lessons/sinatra-cookies-readme'>Sessions and Cookies</a> on Learn.co and start learning to code for free.</p>
