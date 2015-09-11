# Cookies and Sessions

## Objectives

1. Define cookies. 
2. Define sessions. 
3. Learn the difference between sessions and cookies.

## How do your websites recognize you?

When you visit Facebook, chances are, you'll find you're logged in and be taken to your timeline directly. If you check your gmail account, you might see advertisements relating to search terms you typed into Google earlier that day. When you shop on Amazon, your shopping cart stays full while you continue to shop all the way up until you checkout. How is this possible? Is your computer spying on you all the time? The answer is, sort of. 

Before we can understand what is so amazing about the kind of persistence and recognition we've come to expect from our web applications, we need to understand something about how the web works. 

> HTTP is a stateless protocol, treating each request as an independent transaction that is unable to use information from any previous requests. This means there is no way within the hypertext transfer protocol to remember a user’s identity from page to page; instead, web applications requiring user login must use a session, which is a semi-permanent connection between two computers (such as a client computer running a web browser and a server running Rails).

>–– Michael Hartl, *The Ruby on Rails Tutorial*

A **session** is simply an object, like a hash, that stores data describing a client's interaction with a website at a given point in time. The session hash lives on the server. Your application can access it in any of your controllers at any point in time. 

How does a session know who is interacting with a website? Through **cookies**. Cookies are are snippets of text placed on the user’s browser. Cookies persist from one page to the next when you are browsing the web. So, they can store information (such as a user id) that can then be used by the application to retrieve the logged-in user from the database, among other things. 

## How do Cookies Work?

Here's the general flow: 

1. You visit a webpage, www.facebook.com 
2. The web application that is Facebook receives that request and creates a cookie with some information about you as a user. 
3. Facebook sends that cookie *back to the browser* where it is stored temporarily. The cookie will last until you log out of Facebook, close your browser or clear your cache. 
4. Every subsequent request you, the client, sends to www.facebook.com sends the cookies *back to the server* where your application can access it, get information out of and alter it.

### What is contained in a cookie?

Cookies will usually have a URL to the website that generated it, the date on which it was created (and the date on which it expired, if applicable), and other pertinent information that has been requested by the web application (such as remembered login information, user preferences, etc).

### Session Cookies vs. Persistent Cookies

There are two primary kinds of cookies: session and persistent.

**Session cookies** allow a website to keep track of your movement from page to page for that specific session (from the time you log in to the time you log out/close the browser). Session cookies simply allow you to navigate through a site without repeatedly having to authenticate yourself on every new page you visit within the web application domain. Session cookies expire every time out log out or navigate away from the website.

Let's walk through an example of what would happen without a session cookie. If you were on Amazon, added an item to your shopping cart, and then selected the "Checkout" option, the new page would have no recollection of your prior activity. Your shopping cart would always be empty, even though you explicitly added an item earlier. There would be no record of your activities for that session.

**Persistent cookies** allow a website to remember your user information and preferences for *future* visits. A persistent cookie is stored on your computer, while a session cookie is temporarily stored in your web browser. Persistent cookies allow for faster page loading, automatic login and user authentication, and access to other potential web application features because much of the data that these features require will be hanging out in a persistent cookie, stored on your computer. So, you don't have to go through the cycle of sending a web request to a side and waiting to receive data back from the server in order to for your browser to have your log in info, for example. Persistent cookies are usually created on the first visit to the page after you have created an account, and typically don't expire unless the web application has a protocol in place for cookie expiration, or the user clears their browser's cookie cache.

What would happen if we didn't have persistent cookies? We would have to go to Facebook's login page and type in our email address and passwords every single time we wanted to visit Facebook. Our user settings and preferences would not be remembered, and the quality of the user's experience would go way down.

## Coming Up...

So far, we've defined a **session** as a hash that lives on the server side of our application and stores information about a particular user who is interacting with our website at a given point in time. The session object will get information from and interact with cookies. Later on, we'll learn how to use the session object to build apps that allow users to log in and log out. 


### Resources
- [Cookies.org](http://www.allaboutcookies.org/)
- [HTTP Cookie] (https://en.wikipedia.org/wiki/HTTP_cookie#Session_cookie)