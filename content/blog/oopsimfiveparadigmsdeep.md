---
title: Oops! I'm 5 Paradigms Deep!
# Parse Git commit
enableGitInfo: true

params:
  # Display the last modification date
  displayUpdatedDate: true
  dateFormat: "January 2, 2006"
---
Modern development often involves modern frameworks that are built on top of not one but two or more frameworks.

For example if you want to transform vector images in frontend development and your team is using NextJS, You might use Motion, which is a library on top of React, and also use NextJS which is a framework on top of React + Typescript + Tailwind, and React and Typescript themselves being a framework on top of vanilla Javascript, and Tailwind a framework on top of CSS.

This does make most development easier, but not all.

Often, at this level of complexity and abstraction, development concepts that have already been thought of end up being extremely easy, and a fair amount of edge cases as well. However, you sometimes break the paradigm it is pushing forward, usually by asking something out of the framework that it does not have a shortcut for.

A problem I ran into was trying to click an SVG as a button in NextJS. Next handles the click info. Tailwind handles the animation and SVG. However Next is setup for buttons to be buttons, not SVGs, so you have to have the child item of the SVG communicate to the parent div that it has been clicked so that you can animate the entire div containing the SVG. I learned that vanilla CSS doesn't have child to parent communication, only parent to child, so there are a lot of workarounds around that. Tailwind also has not created a paradigm for this, so you have to work with Tailwind custom classes to communicate to Next how you want the CSS to structure the child to parent relationship so that you can, essentially just click a custom shaped button.

The issue is that when you break a paradigm, you have to figure out which layers you're working between.

A much simpler example is this website. To set the image size in image cards I have to add some arguments, however the documentation isn't clear on them. It just says, add some Hugo image arguments here to handle this. Well, the "Image Card" is a Hextra object. Hextra is built on Hugo. The "Image Arguments" I pass to the card to alter how the image renders are Hugo. And Hugo itself is built on Go. Most of the time I never have to go deeper than Hugo, and luckily this documentation is really explicit about pointing me to the Hugo docs, but often when you are working in these multiframework languages, you have to be really aware of which framework is lacking in ability, and which other framework it's pointing you towards to add that functionality.

It is really, really easy to get lost reading the wrong documentation because you didn't know it couldn't do something, and there's no obvious place to find it.

On top of that, in the case of Motion for SVGs, it's a library on top of React to compensate for the fact that React isn't great at animating SVGs. So in some cases, MANY folks wanted the functionality, and another developer built it in a new framework. So you end up going up and down layers of abstraction and then picking another to throw on top of it.

If you want to navigate the learning process, it's super helpful to understand which framework you're thinking in at the moment, what are its limitations, and where you would go to next. It's also really, really important to understand the syntax of the framework and a bit of what it's doing under the hood. A single block of Next code can involve typscript typing, HTML, tailwind arguments, and React/Next/JS code. Knowing which is which goes lightyears towards helping you figure out which documentation file to open when problem solving.

Good luck!