---
layout: team
title: Team
description: Who we are
permalink: /team/
---

<!-- Blog Filters -->
<div class="mb-3">
  <label for="blog-filter" class="form-label">Filter by Blog Type:</label>
  <select id="blog-filter" class="form-select">
    <option value="all">All</option>
    <option value="Admin">Admin</option>
    <option value="Developer">Developer</option>
    <!-- Add more blog types here -->
  </select>
</div>

<!-- Blog List -->
<div class="row" id="blog-list">
  {% for blog in site.data.blogs %}
    <div class="col-md-4 mb-4 blog-item" data-type="{{ blog.type }}">
      <div class="card h-100">
        <img src="{{ blog.image | relative_url }}" class="card-img-top" alt="{{ blog.name }}">
        <div class="card-body">
          <h5 class="card-title">{{ blog.name }}</h5>
          <p class="card-text">{{ blog.description }}</p>
          <p class="card-text"><strong>Owner:</strong> {{ blog.owner }}</p>
        </div>
      </div>
    </div>
  {% endfor %}
</div>

<script>
  // Filter blogs based on selected blog type
  document.getElementById('blog-filter').addEventListener('change', function () {
    var selectedType = this.value;

    if (selectedType === 'all') {
      // Show all blogs
      document.querySelectorAll('.blog-item').forEach(function (blog) {
        blog.style.display = 'block';
      });
    } else {
      // Filter blogs based on selected type
      document.querySelectorAll('.blog-item').forEach(function (blog) {
        var blogType = blog.getAttribute('data-type');
        if (blogType === selectedType) {
          blog.style.display = 'block';
        } else {
          blog.style.display = 'none';
        }
      });
    }
  });
</script>

On this page you can list team members by defining them in [`_data/team.yml`](https://raw.githubusercontent.com/peterdesmet/petridish/main/_data/team.yml).
