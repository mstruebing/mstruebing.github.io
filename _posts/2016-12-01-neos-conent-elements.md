---
layout: post
section-type: post
title: 'Example Neos Content Elements #0 Introduction'
category: tech
tags: [ 'neoscms', 'programming', 'tutorial', 'guide' ]
---

I have decided to make tutorials about how to create small Neos content elements and for that purpose I have set up a repository
which you can find [here](https://github.com/mstruebing/neos-content-elements).

I only used the [neos-base-distribution(2.3)](https://github.com/neos/neos-base-distribution) and added a new empty site package.

Then I headed to `/Packages/Sites/MStruebing.ContentElements/Resources/Private/Templates/Page/Default.html`  
and added these line  

```
<link rel="stylesheet" type="text/css" href="{f:uri.resource(path: 'resource://MStruebing.ContentElements/Public/Styles/Main.css')}">
```
To the stylesheets section and these lines

```
<script type="text/javascript"
    src="{f:uri.resource(path: 'resource://MStruebing.ContentElements/Public/JavaScript/App.js')}"
    async>
</script>
```

to the bodyScript sections.

I also created these two files  
`/Packages/Sites/MStruebing.ContentElements/Resources/Public/Styles/Main.css`  
`/Packages/Sites/MStruebing.ContentElements/Resources/Public/JavaScript/App.js`  

Anything else is not modified and I will only modify them within the content element tutorials so you can follow them and have anything in place.

I will edit this post and add a list with every content element I have created.

# Content elements
- [Link Button Fluid]({{site.url}}/tech/2016/12/01/neos-example-button-fluid.html)
