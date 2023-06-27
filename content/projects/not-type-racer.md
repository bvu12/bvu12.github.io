---
title: "Not-TypeRacer"
date: 2022-03-20
draft: false
icon: keyboard
description: "A minimalistic typing challenge featuring various typing modes and a global leaderboard."
internalUrl: /projects/not-type-racer/
weight: 10
---
{{< alert "github" >}}
Check out the code on [Github](https://github.com/cartiervu/Type-Racer) or ~~play the game for yourself [here](https://blissful-joliot-5397ba.netlify.app/)~~ (redeployment is in progress)!
{{< /alert >}}

A minimalistic typing challenge featuring various typing modes and a global leaderboard.

![Demo of the game](https://user-images.githubusercontent.com/43510280/159205352-56191231-de63-4bf9-be7d-0c059813cde2.gif)


## Learning objectives
I set off on developing this project to meet a few goals:
- [x] Learn how to collaborate with others to complete a project
- [x] Learn how to use the <mark>MERN</mark> stack
- [x] Deploy a project into the wild

## Technologies used
| Technology                                 | Description                                                                             |
|--------------------------------------------|-----------------------------------------------------------------------------------------|
| [MongoDB](https://www.mongodb.com/)        | a NoSQL database used to store our text for the challenges and the highscores           |
| [Express](https://expressjs.com/)          | a minimalist web framework for Node.js that helps us get the HTTP server up and running |
| [React](https://react.dev/)                | our frontend library                                                                    |
| [Node.js](https://nodejs.org/en) | our backend server environment                                                          |

## How does it work
### Backend
Text is fetched randomly via `REST` from our `MongoDB` database - this includes Wikipedia articles, words from the English dictionary or quotes.

When a user's score (either time-based or words-per-minute-based) enters the top-10, they are prompted to enter their name on the global leaderboard. This is saved back to our database, and older values are pruned.

### Frontend
Text is fetched can begin typing. We have an event handler that triggers the timer to start recording as soon as a keystroke is pressed, and we regularly push the current time-stamp in order to calculate the user's `wpm` over time.
```typescript jsx
const handleKeyPress = (event) => {
  if (!timer.startTime) {
    timer.startTime = performance.now();
    setStartCountdownTimer(true);
  }
  setUserText(event.target.value);
  if (event.target.value === (quoteObj.array[quoteObj.currIndex])) {
    timeSplits.push(performance.now());
    quoteObj.currIndex++;
    setUserText('');
    if (quoteObj.currIndex >= quoteObj.array.length) {
      onFinish();
    }
  }
}
```
The user actually types into a focused-state user input box, while the text shown on screen is rendered from a few parts:
* The **correct** text so far (shown in blue)
* Any **incorrect** text so far (shown in red)
* The **remaining** text is shown in black

These are calculated by comparing what is in the input box against the original string. Furthermore, we prevent users' from backspacing too far by saving fully correct words in a separate array.