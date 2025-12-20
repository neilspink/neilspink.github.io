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
- Support the idea with a tip.  

That’s it. No feeds. No distractions. Just you versus the next 100 days.

![100Days.ink landing page](100daysink.png)

The idea comes from watching the video [I Worked Out Like David Goggins for 100 Days](https://youtu.be/vWU5O7cK7aI?si=Qvuerw0Zx3Y68PMf). Both entertaining and showing what happens when you truely commit to goal. Momentum compounds when you consistenly deliver. It lit the spark for my own 100-day project but instead of doing fitness, I wanted to program again and why not build a commitment engine that backs you on such a venture. Something that turns promises into action and accountability into a game you can actually win.

I wanted massive scaling capacity and chose Firebase. Their NoSQL backend provides granual access control and easy auth. I eventually extended with Firebase Storage for images, because words aren’t always enough. On top of that I run a free cron-job.org task to push daily reminders with short coaching notes to your mailbox and a weekly digest newsletter. To make it dynamic, the AI coach changes tone: if you skip check-ins, the temperature parameter gets dialed up, making the responses a little sharper, a little more urgent. The app is minimal on purpose, a fun MVP. 

I didn’t expect login and then email to be the hardest parts of the 100days.ink project. If registration emails land in the spam folder, your app is dead before it starts. 

![100Days.ink regristration page with spam folder notice](commitment-saved-confirmation.png)

Even with a notice to look in the spam folder, few persons actually completed the registration.

![Spam mail example](spam-mail2.png)

You get what you pay for. And this one-size-fits-all backend forced me to jam Firebase’s user model into mine. Registration emails come from their *.firebaseapp.com domain. That’s a red flag for spam filters when your sending domain is 100days.ink. 

![Firebase authenication console](firebase-users.png)

The Firestore database I found very practical. 

![Firestore database](firebase-database-entry.png)

I liked building in Next.js with TypeScript. The API routes, file-based routing, server + client all in one was a good first experience. I’ve worked with Angular before and completed a project in Ember.js, but moving into the React ecosystem was a great. 

Making it mobile friendly was important to me. You get a link every day to reflect on your 100 day mission. 

<img src="UI-day1.jpg" alt="Day 1 reflection" width="275px" />

Every day, the system runs a user’s most recent reflections through OpenAI, combining their goal, coaching style, and behavioral patterns to generate personalized advice and an email subject line in their coach’s voice. It tags each reflection with a “vibe” like grit or desperation, adjusts the tone dynamically based on past engagement, trying to keep users moving forward—even if it has to jolt them.

I was worried OpenAI usage might blow up my budget, so I limited output length and kept prompts tight. But it turns out, even with daily usage across multiple users, the cost has been laughably low.

![OpenAI costs](openai.png)

I pushed 100days on X and ran a small ad campaign, but it didn’t gain much traction. In September I stared building the social features, but ultimately decided to wrap the project.

![Github commits](github.png)

