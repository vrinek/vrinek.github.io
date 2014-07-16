---
layout: post
title: "Last few days"
date: 2014-07-16 10:15:11
categories: game-one
---

**It is finished!!!**

Not App Store quality yet, not for mass distribution but nevertheless it is in a very playable state and most importantly: **it is fun!**

<iframe width="320" height="568" src="//www.youtube.com/embed/WMDzIdD4qG4?rel=0" frameborder="0" allowfullscreen></iframe>

The video is not amazingly informative, so here goes the narration:

- The player's goal is to keep the ball on the disc for as long as possible
- Bubbles that reach the bottom push the ball towards that color's direction
- Tap and hold a bubble to destroy it
- Tap and release a bubble to speed it up (to make it count as fast as possible)
- The game speeds up gradually

## Next steps

- **Player feedback.** The more the better.
- **Better graphics.** I probably need a visual artist for that.
- **Audio.** It feels somehow _flat_ without sound.
- **Experiment with the layout.** Maybe having the bubbles moving upwards?
- **Experiment with the scoring logic.** Right now the score is incremented every time a bubble is generated. I think it should be incremented every time a bubble is applied to the disc.
- **Menu screen.**
- **Briefly explain the gameplay.** Right now, players find it difficult to relate the ball's movement to the disc's state to the bubbles.
- **Animations for more intuitiveness.** An explanation text is not always ideal. A player should be able to figure out the relationship between the various gameplay elements with no explanation.
- **More dimensions of progression.** Different discs (more and less numbers of colors), different bubbles (bigger/smaller, multi-colored, special ones).
- **Persist the high score.** Right now there is no persistency, not even on the same device. It would be nice to keep the high score somewhere and maybe even implement Game Center leaderboards.
- **Release!** Yes, at some point I think I should release it on the App Store.

## What I learned

**Swift** is an enjoyable language. It mostly feels like C#. I will definitely go back to it in the future.

**SpriteKit** is a great and simple 2D game engine. It provides a lot of conveniences and usually behaves as expected. Compared to Unity, SpriteKit is a notch better than Unity's 2D implementation which makes sense since Unity is 3D under the hood.

**XCode** is a tool I am not yet comfortable with. I will need to invest some time to get used to it. At work I use SublimeText and I constantly find myself trying and failing to use the same shortcuts. Even the interface and its capabilities are alien to me. I have some problems trying to distribute the game to friends to try it out, I have no idea how to do it. I will surely need to invest some time to learn this tool if I am going to be coding in it.

My process worked. Leaving only the last few days for coding the actual game was a good idea. **Design before implementation, inspiration before design.** I will keep this up and try to stick to it a little more.

Blogging every day didn't work. I usually forget it and even when I remember it, it is usually the next day in the morning.

---

Now that the first prototype is done, it's time to begin the second one. I will (hopefully) be blogging about the basic idea tonight.
