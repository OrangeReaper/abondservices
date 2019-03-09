---
layout: page
sidebar: left
subheadline: Home Automation
title:  "Movement detection using the RCWL-0516 and HC-SR501 sensors"
teaser: "A novel solution to false triggering."
breadcrumb: true
tags:
    - movement detection
    - rcwl-0516
    - hc-sr501
categories:
    - Home_Automation
image:
    thumb: movement-detection-thumb.png
    title: movement-detection.png
    caption_url: http://unsplash.com
---
Using [Home Assistant](https://www.home-assistant.io/) My objective was to implement motion detection in my hallway and, if it is dark, switch on a light until motion is no longer detected. My first attempt was with the HC-SR501; this “worked” but I had issues with the light turning on upto 3 times an hour when no-one was present in the hallway. Next I tried the RCWL-0516; this “worked” as well as the HC-SR501 (ie false triggering several times an hour).

So, in my experience, both the RCWL-0516 and the HC-SR501 reliably detect ‘real movement’ but, a quick search on the internet shows false triggering to be a common problem with them; ie they are both very cheap but suffer from this downside.

HC-SR501 set up: Counterintuitively, With some experimentation, I discovered that the false triggering decreased when the sensitivity was increased; I slowly increased the sensitivity until the false triggers occurred several hours apart and set the ‘delay’ potentiometer to around 3 seconds.

RCWL-0516 setup: “solutions” offered around the web tend to revolve around adding pi filters into the power lines, use of ferrite beads or ‘metal boxing’. Some users reporting success with this, and others report failure. After some experimentation I found that the positioning of the unit was everything; moving the RCWL-0516 an inch or two would reduce or increase the false trigger rate from 4-5 times a minute to less than once an hour. In particular moving the device away from a nearby radiator and mirror reduced false triggering significantly. No pi filter, no ferrite bead and no metal boxing. I was again able to get to the position where false triggers were several hours apart.

However, I don’t want any false triggers in my application, and using a single device (RCWL-0516 or HC-SR501) I was still seeing the occasional false trigger turning on my hallway light.

Not happy with this, I came up with the idea to use the RCWL-0516 and the HC-SR501 in tandem. I didn’t come across this idea anywhere during my search for a solution, I thought I would post it here for anyone to take advantage of.

The basic idea is to place both devices in the field of interest and use conditional logic in the automations to filter out the false triggers. In other words, if one device triggers then, before any action is taken a check is made to see if the other device has also triggered. Assuming the ‘false triggers’ are random events, this should drastically reduce the probability of a false detection because both devices have to trigger at the same time before any action is taken; and this should only happen during ‘real movement’.

*Example: the probability of two events occurring at the same time is calculated by multiplying their respective probabilities together; assume trigger pulse of each device is 3secs and each device sends a ‘false trigger’ 3 times an hour; this gives a probability of ‘false trigger’ of 9:3600 (or 9 seconds in 3600); multiply by itself and this gives us 81:12960000 or once every 160,000 seconds (44.44 hours).*

The approach worked perfectly, I only see the light turn on when there is ‘real movement’ in the hallway. I’m happy that I have a solution that works with no soldering involved!

You can see my setup [here](https://github.com/OrangeReaper/homeassistant).

To discuss this post goto the [Home Assistant Community](https://community.home-assistant.io/t/movement-detection-using-the-rcwl-0516-and-hc-sr501-sensors/104074)

