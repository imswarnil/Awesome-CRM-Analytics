# Awesome CRM Analytics By Swarnil [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of the best resources, tools, and inspiration for CRM analytics.

> Inspired by [awesome](https://github.com/sindresorhus/awesome), contributions welcome!

## Table of Contents
- [Articles & Tutorials](#articles--tutorials)
- [Open Source Tools](#open-source-tools)
- [Libraries](#libraries)
- [Communities & Blogs](#communities--blogs)
- [Datasets](#datasets)
- [Other Awesome Lists](#other-awesome-lists)

## Articles & Tutorials
- [What is CRM Analytics?](https://www.salesforce.com/products/crm-analytics/overview/)
- [CRM Analytics: A Comprehensive Guide](https://www.datapine.com/blog/crm-analytics/)

## Open Source Tools
- [Metabase](https://www.metabase.com/) - Open-source business intelligence.
- [Superset](https://superset.apache.org/) - Modern data exploration and visualization.
- [Redash](https://redash.io/) - Connect and query your data sources.

## Libraries
- [Pandas](https://pandas.pydata.org/) - Python data analysis.
- [Plotly](https://plotly.com/python/) - Interactive analytics & visualization.

## Communities & Blogs
- [r/CRM](https://www.reddit.com/r/CRM/)
- [Customer Think](https://customerthink.com/)

## Datasets
- [Kaggle CRM Datasets](https://www.kaggle.com/search?q=crm+datasets)
- [UCI Machine Learning Repository: Bank Marketing](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)

## Other Awesome Lists
- [Awesome Analytics](https://github.com/onurakpolat/awesome-analytics)
- [Awesome Business Intelligence](https://github.com/awesome-jobs/awesome-business-intelligence)

---
layout: default
title: "Awesome CRM Analytics"
---

<div id="filter-bar" class="field is-grouped is-grouped-multiline">
  <!-- Filter buttons will be inserted here by JS -->
</div>

<div id="resource-list">
  {% for r in site.data.resources %}
    <div class="box resource-card" data-category="{{ r.category }}">
      <span class="icon">{{ r.icon }}</span>
      <a href="{{ r.url }}" target="_blank"><strong>{{ r.title }}</strong></a>
      <p>{{ r.description }}</p>
    </div>
  {% endfor %}
</div>

<script>
  // Filter logic: collect categories, make buttons, show/hide .resource-card
  document.addEventListener("DOMContentLoaded", function() {
    const cards = document.querySelectorAll('.resource-card');
    const categories = Array.from(new Set(Array.from(cards).map(c => c.dataset.category)));
    const filterBar = document.getElementById('filter-bar');
    categories.forEach(cat => {
      const btn = document.createElement('button');
      btn.className = "button is-small";
      btn.innerText = cat;
      btn.onclick = function() {
        cards.forEach(card => {
          card.style.display = (card.dataset.category === cat) ? "" : "none";
        });
      };
      filterBar.appendChild(btn);
    });
    // Add a reset button
    let reset = document.createElement('button');
    reset.className = "button is-small is-light";
    reset.innerText = "Show All";
    reset.onclick = function() { cards.forEach(card => card.style.display = ""); };
    filterBar.appendChild(reset);
  });
</script>