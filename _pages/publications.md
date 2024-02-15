---
layout: page
permalink: /publications/
title: publications
years: [2023, 2022, 2021, 2020, 2019, 2018, 2017, 2016, 2015, 2014]
description: 
nav: true
nav_order: 1
---

<div class="year-selector">
  <label for="yearSelect">Select a Year: </label>
  <select id="yearSelect" onchange="filterByYear()">
    <option value="all">All Years</option>
    <!-- JavaScript will populate years here -->
  </select>
</div>
<script>
  const minYear = 2010; // Adjust based on your data
  const maxYear = new Date().getFullYear(); // Current year
  const select = document.getElementById('yearSelect');
  for (let year = maxYear; year >= minYear; year--) {
    const option = document.createElement('option');
    option.value = option.textContent = year;
    select.appendChild(option);
  }
</script>

<script>
function filterByYear() {
  const selectedYear = document.getElementById('yearSelect').value;
  const entries = document.querySelectorAll('.row .col-sm-8');
  
  entries.forEach(entry => {
    const entryYear = entry.getAttribute('data-year');
    if (selectedYear === 'all' || entryYear === selectedYear) {
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
