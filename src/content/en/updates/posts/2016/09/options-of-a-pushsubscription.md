---
layout: updates/post
title: "Options of a PushSubscription"
description: "You can now access the options used when subscribing a user to
push."
published_on: 2016-09-08
updated_on: 2016-09-06
authors:
  - mattgaunt
tags:
  - push
featured_image: /web/updates/images/2015/10/web-animations-resources.png
---

When a pushsubscriptionchange event occurs, it's an opportunity for a developer
to re-subscribe the user for push. One of the pain points of this is that to
re-subscribe a user, the developer has to keep the applicationServerKey (and any
other subscribe() options) in sync between the web page's JavaScript and their
service worker.

In Chrome version 54+ you can now access the options via the options parameter
in a subscription object, known as
[PushSubscriptionOptions](https://www.w3.org/TR/push-api/#pushsubscriptionoptions-dictionary).

The following snippet of code can be copy and pasted into
[simple-push-demo](https://gauntface.github.io/simple-push-demo/) to see what
the options look like. The code simply gets the current subscription and prints
out subscription.options.

    navigator.serviceWorker.ready.then(registration => {  
      return registration.pushManager.getSubscription();  
    })  
    .then(subscription => {  
      if (!subscription) {  
        console.log('No subscription 😞');  
        return;  
      }

      console.log('Here are the options 🎉');  
      console.log(subscription.options);  
    });

With this small piece of information you can re-subscribe a user in the
[pushsubscriptionchange](https://www.w3.org/TR/push-api/#the-pushsubscriptionchange-event)
event like so:

    self.addEventListener('pushsubscriptionchange', e => {  
      e.waitUntil(registration.pushManager.subscribe(e.oldSubscription.options)  
        .then(subscription => {  
          // TODO: Send new subscription to application server  
        }));  
    });

It's a small change, but will be super useful in the future.
