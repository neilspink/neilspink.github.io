I’ve been building [100days.ink](https://100days.ink), a small app with a big purpose:
help people commit to something for 100 days and actually follow through.

The rules are simple:

- Write down your 100-day commitment.
- Pick a start date.
- Decide if it’s private, public, or shared with the community.
- Support the idea with a tip.

That’s it. No feeds. No distractions. Just you versus the next 100 days.

![100Days.ink landing page](100daysink.png)

The idea came from watching [I Worked Out Like David Goggins for 100 Days](https://youtu.be/vWU5O7cK7aI?si=Qvuerw0Zx3Y68PMf).
It’s entertaining, but also shows what happens when you truly commit to a goal. Momentum compounds when you consistently deliver.
It lit the spark for my own 100-day project, but instead of doing fitness, I wanted to program again. And why not build a commitment engine that backs you on that venture: something that turns promises into action and accountability into a game you can actually win.

I wanted massive scaling capacity and chose Firebase. Their NoSQL backend gives granular access control and easy auth.
I added Firebase Storage for images, because words aren’t always enough.
On top of that I run a free cron-job.org task to push daily reminders with short coaching notes to your mailbox, plus a weekly digest.

To make it dynamic, the AI coach changes tone: if you skip check-ins, the “temperature” gets dialed up a bit. More direct. More urgent.
The app is minimal on purpose. A fun MVP.

I didn’t expect login and email to be the hardest parts of the project. If registration emails land in spam, your app is dead before it starts.

![100Days.ink registration page with spam folder notice](commitment-saved-confirmation.png)

Even with a notice to check spam, few people actually completed registration.

![Spam mail example](spam-mail2.png)

You get what you pay for. And this one-size-fits-all backend forced me to jam Firebase’s user model into mine.
Registration emails come from their *.firebaseapp.com domain. That’s a red flag for spam filters when your sending domain is 100days.ink.

The Firestore database was very practical.

I liked building in Next.js with TypeScript. API routes, file-based routing, server + client in one place — good first experience.
I’ve worked with Angular and completed a project in Ember.js, but moving into the React ecosystem was great.

Making it mobile friendly was important to me. You get a link every day to reflect on your 100-day mission.

<img src="UI-day1.jpg" alt="Day 1 reflection" width="375" />

Every day, the system runs a user’s most recent reflections through OpenAI, combining their goal, coaching style, and recent behavior to generate personalized advice and an email subject line in the coach’s voice.
It tags reflections with a “vibe” (grit, frustration, etc.) and adjusts tone based on engagement — trying to keep users moving forward.

![Example emails](emails.png)

I was worried OpenAI usage might blow up my budget, so I limited output length and kept prompts tight.
It turns out the cost was laughably low.

![OpenAI costs](openai.png)

I pushed 100days on X and ran a small ad campaign, but it didn’t gain much traction.
In September I started building social features, but ultimately decided to wrap the project.

![Github commits](github.png)

There were several cool parts of the project (technical):

- AI coaching personalities (data-driven archetypes + guardrails)
- A daily coaching pipeline built on reflections + goal context
- Time-limited “mission day” links (mobile-first)
- Reflection timeline with optional image uploads + failure UX
- Email engine using Markdown templates (daily + weekly digest)
- Stripe “tip” checkout as a simple monetization path

I’m keeping the repo private for now. If you’re curious, I’ll share a walkthrough or selected snippets.
