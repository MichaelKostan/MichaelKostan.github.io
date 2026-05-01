---
layout: default
title: The Numbers Don't Lie
---

# The Numbers Don't Lie

*Part 1 of 4 — [Cost of Living in New Zealand](index.md)*

---

Both series indexed to 2015 = 100 so they can be compared on one chart.
Click a label in the legend to show or hide that line.

<canvas id="chart" width="600" height="300"></canvas>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
// -------------------------------------------------------
// DATA — matches 01-the-numbers_data.md exactly
// CPI: raw index values from data file (base: Jun 2017 = 1000)
// Income: median weekly NZD from data file
// Both reindexed here to 2015 = 100 for comparison
// CPI 2015 base = 978, Income 2015 base = 595
// -------------------------------------------------------

var years = [2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024, 2025, 2026, 2027];

// CPI indexed to 2015=100  (raw / 978 * 100)
var cpiActual    = [100.0, 100.7, 102.6, 104.2, 105.8, 107.7, 111.9, 119.9, 126.8, 130.6, 134.5, null,  null ];
var cpiForecast  = [null,  null,  null,  null,  null,  null,  null,  null,  null,  null,  134.5, 138.5, 142.7];

// Income indexed to 2015=100  (raw / 595 * 100)
// 2015-2018 estimated, 2021 derived — see data file notes
var incActual    = [100.0, 102.9, 106.2, 110.1, 118.7, 109.6, 129.4, 142.5, 154.8, 161.2, 161.2, null,  null ];
var incForecast  = [null,  null,  null,  null,  null,  null,  null,  null,  null,  null,  161.2, 164.4, 167.7];

new Chart(document.getElementById('chart'), {
  type: 'line',
  data: {
    labels: years,
    datasets: [
      {
        label: 'CPI (actual)',
        data: cpiActual,
        borderColor: 'steelblue',
        backgroundColor: 'transparent',
        spanGaps: false
      },
      {
        label: 'CPI (forecast)',
        data: cpiForecast,
        borderColor: 'steelblue',
        backgroundColor: 'transparent',
        borderDash: [6, 4],
        spanGaps: false
      },
      {
        label: 'Income (actual)',
        data: incActual,
        borderColor: 'darkorange',
        backgroundColor: 'transparent',
        spanGaps: false
      },
      {
        label: 'Income (forecast)',
        data: incForecast,
        borderColor: 'darkorange',
        backgroundColor: 'transparent',
        borderDash: [6, 4],
        spanGaps: false
      }
    ]
  },
  options: {
    plugins: {
      legend: {
        // clicking a legend item toggles that dataset on/off
        onClick: function(e, legendItem, legend) {
          var index = legendItem.datasetIndex;
          var ci = legend.chart;
          if (ci.isDatasetVisible(index)) {
            ci.hide(index);
          } else {
            ci.show(index);
          }
        }
      }
    }
  }
});
</script>

---

→ [Data sources and references](01-the-numbers_data.md)
