<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>War & Economic Impact — README</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;600&family=IBM+Plex+Sans:wght@300;400;600&display=swap');

  :root {
    --bg:       #0d1117;
    --surface:  #161b22;
    --border:   #30363d;
    --accent:   #e06c3a;
    --accent2:  #4e9af1;
    --text:     #e6edf3;
    --muted:    #8b949e;
    --green:    #3fb950;
    --tag-bg:   #21262d;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'IBM Plex Sans', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    max-width: 860px;
    margin: 0 auto;
    padding: 48px 28px 80px;
  }

  /* ── header ─────────────────────────────────────────────── */
  .header {
    border-bottom: 1px solid var(--border);
    padding-bottom: 28px;
    margin-bottom: 36px;
    animation: fadeDown 0.5s ease both;
  }
  .repo-meta {
    display: flex;
    align-items: center;
    gap: 10px;
    color: var(--muted);
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
    margin-bottom: 14px;
  }
  .repo-meta span { color: var(--accent2); }
  h1 {
    font-size: 28px;
    font-weight: 600;
    letter-spacing: -0.5px;
    margin-bottom: 10px;
  }
  .subtitle {
    color: var(--muted);
    font-size: 14px;
    max-width: 560px;
  }
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 18px;
  }
  .badge {
    background: var(--tag-bg);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 3px 10px;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--muted);
  }
  .badge.green  { border-color: #238636; color: var(--green); }
  .badge.orange { border-color: #9a5200; color: var(--accent); }
  .badge.blue   { border-color: #1f6feb; color: var(--accent2); }

  /* ── section headings ───────────────────────────────────── */
  h2 {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: var(--muted);
    margin: 40px 0 14px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  h2::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── overview block ─────────────────────────────────────── */
  .overview-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 24px;
  }
  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 16px 18px;
    animation: fadeUp 0.5s ease both;
  }
  .stat-card .label {
    font-size: 11px;
    font-family: 'IBM Plex Mono', monospace;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 4px;
  }
  .stat-card .value {
    font-size: 20px;
    font-weight: 600;
    color: var(--text);
  }
  .stat-card .value.accent  { color: var(--accent); }
  .stat-card .value.accent2 { color: var(--accent2); }
  .stat-card .value.green   { color: var(--green); }

  /* ── research questions ─────────────────────────────────── */
  .questions {
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent);
    border-radius: 6px;
    padding: 18px 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .question {
    display: flex;
    gap: 12px;
    align-items: flex-start;
  }
  .q-label {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    background: #2a1a0f;
    border: 1px solid #9a5200;
    border-radius: 3px;
    padding: 2px 7px;
    white-space: nowrap;
    margin-top: 2px;
  }
  .question p { font-size: 14px; color: var(--text); }

  /* ── file cards ─────────────────────────────────────────── */
  .file-list { display: flex; flex-direction: column; gap: 12px; }

  .file-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 18px 20px;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 0 18px;
    align-items: start;
    text-decoration: none;
    color: inherit;
    transition: border-color 0.15s, background 0.15s;
    animation: fadeUp 0.4s ease both;
  }
  .file-card:hover {
    border-color: var(--accent2);
    background: #1a2030;
    cursor: pointer;
  }
  .file-icon {
    font-size: 22px;
    line-height: 1;
    padding-top: 2px;
  }
  .file-name {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 14px;
    font-weight: 600;
    color: var(--accent2);
    margin-bottom: 4px;
  }
  .file-type {
    display: inline-block;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    background: var(--tag-bg);
    border: 1px solid var(--border);
    border-radius: 3px;
    padding: 1px 6px;
    margin-bottom: 8px;
  }
  .file-desc { font-size: 13.5px; color: var(--muted); line-height: 1.6; }
  .file-contents { margin-top: 10px; }
  .file-contents li {
    font-size: 12.5px;
    color: #6e8099;
    list-style: none;
    padding: 2px 0;
  }
  .file-contents li::before {
    content: '→ ';
    color: var(--accent);
    font-family: 'IBM Plex Mono', monospace;
  }

  /* ── pipeline ───────────────────────────────────────────── */
  .pipeline {
    display: flex;
    align-items: center;
    gap: 0;
    flex-wrap: wrap;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 16px 20px;
    overflow: hidden;
  }
  .pipe-step {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--text);
    padding: 5px 12px;
    border-radius: 4px;
    white-space: nowrap;
  }
  .pipe-step.active { background: #1f3a26; color: var(--green); border: 1px solid #238636; }
  .pipe-arrow {
    color: var(--border);
    font-size: 16px;
    padding: 0 4px;
    font-family: monospace;
  }

  /* ── quick start ────────────────────────────────────────── */
  .code-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 16px 20px;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
    color: #a5c261;
    line-height: 1.9;
  }
  .code-block .comment { color: #4a5568; }
  .code-block .cmd     { color: var(--accent2); }

  /* ── results table ──────────────────────────────────────── */
  table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
    font-family: 'IBM Plex Mono', monospace;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    overflow: hidden;
    margin-bottom: 10px;
  }
  th {
    background: var(--tag-bg);
    color: var(--muted);
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 1px;
    padding: 10px 14px;
    text-align: left;
    border-bottom: 1px solid var(--border);
  }
  td {
    padding: 9px 14px;
    border-bottom: 1px solid var(--border);
    color: var(--text);
  }
  tr:last-child td { border-bottom: none; }
  tr:hover td { background: #1a2030; }
  .good  { color: var(--green); }
  .warn  { color: var(--accent); }
  .info  { color: var(--accent2); }

  /* ── footer ─────────────────────────────────────────────── */
  .footer {
    margin-top: 56px;
    padding-top: 20px;
    border-top: 1px solid var(--border);
    font-size: 12px;
    color: var(--muted);
    font-family: 'IBM Plex Mono', monospace;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 8px;
  }

  /* ── animations ─────────────────────────────────────────── */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-12px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(10px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .file-card:nth-child(1) { animation-delay: 0.05s; }
  .file-card:nth-child(2) { animation-delay: 0.12s; }
  .file-card:nth-child(3) { animation-delay: 0.19s; }
  .stat-card:nth-child(1) { animation-delay: 0.05s; }
  .stat-card:nth-child(2) { animation-delay: 0.10s; }
  .stat-card:nth-child(3) { animation-delay: 0.15s; }
  .stat-card:nth-child(4) { animation-delay: 0.20s; }

  @media (max-width: 580px) {
    .overview-grid { grid-template-columns: 1fr 1fr; }
    .pipeline { gap: 6px; }
    .pipe-arrow { display: none; }
  }
</style>
</head>
<body>

<!-- ── HEADER ──────────────────────────────────────────────────────── -->
<div class="header">
  <div class="repo-meta">
    <span>student</span> / <span>war-economic-impact</span>
  </div>
  <h1>War &amp; Economic Impact</h1>
  <p class="subtitle">
    A full data science pipeline — from raw conflict data to predictive modelling —
    exploring the economic footprint of armed conflict across 100,000 observations.
  </p>
  <div class="badges">
    <span class="badge green">Python 3.10</span>
    <span class="badge blue">scikit-learn</span>
    <span class="badge blue">seaborn</span>
    <span class="badge blue">pandas</span>
    <span class="badge orange">100,000 rows</span>
    <span class="badge">1939 – 2026</span>
    <span class="badge">5 Regions</span>
  </div>
</div>

<!-- ── OVERVIEW ────────────────────────────────────────────────────── -->
<h2>Overview</h2>

<div class="overview-grid">
  <div class="stat-card">
    <div class="label">Dataset Size</div>
    <div class="value accent2">100,000</div>
    <div style="font-size:12px;color:var(--muted);margin-top:2px;">rows × 35 features</div>
  </div>
  <div class="stat-card">
    <div class="label">Conflict Types</div>
    <div class="value">5</div>
    <div style="font-size:12px;color:var(--muted);margin-top:2px;">Civil · Interstate · World · Asymmetric</div>
  </div>
  <div class="stat-card">
    <div class="label">Classification AUC</div>
    <div class="value green">0.937</div>
    <div style="font-size:12px;color:var(--muted);margin-top:2px;">Ongoing vs Resolved</div>
  </div>
  <div class="stat-card">
    <div class="label">GDP Variance Explained</div>
    <div class="value accent">25%</div>
    <div style="font-size:12px;color:var(--muted);margin-top:2px;">by conflict type alone (η²)</div>
  </div>
</div>

<div class="questions">
  <div class="question">
    <span class="q-label">REGRESSION</span>
    <p>Which economic indicators best predict the total financial scale of a conflict?</p>
  </div>
  <div class="question">
    <span class="q-label">CLASSIFICATION</span>
    <p>Can a conflict's economic damage profile predict whether it is still ongoing or resolved?</p>
  </div>
</div>

<!-- ── PIPELINE ────────────────────────────────────────────────────── -->
<h2>Pipeline</h2>
<div class="pipeline">
  <span class="pipe-step active">Data Wrangling</span>
  <span class="pipe-arrow">→</span>
  <span class="pipe-step active">EDA</span>
  <span class="pipe-arrow">→</span>
  <span class="pipe-step active">Hypothesis Testing</span>
  <span class="pipe-arrow">→</span>
  <span class="pipe-step active">Regression</span>
  <span class="pipe-arrow">→</span>
  <span class="pipe-step active">Classification</span>
  <span class="pipe-arrow">→</span>
  <span class="pipe-step active">Clustering</span>
  <span class="pipe-arrow">→</span>
  <span class="pipe-step active">Interpretation</span>
</div>

<!-- ── FILES ───────────────────────────────────────────────────────── -->
<h2>Repository Files</h2>
<div class="file-list">

  <div class="file-card">
    <div class="file-icon">📋</div>
    <div>
      <div class="file-name">Final_Project_Description</div>
      <span class="file-type">.ipynb &nbsp;·&nbsp; READ FIRST</span>
      <p class="file-desc">
        The original project brief from the course marker. Contains all formal requirements,
        grading criteria, and deliverable specifications. Start here to understand what
        the project is evaluating and why each section exists.
      </p>
      <ul class="file-contents">
        <li>Dataset requirements and minimum thresholds</li>
        <li>Wrangling, EDA, and modelling specifications</li>
        <li>Grading rubric and evaluation emphasis</li>
        <li>Deliverable checklist and presentation guidelines</li>
      </ul>
    </div>
  </div>

  <div class="file-card">
    <div class="file-icon">⚙️</div>
    <div>
      <div class="file-name">Project_Code</div>
      <span class="file-type">.ipynb &nbsp;·&nbsp; SOURCE CODE</span>
      <p class="file-desc">
        The complete, fully-runnable analysis notebook. Executes end-to-end from raw CSV
        to final model metrics. Every cell includes markdown explaining what is being done
        and why before the code runs.
      </p>
      <ul class="file-contents">
        <li>Data wrangling &amp; feature engineering (7 steps)</li>
        <li>EDA — 4 targeted visualisations with interpretations</li>
        <li>Statistical testing — Chi-square, Kruskal-Wallis, Mann-Whitney</li>
        <li>Regression — Linear &amp; Random Forest on log(Cost_of_War)</li>
        <li>Classification — Logistic &amp; RF on Conflict Status (AUC 0.937)</li>
        <li>K-Means clustering (k=2) with PCA projection</li>
      </ul>
    </div>
  </div>

  <div class="file-card">
    <div class="file-icon">📄</div>
    <div>
      <div class="file-name">Written_Report</div>
      <span class="file-type">.txt &nbsp;·&nbsp; WRITTEN REPORT</span>
      <p class="file-desc">
        A concise written report covering every section of the project in plain language.
        Structured for a non-technical audience — no code, just findings, results, and
        what they mean in practice.
      </p>
      <ul class="file-contents">
        <li>Project Overview — dataset, questions, feature engineering</li>
        <li>Key Visuals — purpose and finding for each figure</li>
        <li>Statistical Results — all three tests with effect sizes</li>
        <li>Model Performance Table — regression and classification metrics</li>
        <li>Interpretation &amp; Conclusion — findings, limitations, next steps</li>
      </ul>
    </div>
  </div>

</div>

<!-- ── KEY RESULTS ──────────────────────────────────────────────────── -->
<h2>Key Results</h2>

<table>
  <thead>
    <tr>
      <th>Task</th><th>Model</th><th>Primary Metric</th><th>Value</th><th>Note</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Regression</td>
      <td>Linear Regression</td>
      <td>Test R²</td>
      <td class="warn">−0.001</td>
      <td style="color:var(--muted);font-size:11px;">War cost ≠ economic damage</td>
    </tr>
    <tr>
      <td>Regression</td>
      <td>Random Forest</td>
      <td>Test RMSE</td>
      <td class="warn">0.986</td>
      <td style="color:var(--muted);font-size:11px;">~2.6× error in USD terms</td>
    </tr>
    <tr>
      <td>Classification</td>
      <td>Logistic Regression</td>
      <td>ROC-AUC</td>
      <td class="good">0.9362</td>
      <td style="color:var(--muted);font-size:11px;">Strong linear separability</td>
    </tr>
    <tr>
      <td>Classification</td>
      <td>Random Forest</td>
      <td>ROC-AUC</td>
      <td class="good">0.9366</td>
      <td style="color:var(--muted);font-size:11px;">Matches LR — boundary is linear</td>
    </tr>
    <tr>
      <td>Statistics</td>
      <td>Kruskal-Wallis</td>
      <td>η² (GDP vs Type)</td>
      <td class="info">0.251</td>
      <td style="color:var(--muted);font-size:11px;">Large effect — largest finding</td>
    </tr>
  </tbody>
</table>

<!-- ── QUICK START ──────────────────────────────────────────────────── -->
<h2>Quick Start</h2>
<div class="code-block">
  <span class="comment"># 1. Clone the repository</span><br>
  <span class="cmd">git clone</span> https://github.com/student/war-economic-impact<br>
  <span class="cmd">cd</span> war-economic-impact<br><br>
  <span class="comment"># 2. Install dependencies</span><br>
  <span class="cmd">pip install</span> pandas numpy matplotlib seaborn scikit-learn scipy<br><br>
  <span class="comment"># 3. Place the dataset in the project root</span><br>
  war_economic_impact_dataset.csv<br><br>
  <span class="comment"># 4. Run the notebook top-to-bottom</span><br>
  <span class="cmd">jupyter notebook</span> Project_Code.ipynb
</div>

<!-- ── FOOTER ───────────────────────────────────────────────────────── -->
<div class="footer">
  <span>war-economic-impact · Data Science Mini-Project</span>
  <span>Python · pandas · scikit-learn · seaborn · scipy</span>
</div>

</body>
</html>
