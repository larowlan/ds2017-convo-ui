## OK Drupal
### Using Drupal & dialogflow to power the conversational interfaces of the future

Note:
- The api formerly known as api.ai

--

<!-- .slide: data-background="./images/willis.jpg" -->

## What we'll cover

Note:
- Some basics of conversational UI
- Creating a project with dialogflow
- Fulfillment with Drupal
- Pushing your entities to dialogflow

--

## But first

--

<!-- .slide: data-background="./images/dumpster.jpg" -->
## Live Demo!

What could possibly go wrong?

---

## Terminology

Note:
- so let's go over some of the terminology we're going to cover

--

## Intents

Note:
- mapping what the user says into an action
- 'Order some pizza?'
- 'What is the wait time?'

--

## Entities

Note:
- familiar w/ from Drupal
- basically the same
- collection of objects
- synonyms

--

## Context

Note:
- conversation is threaded
- humans keep track
- 'play something by Kurt Vile'
- 'give me another one'

--

## Fulfillment

Note:
- Dynamic responses
- Where Drupal fits in

---

## Design considerations

Note:
- So conversation is hard
- You need to plan
- Nothing worse than poor UX/ rabbit holes

--

## You need to think about

- Scope
- Personality
- Flow

--

## Scope

Note:
- Make it clear what you can and can't do
- Avoid unrelated questions and dead-ends
- Good intro text

--

<!-- .slide: data-background="./images/twine.png" -->
## Mapping out the flow

- https://twinery.org/2/

Note:
- Use a flow charting tool 

--

## Start with the happy path

Note:
- User gets it straight away
- Typical flow

--

## Don't forget the unhappy path

Note:
- Add a 'help' if you get stuck
- Redirect them to other forms
- Start over

--

## Character

Note:
- Keep it interesting
- Make it fun
- Make it unique

---

## Dialogflow
(formerly api.ai)

Note:
- tool of choice

--

## Your first intent

Note:
- User says
- Machine learning
- Enter 5-10 to seed it
- The more the better

--

## Creating some entities

Note:
- Some are fixed
- Some are dynamic (more on that later)
- Synonyms are important

--

## Tracking context

Note:
- Play a song by 'Beulah'
- Play another song
- Expiring context
- Requiring context

--

## Fulfillment with Drupal

Note:
- Configure url
- configure password

---

## Drupal

--

## Chatbot API

<code>drupal.org/project/chatbot_api</code>

--

## Dialogflow webhook

<code>drupal.org/project/api_ai_webhook</code>

--

## Intent plugins
(show me some code)

Note:
- https://github.com/previousnext/pnx-d8/blob/master/app/modules/custom/pnx_bot/src/Plugin/Chatbot/Intent/Blogs.php

--

## Pushing entities
(show me some site building)

---

## Recap

* Demo
* Terminology
* Dialogflow
* Drupal

Note:
- Go out and make something cool

---

<!-- .slide: data-background="./images/turtle.jpg" -->

## Looping back

@larowlan

Let me know if you build something interesting

Note:
- Senior Drupal Developer with PNX
- QLD based

--

## Image credits

- https://flic.kr/p/73DhiT
- https://flic.kr/p/smA95B

--
