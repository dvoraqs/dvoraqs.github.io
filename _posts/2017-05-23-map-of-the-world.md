---
layout: post
title:  "Map of the World"
date:   2017-05-23 22:45:00 -0600
categories: java neo4j dependency intellij
---

Let me tell you the story of my Github repository [**intellij-dependency-grapher**](https://github.com/dvoraqs/intellij-dependencies-grapher). It's not my best work and it doesn't even do it's job all that well, but I'm still proud of it because it is a symbol of many things I value. 

# The Problem

At the project I was on, our team had the problem of extracting a large chunk of code from a larger codebase -- we called this the "old world". There were lots of dependencies to untangle and we had a hard time digesting what was there because of the scale. I wish I had numbers to show, but this codebase was several gigabytes large. There was a lot of legwork to put some of those pieces together and there was not a lot of time for wasted effort. I saw an opportunity here to try to represent this codebase visually in order to see lots of information in a quickly digestible way.

# The Struggle

After work, I used some of my spare time to see if I could help solve this problem. My interest and time sensitivity fueled my efforts. I purposefully neglected best practice a bit because I was more interested in making something that could be useful and would otherwise be slowed down.

First, I tried to see if I could represent a similar codebase in [**D3.js**](d3js.org) using sources that we had available - calls to `gradle dependencies`, *[**Intellij**](https://www.jetbrains.com/idea/) dependency analysis* and *manual inspection*. I used regex to transform the data and plugged it into a few premade graphs. As I did the transformations, I committed each step so that I could try to recreate them later. There was limited success because of the effort that it seemed to take to try out different graphs and transform for each one or create our own graph display. 

I stopped working on *D3.js* sbecause I was introduced to [**Neo4j**](https://neo4j.com/), a graphing database, which captured my interest from there. It seemed that once we could get the data loaded, there were lots of possiblities in terms of making queries and playing with the graphs. Luckily I found a tool ([forked here](https://github.com/dvoraqs/dependency-graph)) to load dependency data into *Neo4j* from data in a specific format. 

I shifted my effort into building a pipeline between the *Intellij dependency analysis XML export* and that format. Working in shell, I created some scripts to automate the transformation process that I was doing manually earlier. Honestly, this was the part I had the most fun with.

# The Reward

When I had shown my progress to coworkers earlier, it was difficult to explain what I had done manually and hard to trust that it was correct. With these scripts, I could show the process in a concrete way and even change it if we saw errors or better ways to do it. Using their feedback, I made improvements and have more to make. I'm hoping to get to those at some point, but for now, they will go into my backlog and be prioritized against my other tasks.

For myself, working on this side project gave me more confidence at work because it gave me practice making decisions and using some of the same skills. I did *something* here and that is more than I can say for most of the problems I've encountered in the past. It's something that I want to do again if I see another good opportunity.