# What happens when we click ```www.google.com``` in our browser?

So basically what I want to find out is what happens behind the scenes when we type ```www.google.com``` in a browser and how information eventually gets displayed on the screen.

Right below is what I'll be covering...

## Table of Contents

1. [Introduction](#introduction)
2. [Browser and DNS](#browser-and-dns)

## Introduction

So first of all, the text we enter into the browser, say ```www.google.com``` is what we call a URL, which is short for **Uniform Resource Locator**.

A **URL** is the reference that the browser uses to find the information/resource/service that we are looking for on the internet.

So in the process we are going to dissect, there are some basic key concepts we should be familiar with...

Namely:

- Browser
    > This is an application for accessing websites.
- URL
    > This is a **Uniform Resource Locator**, prety much what it means is in its words. It helps the browser locate the resource, it is a reference to a resource. 

- DNS
    > This stands for **Domain Name System**, which converts and stores the references of URLs to their sibling, or rather, related IP addresses.
    <br>
    > To avoid any confusion, and IP address looks something like this ```172.0.0.1``` (this is for local host however).

- TCP/IP
    > Stands for **Transmission Control Protocol/Internet Protocol**, which is the framework that enables data transmission across interconnected networks(in our case the internet).
    > It contains several layers (Application, Transport, Internet and network access layers) all of which have various purposes, but in summary it breaks the data into segments, adds IP addresses and determines the route, then at the end of it, it converts the segments into a form transferable over the medium.
    >> Seems like a lot to handle, but we'll see what it means.

- HTTP
    > Stands for **Hyper Text Markup Language** which is basically the foundation of communication on the **World Wide Web**.

So as we already know what a browser is, let's dive right into what happens in it.

We will be looking into the ```google.com``` URL.

## Entering the URL into the browser

So first we type the URL and press enter on our browser search bar.
Ever wondered what happens when you do that?? I've also been wondering what happens...

So first the browser identifies the parts of the URL.

> If you've ever noticed, the browser automatically adds the HTTP protocol to the beginning of a URL.

So....the parts of the URL:

```https://www.google.com```

```https://```
This is the scheme, that tells the browser to make a connection to the server using the protocol **TLS**(Transport Level Security)

Next is ```www.google.com```, this is the domain name of the site, it points to a specific server's IP address.
Just like the way I have a friend with the name *Michael Onyango Johnson Olsen*, who I simply call *Mike Ojo*, which is simpler for me and other people to comprehend, is just the same way the domain works.

I can't even imagine trying to cramming **"www.google.com's"** IP address **https://142.250.190.78**

That's the reason why domains, make accessing this specific IP address more understandable.

## Browser looking up the IP address for the domain

So now we have the domain ```www.google.com```, what next?

**DNS lookup** is what occurs at this point.

As we know what a DNS is as seen in the [introduction](#introduction), we now look for th IP adress of the server hosting the website using the domain we typed in.

> just a reminder as we go forward in this section...the IP address for google.com is ```142.250.190.78```.

THe DNS lookup, is a complex set of steps, but we will cover the necessary steps. But first we need to know several terms:

- **DNS recursor:** This is a server designed to receive queries from client machines through applications such as web browsers.
*Just like a librarian*
- **Root Nameserver:** Is a collection of references to more specific locations. *Kinda like a translator for a browser; if you key in gibberish it tries to see what makes sense from it.*
- **Authoritative Nameserver:** is the final name server, which is the last stop in the name server query. If the nameserver has access to the requested record, it will return the IP address to the requested record.
- **Recursive DNS resolver:** this is a computer that takes time tracking down the client request until it finds the DNS record, by making a series of requests; it may use **caching**(a data persistence process, making requests faster by serving the requested record earlier in the lookup)
- **Authoritative DNS server:** this is a server that actually holds, and is responsible for the DNS resource records. It typically responds with the queried resource record. *It satisfies queries with its own data*

> Recursive DNS resolvers include: **Google DNS** and **OpenDNS**.
> An example of a nameservers is **Cloudflare**.

Okay, now that those are roughly covered, let's dive into the steps in a DNS lookup.

- user types in the URL '**google.com**'
- The resolver queries a DNS root nameserver(s).
- The root server responds to the resolver with the address of a 'top level domain' DNS server.
- the server makes a request to the .com 'top level domain' (TLD)
- the TLD server responds with the IP address of the domain's nameserver, **google.com**
- Then finally, the recursive resolver sends a query to the domain's nameserver.
- The IP address for **google.com** is then returned to the resolver from the nameserver.
- The DNS resolver responds to the web browser with the IP address of the domain requested.

So that's a tonne of information, simply put:

- We search: 'www.google.com'
- the browser asks the DNS "where in the world am I getting the information to show the user from?!"
- then the DNS goes to look for it.
- when it finds it, now in a language only computers can understand, it returns it to the browser as **http://142.250.190.78**
- now this gives us the HTTP request the browser can run and finally display the webpage.

## Browser creates a  TCP connection with server

This is where the packets from a client browser get routed through the router through an internet exchange to witch ISPs or networks to find the server with the IP address to connect to.

Now there's another big word, **CDN**(Content Delivery Network). This is a network of caching servers that improve the performance of a site/app by bringing content closer to the user.

When the browser find's the server on the internet, a TLS handshake is made to secure the communication.
We'll need to be keen on **TCP** and **TLS** topics...

So, once the browser has connected to the serve, we now send the HTTP request to get the resource

## Browser Makes HTTP request to server

So now the browser follows the rules to make a HTTP request to the server, containing a request line, headers, and a body.

- request line contains the following:

  - request method (GET, POST, PUT, PATCH, DELETE...)
  - The path
  - The HTTP version

- The headers contain metadata
- The body, usually empty for a get request like ours 'www.google.com' coz we want to view the data. But for POST, PUT or PATCH methods, it would contain data from the client/user to create/update.

## Server processes the request

The browser recieves the HTTP request, and now want's to grant the user the browser client the user the data they requested for...

So the server gives a response that contains the following:

- **Status line:**  Which contains the status of the request, if it is okay or not.
- **Response Headers:** which tell the browser how to handle the data.
- **The resource that was asked for:** this appears as HTML, CSS JS, or image files...or some other form of data.

## Browser renders the content

Now we're at the finalé.

So, the first get request returns HTML, which structures the page, within it, it is linked to other JS, or CSS documents. Usually to add more properties to the web page.

## REFERENCES

1. [Superuser](https://superuser.com/questions/31468/what-exactly-happens-when-you-browse-a-website-in-your-browser)
2. [Geek for Geeks Article](https://www.geeksforgeeks.org/what-happens-when-we-type-a-url/)
2. [AWS Article](https://aws.amazon.com/blogs/mobile/what-happens-when-you-type-a-url-into-your-browser/)