---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
widget1:
  title: "Blog & Portfolio"
  url: '/blog/'
  image: widget-1-302x182.jpg
  text: 'Welcome... to my blog; I Started in March 2019. In this blog I present information on System Engineering and Home Automation Topics. I hope you enjoy the blog! Thanks for stopping by!'
widget2:
  title: "AndyMOTE Project"
  url: 'https://andymote.abondservices.com/'
  image: andymote.png
  text: '<em>AndyMOTE: </em>Control all your infra-red devices from one Mobile App <br> The AndyMOTE App provides a single interface for multiple infra-red remote controls.'

#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
#callforaction:
#  url: https://tinyletter.com/feeling-responsive
#  text: Inform me about new updates and features ›
#  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---

<div id="videoModal" class="reveal-modal large" data-reveal="">
  <div class="flex-video widescreen vimeo" style="display: block;">
    <iframe width="1280" height="720" src="https://www.youtube.com/embed/3b5zCFSmVvU" frameborder="0" allowfullscreen></iframe>
  </div>
  <a class="close-reveal-modal">&#215;</a>
</div>
