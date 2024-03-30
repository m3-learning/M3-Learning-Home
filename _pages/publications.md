---
layout: page
permalink: /publications/
title: publications
years: [2023, 2022, 2021, 2020, 2019, 2018, 2017, 2016, 2015, 2014]
description: 
nav: true
nav_order: 1
---

<div class="filters">
  <div class="year-selector">
    <label for="yearSelect">Select a Year: </label>
    <select id="yearSelect" onchange="filterPublications()">
      <option value="all">All Years</option>
      <!-- JavaScript will populate years here -->
    </select>
  </div>

  <!-- Publication Type Selector -->
  <div class="type-selector">
    <label for="typeSelect">Select a Publication Type: </label>
    <select id="typeSelect" onchange="filterPublications()">
      <option value="all">All Types</option>
      <option value="article">article</option>
      <option value="conference">Conference Papers</option>
      <option value="book">Book Chapters</option>
      <!-- Add more types as needed -->
    </select>
  </div>
</div>

<script>
  const minYear = 2010; // Adjust based on your data
  const maxYear = new Date().getFullYear(); // Current year
  const yearSelect = document.getElementById('yearSelect');
  for (let year = maxYear; year >= minYear; year--) {
    const option = document.createElement('option');
    option.value = option.textContent = year;
    yearSelect.appendChild(option);
  }
</script>

<script>
function filterPublications() {
  const selectedYear = document.getElementById('yearSelect').value;
  const selectedType = document.getElementById('typeSelect').value;
  const entries = document.querySelectorAll('.row .col-sm-8');
  
  entries.forEach(entry => {
    const entryYear = entry.getAttribute('data-year');
    const entryType = entry.getAttribute('data-type'); // Ensure your entries have this attribute
    const matchYear = selectedYear === 'all' || entryYear === selectedYear;
    const matchType = selectedType === 'all' || entryType === selectedType;

    if (matchYear && matchType) {
      entry.parentElement.style.display = '';
    } else {
      entry.parentElement.style.display = 'none';
    }
  });
}
</script>

<!-- _pages/publications.md -->
<div class="publications">

{% bibliography %}

</div>
