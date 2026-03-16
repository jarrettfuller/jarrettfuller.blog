---
layout: post
title: Building my own bookmarking software
categories:
- Technology
description: "With the help of Claude Code, I finally have the bookmarking app I've always wanted."
---

Last week, [Craig Mod wrote about the "bonkers" finance app he built for himself over the course of a week with Claude Code](https://craigmod.com/essays/software_bonkers/):

> For the first time in my life, I have a dashboard that gives me a true, holistic view, of everything financial happening in my life and business. I’ve named my glorious contraption `TaxBot2000`. It is astounding. Let me repeat: _I built this in five days_.

> It’s not perfect, and it’s not done, but it is already better than what I had been using for the last decade. Until now, I’ve leaned heavily on Quicken — closed-source subscription software that often fails to connect to accounts with two-factor-authentication, silently losing chunks of financial data. Previously, I’ve mixed Quicken with Google Sheets, using a stack of Google Scripts to move information back and forth between currencies and formats and countries. I’ve used Japanese accounting software to export Japanese bank accounts and credit cards, and then reconfigure and import them into Quicken as converted accounts. Anyway, complicated and weird and a bit quirky: my situation. For TaxBot2000? No problem. I don’t think I’ll open Quicken again.

My own experience with AI, admittedly, has been minimal: I use it to summarize the interviews I record for Scratching the Surface and it helped me pull out big themes from the conversations I had when working on my forthcoming book. When I got a new computer and had to migrate my decade-old Jekyll static website over, I used Claude to help me troubleshoot setting it up again fresh; then used it to help me build some simple photo galleries for my website. Perhaps naively, I feel little fear in it taking my job and as [I've written before](https://www.fastcompany.com/91382025/ai-isnt-designs-biggest-problem), I don't think it fundamentally changes my industry as much as speeds up a trend a long time in the making. My partner has made copious use of AI agents in her work that has me intrigued with possibilities in new ways. 

This, combined with Mod's ambition, inspired me to spend some time on Sunday morning building a custom bookmarking app for myself. For the better part of twenty years, I've used bookmarking software as my second brain: to save links, articles, urls, and documents that I may want to refer back to. I started with del.icio.us in the early web 2.0 days before flirting with the shortlived Google Bookmarks. For the better part of a decade, I lived and died inside Evernote where I threw everything I may want to reference later. As Evernote got increasly bloated (and I continued to use it in a way it wasn't really designed for), I left ten years ago, briefly for Are.na before settling on Pinboard. Pinboard is stupidly simple: I save links via a bookmarklet. I copy quotes or notes into a text field and assign it some tags. Done. (I pay extra for the web cache version that saves archives of the pages but have never actually used it.)

I've been happy with Pinboard overall and have nearly 5000 links saved in my account. But the service hasn't been noticeably updated in years and feels dormant. I'm noticing increased errors in saves and I've never gotten it work quite right (with apis and partner apps) on iOS. I'd been on the lookout for something to migrate too but all seem overly complex for my simple needs. I realized I could build one for myself.

And so I did. Over the course of about an hour and half, I got up and running a super-simple bookmarking app. Here's how it works:

1. In Safari, there's a bookmarklet button (just like Pinboard) that opens a new window. In that window, the page title and url are pre-saved and there's a text box for notes and a field for tags.
2. When I click save, a python server saves that data in a markdown file named `YYMMDD_title-of-the-webpage.md`, my preferred naming convention for all my files, into a folder on Dropbox.
3. That Dropbox folder is called `Bookmarks` and lives in my Obsidian vault so I can now open and search all my bookmarks in Obsidian.

And that's it! Like I said, my needs are simple. I increasingly want all my documents as text files so I'm not bound to any app or format and now nothing lives on a server or in the cloud, it's all saved locally and synced via Dropbox. All my writing happens in Obsidian already — from essays to quick notes to journaling — and having all my bookmarks in Obsidian turns it into a powerful archive of both reading and writing; a place to both research and produce. 

<figure>
<img src="/images/260316_bookmark-obsidian.png">
<figcaption>Example of the Markdown file the server creates for me as it's seen in Obsidian.</figcaption>
</figure>

After some back and forth on specific features and getting the local server running, most of my time was spent formatting the Markdown files the way I wanted them. Then, I gave Claude the json file of all 5000 bookmarks in Pinboard and asked it to turn those into .md files too, named and formatted the same way. I downloaded that zip file and threw it in my `Bookmarks` folder, essentially rebuilding my entire Pinboard archive locally. Inside Obsidian, it's still searchable, linkable, and, most importantly for me, integrated into my writing environment.

Next steps are building the iOS bookmarklet so I can save links from my phone and iPad and then customizing the design for the popup windows to better match my aesthetic. Was this a complex project, not at all. It's on the easy side of what these models can do. It's no finance app, that's for sure. But does it solve a simple problem for me, in the exact way I want? Yes. Does it divorce me from living inside someone else's platform? Yes. Does it keep my bookmarks in an easily transferrable format in case my tastes change in the future? Yes. All these things are important to me and I love that I can roll my own solutions for these particular values. In this way, it feels less like something new and more like the decades long open-source software movement. 

[Paul Ford, in an essay for the *New York Times* recently wrote](https://www.nytimes.com/2026/02/18/opinion/ai-software.html):

> All of the people I love hate this stuff, and all the people I hate love it. And yet, likely because of the same personality flaws that drew me to technology in the first place, I am annoyingly excited.

That's how I feel, honestly. After building this little bookmarklet and saving my first files, I felt a pride like the one I remember feeling in high school, [building my first websites](https://untappedjournal.com/stories/jarrett-fuller-building-with-simple-tools-longevity). Then I felt stupid because I didn't build anything at all this time, I just asked a Claude to do it for me. But that ability to ask, for someone like me with just enough programming experience, feels like it opens up a world of possiblities in the same way learning to code html did twenty years ago. Today, anyone can build a website with simple tools, drag and drop interfaces, and premade templates. Maybe that's the future of software too? 
