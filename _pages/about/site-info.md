---
layout: single
title: Site Information
modified: "04-01-2015"
permalink: /about/site-info/
---

Odds are if you have ended up on this site you found something interesting or helpful. The following information gives insight on the tools and technologies used on this site. 

## Nerd facts

<article>

<details>
  <summary>This website is built using <u><a href= "http://jekyllrb.com">Jekyll</a></u>.</summary>
  <p>Jekyll is the backbone of this site. It is a powerful engine that allows me to write plain text files. Jekyll then handles converting all the css, liquid tags, code blocks, html snippets, etc. into a pretty static web site. Since this site is static it allows me to quickly modify sections. Also, it is quite fast to serve static pages so response time should always be pretty good. </p>
</details>
<details>
  <summary>All content is written in <u><a href= "http://en.wikipedia.org/wiki/Markdown">Markdown</a></u>.</summary>
  <p>If you are not familiar with markdown it allows me to write plain text in such a way that an engine will be able to transform that text into a rich format like html. All this means I can write using any text editor I want (even vim if I so please) and create content without having to write all those dirty html tags. How many times have you forgotten to add that forward slash on a end tag resulting in a malformed page? </p>
</details>
<details>
  <summary>Hosting for this website is by <u><a href= "https://pages.github.com/">Github Pages</a></u>.</summary>
  <p>Github pages makes hosting a website easy. If Jekyll is my bread, Github Pages is my butter. Hosting a website via Apache, Nginx, or IIS isn't rocket science however by using Github my raw code and static html are right next to each other. As you can imagine this makes things easier to troubleshoot. </p>
</details>
<details>
  <summary>Site code can be found in the follow repo <u><a href= "https://github.com/clburlison/clburlison.github.io">clburlison.github.io</a></u>.</summary>
  <p>I <3 Github. Git is such a nice version control system to work with. All content is publicly accessible for two reasons: 1) I want others to be able to see how this site was created. 2) Sharing this code means if you find something you like you are able to copy/paste working code. With that said please don't blatantly steal written work of mine without crediting me. </p>
</details>
<details>
  <summary>Content delivery network provided by <u><a href= "http://www.cloudflare.com">CloudFlare</a></u>.</summary>
  <p>Cloudflare is much more than just my Content deliver network (CDN). Cloudflare also runs my DNS for the domain clburlison.com, has the ability to directly inject code into my website, gives me a flexible SSL for free, and has some nice built in reporting features. Of those the SSL certificate is likely the coolest. Though I do not have a true SSL setup, content that you view is secure from your end to Cloudflare's servers.<br><br>They also have support to use CNAME alias records which means I am able to point my domain to clburlison.github.io.</p>
</details>
<details>
  <summary>Search bar powered by by <u><a href= "https://swiftype.com/">Swiftype</a></u>.</summary>
  <p>I use to inject the search bar via Cloudflare's build in app support but the results were unreliable. Since then I have now embed the search bar in the header of this site. This might not give me the best results but it is definitely a 10/10 when you realize this is the free tier. The lack of an easy to search is definitely one of the downsides of a static website.</p>
</details>
<details>
  <summary>Content ideas are tracked via <u><a href= "https://github.com/clburlison/clburlison.github.io/issues">Github Issues</a></u> and <u><a href= "https://waffle.io/clburlison/clburlison.github.io">Waffle.io</a></u>.</summary>
  <p><a href="http://waffle.io/clburlison/clburlison.github.io"><img src="https://badge.waffle.io/clburlison/clburlison.github.io.svg?label=ready&title=Ready" alt="Ready"></a>
    <a href="http://waffle.io/clburlison/clburlison.github.io"><img src="https://badge.waffle.io/clburlison/clburlison.github.io.svg?label=in%20progress&title=In%20Progress" alt="In Progress"></a><br>
    At any given time I might have 20 plus ideas or topics that I wish to write about. To keep track of these various ideas I create a Github issue. This allows me to add links or any notes that might be needed for me to understand what I wanted to write about. That means some of my issues might not make sense to you. Waffle.io just gives me a visual to keep me working on one or two topics at a time. The "Ready" tag is for content I am planning on writing about soon. The "In Progress" tag is for content ideas I'm working on right now.<br><br> With that said if you ever have any questions or would like for me to write about a specific topic feel free to create an issue and I will certainly think about it.  </p>
</details>
<details>
  <summary>The theme for this website was created by <u><a href= "https://mademistakes.com/">Michael Rose</a></u>.</summary>
  <p>Michael Rose is a pretty awesome individual who is not only talented in web design but is also know for his drawings using the iOS app Paper. He also maintains a few other awesome Jekyll themes if you are interested. Lastly, his coding is very clear with plenty of code comments to help you understand what you're about to affect by changing values. </p>
</details>
<details>
  <summary>Travis-ci builds my website <u><a href= "https://travis-ci.org/clburlison/clburlison.github.io/builds">Build History</a></u>.</summary>
  <p><a href="https://travis-ci.org/clburlison/clburlison.github.io"><img src="https://travis-ci.org/clburlison/clburlison.github.io.svg?branch=source" alt="Build Status"></a> <br> 
    Travis-ci is a continuos integration application that pulls the contents of my Github repo on every commit I submit to the source branch. The purpose of using Travis to build my Jekyll site, over Github pages, is the ability to use custom plug-ins. When Github pages runs Jekyll sites they run all plug-ins using the <code>--safe</code> for security reasons. Other benefits to using Travis include the ability to have a running record of all my builds. This allows me to know at any given point in time when I broke something. </p>
</details>
<details>
  <summary>User tracking is enabled and provided by <u><a href= "https://www.google.com/analytics/">Google Analytics</a></u>.</summary>
  <p>Google rules the world. I do enable user tracking simply for the purpose of knowing viewership. Knowing which articles are the most popular help me when deciding what content I want to write about next.</p>
</details>
<details>
  <summary>Site comments are provided by <u><a href= "https://disqus.com">Disqus</a></u>.</summary>
  <p>Disqus is a free service. It is widely used. It also allows users to login via different social media sites. What is not to like?</p>
</details>

</article>

<br>

# Why Static?
I really dislike CMS websites. When I see blogs that have code snippets that are a pain to view I cry a little. Sure Jekyll is harder to get the way you want. Customizing it can be very time consuming and confusing. However, the payoff is full control and ultimate flexibility. Also, the extra overhead on my plate to create this website the way I have is both fun and I believe provides the best experience. But what do I know...I just fix Macs.

I have tried both Blogger and Wordpress prior to finally getting latched onto Jekyll. You won't find those sites...