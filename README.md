# Imagine

After wasting many hours picking images for albums and artists in my streaming music application,
[bemused](https://github.com/pfarrell/bemused), I started writing an application to help me pick
the images. It took only a few seconds to realize, I have a the makings of a project that could 
benefit from machine learning. I have now built up a training set of images I have selected and
if I can generate a set of images I reject, then I have built up a perfect training set for an 
 algorithm that could make recommendations or even decide. I've avoided applying ML to things that
 don't really need it, but _this_ is a classic problem.

This project will have a few phases that will be tracked in this repository:

For all my various datasets, I have these steps to do.  I will start with the Music site.

* Phase 1: Generate our training dataset
* Phase 2: Discover and test some image algorithms
* Phase 3: Use the algorithm to pick real images for existing Bemused data
* Phase 4: Determine how good we did

## What are the problems I'm trying to solve?

### Bemused (Music stuff)
1. I would like to automate the way I make decisions about choosing an image for an artist.
  * I have about 1,000 artists with images available.  I have 9,000 without an image.  
  * I need to add images I rejected to my training set
1. I would like to auto-favorite tracks.
  * I have a few years of logs of music that's been streamed on my website.
  * I need to augment my data with some more features about the music itself
1. I would like to auto-generate playlists. Based on my favorite music
  * I will definitely need more information about my music.
1. I would like to deduplicate artists in my library. (may be a non-ML task)
1. I would like to use get suggestions for what I could listen to.

### Pigeon (Web stuff)
1. I would like to automate recommendations on posts I should read from weblogs, [Hacker News](https://news.ycombinator.com),
[Lobsters](https://lobsters.ai)
  * I have years of saved websites from my personal caching site, pigeon
  * I have a bunch of favorites at Hacker News

### Gmail (Email stuff)
1. I would like to prioritize my inbox and find messages I missed over the years
  * I have years of emails I have read and responded to for training

#### Non ML

1. I would like to automate the way I choose images for my music.
1. I would like to deduplicate artists in my library. (may be an ML task)

## Phase 1: Building the datasets

Bemused (formerly PShare) is a personal music project I've been working on since 2003. In the 
beginning, I created it as a simple way for me to download my mp3 files on new computers. Over time,
I bought a flash plugin that allowed me to stream music to my devices. This clearly better. As 
html5 developed, I rewrote the site in Ruby and used JPlayer to use the streaming capabilities 
that became native parts of browser apis.  Somewhere in the 2000's, I started adding support for 
images. At first, I acquired artwork from Amazon when I would import mp3 files.  Later, I added
supprt for manually overriding or setting these images.  As of this writing, I have about a thousand
artist images out of ten thousand in my system.  There are a large number of duplicates, but I still
have a huge amount of artists without images.

