---
title: "Higher or Lower?"
date: 2023-06-25
draft: false
icon: ssense
description: "A webgame where the user guesses which article of designer clothing is more expensive."
internalUrl: /projects/higher-or-lower/
weight: 10
---
{{< alert "github" >}}
Check out the code on [Github](https://github.com/bvu12/ssense-game) or play the game for yourself [here](https://ssense-game.vercel.app)!
{{< /alert >}}

A webgame where the user guesses which article of designer clothing is more expensive.

![Demo of the game](https://raw.githubusercontent.com/bvu12/bvu12.github.io/master/content/projects/ssense/ssense.gif)


## Learning objectives
I set off on developing this project to meet a few goals:
- [x] Challenge myself to complete and deploy a project end-to-end by myself
- [x] Learn how to use <mark>Next.js</mark> with <mark>TypeScript</mark> and <mark>Tailwind CSS</mark>
- [x] Learn how to take feedback on my own work to make it better

## Technologies used
| Technology                                    | Description                                                                                 |
|-----------------------------------------------|---------------------------------------------------------------------------------------------|
| [MongoDB](https://www.mongodb.com/)    | a NoSQL database used to store our products                                                 |
| [Next.js](https://nextjs.org/)                | a React framework used to develop the frontend + backend and used to deploy the application |
| [Tailwind CSS](https://tailwindcss.com/)      | a CSS framework used to style the frontend                                                  |
| [TypeScript](https://www.typescriptlang.org/) | a superset of JavaScript that adds static types                                             |

## How does it work
### Backend
On page load, a few products are randomly fetched from our `MongoDB` database into a list. To improve performance, subsequent products are periodically fetched in the background as the user gets more correct answers.

### Frontend
Two cards are initially displayed side-by-side on the screen, when the user correctly selects the more expensive product we increment the state of a counter variable. This `setState` operation slides down along our product array and re-renders the next product. When you incorrectly select a product, the `Gameover` screen shows and places all `products[0...n]` into a carousel.  

We have the ability to restart the game over again by calling our `startGame` function:
```typescript jsx
const startGame = (productAPISuffix: string) => {
  setIsLoading(true);
  fetchProducts(productAPISuffix).then(() => {
    setGameType(productAPISuffix);
    setScore((prevScore) => ({
      currentScore: 0,
      hiScore: prevScore.hiScore,
    }));
    setIsGameOver(false);
    setIsLoading(false);
  });
};
```