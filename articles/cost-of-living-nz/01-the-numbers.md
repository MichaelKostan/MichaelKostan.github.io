---
layout: default
title: The Numbers Don't Lie
description: Ten years of NZ cost increases mapped against income growth — sourced directly from Stats NZ.
---

<style>
:root {
  --ink:#0e0d0b; --paper:#f6f1e9; --paper2:#ede7da; --rule:#c8c0b0;
  --accent:#c13a2b; --accent2:#1a4f72; --gold:#a86c1a;
  --muted:#6b6354; --verified:#1a6644; --estimated:#7a5c18;
}
.nz { font-family: Georgia, serif; }
.kicker {
  font-family:'Courier New',monospace; font-size:11px; letter-spacing:.16em;
  text-transform:uppercase; color:var(--accent); margin-bottom:14px;
  display:flex; align-items:center; gap:10px;
}
.kicker::after { content:''; flex:1; height:1px; background:var(--accent); opacity:.3; }
.lede {
  font-size:16px; color:var(--muted); line-height:1.65; font-style:italic;
  border-left:3px solid var(--rule); padding-left:18px; margin:0 0 28px;
}
.stat-grid {
  display:grid; grid-template-columns:repeat(auto-fit,minmax(140px,1fr));
  gap:1px; background:var(--rule); border:1px solid var(--rule);
  border-radius:6px; overflow:hidden; margin:28px 0;
}
.stat-cell { background:var(--paper); padding:16px 18px; }
.stat-cell.dark { background:var(--ink); }
.stat-val { font-family:Georgia,serif; font-size:32px; font-weight:700; line-height:1; margin-bottom:5px; }
.stat-cell.dark .stat-val { color:var(--paper); }
.stat-lbl { font-family:'Courier New',monospace; font-size:10px; letter-spacing:.06em; text-transform:uppercase; color:var(--muted); line-height:1.4; }
.stat-cell.dark .stat-lbl { color:rgba(246,241,233,.4); }
.insight-bar {
  background:var(--ink); color:#f6f1e9; border-radius:6px;
  padding:16px 20px; font-size:14px; line-height:1.65;
  margin:0 0 28px; font-style:italic;
}
.insight-bar strong { font-style:normal; color:#f5c842; }
.chart-wrap {
  background:white; border:1px solid var(--rule); border-radius:6px;
  padding:20px; margin:0 0 8px;
}
.chart-legend { display:flex; flex-wrap:wrap; gap:7px; margin-bottom:16px; }
.legend-btn {
  display:inline-flex; align-items:center; gap:7px; padding:4px 11px;
  border-radius:4px; font-family:'Courier New',monospace; font-size:11px;
  cursor:pointer; border:1.5px solid; background:transparent; transition:opacity .15s;
}
.legend-btn.off { opacity:.25; }
.chart-box { position:relative; height:280px; width:100%; }
.chart-note { font-family:'Courier New',monospace; font-size:10px; color:var(--muted); text-align:right; margin:6px 0 0; }
.refs-wrap { margin:32px 0 0; border:1px solid var(--rule); border-radius:6px; overflow:hidden; }
.refs-btn {
  display:flex; align-items:center; justify-content:space-between;
  padding:13px 18px; background:var(--paper2); cursor:pointer;
  border:none; width:100%; text-align:left;
  font-family:'Courier New',monospace; font-size:11px;
  letter-spacing:.1em; text-transform:uppercase; color:var(--muted); gap:12px;
}
.refs-btn:hover { background:var(--rule); color:var(--ink); }
.refs-icon { width:18px; height:18px; border:1.5px solid currentColor; border-radius:50%; display:flex; align-items:center; justify-content:center; flex-shrink:0; font-size:13px; transition:transform .2s; }
.refs-btn[aria-expanded="true"] .refs-icon { transform:rotate(45deg); }
.refs-body { display:none; padding:18px; background:white; font-family:sans-serif; font-size:13px; line-height:1.6; }
.refs-body.open { display:block; }
.ref-row { display:grid; grid-template-columns:24px 1fr; gap:0 10px; margin-bottom:12px; }
.ref-n { font-family:'Courier New',monospace; font-size:10px; color:var(--accent); font-weight:600; padding-top:2px; }
.ref-c a { color:var(--accent2); word-break:break-all; }
.ref-m { display:block; font-family:'Courier New',monospace; font-size:10px; color:var(--muted); margin-top:2px; }
.bdg { font-size:9px; padding:2px 5px; border-radius:2px; font-weight:600; letter-spacing:.05em; text-transform:uppercase; font-family:'Courier New',monospace; }
.bv { background:#e6f2ec; color:var(--verified); }
.be { background:#fdf4e3; color:var(--estimated); }
.bd { background:#eef2f8; color:var(--accent2); }
.bf { background:var(--paper2); color:var(--muted); }
.series-nav { display:flex; gap:0; margin-bottom:32px; border:1px solid var(--rule); border-radius:4px; overflow:hidden; font-family:'Courier New',monospace; font-size:10px; }
.series-nav a,.series-nav span { flex:1; padding:9px 11px; border-right:1px solid var(--rule); text-decoration:none; color:var(--muted); line-height:1.3; }
.series-nav a:last-child,.series-nav span:last-child { border-right:none; }
.series-nav .cur { background:var(--ink); color:#f6f1e9; }
.series-nav a:hover:not(.cur) { background:var(--paper2); }
.nav-n { display:block; font-weight:600; margin-bottom:2px; opacity:.55; }
.cur .nav-n { opacity:.4; }
@media(max-width:580px){
  .series-nav{flex-direction:column;}
  .series-nav a,.series-nav span{border-right:none;border-bottom:1px solid var(--rule);}
  .stat-grid{grid-template-columns:repeat(2,1fr);}
}
</style>

<div class="nz">

<nav class="series-nav">
  <span class="cur"><span class="nav-n">01</span>The Numbers Don't Lie</span>
  <a href="02-my-story"><span class="nav-n">02</span>I Earn Good Money…</a>
  <a href="03-moving-the-needle"><span class="nav-n">03</span>What Would Move the Needle?</a>
  <a href="04-lets-talk"><span class="nav-n">04</span>Let's Talk</a>
</nav>

<p class="kicker">Data &amp; evidence — New Zealand 2015–2027</p>

# The Numbers Don't Lie

<p class="lede">Ten years of cost increases mapped against income growth — sourced directly from Stats NZ, with every data point confidence-rated.</p>

<div class="stat-grid">
  <div class="stat-cell dark"><div class="stat-val" style="color:#f5c842">+34.2%</div><div class="stat-lbl">Official CPI<br>2015 → 2025</div></div>
  <div class="stat-cell dark"><div class="stat-val" style="color:#6db88a">+61%</div><div class="stat-lbl">Median income<br>2015 → 2025</div></div>
  <div class="stat-cell"><div class="stat-val" style="color:#6b6354">$959</div><div class="stat-lbl">Median weekly<br>income (2025)</div></div>
  <div class="stat-cell"><div class="stat-val" style="color:#1a4f72">1,312.8</div><div class="stat-lbl">CPI index<br>(base Jun 2017=1000)</div></div>
</div>

<div class="insight-bar">
  Wages grew <strong>+61%</strong> over the decade. Official inflation was <strong>+34%</strong>. On paper this looks like a real gain — but CPI averages across <em>everything</em>, including goods getting cheaper. The costs you cannot escape grew far faster.
</div>

<div class="chart-wrap">
  <div class="chart-legend">
    <button class="legend-btn" data-s="cpi" style="color:#374151;border-color:#374151;">
      <svg width="22" height="8"><line x1="0" y1="4" x2="22" y2="4" stroke="currentColor" stroke-width="2.5"/></svg>CPI All Groups
    </button>
    <button class="legend-btn" data-s="inc" style="color:#a86c1a;border-color:#a86c1a;">
      <svg width="22" height="8"><line x1="0" y1="4" x2="22" y2="4" stroke="currentColor" stroke-width="2.5" stroke-dasharray="6 3"/></svg>Median Income
    </button>
  </div>
  <div class="chart-box"><canvas id="c" aria-label="NZ CPI and median income indexed to 2015=100, 2015 to 2027."></canvas></div>
  <p class="chart-note">Index: 2015 = 100 · Shaded = forecast 2026–2027 · ◆ estimated · Sources: Stats NZ</p>
</div>

<div class="refs-wrap">
  <button class="refs-btn" aria-expanded="false" onclick="this.setAttribute('aria-expanded',this.getAttribute('aria-expanded')==='true'?'false':'true');document.getElementById('rb').classList.toggle('open')">
    <span>Sources &amp; references — 6 sources, all Stats NZ</span>
    <span style="display:flex;align-items:center;gap:7px;"><span style="font-size:10px;opacity:.6">click to expand</span><span class="refs-icon">+</span></span>
  </button>
  <div class="refs-body" id="rb">

    <p style="font-family:'Courier New',monospace;font-size:10px;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:12px;padding-bottom:8px;border-bottom:1px solid var(--rule);">Series 01 — Consumer Price Index</p>

    <div class="ref-row"><div class="ref-n">[1]</div><div class="ref-c">Stats NZ — <strong>Consumers Price Index indicator</strong><br><a href="https://www.stats.govt.nz/indicators/consumers-price-index-cpi/" target="_blank" rel="noopener">stats.govt.nz/indicators/consumers-price-index-cpi/</a><span class="ref-m">Primary official source · Accessed May 2026</span></div></div>

    <div class="ref-row"><div class="ref-n">[2]</div><div class="ref-c">rateinflation.com — <strong>NZ Historical CPI 1926–2026</strong> (republishes Stats NZ data verbatim)<br><a href="https://www.rateinflation.com/consumer-price-index/new-zealand-historical-cpi/" target="_blank" rel="noopener">rateinflation.com/consumer-price-index/new-zealand-historical-cpi/</a><span class="ref-m">Updated April 21 2026 · Base: June 2017 quarter = 1000</span></div></div>

    <div class="ref-row"><div class="ref-n">[3]</div><div class="ref-c">Stats NZ — <strong>CPI methodology: DataInfo+</strong><br><a href="https://datainfoplus.stats.govt.nz/item/nz.govt.stats/8b0860b8-cf63-4f12-a578-8eed8ba69ac3/159" target="_blank" rel="noopener">datainfoplus.stats.govt.nz — CPI methodology</a><span class="ref-m">Explains basket, weights, base period resets</span></div></div>

    <p style="font-family:'Courier New',monospace;font-size:10px;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin:16px 0 12px;padding-bottom:8px;border-bottom:1px solid var(--rule);">Series 02 — Median Weekly Income</p>

    <div class="ref-row"><div class="ref-n">[4]</div><div class="ref-c">Stats NZ — <strong>LMS Income: June 2020</strong> — confirms $652 (−7.6%) and by subtraction $706 for 2019<br><a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2020-quarter/" target="_blank" rel="noopener">stats.govt.nz — LMS Income June 2020</a></div></div>

    <div class="ref-row"><div class="ref-n">[5]</div><div class="ref-c">Stats NZ — <strong>LMS Income: June 2022</strong> — confirms $848 (+10.1%) and by subtraction $770 for 2021<br><a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2022-quarter/" target="_blank" rel="noopener">stats.govt.nz — LMS Income June 2022</a></div></div>

    <div class="ref-row"><div class="ref-n">[6]</div><div class="ref-c">Stats NZ — <strong>LMS Income: June 2023, 2024 &amp; 2025</strong> — confirms $921, $959, $959<br>
      <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2023-quarter/" target="_blank" rel="noopener">2023</a> ·
      <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2024-quarter/" target="_blank" rel="noopener">2024</a> ·
      <a href="https://www.stats.govt.nz/information-releases/labour-market-statistics-income-june-2025-quarter/" target="_blank" rel="noopener">2025</a>
    </div></div>

    <p style="font-family:'Courier New',monospace;font-size:10px;color:var(--muted);margin-top:12px;">
      <span class="bdg bv">Verified</span> direct Stats NZ source &nbsp;
      <span class="bdg bd">Derived</span> arithmetic from two verified figures &nbsp;
      <span class="bdg be">Estimated</span> interpolated from trend &nbsp;
      <span class="bdg bf">Forecast</span> trend extrapolation
    </p>
  </div>
</div>

</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
const YR=['2015','2016','2017','2018','2019','2020','2021','2022','2023','2024','2025','2026','2027'];
const FI=10;
const CPI=[100.0,100.6,102.5,104.2,105.8,107.6,111.9,119.9,126.8,130.5,134.2,138.2,142.4];
const INC=[100.0,102.9,106.2,110.1,118.7,109.6,129.4,142.5,154.8,161.2,161.2,164.4,167.7];
const EST=[1,1,1,1,0,0,0,0,0,0,0,0,0]; // 1=estimated
function sp(a){return{act:a.map((v,i)=>i<=FI?v:null),fc:a.map((v,i)=>i>=FI?v:null)};}
const c=sp(CPI),ic=sp(INC);
const shade={id:'s',beforeDraw(ch){
  const{ctx,chartArea:ca,scales:sc}=ch;if(!ca)return;
  const x1=sc.x.getPixelForValue(FI),x2=sc.x.getPixelForValue(12);
  ctx.save();ctx.fillStyle='rgba(14,13,11,.04)';ctx.fillRect(x1,ca.top,x2-x1,ca.bottom-ca.top);
  ctx.strokeStyle='rgba(14,13,11,.15)';ctx.lineWidth=1;ctx.setLineDash([3,3]);
  ctx.beginPath();ctx.moveTo(x1,ca.top);ctx.lineTo(x1,ca.bottom);ctx.stroke();ctx.setLineDash([]);
  ctx.fillStyle='rgba(14,13,11,.3)';ctx.font='10px "Courier New"';ctx.fillText('FORECAST →',x1+6,ca.top+14);
  ctx.restore();
}};
const chart=new Chart(document.getElementById('c').getContext('2d'),{
  type:'line',
  data:{labels:YR,datasets:[
    {label:'CPI (actual)',data:c.act,borderColor:'#374151',borderWidth:2.5,pointRadius:3,pointBackgroundColor:'#374151',tension:.35,fill:false,spanGaps:false},
    {label:'CPI (fc)',data:c.fc,borderColor:'#374151',borderWidth:1.5,borderDash:[5,4],pointRadius:ctx=>ctx.dataIndex>FI?3:0,pointStyle:'triangle',pointBackgroundColor:'#374151',tension:.35,fill:false,spanGaps:false},
    {label:'Income (actual)',data:ic.act,borderColor:'#a86c1a',borderWidth:2.5,borderDash:[6,3],
      pointRadius:ctx=>ctx.dataIndex<=FI?4:0,
      pointStyle:ctx=>EST[ctx.dataIndex]?'rectRot':'circle',
      pointBackgroundColor:ctx=>EST[ctx.dataIndex]?'#f5c842':'#a86c1a',
      tension:.35,fill:false,spanGaps:false},
    {label:'Income (fc)',data:ic.fc,borderColor:'#a86c1a',borderWidth:1.5,borderDash:[5,4],pointRadius:ctx=>ctx.dataIndex>FI?3:0,pointStyle:'triangle',pointBackgroundColor:'#a86c1a',tension:.35,fill:false,spanGaps:false},
  ]},
  options:{
    responsive:true,maintainAspectRatio:false,
    plugins:{legend:{display:false},tooltip:{filter:i=>i.raw!==null,callbacks:{label:c=>`${c.dataset.label.split(' ')[0]}: ${c.parsed.y.toFixed(1)}`}}},
    scales:{
      x:{ticks:{font:{family:'"Courier New",monospace',size:10},color:'#6b6354',maxRotation:0},grid:{color:'rgba(14,13,11,.06)'}},
      y:{min:90,max:175,ticks:{font:{family:'"Courier New",monospace',size:10},color:'#6b6354'},grid:{color:'rgba(14,13,11,.06)'},title:{display:true,text:'Index (2015 = 100)',font:{family:'"Courier New",monospace',size:10},color:'#6b6354'}}
    }
  },
  plugins:[shade]
});
document.querySelectorAll('.legend-btn').forEach(b=>{
  b.addEventListener('click',()=>{
    const idx=b.dataset.s==='cpi'?[0,1]:[2,3];
    const h=!chart.getDatasetMeta(idx[0]).hidden;
    idx.forEach(i=>chart.getDatasetMeta(i).hidden=h);
    b.classList.toggle('off',h);chart.update();
  });
});
</script>
