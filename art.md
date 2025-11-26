---
layout: page
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
    title: "Social Portfolio Carousel"
  - file: daniel_heinzelman_the_header.gif
    title: "The Header - A Study in Motion on Canva"
  - file: case_study_workflow_optimzation_v1.pdf
    title: "A Case Study of Workflow Optimization"
---

ART (2D)
========

Here's some of the art that I have made.

Browse my illustrations and design work below.

## ILLUSTRATION

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

## DESIGN / CANVA

<div class="art-grid">
  {% for img in page.canva_projects %}
    <div class="art-item">
      <a href="/images/art/canva/{{ img.file }}" target="_blank">
        <img src="/images/art/canva/{{ img.file }}" alt="{{ img.title }}">
      </a>
      <p>{{ img.title }}</p>
    </div>
  {% endfor %}
</div>