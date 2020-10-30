---
layout: article
title:  "Deep Dives"
excerpt: "Best Practices and Deep Dives for Algorithm Development and Model Deployment"
categories: algorithm-development
tags: [algo-dev]
show_related: false
author: steph_kim
image:
  teaser: /icons/algo.svg
---

<div class="row lang-tile-container">
  {% assign post_title = "Local Development: emulating the Algorithmia execution environment" %}
  <div class="col-xs-6 col-sm-6 col-md-4" style="text-decoration: none!important;">
    <a href="{{site.baseurl}}/algorithm-development/advanced-algorithm-development/local-development" title="{{ post_title }}" class="post-teaser lang-tile lang-tile-large" style="text-decoration: none!important;">
      <div style="min-height:60%"><img class="larger_icon" src="{{site.cdnurl}}{{site.baseurl}}/images/post_images/local_development/local_development.png" alt="icon" itemprop="image"></div>
      <p itemprop="name" class="lg text-primary">{{ post_title }}</p>
    </a>
  </div>
  {% assign post_title = "Inspecting Algorithms: determining the live list of packages / dependencies" %}
  <div class="col-xs-6 col-sm-6 col-md-4" style="text-decoration: none!important;">
    <a href="{{site.baseurl}}/algorithm-development/advanced-algorithm-development/list-packages" title="{{ post_title }}" class="post-teaser lang-tile lang-tile-large" style="text-decoration: none!important;">
      <div style="min-height:60%"><img class="larger_icon" src="{{site.cdnurl}}{{site.baseurl}}/images/post_images/list_packages/dependencies.png" alt="icon" itemprop="image"></div>
      <p itemprop="name" class="lg text-primary">{{ post_title }}</p>
    </a>
  </div>
  {% assign post_title = "Multithreading: call many Algorithms in parallel" %}
  <div class="col-xs-6 col-sm-6 col-md-4" style="text-decoration: none!important;">
    <a href="{{site.baseurl}}/algorithm-development/advanced-algorithm-development/multithreading" title="{{ post_title }}" class="post-teaser lang-tile lang-tile-large" style="text-decoration: none!important;">
      <div style="min-height:60%"><img class="larger_icon" src="{{site.cdnurl}}{{site.baseurl}}/images/post_images/multithreading/multithreading.png" alt="icon" itemprop="image"></div>
      <p itemprop="name" class="lg text-primary">{{ post_title }}</p>
    </a>
  </div>
  {% assign post_title = "Batch Processing: efficiently run predictions on large data volumes" %}
  <div class="col-xs-6 col-sm-6 col-md-4" style="text-decoration: none!important;">
    <a href="{{site.baseurl}}/algorithm-development/advanced-algorithm-development/batch-processing" title="{{ post_title }}" class="post-teaser lang-tile lang-tile-large" style="text-decoration: none!important;">
      <div style="min-height:60%"><img class="larger_icon" src="{{site.cdnurl}}{{site.baseurl}}/images/post_images/batch-processing/batch_processing.png" alt="icon" itemprop="image"></div>
      <p itemprop="name" class="lg text-primary">{{ post_title }}</p>
    </a>
  </div>
  {% assign post_title = "Examples on how to remove performance bottlenecks, from bandwidth to compute" %}
  <div class="col-xs-6 col-sm-6 col-md-4" style="text-decoration: none!important;">
    <a href="{{site.baseurl}}/algorithm-development/advanced-algorithm-development/dealing-with-bottlenecks" title="{{ post_title }}" class="post-teaser lang-tile lang-tile-large" style="text-decoration: none!important;">
      <div style="min-height:60%"><img class="larger_icon" src="{{site.cdnurl}}{{site.baseurl}}/images/post_images/dealing_with_bottlenecks/dealing_with_bottlenecks.png" alt="icon" itemprop="image"></div>
      <p itemprop="name" class="lg text-primary">{{ post_title }}</p>
    </a>
  </div>
</div>
