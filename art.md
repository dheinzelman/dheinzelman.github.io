---
layout: page
title: art
permalink: /art/
# --------------------------------------------------------
# LIST YOUR IMAGES BELOW
# --------------------------------------------------------
illustrations:
  - file: pumpkin_receipt_art.png
    title: "Pumpkin Receipt Art for Barnes & Noble, Inc."
  - file: cookie_receipt_art.png
    title: "Cookie Receipt Art for Barnes & Noble, Inc."
  - file: inktober_1_poison_2018.png
    title: "Inktober 2018 Drawing"
  - file: valentines_day_2022.png
    title: "Valentines Day 2022 Drawing"

canva_projects:
  - file: social_portfolio_carousel_v1.gif
    title: "Social Media Post - Portfolio Carousel"
  - file: daniel_heinzelman_the_header_v1.gif
    title: "The Header - A Study in Motion"
  - file: case_study_workflow_optimization_v1.pdf
    title: "One-Pager - Case Study - Workflow Optimization"
---

<style>
/* This CSS creates the Grid Layout */
.art-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  margin-bottom: 40px;
}

.art-item {
  border: 1px solid #eee;
  padding: 10px;
  text-align: center;
  border-radius: 5px;
  background: #fff;
}

.art-item img {
  width: 100%;
  height: auto;
  display: block;
  margin-bottom: 10px;
  border-radius: 3px;
}

.art-item p {
  margin: 0;
  font-size: 0.9em;
  color: #666;
}
</style>

## Illustrations

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

## Canva Projects

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