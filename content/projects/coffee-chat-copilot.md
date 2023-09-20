---
title: "Coffee Chat Copilot"
date: 2023-09-07
draft: false
icon: coffeechatcopilot
description: "Transcribe, summarize, and get suggestions on talking points for your conversations - eliminating manual note-taking and maximize networking efficiency"
internalUrl: /projects/coffee-chat-copilot/
weight: 9
---

{{< alert "dev" >}}
This project was built during Hack the North 2023 - check out our [Devpost](https://devpost.com/software/coffee-copilot) for all the details!
{{< /alert >}}

Below is a conversation between us and Steve - another Hack the North participant. Notice the two main points: we summarize the conversation and also suggest future speaking points!

![Sample coversation](https://d112y698adiu2z.cloudfront.net/photos/production/software_photos/002/592/338/datas/gallery.jpg)

## Inspiration

In the fast-paced world of networking and professional growth, connecting with students, peers, mentors, and like-minded individuals is essential. However, the need to manually jot down notes in Excel or the risk of missing out on valuable follow-up opportunities can be a real hindrance.

## What it does

Coffee Chat Copilot transcribes, summarizes, and suggests talking points for your conversations, eliminating manual note-taking and maximizing networking efficiency. Also able to take forms with genesys.

## How we built it

### Backend:

- Cohere was used for both text summarization and text generation using their latest Coral model
- AssemblyAI was used for speech-to-text transcription and speaker diarization (i.e. identifying who is talking)
- Python + FastAPI was used to serve HTTP requests
- CockroachDB was used to store user and conversation data

### Frontend:

- We used Next.js for its frontend capabilities

## Challenges we ran into

We ran into a few of the classic problems - going in circles about what idea we wanted to implement, biting off more than we can chew with scope creep and some technical challenges that seem like they should be simple (such as sending an audio file as a blob to our backend 😒).

## Accomplishments that we're proud of

A huge last minute push to get us over the finish line.

## What we learned

We learned some new technologies like working with LLMs at the API level, navigating heavily asynchronous tasks and using event-driven patterns like webhooks. Aside of technologies, we learned how to disagree but move forwards, when to cut our losses and how to leverage each others strengths!

## What's next for Coffee Chat Copilot

There's quite a few things on the horizon to look forwards to:

- Adding sentiment analysis
- Allow the user to augment the summary and the prompts that get generated
- Fleshing out the user structure and platform (adding authentication, onboarding more users)
- Using smart glasses to take pictures and recognize previous people you've met before
