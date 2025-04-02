---
title: FloodyBot
---

Goal: 

Will your house flood due to climate change? Will it be covered under insurance? Put your address into FloodyBot to get a 3D map of flood zones and insurance coverage zones for your home address.

Why: 

Around 2019, a prominent news org released an article warning that home insurance providers were not planning to increase coverage to match predicted climate crises. Specifically flood and fire. Around the same time, predictive flood maps for climate coverage were starting to get built. It didn't exist in a robust form then, but [climate central now has a great tool](https://coastal.climatecentral.org/). I wanted to make this more visual, creating a 3d map that people could explore. I've always felt visceral tools let people experience more abstract concepts in an approachable way. [Rayshader](https://www.rayshader.com/) looked like a good library to work with.

[Rayshader](https://www.rayshader.com/reference/figures/smallfeature.png)

[Climate Central - Small hurricane surge in 2070](https://imgur.com/YkeqDKr)

[This article](https://ecori.org/home-insurance-costs-rise-due-to-demand-costs-of-rebuilding/) goes in depth on Rhode Island's current situation regarding flood insurance. 

Motivation: 

I thought it would be interesting to have a Twitter bot, in 2020, where you could tweet your address and get a shareable picture of the flood situation. This would help not only with looking at a home you own, but also one you plan to buy. This was pre-housing-crisis. It seems like many sensible issues for new home owners are no longer a concern. The concept also needed some work to answer questions like "Would a user want to publicly tweet their home address and in return get a public 3D picture of their home." Probably not. Either way the first step was to build it.

Final Tech Stack:

This used R, the R rayshader library, and a Windows AWS instance.

Process:

There were a lot of things I was unaware of at the time of making this. 

A big early barrier was getting access to the Twitter API. I had used a handful of APIs at that point and the biggest barrier for new devs is always access and rate limiting. As far as APIs are concerned, the world is not your oyster, you need to get into the club, and you need to behave.

I ended up applying for API access multiple times and by the final stages of this project never got it. One of the reasons was that Twitter at the time was constantly improving spam monitoring and there was some data scandal during that time that caused them to tighten up token access. It didn't prevent me from ever being elligible, it just lengthed the wait for access beyond the scope of the project.

Another early barrier was not understanding gaps in documentation and reality and how to read error codes in a more comprehensive way. I initially tried to run this on linux. The errors I kept getting were that XYZ library couldn't be installed. So I ended up installing the dependencies manually via cli 1 by 1 until I hit one that wouldn't work. I went into the documentation and I saw it was Windows only. Now I would just restructure the project in some way, but I kept going down the rabbit hole of trying to get it to work on Linux. Eventually I reached out to the Rayshader dev on Twitter DMs and he said that it was a Windows only R library. I either missed that in the documentation or it wasn't there. Either way it was quite a lot of time wasted. A big reason for this issue was that my home laptop was running Windows 10, so it worked fine on my local PC, and then encountered "crazy" errors on my cloud machine. Obviously you can't run an exe on linux, but I wasn't aware that even Python and R libraries require not just OS specific, but processor specific releases. This was how I learned that.

I then researched cheap AWS instances, spun up a very small and cheap $10/mo AWS Windows instance. Installed and ran the software and presto it spit out this image on the webserver.

[FloodyBot image output](https://imgur.com/HIqZd5r)

FloodyBoy image output.

There was a long way to go and I basically did not find this project fun any more, and the general public did not seem to care too much about it so I dropped it.

Unfortunately there's no repository

The code:

Unfortunately I was still a Git newbie. I was coding on my laptop and then copying and pasting the files from my code editor locally to my code editor in my Digital Ocean/AWS code editor window. Then when I was done with the projects I deleted the instances and a few years later my laptop bit the dust.

Generally speaking, the AWS instance ran some Apache or similar webserver and served from the default webaddress AWS gave it. It had the necessary R libraries including rayshader installed and Windows permissions set through PowerShell to run all of this software. It then took GPS coordinate input and spat out an image with a hard coded water level, saving the image to the computer, which I then took a screen shot of as proof.

Rayshader uses XYZ map coordinates to generate location and height data for the map. You can specify the size of the map you want to show (1, 10, 100 miles wide etc.) And you can specify the location with latitude and longitude coordinates.

The code itself instantiated Rayshader in R, called a command to generate an image using latitude, longitude, area, water level, and a few other inputs, and then saved that file to disk.

Future:

Many scientists have created flood maps and, as a climate activist, the public generally does not care. These maps are complex. The science is complex. And these maps don't empower anyone to make any change. Knowing that your new house won't have flood coverage doesn't significantly change a lot of home buying choices because flood coverage is reducing nation wide. The amount of options to choose from aren't great. This would take more the form of an awareness raising art project than a home buying tool.

There are a lot of concerns with this project complexity wise, how to run and fund a server that is using a lot of GPU compute which is expensive. How to run that at scale as well. How to get public interest. How to find datasets that can be mapped to the rayshader visualizer. Connecting the Twitter API to this software. Creating user input that will take an address, validate it, and convert it to Latitude and Longitude coordinates for Rayshader. Deciphering the unit difference for flood height in climate maps and unit height within Rayshader. Meters to an unspecified integer amount. I am not sure if that was within the Rayshader documentation at that point.

These are all solveable.