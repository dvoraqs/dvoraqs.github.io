---
layout: post
title:  "Visualizing Dependencies"
categories: java neo4j dependency intellij
---
Let me tell you the story of my Github repository (intellij-dependency-grapher)[https://github.com/dvoraqs/intellij-dependencies-grapher]. It's not my best work and it doesn't even do it's job all that well, but I'm still proud of it because it is a symbol of many things I value. 

At the project I was on, we had the problem of extracting a large chunk of code from a larger codebase. We had a hard time digesting what was there because of the scale. I wish I had numbers to show you, but this codebase was several gigabytes large. 

We looked at Gradle files for artifact and project-level dependency information and at Java files for namespace and class-level dependency information. That was a lot of legwork to put some of those pieces together. Noticing that, there were some small initiatives to make this process easier. We learned about the `gradle dependencies` command and got a file with that information about our project as the source that we could use with (D3.js)[d3js.org]. I played around a bit to get it working, but I wanted to see more detail than what this provided.

Before long, we found that Intellij could do some of the analysis for us. Ignoring some of the dependability of the results, we also found that they could be exported in an XML format. This was a great source of information with all of its detail, but it was still too much and I wanted to see if I could use it with *D3.js*.

I tried an experiment to convert the XML export that I had to a JSON file that could be consumed by *D3.js*. It was a naive set of regex replacements that had two goals: to change the format of the data and to filter the data for relevance. I did this in a local Git repo and made step-wise commits so that I could go back if I found that I had accidently ruined what was there, but they also gave me a record of the effect of each step.

It worked okay -- I showed my coworkers and we were not completely happy with what we was seeing in the graph and how the data format would not work between visualizations. It was also hard to justify that the data was correct because it was a process to explain what I had done and that I was doing it correctly. They told me about a graphing database called (Neo4j)[https://neo4j.com/] and I became interested in using it. I debated with myself which tool might be more valuable to our case, but without knowing much about either one, I felt like *Neo4j* would have more emergent functionality that we could use with the result of my work, so I focused on trying to use our data with it.

I found a tool that I could use to create a dependency graph for us in *Neo4j* if we provided the data in a specific format. I did a bit of extra work in my repo to convert my JSON data and loaded it into *Neo4j* using this tool as a proof of concept. It was fun to play with, but I felt like I had made mistakes when filtering the data and I was not seeing what I had wanted. Rather than go through the process again, I thought it would be better to automate it.

I used the repo that I had as a model for what should happen, and I recorded each step in a script that I could run on the original export from Intellij. This made it much easier to explain what was happening, see errors, make corrections, and respond to a codebase that was still changing. The thing that was up for debate for me at that point was which information in the data we should keep or throw away.

I showed this again to my coworkers. They gave some feedback and started asking for things.

I cleaned it up a little bit and showed it to the team. I also showed it to my coach who let me know about better ways I could do the same thing. There are a few things I still want to do with it and I have a plan for how they could get done, but I may never get around to it. I am off of the project now because I was needed more in other places, so that makes it less of a priority for now.

It showed me the value of 
- practice in gaining confidence
- action over deliberation
- getting feedback early
- learning as you go
- iterative improvement