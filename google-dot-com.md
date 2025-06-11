# What happens when we click ```www.google.com``` in our browser?

So basically what I want to find out is what happens behind the scenes when we type ```www.google.com``` in a browser and how information eventually gets displayed on the screen.

Right below is what I'll be covering...

## Table of Contents

1. [Introduction](#introduction)

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

## REFERENCES

1. [Superuser](https://superuser.com/questions/31468/what-exactly-happens-when-you-browse-a-website-in-your-browser)
2. [Geek for Geeks Article](https://www.geeksforgeeks.org/what-happens-when-we-type-a-url/)
