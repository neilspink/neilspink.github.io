---
title: "100days.ink — A Commitment Engine"
date: 2025-09-07
tags: ["100days", "commitment", "focus", "execution"]
---

I’ve been building [100days.ink](https://100days.ink), a small app with a big purpose:  
help people commit to something for 100 days and actually follow through.

The rules are simple:

- Write down your 100-day commitment.  
- Pick a start or end date.  
- Decide if it’s private, public, or shared with the community.  
- Put some skin in the game — tip from $2 to $147.  

That’s it. No feeds. No distractions. Just you versus the next 100 days.

![100Days.ink landing page](100daysink.png)

The idea comes from watching the video [I Worked Out Like David Goggins for 100 Days](https://youtu.be/vWU5O7cK7aI?si=Qvuerw0Zx3Y68PMf). Both entertaining and showing what happens when you commit: momentum compounds, discipline hardens and you leave the dabbling behind. It lit the spark for my own 100-day project but instead of doing fitness, I wanted to build a commitment engine that backs you on such a venture. Something that turns promises into action and accountability into a game you can actually win.

Right now the codebase is still private, but I’ve been iterating in the open with a lean stack. Firebase with it's NoSQL backend providing granual access control and easy auth. I extended with Firebase Storage for images, because words aren’t always enough. On top of that I run a free cron-job.org task to push daily reminders with short coaching notes to your mailbox and a weekly digest newsletter. To make it dynamic, the AI coach changes tone: if you skip check-ins, the temperature parameter gets dialed up, making the responses a little sharper, a little more urgent. It was fun hacking psychology into the code.

The app is minimal on purpose, a fun MVP.