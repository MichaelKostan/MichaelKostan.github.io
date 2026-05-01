---
layout: default
title: The Numbers Don't Lie
description: Ten years of cost increases mapped against income growth — sourced directly from Stats NZ with confidence levels shown for every data point.
---

<style>
/* ── PAGE STYLES ─────────────────────────────── */
:root {
  --ink:       #0e0d0b;
  --paper:     #f6f1e9;
  --paper2:    #ede7da;
  --rule:      #c8c0b0;
  --accent:    #c13a2b;
  --accent2:   #1a4f72;
  --gold:      #a86c1a;
  --muted:     #6b6354;
  --verified:  #1a6644;
  --estimated: #7a5c18;
}

.nz-article { font-family: 'Georgia', serif; max-width: 780px; margin: 0 auto; }

.series-nav {
  display: flex; gap: 0; margin-bottom: 40px;
  border: 1px solid var(--rule); border-radius: 4px; overflow: hidden;
  font-family: 'Courier New', monospace; font-size: 11px;
}
.series-nav a, .series-nav span {
  flex: 1; padding: 10px 12px; border-right: 1px solid var(--rule);
  text-decoration: none; color: var(--muted); line-height: 1.3;
}
.series-nav a:last-child, .series-nav span:last-child { border-right: none; }
.series-nav .current { background: var(--ink); color: #f6f1e9; }
.series-nav a:hover:not(.current) { background: var(--paper2); }
.nav-num { display: block; font-weight: 600; margin-bottom: 2px; opacity: 0.6; }
.current .nav-num { opacity: 0.5; }

.kicker {
  font-family: 'Courier New', monospace; font-size: 11px;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--accent); margin-bottom: 16px;
}

.lede {
  font-size: 18px; color: var(--muted); line-height: 1.65;
  font-style: italic; margin-bottom: 32px;
  border-left: 3px solid var(--rule); padding-left: 20px;
}

/* stat squares */
.stat-grid {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1px; background: var(--rule); border: 1px solid var(--rule);
  border-radius: 6px; overflow: hidden; margin: 32px 0;
}
.stat-cell { background: var(--paper); padding: 18px 20px; }
.stat-cell.dark { background: var(--ink); }
.stat-val {
  font-family: Georgia, serif; font-size: 34px;
  font-weight: 700; line-height: 1; margin-bottom: 6px;
}
.stat-lbl {
  font-family: 'Courier New', monospace; font-size: 10px;
  letter-spacing: 0.06em; text-transform: uppercase;
  color: var(--muted); line-height: 1.4;
}
.stat-cell.dark .stat-lbl { color: rgba(246,241,233,0.4); }

