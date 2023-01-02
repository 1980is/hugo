---
title: "Shortcodes Test"
date: 2022-12-22T19:39:09Z
draft: true
showcomments: true
tags: ["personal", "linux", "win"]
categories: ["Linux"]
featured_image: "merc.jpg"
---

<!-- {{< myshortcode color="blue" >}} -->

<!-- {{< myshortcode src="images/oldman.jpg" >}} -->

{{ $image := resources.Get "images/oldman.jpg" }}
<img src="{{ $image.RelPermalink }}" />

