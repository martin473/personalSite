---
title: Fast Deployments at Blade UI High
---
My current obsession is tech stacks that are easy to setup prototype and deploy. Most projects never become enormous and there’s almost no reason for any developer to be maintaining enterprise level code on a small scale.

The main reason for this is unless the enterprise toolkit is low cost and default within the framework (such as django,) you have to spend a significant amount of time working with new paradigms and building features into your software that may never get used.

This is my journey as well. It’s a path of learning I’m embarking on and I am expecting things to break. I want to know how my current paradigm crashes against the real world. I expect it to be incredibly useful, and also have serious limitations. Hopefully at the end of this project I’ll have a better grasp on things.

My goal is to build a Next.JS XBox 360 style blades UI. I think Windows is the king of horrifically impractical UI.
![Blades UI](https://i.redd.it/glu5q2sfirdc1.jpeg)

I also think when you follow material design to it’s foundation, or many other UI paradigms, you just get excessive menu diving.

The way humans handle visual space IRL is not through invisible paper layers, drop down menus, swiping through pages. You’re essentially navigating a non-intuitive 3D grid that has no way of “feeling” what state you are in. With a sword you feel balance. With a book you can pinch and rub the page if you think two pages got stuck together. Humans can quickly look at clouds and use pattern recognition to determine if they are sirius or cumulonimbus. The moon has phases and craters we can visibly see. Smells, tastes, sights, sounds. There is so much context in the world, and the current state of UI is to present a seriously large amount of non-technical folks with a constantly changing menu maze to swipe around in. Sorry we updated, the menu changed. You closed an app, the swipe order of applications changed. You reinstalled something you have to go through the entire tutorial again. 10,000 push notifications vying for you to be the user that creates the 0.5% engagement bump this month. It’s really a function of where we are.

I think material 3 as a UI kit is beautiful however. It’s got a lot going for it and I particularly love the motion and color research they did. But maybe we can move away from popup menus, swipe menus, etc. They were a good second paradigm for smartphones, but as always, I think we can do more.

Until I learn how to look into the future, I’d love to look into the past, at “bad” UIs. Ones that make me nostalgic. The Kyocera phone menu. The iPod wheel menu. XBox 360 Blades. Windows XP color schemes. Some of these things are a function of limitation. The palm pilot had a special touch pad for drawing characters because the touch screen and the display screen were separate. Some are functions of design philosophy. The iPod had many competitors. An Mp3 player was not difficult to come by at the time, but the concept of having 1 button drove mac to create a giant scroll wheel that could be pushed down at 4 points. It was non intuitive at first, but you could use it in your pocket with your eyes closed. Somehow the iPhone got so simple that you couldn’t access more complex features and if you wanted to adjust your user experience, you were usually locked into their way of doing things.

![Macbook Wheel](https://www.gamengadgets.com/wp-content/uploads/2016/09/macbook_wheel_by_jayfreelancer.jpg)

My code design philosophy is to create fast with online IDEs, drag and drop editors, in robust languages that can implement very advanced features like UI kits, CSS kits etc. My two languages of choice are Flutter and Next.JS. They both have serious limitations, one being that users are suggesting if Next.JS isn’t hosted on a Vercel instance, then it is artificially throttled in some way and has slower page load times. Flutter seems to just have some limitation aura around it that I can’t quite parse.

Experimentally, I hope to create a beautifully “bad” UI that is fun to use. And maybe intuitive in some way.

Wish me luck.
