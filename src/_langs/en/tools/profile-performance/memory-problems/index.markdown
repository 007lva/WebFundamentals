---
rss: false
layout: section
title: "Fix Memory Problems"
seotitle: "Fix Memory Problems Using Chrome DevTools Memory Profiling"
description: "Memory loss occurs when a program repeatedly fails to return memory it has obtained for temporary use. Watch out for memory leaks, bloat, and forced garbage collection."
introduction: "Memory loss occurs when a program repeatedly fails to return memory it has obtained for temporary use. Watch out for memory leaks, bloat, and forced garbage collection."
article:
  written_on: 2015-04-14
  updated_on: 2015-05-19
  order: 4
authors:
  - megginkearney
priority: 0
collection: profile-performance
panel: profiles
id: memory-problems
---

{% wrap content %}

New to memory management? Learn the [terminology and fundamentals](https://web-central.appspot.com/web/tools/profile-performance/memory-problems/memory-101) first. Once you are familiar with those, check for these three key memory problems:

Does page use too much memory?

Track the number of live DOM nodes, documents, and JS event listeners in the inspected render process using the Chrome DevTools Memory view. As a rule of thumb, avoid holding references to DOM elements you no longer need to use, unbind unneeded event listeners, and take care when storing large chunks of data you aren't going to use.

Does page have memory leaks?

Narrow down leaks by looking at JS object allocation in real-time using the Chrome DevTools object allocation tracker. You can also use the heap profiler to take JS heap snapshots, analyze memory graphs, and compare snapshots to discover what objects are not being cleaned up by garbage collection.

Determine garbage collection frequency

If you are GCing frequently, you may be allocating too frequently. Identify pauses of interest using the Chrome DevTools Timeline memory view.

![Memory profiling](imgs/memory-profiling.png)

{% endwrap %}
