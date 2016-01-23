---
layout: post
title: "Image Captioning - Baby steps - Types of images"
description: ""
category: [technical]
tags: [ai , ml, image captions]
---
{% include JB/setup %}

Since I am researching on image captioning and have avid interest in photography I first decided to understand how many types of images are there. There are so many questions that came up from them.

- Can we understand that this is an image taken from a kaleidoscope or is it a panoramic photo. 
- Is it a sunrise or a sunset?
- Is clip art image recognition possible and how
- How to differentiate between past and present photos of same object in the same environment. 
- Can the computer just classify correct what kind an image is ? What category an image belongs to? 
- How to differentiate the [vintage print](http://www.wikiwand.com/en/Vintage_print) from other duplicates. 

When I am reading the papers I think I can do this, this problem looks approachable, but as soon as I start searching for different types of images, boy! I should have known that there are 50 different kinds, I thought of processing what kinds of questions are possible for each of these. These are questions that I will try to answer way into the future because first I need to write them all down first. 

The artificial would include comics, clip arts, paintings, sketches (what about real life 3D sketches and that actual 3D object assuming that the sketch is really real-life) I think these are some kind of outliers but it is still worth looking into. 

Taking wikipedia as the state of art (there may be something else but let me start with wiki), it lists 80 categories. Here are some of the features of these items that I can think of (there may be many more) So, can a RNN identify all these? Let me go check!


- Nature Photography - natural scenery + anything outdoors 
    - [Cloudscape photography](http://www.wikiwand.com/en/Cloudscape_photography)
    - [Geophotography](http://www.wikiwand.com/en/Geophotography) which focuses on the landscape structures, the soil, rock formation
- Wildlife Photography 
    - animals in their natural environment
- Black and White   
    - contrast and shadows are played around with
- Wedding Photography
- HDR Photography
- Travel Photography
- Time Lapse Photography
    - [Long-exposure photography](http://www.wikiwand.com/en/Long-exposure_photography)
    - Flash Photography
    - [Lomography](http://www.wikiwand.com/en/Lomography) 
    - [Fireworks photography](http://www.wikiwand.com/en/Fireworks_photography)
- Macro Photography (brings out the minute details, which might be very difficult to learn, EG is this an eye of a ant or bee)
- Underwater Photography
- HI Speed Photography - might be very difficult to decipher what the elements actually are
- [Panoramic Photography](https://en.wikipedia.org/wiki/Panoramic_photography) - difficult to understand what elements are 
- [Motion / blur / Action / High Speed Photography](https://en.wikipedia.org/wiki/High-speed_photography)
- Infrared Photography
- Infant / new born Photography
- Past and Present Photography
- Sunrise / Sunset Photography
- Rain Photography
- Color Photography
- Storm Photography (can we differentiate between hurricane, tornado, water spout, blizzard, avalanche)
- Rainbow Photography
- Bird Photography
- [Night Photography]()
- [Astrophotography]() - of the skies, we might not even have a large enough dataset for them. If we can get something to train on then maybe we can achieve trying to be able to learn.
    -[Satellite imagery](http://www.wikiwand.com/en/Satellite_imagery) 
    - [Kirlian photography](http://www.wikiwand.com/en/Kirlian_photography) for corona discharge 
- Photojournalism
- Comics Clip arts paintings (if its a really good 3d sketch or just the actual person)
- [Stock Photography]()
- [Vernacular Photography]()
- [Abstract Photography](https://en.wikipedia.org/wiki/Abstract_photography) (does not have any relation with the natural environment)
- [Aerial Photography](http://www.wikiwand.com/en/Aerial_photography)
- [Analog Photography]() but this cant really be used because it focuses on the type of device which is used for photography, which is mainly analog devices which use films. These days digital images are used. Also the input to the computer will be digital so in one way or the other the image has to be digitized. 
- [Architectural Photography](http://www.wikiwand.com/en/Architectural_photography)
- [Aviation Photography](http://www.wikiwand.com/en/Aviation_photography)
- [Banquet Photography](https://en.wikipedia.org/wiki/Banquet_photo)
- Fashion Photography
    - Beauty Photography - display usually the human face in different lighting and colors (with cosmetic)
    - [Boudoir photography](http://www.wikiwand.com/en/Boudoir_photography)
- [Medical photography](http://www.wikiwand.com/en/Medical_photography)
    - [Burns Archive](http://www.wikiwand.com/en/Burns_Archive)
    - [Post-mortem photography](http://www.wikiwand.com/en/Post-mortem_photography)
- [Close-up Photography](http://www.wikiwand.com/en/Close-up)
    - [Fancy portrait](http://www.wikiwand.com/en/Fancy_portrait) 
- [Concert Photography](https://en.wikipedia.org/wiki/Concert_photography)
- [Film still ](http://www.wikiwand.com/en/Film_still) - What about a problem of giving a single image and being able to answer which movie it came from. 
    - [Tele-snaps](http://www.wikiwand.com/en/Tele-snaps) 
- [Food photography](http://www.wikiwand.com/en/Food_photography) - identify what kind of food, native to what place, what might be the usual ingredients, give some recipes
- [Forensic photography](http://www.wikiwand.com/en/Forensic_photography)
- [Genre art](http://www.wikiwand.com/en/Genre_art) brings about elements of everyday life
    - [Lifestyle photography](http://www.wikiwand.com/en/Lifestyle_photography) 
    - [Secret photography](http://www.wikiwand.com/en/Secret_photography)
    - [Candid photography](http://www.wikiwand.com/en/Candid_photography)


