/* insight bar */
.insight-bar {
  background: var(--ink); color: #f6f1e9; border-radius: 6px;
  padding: 18px 22px; font-size: 15px; line-height: 1.65;
  margin: 28px 0; font-style: italic;
}
.insight-bar strong { font-style: normal; color: #f5c842; }

/* series header */
.series-hdr {
  display: flex; align-items: center; gap: 16px;
  margin: 48px 0 24px; padding-top: 32px;
  border-top: 2px solid var(--ink);
}
.series-num {
  font-family: Georgia, serif; font-size: 48px;
  font-weight: 700; color: var(--rule); flex-shrink: 0; line-height: 1;
}
.series-meta { flex: 1; }
.series-tag {
  font-family: 'Courier New', monospace; font-size: 10px;
  letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted);
}
.series-title { font-size: 20px; font-weight: 700; margin-top: 2px; }
.status-badge {
  font-family: 'Courier New', monospace; font-size: 10px;
  padding: 4px 10px; border-radius: 3px; font-weight: 600;
  letter-spacing: 0.06em; text-transform: uppercase; flex-shrink: 0;
}
.sv { background: #e6f2ec; color: var(--verified); border: 1px solid #b8ddc8; }
.sp { background: #fdf4e3; color: var(--estimated); border: 1px solid #e8d09a; }

/* method note */
.method-note {
  border-left: 3px solid var(--accent2); background: #f0f4f8;
  border-radius: 0 6px 6px 0; padding: 14px 18px;
  margin: 16px 0; font-size: 13px; line-height: 1.6; font-family: sans-serif;
}
.method-note strong { color: var(--accent2); }
.method-note.warn { border-left-color: var(--estimated); background: #fdf4e3; }
.method-note.warn strong { color: var(--estimated); }

/* chart */
.chart-wrap {
  background: white; border: 1px solid var(--rule); border-radius: 6px;
  padding: 22px; margin: 24px 0;
}
.chart-legend { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 18px; }
.legend-btn {
  display: inline-flex; align-items: center; gap: 8px; padding: 5px 12px;
  border-radius: 4px; font-family: 'Courier New', monospace; font-size: 11px;
  cursor: pointer; border: 1.5px solid; background: transparent;
  transition: opacity 0.15s; letter-spacing: 0.04em;
}
.legend-btn.off { opacity: 0.25; }
.chart-container { position: relative; height: 300px; width: 100%; }
.chart-note {
  font-family: 'Courier New', monospace; font-size: 10px;
  color: var(--muted); text-align: right; margin-top: 8px;
  letter-spacing: 0.03em;
}

/* data table */
.dt-wrap { margin: 20px 0; overflow-x: auto; }
.dt {
  width: 100%; border-collapse: collapse;
  font-family: 'Courier New', monospace; font-size: 12px;
}
.dt th {
  background: var(--ink); color: #f6f1e9; padding: 9px 13px;
  text-align: left; font-size: 10px; letter-spacing: 0.08em;
  text-transform: uppercase; white-space: nowrap;
}
.dt td { padding: 8px 13px; border-bottom: 1px solid var(--rule); white-space: nowrap; }
.dt tr:nth-child(even) td { background: var(--paper2); }
.dt tr.fc td { color: var(--muted); font-style: italic; }

.bdg {
  font-size: 9px; padding: 2px 6px; border-radius: 2px; font-weight: 600;
  letter-spacing: 0.06em; text-transform: uppercase;
  font-family: 'Courier New', monospace; vertical-align: middle;
}
.bv { background: #e6f2ec; color: var(--verified); }
.be { background: #fdf4e3; color: var(--estimated); }
.bd { background: #eef2f8; color: var(--accent2); }
.bf { background: var(--paper2); color: var(--muted); }

/* references */
.refs-wrap {
  margin: 48px 0 0; border: 1px solid var(--rule);
  border-radius: 6px; overflow: hidden;
}
.refs-btn {
  display: flex; align-items: center; justify-content: space-between;
  padding: 15px 20px; background: var(--paper2); cursor: pointer;
  border: none; width: 100%; text-align: left;
  font-family: 'Courier New', monospace; font-size: 11px;
  letter-spacing: 0.1em; text-transform: uppercase; color: var(--muted);
  gap: 12px;
}
.refs-btn:hover { background: var(--rule); color: var(--ink); }
.refs-icon {
  width: 20px; height: 20px; border: 1.5px solid currentColor;
  border-radius: 50%; display: flex; align-items: center; justify-content: center;
  flex-shrink: 0; font-size: 14px; transition: transform 0.2s;
}
.refs-btn[aria-expanded="true"] .refs-icon { transform: rotate(45deg); }
.refs-body { display: none; padding: 20px; background: white; }
.refs-body.open { display: block; }
.ref-group { margin-bottom: 20px; }
.ref-group-lbl {
  font-family: 'Courier New', monospace; font-size: 10px;
  letter-spacing: 0.14em; text-transform: uppercase; color: var(--muted);
  margin-bottom: 10px; padding-bottom: 6px; border-bottom: 1px solid var(--rule);
}
.ref-row {
  display: grid; grid-template-columns: 26px 1fr; gap: 0 10px;
  margin-bottom: 12px; font-size: 13px; line-height: 1.55; font-family: sans-serif;
}
.ref-n { font-family: 'Courier New', monospace; font-size: 10px; color: var(--accent); font-weight: 600; padding-top: 2px; }
.ref-c a { color: var(--accent2); word-break: break-all; }
.ref-m { display: block; font-family: 'Courier New', monospace; font-size: 10px; color: var(--muted); margin-top: 3px; }

.footer-bar {
  display: flex; justify-content: space-between; align-items: center;
  flex-wrap: wrap; gap: 16px; margin-top: 48px; padding-top: 24px;
  border-top: 1px solid var(--rule);
  font-family: 'Courier New', monospace; font-size: 11px; color: var(--muted);
}
.next-btn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 9px 18px; border: 1.5px solid var(--ink); border-radius: 4px;
  font-family: 'Courier New', monospace; font-size: 11px; letter-spacing: 0.06em;
  text-decoration: none; color: var(--ink); text-transform: uppercase;
  transition: all 0.15s;
}
.next-btn:hover { background: var(--ink); color: #f6f1e9; }

@media (max-width: 600px) {
  .series-nav { flex-direction: column; }
  .series-nav a, .series-nav span { border-right: none; border-bottom: 1px solid var(--rule); }
  .series-hdr { flex-direction: column; align-items: flex-start; }
  .stat-grid { grid-template-columns: repeat(2, 1fr); }
}
</style>

<div class="nz-article">

<!-- series nav -->
<nav class="series-nav" aria-label="Article series">
  <span class="current"><span class="nav-num">01</span>The Numbers Don't Lie</span>
  <a href="02-my-story.html"><span class="nav-num">02</span>I Earn Good Money…</a>
  <a href="03-moving-the-needle.html"><span class="nav-num">03</span>What Would Move the Needle?</a>
  <a href="04-lets-talk.html"><span class="nav-num">04</span>Let's Talk</a>
</nav>

<p class="kicker">Data &amp; evidence — New Zealand 2015–2027</p>

# The Numbers Don't Lie

<p class="lede">Ten years of cost increases mapped against income growth. This page publishes only what we can source directly from Stats NZ — with every reference linked and confidence levels shown for every data point.</p>

<!-- stat squares -->
<div class="stat-grid">
  <div class="stat-cell dark">
    <div class="stat-val" style="color:#f5c842">+34.2%</div>
    <div class="stat-lbl">Official CPI<br>2015 → 2025</div>
  </div>
  <div class="stat-cell dark">
    <div class="stat-val" style="color:#6db88a">+61%</div>
    <div class="stat-lbl">Median income<br>2015 → 2025</div>
  </div>
  <div class="stat-cell">
    <div class="stat-val" style="color:#6b6354">$959</div>
    <div class="stat-lbl">Median weekly<br>income (2025)</div>
  </div>
  <div class="stat-cell">
    <div class="stat-val" style="color:#1a4f72">1,312.8</div>
    <div class="stat-lbl">CPI index<br>(base Jun 2017=1000)</div>
  </div>
</div>

<div class="insight-bar">
  Wages grew <strong>+61%</strong> over the decade. Official inflation was <strong>+34%</strong>. On paper this looks like a real gain — but CPI averages across <em>everything</em>, including goods getting cheaper. The costs you cannot escape grew far faster. More series coming as each source is verified.
</div>

---

<!-- ── SERIES 1: CPI ── -->
<div class="series-hdr">
  <div class="series-num">01</div>
  <div class="series-meta">
    <div class="series-tag">Series · Consumer Price Index</div>
    <div class="series-title">Official Inflation (CPI) — All Groups</div>
  </div>
  <span class="status-badge sv">✓ Fully verified</span>
</div>

<div class="method-note">
  <strong>Source:</strong> Stats NZ — Consumers Price Index, published quarterly. Annual figures shown are the average of four quarterly readings. Base period: June 2017 quarter = 1000. Reindexed here to 2015 = 100 for comparison.<br><br>
  <strong>Why CPI matters:</strong> This is New Zealand's official inflation measure. It covers approximately 98% of the usually-resident NZ population and tracks price changes across ~700 goods and services. It is the benchmark all other series in this article are measured against. Note that CPI is a <em>weighted average</em> — categories getting cheaper (electronics, clothing) offset categories rising fast. Your lived experience will differ from the headline number.
</div>

<!-- chart -->
<div class="chart-wrap">
  <div class="chart-legend">
    <button class="legend-btn" data-series="cpi" style="color:#374151;border-color:#374151;">
      <svg width="24" height="8"><line x1="0" y1="4" x2="24" y2="4" stroke="currentColor" stroke-width="2.5"/></svg>
      CPI All Groups
    </button>
    <button class="legend-btn" data-series="income" style="color:#a86c1a;border-color:#a86c1a;">
      <svg width="24" height="8"><line x1="0" y1="4" x2="24" y2="4" stroke="currentColor" stroke-width="2.5" stroke-dasharray="6 3"/></svg>
      Median Income
    </button>
  </div>
  <div class="chart-container">
    <canvas id="mainChart" aria-label="Line chart: NZ CPI and median income indexed to 2015=100, 2015 to 2027. CPI reaches 134 by 2025. Income reaches 161 by 2025 then plateaus."></canvas>
  </div>
  <p class="chart-note">Index: 2015 = 100 · Shaded area = forecast 2026–2027 · ◆ = estimated data point · Sources: Stats NZ CPI &amp; HLFS Income releases</p>
</div>

## CPI Data Table

<div class="dt-wrap">
<table class="dt" aria-label="CPI annual data 2015 to 2027">
<thead>
<tr><th>Year</th><th>CPI (annual avg)</th><th>Index 2015=100</th><th>YoY change</th><th>Confidence</th></tr>
</thead>
<tbody>
<tr><td>2015</td><td>978.2</td><td>100.0</td><td>—</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2016</td><td>984.5</td><td>100.6</td><td>+0.6%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2017</td><td>1,002.7</td><td>102.5</td><td>+1.9%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2018</td><td>1,018.8</td><td>104.2</td><td>+1.6%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2019</td><td>1,035.3</td><td>105.8</td><td>+1.6%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2020</td><td>1,053.0</td><td>107.6</td><td>+1.7%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2021</td><td>1,094.5</td><td>111.9</td><td>+3.9%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2022</td><td>1,173.0</td><td>119.9</td><td>+7.2%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2023</td><td>1,240.3</td><td>126.8</td><td>+5.7%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2024</td><td>1,276.5</td><td>130.5</td><td>+2.9%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2025</td><td>1,312.8</td><td>134.2</td><td>+2.9%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr class="fc"><td>2026 ◈</td><td>~1,352</td><td>~138.2</td><td>~+3.0%</td><td><span class="bdg bf">Forecast</span></td></tr>
<tr class="fc"><td>2027 ◈</td><td>~1,393</td><td>~142.4</td><td>~+3.0%</td><td><span class="bdg bf">Forecast</span></td></tr>
</tbody>
</table>
</div>

---

<!-- ── SERIES 2: INCOME ── -->
<div class="series-hdr">
  <div class="series-num">02</div>
  <div class="series-meta">
    <div class="series-tag">Series · Household Labour Force Survey</div>
    <div class="series-title">Median Weekly Income — All Sources</div>
  </div>
  <span class="status-badge sp">⚠ Partial — 2015–2018 estimated</span>
</div>

<div class="method-note">
  <strong>Source:</strong> Stats NZ — Labour Market Statistics (Income), June quarter annual release. Figures are median weekly income from <em>all sources</em>: wages, self-employment, and government transfers. Collected via the Household Labour Force Survey (HLFS).<br><br>
  <strong>Series break:</strong> The NZ Income Survey (NZIS) was discontinued June 2016 and replaced by the HLFS Income module. The two surveys use different methodology and are not perfectly comparable. Data for 2015–2018 is estimated by back-interpolating from the 2019 confirmed HLFS figure using historical NZIS growth rates. These years are clearly flagged below and carry higher uncertainty.
</div>

## Income Data Table

<div class="dt-wrap">
<table class="dt" aria-label="Median weekly income data 2015 to 2027">
<thead>
<tr><th>Year</th><th>Weekly income (NZD)</th><th>Index 2015=100</th><th>YoY change</th><th>Confidence</th></tr>
</thead>
<tbody>
<tr><td>2015</td><td>~$595</td><td>100.0</td><td>—</td><td><span class="bdg be">Estimated</span></td></tr>
<tr><td>2016</td><td>~$612</td><td>102.9</td><td>~+2.9%</td><td><span class="bdg be">Estimated</span></td></tr>
<tr><td>2017</td><td>~$632</td><td>106.2</td><td>~+3.3%</td><td><span class="bdg be">Estimated</span></td></tr>
<tr><td>2018</td><td>~$655</td><td>110.1</td><td>~+3.6%</td><td><span class="bdg be">Estimated</span></td></tr>
<tr><td>2019</td><td>$706</td><td>118.7</td><td>+7.8%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2020</td><td>$652</td><td>109.6</td><td>−7.6%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2021</td><td>$770</td><td>129.4</td><td>+18.1%</td><td><span class="bdg bd">Derived</span></td></tr>
<tr><td>2022</td><td>$848</td><td>142.5</td><td>+10.1%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2023</td><td>$921</td><td>154.8</td><td>+8.6%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2024</td><td>$959</td><td>161.2</td><td>+4.1%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr><td>2025</td><td>$959</td><td>161.2</td><td>0.0%</td><td><span class="bdg bv">Verified</span></td></tr>
<tr class="fc"><td>2026 ◈</td><td>~$978</td><td>~164.4</td><td>~+2.0%</td><td><span class="bdg bf">Forecast</span></td></tr>
<tr class="fc"><td>2027 ◈</td><td>~$998</td><td>~167.7</td><td>~+2.0%</td><td><span class="bdg bf">Forecast</span></td></tr>
</tbody>
</table>
</div>

<div class="method-note warn">
  <strong>Note on 2020 income dip:</strong> The $652 figure reflects the COVID-19 impact — reduced hours, job losses, and government income support replacing regular employment income during the lockdown period. Stats NZ explicitly noted this in the release. The 2021 rebound to $770 reflects both economic recovery and elevated government transfer payments in that year. Both are real data points, not anomalies.
</div>

<div class="method-note warn">
  <strong>Note on 2021 (Derived):</strong> The 2022 Stats NZ release states income increased by $78 (10.1%) to $848. Working backwards: $848 − $78 = $770 for 2021. This is arithmetic from two confirmed figures, not an estimate or assumption.
</div>

---

## What's coming next

The following series are being sourced and verified to the same standard before being added to this page:

| Series | Source | Status |
|--------|--------|--------|
| Grocery / food prices | Stats NZ CPI — Food subgroup | 🔄 In progress |
| Council rates | Stats NZ CPI — Local authority charges | 🔄 In progress |
| Home insurance | Stats NZ CPI — Insurance subgroup | ⏳ Queued |
| Electricity | MBIE / Electricity Authority | ⏳ Queued |
| Domestic airfares | Stats NZ CPI — Passenger transport | ⏳ Queued |
| Petrol / fuel | MBIE weekly fuel monitoring | ⏳ Queued |
| Mortgage costs | RBNZ interest rate data | ⏳ Queued |

Each series will show the same confidence badge, source link, and methodology note as above.

---

<!-- REFERENCES -->
<div class="refs-wrap">
  <button class="refs-btn" aria-expanded="false" onclick="toggleRefs(this)">
    <span>Sources &amp; references — 6 sources for this page</span>
    <span style="display:flex;align-items:center;gap:8px;">
      <span style="font-size:10px;opacity:0.6;">click to expand</span>
      <span class="refs-icon">+</span>
    </span>
  </button>
  <div class="refs-body" id="refsBody">

    <div class="ref-group">
      <div class="ref-group-lbl">Series 01 — Consumer Price Index</div>

      <div class="ref-row">
        <div class="ref-n">[1]</div>
        <div class="ref-c">
          Stats NZ — <strong>Consumers Price Index (CPI) indicator page</strong><br>
          Primary official source. Quarterly releases with all-groups index and subgroup breakdowns.<br>
          <a href="https://www.stats.govt.nz/indicators/consumers-price-index-cpi/" target="_blank" rel="noopener">stats.govt.nz/indicators/consumers-price-index-cpi/</a>
          <span class="ref-m">Publisher: Stats NZ Tatauranga Aotearoa · Accessed: May 2026</span>
        </div>
      </div>

      <div class="ref-row">
        <div class="ref-n">[2]</div>
        <div class="ref-c">
          rateinflation.com — <strong>New Zealand Historical CPI 1926–2026</strong><br>
          Annual average CPI values used in this data table. Site republishes Stats NZ quarterly data verbatim. Annual figures are the mean of four quarterly readings. Base: June 2017 quarter = 1000.<br>
          <a href="https://www.rateinflation.com/consumer-price-index/new-zealand-historical-cpi/" target="_blank" rel="noopener">rateinflation.com/consumer-price-index/new-zealand-historical-cpi/</a>
          <span class="ref-m">Last updated: April 21, 2026 · Accessed: May 2026 · Data verified against Stats NZ primary source</span>
        </div>
      </div>

      <div class="ref-row">
        <div class="ref-n">[3]</div>
        <div class="ref-c">
          Stats NZ — <strong>CPI methodology: DataInfo+</strong><br>
          Explains basket construction, expenditure weights, base period resets, and the 2017 review that reset the index to June 2017 = 1000. Confirms ~98% population coverage.<br>
          <a href="https://datainfoplus.stats.govt.nz/item/nz.govt.stats/8b0860b8-cf63-4f12-a578-8eed8ba69ac3/159" target="_blank" rel="noopener">datainfoplus.stats.govt.nz — CPI methodology</a>
          <span class="ref-m">Publisher: Stats NZ Tatauranga Aotearoa</span>
        </div>
      </div>
    </div>

    <div class="ref-group">
      <div class="ref-group-lbl">Series 02 — Median Weekly Income</div>

      <div class="ref-row">
        <div class="ref-n">[4]</div>
        <div class="ref-c">
          Stats NZ — <strong>Labour market statistics (income): June 2020 quarter</strong><br>
          Directly confirms 2020 figure ($652, −7.6%). By arithmetic subtraction ($652 + $54 = $706) confirms the 2019 figure used in this table.<br>
          <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2020-quarter/" target="_blank" rel="noopener">stats.govt.nz — LMS Income June 2020</a>
          <span class="ref-m">Published: August 2020 · Publisher: Stats NZ Tatauranga Aotearoa</span>
        </div>
      </div>

      <div class="ref-row">
        <div class="ref-n">[5]</div>
        <div class="ref-c">
          Stats NZ — <strong>Labour market statistics (income): June 2022 quarter</strong><br>
          Directly confirms 2022 figure ($848, +10.1%). By arithmetic ($848 − $78 = $770) the 2021 derived figure is confirmed.<br>
          <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2022-quarter/" target="_blank" rel="noopener">stats.govt.nz — LMS Income June 2022</a>
          <span class="ref-m">Published: August 2022 · Publisher: Stats NZ Tatauranga Aotearoa</span>
        </div>
      </div>

      <div class="ref-row">
        <div class="ref-n">[6]</div>
        <div class="ref-c">
          Stats NZ — <strong>Labour market statistics (income): June 2023, 2024 &amp; 2025</strong><br>
          Confirms: 2023 = $921 (+8.6%) · 2024 = $959 (+4.2%) · 2025 = $959 (unchanged).<br>
          <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2023-quarter/" target="_blank" rel="noopener">2023 release</a> ·
          <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2024-quarter/" target="_blank" rel="noopener">2024 release</a> ·
          <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2025-quarter/" target="_blank" rel="noopener">2025 release</a>
          <span class="ref-m">Publisher: Stats NZ Tatauranga Aotearoa · Accessed: May 2026</span>
        </div>
      </div>

    </div>

    <div class="ref-group">
      <div class="ref-group-lbl">Confidence badge legend</div>
      <p style="font-family:'Courier New',monospace;font-size:11px;color:var(--muted);line-height:2;">
        <span class="bdg bv">Verified</span> Figure confirmed directly from a Stats NZ official release &nbsp;·&nbsp;
        <span class="bdg bd">Derived</span> Calculated by arithmetic from two verified figures &nbsp;·&nbsp;
        <span class="bdg be">Estimated</span> Approximated from adjacent verified data and historical trend rates &nbsp;·&nbsp;
        <span class="bdg bf">Forecast</span> Projected using trend extrapolation — not an official figure
      </p>
    </div>

  </div>
</div>

<!-- footer bar -->
<div class="footer-bar">
  <span>Part 1 of 4 · NZ Cost of Living Series · Data current to May 2026</span>
  <a href="02-my-story.html" class="next-btn">02 My Story →</a>
</div>

</div><!-- end .nz-article -->

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
const YEARS  = ['2015','2016','2017','2018','2019','2020','2021','2022','2023','2024','2025','2026','2027'];
const F_IDX  = 10;

const CPI_IDX = [100.0,100.6,102.5,104.2,105.8,107.6,111.9,119.9,126.8,130.5,134.2,138.2,142.4];
const INC_IDX = [100.0,102.9,106.2,110.1,118.7,109.6,129.4,142.5,154.8,161.2,161.2,164.4,167.7];
const INC_EST = [true,true,true,true,false,false,false,false,false,false,false,false,false];

function split(arr, fIdx) {
  return {
    actual:   arr.map((v,i) => i <= fIdx ? v : null),
    forecast: arr.map((v,i) => i >= fIdx ? v : null),
  };
}

const cpi = split(CPI_IDX, F_IDX);
const inc = split(INC_IDX, F_IDX);

const shadePlugin = {
  id: 'shade',
  beforeDraw(chart) {
    const { ctx, chartArea, scales } = chart;
    if (!chartArea) return;
    const x1 = scales.x.getPixelForValue(F_IDX);
    const x2 = scales.x.getPixelForValue(YEARS.length - 1);
    ctx.save();
    ctx.fillStyle = 'rgba(14,13,11,0.04)';
    ctx.fillRect(x1, chartArea.top, x2 - x1, chartArea.bottom - chartArea.top);
    ctx.strokeStyle = 'rgba(14,13,11,0.15)';
    ctx.lineWidth = 1; ctx.setLineDash([3,3]);
    ctx.beginPath(); ctx.moveTo(x1,chartArea.top); ctx.lineTo(x1,chartArea.bottom); ctx.stroke();
    ctx.setLineDash([]);
    ctx.fillStyle = 'rgba(14,13,11,0.3)';
    ctx.font = '500 10px "Courier New", monospace';
    ctx.fillText('FORECAST →', x1 + 8, chartArea.top + 16);
    ctx.restore();
  }
};

const chart = new Chart(document.getElementById('mainChart').getContext('2d'), {
  type: 'line',
  data: {
    labels: YEARS,
    datasets: [
      { label:'CPI (actual)',    data:cpi.actual,   borderColor:'#374151', borderWidth:2.5, pointRadius:4, pointBackgroundColor:'#374151', pointStyle:'circle', tension:0.35, fill:false, spanGaps:false },
      { label:'CPI (forecast)',  data:cpi.forecast,  borderColor:'#374151', borderWidth:1.5, borderDash:[5,4], pointRadius:ctx=>ctx.dataIndex>F_IDX?4:0, pointStyle:'triangle', pointBackgroundColor:'#374151', tension:0.35, fill:false, spanGaps:false },
      { label:'Income (actual)', data:inc.actual,   borderColor:'#a86c1a', borderWidth:2.5, borderDash:[6,3],
        pointRadius: ctx => ctx.dataIndex<=F_IDX ? 4 : 0,
        pointStyle:  ctx => INC_EST[ctx.dataIndex] ? 'rectRot' : 'circle',
        pointBackgroundColor: ctx => INC_EST[ctx.dataIndex] ? '#f5c842' : '#a86c1a',
        tension:0.35, fill:false, spanGaps:false },
      { label:'Income (forecast)', data:inc.forecast, borderColor:'#a86c1a', borderWidth:1.5, borderDash:[5,4], pointRadius:ctx=>ctx.dataIndex>F_IDX?4:0, pointStyle:'triangle', pointBackgroundColor:'#a86c1a', tension:0.35, fill:false, spanGaps:false },
    ]
  },
  options: {
    responsive:true, maintainAspectRatio:false,
    plugins: {
      legend: { display:false },
      tooltip: {
        filter: i => i.raw !== null,
        callbacks: {
          label: c => {
            const base = c.dataset.label.split(' ')[0];
            const fc   = c.dataset.label.includes('forecast') ? ' ◈ forecast' : '';
            const est  = c.dataset.label.includes('Income') && INC_EST[c.dataIndex] ? ' ◆ estimated' : '';
            return `  ${base}: ${c.parsed.y.toFixed(1)}${fc}${est}`;
          }
        }
      }
    },
    scales: {
      x: { ticks:{ font:{family:'"Courier New",monospace',size:11}, color:'#6b6354', maxRotation:0 }, grid:{ color:'rgba(14,13,11,0.06)' } },
      y: { min:90, max:180,
        ticks:{ font:{family:'"Courier New",monospace',size:11}, color:'#6b6354' },
        grid:{ color:'rgba(14,13,11,0.06)' },
        title:{ display:true, text:'Index (2015 = 100)', font:{family:'"Courier New",monospace',size:10}, color:'#6b6354' }
      }
    }
  },
  plugins: [shadePlugin]
});

document.querySelectorAll('.legend-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    const indices = btn.dataset.series === 'cpi' ? [0,1] : [2,3];
    const hidden = !chart.getDatasetMeta(indices[0]).hidden;
    indices.forEach(i => chart.getDatasetMeta(i).hidden = hidden);
    btn.classList.toggle('off', hidden);
    chart.update();
  });
});

function toggleRefs(btn) {
  const body = document.getElementById('refsBody');
  const open = btn.getAttribute('aria-expanded') === 'true';
  btn.setAttribute('aria-expanded', String(!open));
  body.classList.toggle('open', !open);
}
</script>
