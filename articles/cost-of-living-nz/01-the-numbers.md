---
layout: default
title: The Numbers Don't Lie
---

# The Numbers Don't Lie

*Part 1 of 4 — [Cost of Living in New Zealand](index.md)*

---

Both series indexed to 2015 = 100. Click a label to show or hide that series including its forecast.

<canvas id="chart" width="600" height="300"></canvas>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
// -------------------------------------------------------
// DATA — matches 01-the-numbers_data.md exactly
// CPI: raw index values (base: Jun 2017 = 1000)
// Income: median weekly NZD
// Both reindexed to 2015 = 100 for comparison
// CPI 2015 base = 978, Income 2015 base = 595
// Forecast values appended — 2026 and 2027
// -------------------------------------------------------

var years = [2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024, 2025, 2026, 2027];

// CPI indexed to 2015=100 — actual then forecast joined as one line
// forecast starts at 2025 to connect visually
var cpiData = [100.0, 100.7, 102.6, 104.2, 105.8, 107.7, 111.9, 119.9, 126.8, 130.6, 134.5, 138.5, 142.7];
var cpiSegments = [
  false, false, false, false, false, false, false, false, false, false, false, true, true
]; // true = forecast segment

// Income indexed to 2015=100
// 2015-2018 estimated, 2021 derived — see data file notes
var incData = [100.0, 102.9, 106.2, 110.1, 118.7, 109.6, 129.4, 142.5, 154.8, 161.2, 161.2, 164.4, 167.7];
var incSegments = [
  false, false, false, false, false, false, false, false, false, false, false, true, true
];

// datasets 0 = CPI, 1 = Income
// toggling index 0 hides/shows both CPI datasets (actual + forecast)
new Chart(document.getElementById('chart'), {
  type: 'line',
  data: {
    labels: years,
    datasets: [
      {
        label: 'CPI',
        data: cpiData,
        borderColor: 'steelblue',
        backgroundColor: 'transparent',
        segment: {
          borderDash: function(ctx) {
            return cpiSegments[ctx.p1DataIndex] ? [6, 4] : [];
          }
        },
        spanGaps: false
      },
      {
        label: 'Income',
        data: incData,
        borderColor: 'darkorange',
        backgroundColor: 'transparent',
        segment: {
          borderDash: function(ctx) {
            return incSegments[ctx.p1DataIndex] ? [6, 4] : [];
          }
        },
        spanGaps: false
      }
    ]
  },
  options: {
    plugins: {
      legend: {
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
