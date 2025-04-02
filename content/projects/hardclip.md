---
title: Distortion Plugin - Hardclipper
---

Overview:

Create my first audio plugin that can be used in any modern DAW.

![Hardclipping](https://www.fruityloopssamples.com/wp-content/uploads/2013/08/fx_clip1.jpg)

Dev Roadmap:

Read [Designing Audio Effect Plugins in C++ by Will Pirkle](https://www.amazon.com/Designing-Audio-Effect-Plugins-C/dp/1138591939/). Created UI Elements, basic code infrastructure for running DSP software, and audio processing logic that took incoming sound, applied a hardclip effect, and output properly affected sound. Coded first on Linux, finally on Windows. Released useable VST file that worked in both Reaper on Linux and Ableton on Windows.

The biggest technical challenge from a software perspective was performing proper math functions on the audio and learning the math JUCE expected. Audio signals move from 1 to -1 in an oscillating wave. There are exceptions to this, but generally this is the case. 0 is silence. 1 and -1 are the exact same things but when coming out of a speaker they are the same volume but opposite pressure values for the speaker. In mathematical terms I would call this absolute normalization. As in they do eventually become a physical waveform that can be measured in different physical units, but within the computer before they are unitless values from -1 (minimum) to 1 (maximum). JUCE or your DAW will then convert those values to the proper decibel level using other math. There's more to it than that but those are the basics.

After that, the audio was moving from 0 to 1, so though it was audible, it was half as loud even at full volume. Once I implemented the proper math to get the signal to move from -1 to 1, I had to create a hard clip effect.

A hard clip effect takes the top of a waveform and cuts it off. This is a desireable sound effect for musicians. Mathematically it's just a truncate function, but you have to include the proper JUCE setup so that it can do this a bunch of times to each sample in the buffer and automatically adjust the sample rate when the user changes it in their DAW. The other issue is hardclipping things actually makes them quiter. Mathematically 1 truncated to 0.4 is 0.4, so that is your new volume. Its a simple inversion, you just truncate it by a certain amount, and then do inverse multiplication by the same amount. This will get you a waveform that is the same volume with the hardclip effect added.

Hardclipping is supposed to simulate turning the volume knob up on a digital mixer so high that it distorts by cutting the top of the waveform off. This doesn't make it any louder, but due to psychoacoustics, hardclipped waveforms feel louder. Hardclipping by 1db is actually a common mastering trick. It makes the sound feel louder while actually not feeling like any distortion was added. It's very subtle and very awesome.

Unfortunately this code was at the beginning of me learning github and I just pushed an empty folder with the readme files. Then my laptop died. I don't currently have the codebase on hand.

Diary:

I love reading about DSP. It was pretty fun reading through this book and learning the basics. A few small hurtles were learning the data paradigms for live DSP. You can read more on this, but there's sample rate, Nyquist frequency, buffer size, ramping data to new buffer values, connecting with the UI and more. It seems to be a constant that actually writing the software is never seriously challenging, it's always the environment setup and deployment that challenges me.

JUCE is in C++ and is cross platform, however the development ecosystem for it is very different depending on what os you are using. Windows and Mac are close to each other in difficulty. Using a few mainstream code editors like XCode, Visual Studio, or VSCode, you can go from knowing almost nothing to coding and deploying runnable executables within about an hour. JUCE uses it's own IDE Projucer to bundle together the necessary build files so that the resulting C++ files can be built on any system, creating an executable for that environment. It is very close to 1 click in each IDE to pass it on to the next provided your code compiles. Linux is capable of doing the exact same thing, but it takes more setup. JUCE didn't at the time have a significant amount of documentation on the Linux side of things. There were multiple competing standards within the community for IDEs both for coding and for building. Each one required a slightly different setup, and installation for each setup was different depending on your Linux env. I picked Linux because my chromebook weighs a couple pounds, and I can develop anywhere remotely using Digital Ocean. My Windows laptop was a gigantic loud gaming computer with no battery life. But it was completely necessary to code in Windows just due to the speed of iteration and amount of documentation for the build process.

I have learned from many projects that development environment is almost more important than the coding language. There are always going to be significant exceptions but languages like C++ are usually required for performant local hardware such as video games and audio software. Languages like Flutter are purpose built for cross platform build and development cycle within one language. Next.Js and similar are built for flexible, fast, and scalable frontend. Django is built for flexible full stack development. The list goes on, but there's almost no reason IMO to push through a bad dev environment if you can just change it to something that works better. I have spent more time trying to push through non-ideal but theoretically convenient dev environments than I have writing actual code.

Suggestions:

No real suggestions. I would like to code more small scale projects. They are satisfying to build and feel finished when they are done. I learned a lot from this project as well. Enough about DSP to be dangerous, and enough about significant stumbling blocks to move faster next time. My goal is to code FET modelling software and create new and interesting distortion plugins, potential FM synthesis distortion as well.