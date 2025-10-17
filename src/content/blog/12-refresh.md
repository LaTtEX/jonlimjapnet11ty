---
type: Post
slug: refresh
title: Refresh
date: '2025-10-17'
description: >-
  Journey away from Ghost and into Eleventy
image: "/images/hiroshimabridge.jpg"
---

For the past 2 years I have been meaning to migrate this site away from its previous platform. I have been using [Ghost CMS](https://docs.ghost.org/) for this site, and while it's beautiful and functional, it's becoming unbearably expensive. With a virtual machine running on Azure, along with all the requisite services, and I had been meaning to move to a static web application to save on costs.

The biggest hurdle by far was migrating data. While it was fairly easy to obtain a JSON file that contained all of your Ghost entries, and with so little content, this was the easiest first step. 

But what do I do with that data? I ended up having to take three more steps.

<!--more-->

## Step 1 - Choose a static website platform to move to

This was by far the most complicated step in the move. In the past couple of years I have been fiddling initially with [Gatsby](https://www.gatsbyjs.com/), as I have successfully created [ineedavisa.ph](https://ineedavisa.ph) with it. However it had a severe limitation that I couldn't turn a blind eye on -- its lackluster support for Markdown. Most Gatsby templates did not come with Markdown support out of the box, and I ended up having to code my own parser into [ineedavisa.ph](https://ineedavisa.ph). 

That was a deal breaker.

After exploring options such as [Hugo](https://gohugo.io/) and [Jekyll](https://jekyllrb.com/), and running across different obstacles; Node being its own dependency hell, and severely outdated or abandoned design themes and templates, I eventually settled on [Eleventy](https://www.11ty.dev/). Eleventy had Markdown and Frontmatter support out of the box, which made creating new entries easy. 

To address the obsolesence issue, I consulted Google Gemini to help me find which CMS had themes that were actively updated, and this is how I settled on the [Eleventy Netlify Blog Starter](https://github.com/netlify-templates/eleventy-blog-starter/) template.

## Step 2 - Moving everything to Eleventy

I forked the Eleventy Blog Starter template to my own repository, deployed it as an Azure static app, set up the corresponding Github actions, and that's how we have this site. Check out the [jonlimjapnet11ty repo on Github](https://github.com/LaTtEX/jonlimjapnet11ty).

I asked Gemini for help to write a script that would convert my Ghost CMS backup into Frontmatter. While the script worked, I ran into a surprising obstacle -- all my previous content were full of [Unsplash](https://unsplash.com/) plugin code, which I used for adding images to my entries. While having Unsplash images on my entries kept them interesting and vibrant, they were causing problems with my builds. 

As these images were dynamically pulled from Unsplash's own servers, they would time out builds for the site, and I had no choice but to remove these images unless I wanted to download and host them all on Github.

## Step 3 - Cleanup

After configuring everything to work on the static web app, it was time to clean the cloud up. I deleted the Ghost CMS virtual machine, all the network infrastructure, public IP addresses, security policies, backups, and storage from Azure. After 2 years of running in circles, I finally was able to move away from Ghost.

That being said it will probably be some time before my next blog entry. But then again, who knows? I just might start writing more again.