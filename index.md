---
layout: default
title: Anthony Sainez
---

<div id="home">

    <h1>Blog Posts</h1>
    <ul class="posts">
        {% for post in site.posts %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endfor %}
    </ul>

    
    <h1>Highlighted Media</h1>
    <ul class="posts">
        <li><span>27 Jul 2020</span> &raquo; <a href="https://ucm-ling.github.io/articles/aave.html    ">Article: Phonetics</a></li>
        <li><span>11 Apr 2020</span> &raquo; <a href="https://ucm-ling.github.io/articles/writing-sys.html">Article: Writing Systems and Language</a></li>
    </ul>
    

</div>