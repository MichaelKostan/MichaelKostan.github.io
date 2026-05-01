---
layout: default
title: The Numbers Don't Lie
---

# The Numbers Don't Lie

*Part 1 of 4 — [Cost of Living in New Zealand](index.md)*

---

## CPI — Consumer Price Index (2015–2027)

Base: June 2017 quarter = 1,000. Forecast from RBNZ MPS February 2026.

<canvas id="cpiChart" width="600" height="300"></canvas>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
// Data matches 01-the-numbers_data.md — CPI table, column: CPI index
// Years 2026-2027 are forecast (RBNZ MPS Feb 2026)
var years  = [2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024, 2025, 2026, 2027];
var actual = [978,  985,  1003, 1019, 1035, 1053, 1095, 1173, 1240, 1277, 1315, null, null];
var forecast = [null, null, null, null, null, null, null, null, null, null, 1315, 1355, 1396];

new Chart(document.getElementById('cpiChart'), {
  type: 'line',
  data: {
    labels: years,
    datasets: [
      {
        label: 'CPI index (actual)',
        data: actual,
        borderColor: 'steelblue',
        backgroundColor: 'transparent',
        spanGaps: false
      },
      {
        label: 'CPI index (forecast)',
        data: forecast,
        borderColor: 'steelblue',
        backgroundColor: 'transparent',
        borderDash: [6, 4],
        spanGaps: false
      }
    ]
  }
});
</script>

---

→ [Data sources and references](01-the-numbers_data.md)
