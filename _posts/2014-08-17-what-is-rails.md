---
layout: post
title:  "What is Rails?"
date:   2014-08-17
categories: post
---

Ruby on Rails (often referred to as simply Rails) is an open source web application framework written in Ruby. It was created by David Heinemeier Hansson while working on the project management tool, Basecamp. He open sourced it in July of 2004.

Is a full-stack framework that emphasizes the use of well-known software engineering patterns and paradigms, including convention over configuration (CoC), don't repeat yourself (DRY), the active record pattern, and model–view–controller (MVC)

Convention over configuration which one hears a lot when one starts working with the framework means a developer only needs to specify unconventional aspects of the application. For example, if there's a class Sale in the model, the corresponding table in the database is called “sales” by default. It is only if one deviates from this convention, such as calling the table “sale”, that one needs to write code regarding these names.

Don't repeat yourself is self explanatory, it aims at reducing repetition of information of all kinds.

The Models, in the MVC, support logic. Views provide a way to interact with the models, and controllers connect the models and the views.

Adopting these paradigms early on has made Rails very popular because it significantly speeds up development time. It is used by hundreds of internet companies, even twitter was built on Ruby on Rails.
