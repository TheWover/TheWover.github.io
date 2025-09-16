---
layout: post
title: Creating Verbweaver
---

*TLDR: Verbweaver is a nonlinear writing and design suite built for your brain with the ability to procedurally generate linear documents when you need to communicate your ideas into other brains. Also, yes AI agents are actually useful (but only as much as you are at managing them).*

Outline:
What is it?
Why did I make it?
How did I make it?
Show it off
Links and donate

This blog post is about how and why I created Verbweaver the way that I did. To check out the app, visit the website: https://verbweaver.design/

# What is Verbweaver?

Verbweaver is a writing and design platform that thinks in relationships (graphs). It's designed for writers, artists, engineers, developers, analysts, and anyone who wants to design things while linking every idea together and turning those ideas into manageable tasks. Think and take notes in a way that is natural to you. Then, when it comes time to communicate your ideas or information to other people, use the Compiler and the powerful templating engine to generate a linear document in various common filetypes.

Currently, the desktop application is in Beta and your feedback is greatly appreciated. The Desktop app works on Windows, MacOS, and Linux.

You can download Verbweaver at: https://github.com/Verbweaver/verbweaver/releases

![_config.yml]({{ site.baseurl }}/images//Verbweaver/mind_map.png "Mind Map")

# Why make Verbweaver?

*Because I wanted to use it but it did not exist.*

Whether it is designing software, tracking findings in a security review, or writing Tabletop RPG campaigns, some people (a set including me) do not think in a linear format. They come up with ideas or make observations about features, story scenes, technical details, fun dialogue, or anything else. That information may or may not relate to each other in some way. But you want to be able to think without being artificially constrained to fit it into a Word document or some other linear format. 

I created Verbweaver because there did not seem to be any purpose-driven tool available that was designed from the ground up to facilitate non-linear design processes. Sure, you could duct-tape together different tools. And with many Obsidian plugins you could get close. But that approach lacked a unified data model that was shared between each user interface and use case.

At some point, though, you will need to communicate that information to somebody else. To do that you must figure out how to arrange your ideas into a comprehensible linear format and generate a document. In Verbweaver, the solution to that is the flexible Compiler engine that can procedurally generate a document from a template and the set of files (nodes) you wish to include.

# How did I make Verbweaver?

Verbweaver was designed by me and implemented by AI agents and AI-assisted development tools like Cursor. 

Initially, I wrote a design prompt with your standard components. I gave the agent an identity and outlined the major components and requirements of the project. I turned Max Mode on in Cursor and ate some cost to generate the skeleton of the application, including both a web server version and a desktop app version that shared as much code as possible. From there I turned off usage-based pricing, contented myself with whatever my $20 / month got me, and iterated. And iterated. And iterated.

Like any other application I have developed, I kept track of what remained to do. And my vision and requirements shifted as I progressed. Sometimes I had a vision for a user experience that didn't work as well in reality as it did in my head. And there were many minor technical challenges to overcome. But my years of general software development experience paid off. I knew what software engineering practices were relevant, what design decisions were important, and the tradeoffs associated with various technical solutions. I also knew how to communicate bug reports to the agent(s) in a way that provided enough information for them to find and fix bugs. In other words, I still had to understand software engineering and what would be important for any developer to know before they implemented something for me; whether they were human or machine. Essentially, I acted as a knowledgable Project Manager / Product Owner leading a team of engineers where every decision had to be approved by me. Rather than as a solo engineer implementing everything myself. 

This human-in-the-loop approach was slower than others may be able to accomplish using a Project Manager agent. I'm sure I've spent at least a couple hundred hours of my own human time on the project so far. But this high degree of specificity in the input to the model meant that high-level design choices remained (mostly) human and intentional, with the implementation details being handled by the agent. The result? A difficult balance of quality *and* efficiency (compared to implementing everything myself). 

I was still able to accomplish *far* more in the same amount of time while achieving the quality I desired. What I did in a number of months would very likely have taken me the same number of years (working in my spare time) to implement myself. And I, in a sense, was able to accomplish something I would have been unable to do by myself. Not because I could not learn all of the requisite information to complete it; rather, because I would not have undertaken such a huge project on my own and it would have forever remained an idea in my head. Today the idea is realized and you are seeing a reasonably finished beta project rather than never hearing of a project that only existed in an abandoned, private Git repo.

## Lessons Learned

> The agent doesn't know what you want. It remains your burden to communicate that effectively along with any details you would be bothered by it missing.
 
The AI agent can spit out code. But that code is unlikely to be more useful than the AI agent's ability to understand what its use should be.

> Discussing a design before implementation produced FAR greater quality of output and than letting the model read between the lines of my instructions.

Before implementing any new system I explicitly told the AI agent to ask any clarifying questions it may have and discuss the instructions with me before proceeding. This resulted in a back-and-forth, with each feedback loop increasing the specificity of instructions. Often this process would make me consider design decisions and implications I had not yet thought of. Considering them ahead of time significantly reduced the burden of fixing or refining them later. Just like thinking ahead and clear, consistent communication are valuable when working with human intelligences... they are also useful when collaborating with artificial intelligences.

> AI-assisted development is currently very efficient for its cost. But it is rapidly increasing in price and will continue to do so.

As an example of this, Cursor's entire pricing model changed multiple times during the development of Verbweaver. These frontier models (from OpenAI, Anthropic, Google, etc.) have so-far been subsidized by investors and tech companies to keep the price down and increase adoption. But at some point they will have to cover their cost and return ROI to the providers and their investors. Their customers may be gaining efficiencies by its use and lowering their costs, but at the model providers' expense. As such, the price will have to go up. They are the cheapest they are likely to ever be in our lifetimes. Make use of them while they are!

> AI-assisted coding and agent-driven development are here to stay.

 I have seen many funny memes about vibe coding and prompt engineering. We get it. There are a lot of people out there currently mass-producing terrible code that serves very little utility. And that gives off the vibe that these tools aren't actually useful. I also just made a great point about how these tools are going to become more expensive over time.

 But garbage in = garbage out. If people who don't understand software are telling AI agents what to do then they will get software that doesn't understand them or what they need. Put people who could build the app themselves (given enough time or money) in charge and they can direct the agents appropriately to great effect. That is where you achieve true efficiency. And it is a LOT of efficiency. 

 We are certain to continue to see a lot of market volatility and disruption in the AI market. I also suspect that the model developers are about to hit a wall of customer adoption. But the practice of software engineering is fundamentally different than it was even five years ago. 
 
 Use whatever analogy you prefer to make this point. My personal favorite is the rise of high-level programming languages. Before their adoption there were many greybeards protesting that new engineers would not really understand how computers *worked* because they weren't writing in assembly. And, well... they weren't really wrong. But as long as there were enough people who did understand hardware and assembly to be able to build those layers and write compilers... the rest of the world gladly moved on and appreciated the efficiency of work (if not necessarily efficiency of code).
 
 I just made a whole app and business in a few months for a few hundred bucks.

# How Does Verbweaver Work?

Everything is a node; a node is everything.

Verbweaver uses a unified data model where every node (idea or piece of information) is a Markdown file with YAML metadata. Write whatever you want. Daily notes, task details, chapters of a book, technical findings, etc. That is the “content” of the node.

The content is written in  Pandoc formatting, which supports advanced formatting such as tables, lists, images, links, and more. This formatting will be preserved when you export your project to your preferred filetype.

Meanwhile, the YAML metadata is used to track the status of the node as a Task, recording its status, start/due dates, assignee, comments, and more. You can also store custom variables in the metadata (such as chapter and tension in the example) that may be referenced by other nodes and document templates when it comes time to generate a document from your project.

When a node is tracked as a Task it is visible in all of the project management views within Verbweaver. The Tasks section of the UI has a Kanban board, a Calendar, a To-Do checklist, and can generate commonly used charts (Gantt and Burndown).

## Dissecting a Node
```yaml
---
id: node-1757717171182-23xpd5w
title: Chapter 2
type: node
description: A blank starting point.
tags:
  - empty
  - basic
created: '2025-09-12T22:46:11.182Z'
modified: '2025-09-12T22:57:45.325Z'
position:
  x: 987.3333333333335
  'y': 178.48888888888888
links:
  - node-1757717219476-h6i6eb6
task:
  status: in-progress
  priority: medium
  assignee: ''
  dueDate: '2025-09-11'
  startDate: '2025-09-01'
  comments: []
  files: []
priority: medium
assignee: ''
chapter: 2
tension: 2
---
# $title$

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi consequat diam eros, non sodales risus molestie ut. Quisque ipsum lorem, finibus laoreet consequat molestie, congue a orci. Quisque eu tincidunt odio. Sed at tempor urna. Nunc sem ante, aliquam quis finibus vestibulum, sollicitudin at lacus. Nunc vitae enim vitae ligula lacinia pulvinar. Aenean mattis turpis odio, eu tristique dui suscipit ut. Sed egestas lectus velit, id commodo nisi pellentesque ac. Etiam eget dignissim odio, at lacinia magna. Sed ut lectus porttitor, porttitor lorem ut, pretium orci. Nunc posuere diam turpis, eu ullamcorper lacus lobortis non. Quisque interdum ut mauris eget feugiat.
```

Let's look at some of those components in detail.

### Node ID
The ID of the node (such as `node-1757717171182-23xpd5w`) is a unique identifier used by the system. It is normally not something the user would ever need to think about. However, it is possible to reference within one node's content the variables and content of other nodes by their ID. 

- Another node’s content: `$node-<ID>.content$`
- A variable of another node: `$node-<ID>.vars.character_name$`
- A frontmatter field: `$node-<ID>.metadata.priority$`
- Conditional on another node: `$if(node-<ID>.vars.ready)$…$endif$`
- Loop over another node’s attachments:
  ```markdown
  $if(node-<ID>.attachments)$
  ### Related Files
  $for(node-<ID>.attachments)$
  - $it.name$ ($it.size$)
  $endfor$
  $endif$
  ```

### Tags

Node tags are very useful when filtering nodes. For example, when picking nodes that will be exported into a document in the Compiler.

### Links

Nodes may be linked to each other. These links are displayed on the Mind Map as visual, dotted lines drawn between nodes. These links can represent any kind of relationship between information such as related concepts, network connections, usage of one by the other, or anything else.

### Task data

If a node is tracked as a Task, then it has various task-tracking metadata. Files may also be attached to it for reference. If those files are images then they may be (optionally) rendered in compiled documents.


# Status and Roadmap

The Verbweaver desktop app is now in a public Beta testing phase.

If it sounds useful to you then please try it out and provide your feedback (ideally as GitHub Issues). If you have an idea for a feature, something doesn't quite work the way you think it should, or the documentation is not accurate, then please let me know. Once I feel that the app has been thoroughly tested and refined I will publish version 1.0.

While Verbweaver is and will remain freely available, when version 1.0 of the desktop app is published it will be available on the Windows Store and Apple Store for those who wish to buy a copy to support development or want the convenience of owning it in their operating system’s app store. You can also [donate](https://verbweaver.design/donate) if wish to do so.

A self-hosted web server version with enhanced collaboration features is under development. After version 1.0 of the desktop app is completed, I will shift focus to completing the web version.

![_config.yml]({{ site.baseurl }}/images//Verbweaver/verbweaver_default_256.png "Verbweaver Logo") 