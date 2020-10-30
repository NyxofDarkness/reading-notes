From the Duckett HTML book:

# Chapter 16: “Images” (pp.406-427)

> control the size and alignment of your images using CSS rules, keeping them out of the HTML markup
1. specify the size and alignment of an image
2. add backround images to boxes
3. create image rollovers in CSS
4. images can be aligned both horizontally and vertically
5. backround images can be attached to any box on the page, and can be repeated or appear just once.
6. you can create image rollover effects by moving the background position of an image
7. to reduce the number of images your browser has to load, you can use sprites page 417

# Chapter 19: “Practical Information” (476-492)

1. search engine optimization helps people find your site from popular search engines
2. tools like google analytics allow you to see how many people visit your site, how they find it, and what they dle when they get there. 
3. to put your site on the web you need to get a domain name and web hosting
4. FTP programs allow you to transfer files from your local computer to the web server

# This MDN article on audio and video elements

1. HTML5 allows you to embed `<video>` and `<audio>` into your websites

An example of this is action:
`<video controls>`
 ` <source src="rabbit320.mp4" type="video/mp4">`
  `<source src="rabbit320.webm" type="video/webm">`
 ` <p>Your browser doesn't support HTML5 video. Here is a <a href="rabbit320.mp4">link to the video</a> instead.</p>`
`</video>`

2. part of HTML5 
`HTMLMediaElement.play()`, `HTMLMediaElement.pause()`,

this interface is available to audio and video elements and allows you to control the content programmatically

Good note: The `<video>` element contains two `<source>` elements so that different formats can be loaded depending on the browser viewing the site.

[click here for examples and more!](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs)

# Chapter 9: pages 201-206 only. Flash is no longer supported by many browsers but is an important part of history.

The history of flash, video, and audio.

We just learned about how to use HTML% to embed audio and video links, but flash is what was very popular in the past for adding these elements. since 1990's it has been a popular tool for creating animations and flash movies. 
Since 2005 the technology has been expanded, so even though flash does animations easily, newer technologies such as HTML5 have made it easier than ever to include video and audio on your website.