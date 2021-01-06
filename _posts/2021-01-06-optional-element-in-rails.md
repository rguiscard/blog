---
toc: true
layout: post
description: Conditionally render elements based on the presense of variables
categories: [rails]
title: Optional elements in Rails
---
It is quite often to conditionally render certain elements in Rails. This example is in [slim syntax](http://slim-lang.com/):

    - if flash[:notice].present?
      div.toast.toast-warning
        = flash[:notice]

Can we do better without the `if` ? Try this:

    - flash[:notice]&.tap do |x|
      div.toast.toast-warning = x

