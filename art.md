---
layout: term
title: art
permalink: /art/
# --------------------------------------------------------
# UPDATE YOUR FILENAMES HERE
# --------------------------------------------------------
illustrations:
  - file: pumpkin_receipt_art.jpg
    title: "Pumpkin Receipt Art"
  - file: cookie_receipt_art.png
    title: "Cookie Receipt Art"
  - file: inktober_1_poison_2018.png
    title: "Inktober 2018"
  - file: valentines_day_2022.png
    title: "Valentines Day 2022"

canva_projects:
  - file: social_portfolio_carousel_v1.gif
    path: social_portfolio_carousel_v1/
    title: "Social Portfolio Carousel"
  - file: daniel_heinzelman_the_header_v1.gif
    path: the_header_a_study_in_motion/
    title: "The Header - A Study in Motion"

canva_docs:
  - file: case_study_workflow_optimization_v1.pdf
    path: case_study_workflow_optimization_v1/
    thumbnail: case_study_workflow_optimization_v1.jpg
    title: "Case Study: Workflow Optimization"
---

ART & Design
========

Here's some of the work that I've created.

Browse my: 
- [Illustrations](#illustration)
- [Canva design work](#design--canva)

<h2 id="illustration">ILLUSTRATION</h2>

<style>
/* A Cleaner, "Terminal" Grid */
.art-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 30px;
  margin-bottom: 50px;
}

.art-item {
  /* Removed the white background and border to match the theme */
  text-align: left; 
}

.art-item img {
  width: 100%;
  height: auto;
  display: block;
  margin-bottom: 10px;
  /* Adds a slight border to images only, typical of retro sites */
  border: 1px solid #000; 
}

.art-item p {
  margin: 0;
  font-family: inherit; /* Uses the site's terminal font */
  font-size: 0.9em;
  color: #000;
  font-weight: bold;
}
</style>

<div class="art-grid">
  {% for img in page.illustrations %}
    <div class="art-item">
      <a href="/images/art/illustrations/{{ img.file }}" target="_blank">
        <img src="/images/art/illustrations/{{ img.file }}" alt="{{ img.title }}">
      </a>
      <p>{{ img.title }}</p>
    </div>
  {% endfor %}
</div>

<h2 id="design--canva">DESIGN / CANVA</h2>

<div class="art-grid">
  {% for img in page.canva_projects %}
    <div class="art-item">
      <a href="/images/art/canva/{{ img.path }}{{ img.file }}" target="_blank">
        <img src="/images/art/canva/{{ img.path }}{{ img.file }}" alt="{{ img.title }}">
      </a>
      <p>{{ img.title }}</p>
    </div>
  {% endfor %}
  {% for doc in page.canva_docs %}
    <div class="art-item">
      <a href="/images/art/canva/{{ doc.path }}{{ doc.file }}" target="_blank">
        <img src="/images/art/canva/{{ doc.path }}{{ doc.thumbnail }}" alt="{{ doc.title }}">
      </a>
      <p>{{ doc.title }} (PDF)</p>
    </div>
  {% endfor %}
</div>