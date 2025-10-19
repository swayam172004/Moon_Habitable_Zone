<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>MoonHabitableZone — Exomoon Detection & Moon Stability Zone (MSZ)</title>

  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">

  <!-- Favicons / meta -->
  <meta name="description" content="MoonHabitableZone — Python toolkit for exomoon detection, computing Hill radius / Roche limit and a Moon Stability Zone (MSZ) formula.">
  <meta name="theme-color" content="#0b1221">

  <style>
    :root{
      --bg:#071027;
      --card:#0f1a2b;
      --muted:#98a0b3;
      --accent:#7c5cff;
      --accent-2:#36d6a4;
      --glass: rgba(255,255,255,0.04);
      --glass-2: rgba(255,255,255,0.02);
      --white:#eaf0ff;
      --radius:12px;
      --max-w:1100px;
    }
    html,body{
      height:100%;
      margin:0;
      font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial;
      background: radial-gradient(1200px 500px at 10% 10%, rgba(124,92,255,0.12), transparent),
                  radial-gradient(900px 400px at 90% 90%, rgba(54,214,164,0.06), transparent),
                  var(--bg);
      color:var(--white);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
    }

    .container{
      max-width:var(--max-w);
      margin:40px auto;
      padding:28px;
    }

    header{
      display:flex;
      gap:20px;
      align-items:center;
      margin-bottom:22px;
    }

    .logo{
      width:88px;
      height:88px;
      border-radius:16px;
      display:flex;
      align-items:center;
      justify-content:center;
      background:linear-gradient(135deg,var(--accent),#5a3bff 60%);
      box-shadow: 0 6px 30px rgba(92,70,255,0.12), inset 0 -6px 20px rgba(0,0,0,0.2);
      flex-shrink:0;
    }
    .logo svg{ filter: drop-shadow(0 6px 18px rgba(0,0,0,0.25)); }

    h1{ margin:0; font-size:1.6rem; letter-spacing:-0.2px; }
    .subtitle{ color:var(--muted); margin-top:6px; font-size:0.95rem; }

    .badges{ margin-left:auto; display:flex; gap:8px; align-items:center; flex-wrap:wrap; }

    .hero{
      display:flex;
      gap:24px;
      align-items:flex-start;
      margin-top:18px;
      background: linear-gradient(180deg, var(--glass), transparent);
      border-radius:var(--radius);
      padding:18px;
      box-shadow: 0 6px 30px rgba(0,0,0,0.45);
      border: 1px solid rgba(255,255,255,0.03);
    }

    .hero .lead{
      flex:1;
      min-width:320px;
    }

    .hero .cta{
      display:flex;
      gap:10px;
      margin-top:14px;
      flex-wrap:wrap;
    }

    .btn{
      background:linear-gradient(90deg,var(--accent),#6e54ff);
      color:white; padding:10px 14px; border-radius:10px; text-decoration:none; font-weight:600;
      display:inline-flex; gap:10px; align-items:center; box-shadow: 0 8px 20px rgba(124,92,255,0.12);
    }
    .btn.secondary{
      background:transparent; border: 1px solid rgba(255,255,255,0.06); color:var(--white); font-weight:600;
    }

    main{
      margin-top:22px;
      display:grid;
      grid-template-columns: 1fr 360px;
      gap:20px;
    }

    .card{
      background:linear-gradient(180deg,var(--card), rgba(255,255,255,0.01));
      border-radius:12px;
      padding:18px;
      border:1px solid rgba(255,255,255,0.02);
    }

    .section-title{ font-weight:700; margin:0 0 12px 0; color:var(--white); font-size:1.05rem; }

    .features{ display:grid; grid-template-columns:repeat(2,1fr); gap:12px; }
    .feature{
      background:var(--glass-2);
      border-radius:10px; padding:12px; display:flex; gap:12px; align-items:center;
      border:1px solid rgba(255,255,255,0.02);
    }
    .feature svg{ width:34px; height:34px; flex-shrink:0; }

    .about p{ color:var(--muted); line-height:1.5; margin:0 0 10px 0; }

    .info-list{ color:var(--muted); display:grid; gap:8px; font-size:0.95rem; }
    .info-list a{ color:var(--accent-2); text-decoration:none; }

    .table{
      width:100%;
      border-collapse:collapse;
      font-size:0.95rem;
      color:var(--muted);
    }
    .table th, .table td{ padding:10px 12px; text-align:left; border-bottom:1px dashed rgba(255,255,255,0.02); }
    .table th{ color:var(--white); font-weight:700; font-size:0.95rem; }

    .visual{
      height:160px;
      border-radius:10px;
      background: linear-gradient(90deg, rgba(124,92,255,0.08), rgba(54,214,164,0.04));
      display:flex; align-items:center; justify-content:center;
      color:var(--muted);
      border:1px dashed rgba(255,255,255,0.03);
    }

    footer{ margin-top:28px; color:var(--muted); font-size:0.9rem; display:flex; justify-content:space-between; align-items:center; gap:12px; }

    .authors{ display:flex; gap:10px; align-items:center; }
    .author{ display:flex; flex-direction:column; gap:2px; font-size:0.9rem; color:var(--muted); }
    .small-note{ font-size:0.85rem; color:var(--muted); }

    @media (max-width:980px){
      main{ grid-template-columns: 1fr; }
      .badges{ justify-content:flex-end; }
      .hero{ flex-direction:column; align-items:stretch; }
    }

    /* small code block style */
    pre.code{
      background: #061223;
      padding:12px;
      border-radius:8px;
      overflow:auto;
      color:#cde7ff;
      border:1px solid rgba(255,255,255,0.02);
      font-size:0.9rem;
    }

    /* pill */
    .pill { background: rgba(255,255,255,0.03); padding:6px 10px; border-radius:999px; font-weight:600; color:var(--muted); font-size:0.85rem; border:1px solid rgba(255,255,255,0.02); }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="logo" title="MoonHabitableZone">
        <!-- moon + orbit icon -->
        <svg viewBox="0 0 64 64" width="52" height="52" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <defs><linearGradient id="g" x1="0" x2="1"><stop offset="0" stop-color="#fff" stop-opacity="0.9"/><stop offset="1" stop-color="#fff" stop-opacity="0.6"/></linearGradient></defs>
          <circle cx="32" cy="28" r="12" fill="url(#g)" fill-opacity="0.95"/>
          <path d="M14 44c12-6 26-6 36-2" stroke="rgba(0,0,0,0.08)" stroke-width="6" stroke-linecap="round" />
          <circle cx="44" cy="38" r="1.6" fill="#071029"/>
        </svg>
      </div>

      <div>
        <h1>MoonHabitableZone</h1>
        <div class="subtitle">Python toolkit for exomoon detection, computing Hill radius, Roche limit and a Moon Stability Zone (MSZ) formula.</div>
      </div>

      <div class="badges">
        <img src="https://zenodo.org/badge/DOI/10.5281/zenodo.17366586.svg" alt="DOI" style="height:26px;">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT" style="height:26px;">
        <span class="pill">Python 3.10+</span>
      </div>
    </header>

    <section class="hero card" aria-labelledby="project-overview">
      <div class="lead">
        <h2 id="project-overview" class="section-title">Overview</h2>
        <div class="about">
          <p><strong>MoonHabitableZone</strong> is a research toolkit that blends astrophysics, data science and machine learning to search for moons around exoplanets. It defines a Moon Stability Zone (MSZ) using orbital dynamics — specifically Hill radius and Roche limit — and integrates a Decision Tree model to flag potential moon-hosting planets.</p>

          <div style="display:flex; gap:12px; margin-top:10px; flex-wrap:wrap;">
            <a class="btn" href="https://github.com/swayamsikarwar/MoonHabitableZone">View on GitHub</a>
            <a class="btn secondary" href="https://doi.org/10.5281/zenodo.17366586">DOI / Zenodo</a>
          </div>
        </div>
      </div>

      <aside style="min-width:260px; display:flex; flex-direction:column; gap:12px;">
        <div class="card" style="background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);">
          <div class="section-title" style="font-size:0.95rem;">Quick Stats</div>
          <div style="display:flex; gap:12px; margin-top:8px; align-items:center;">
            <div style="flex:1;">
              <div style="font-size:1.25rem; font-weight:800;">MSZ Formula</div>
              <div class="small-note">MSZ = Stable Radius − Roche Limit</div>
            </div>
            <div style="text-align:right;">
              <div style="font-weight:700; color:var(--accent); font-size:1.1rem;">Validated</div>
              <div class="small-note">Solar System moons</div>
            </div>
          </div>
        </div>

        <div class="card">
          <div class="section-title" style="font-size:0.95rem;">Install & Run</div>
          <pre class="code">git clone https://github.com/swayamsikarwar/MoonHabitableZone.git
cd MoonHabitableZone
pip install -r requirements.txt

# run analysis
python scripts/moon_stability_zone.py

# or notebook
jupyter notebook notebooks/MoonHabitableZone.ipynb</pre>
        </div>
      </aside>
    </section>

    <main>
      <div>
        <section class="card" aria-labelledby="features">
          <h3 id="features" class="section-title">Key Features</h3>
          <div class="features" style="margin-top:8px;">
            <div class="feature">
              <!-- icon -->
              <svg viewBox="0 0 24 24" fill="none" aria-hidden>
                <path d="M12 2v20" stroke="#7c5cff" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
                <path d="M4 12h16" stroke="#36d6a4" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <div>
                <div style="font-weight:700">Orbital Calculations</div>
                <div style="color:var(--muted); font-size:0.92rem;">Hill radius, Roche limit and MSZ calculation suite.</div>
              </div>
            </div>

            <div class="feature">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden>
                <circle cx="12" cy="8" r="3" stroke="#7c5cff" stroke-width="1.6"/>
                <path d="M6 20c4-3 8-3 12 0" stroke="#36d6a4" stroke-width="1.6" stroke-linecap="round"/>
              </svg>
              <div>
                <div style="font-weight:700">Machine Learning</div>
                <div style="color:var(--muted); font-size:0.92rem;">Decision Tree classifier for candidate detection and evaluation metrics.</div>
              </div>
            </div>

            <div class="feature">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden>
                <rect x="3" y="3" width="18" height="14" rx="2" stroke="#7c5cff" stroke-width="1.6"/>
                <path d="M7 21h10" stroke="#36d6a4" stroke-width="1.6" stroke-linecap="round"/>
              </svg>
              <div>
                <div style="font-weight:700">Visualizations</div>
                <div style="color:var(--muted); font-size:0.92rem;">Correlation matrices, scatter plots, MSZ charts saved under results/visualizations/.</div>
              </div>
            </div>

            <div class="feature">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden>
                <path d="M12 2c5.523 0 10 4.477 10 10S17.523 22 12 22 2 17.523 2 12 6.477 2 12 2z" stroke="#7c5cff" stroke-width="1.6"/>
                <path d="M12 7v5l3 3" stroke="#36d6a4" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <div>
                <div style="font-weight:700">Research Reproducible</div>
                <div style="color:var(--muted); font-size:0.92rem;">Code, notebooks and datasets consolidated for reproducible experiments.</div>
              </div>
            </div>
          </div>
        </section>

        <section class="card" style="margin-top:16px;" aria-labelledby="methodology">
          <h3 id="methodology" class="section-title">Methodology</h3>
          <div style="display:grid; gap:12px; margin-top:8px;">
            <div class="pill">Data Collection</div>
            <div class="about">
              <p>Source: NASA Exoplanet Archive. Extracted planetary & host-star features like mass, radius, orbital period, stellar mass and temperature.</p>
            </div>

            <div class="pill">Data Cleaning & Filtering</div>
            <div class="about">
              <p>Nulls and duplicates removed. Focus on planets with Transit Time Variation (TTV > 0) to increase moon-detection sensitivity.</p>
            </div>

            <div class="pill">Orbit Computation</div>
            <div class="about">
              <p>Compute Hill radius, Roche limit, then MSZ = Stable Radius − Roche Limit. If moon diameter &lt; MSZ → stable orbit possible.</p>
            </div>

            <div class="pill">ML Integration & Validation</div>
            <div class="about">
              <p>Decision Tree classifier used for binary classification (has_moon/no_moon). Validated on Solar System cases (Earth–Moon, Jupiter–Europa, Saturn–Titan).</p>
            </div>
          </div>
        </section>

        <section class="card" style="margin-top:16px;" aria-labelledby="results">
          <h3 id="results" class="section-title">Results</h3>

          <p style="color:var(--muted); margin-top:6px;">MSZ and classifier produce candidate lists; examples below are summary entries from validation and candidate detections:</p>

          <div style="overflow:auto; margin-top:10px;">
            <table class="table" role="table" aria-label="Results sample">
              <thead>
                <tr>
                  <th>Exoplanet</th>
                  <th>Stability Zone</th>
                  <th>Potential Moon</th>
                  <th>Validation</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td><strong>TOI 1130 b</strong></td>
                  <td>Stable</td>
                  <td>✅ Likely Host</td>
                  <td>Supported by model</td>
                </tr>
                <tr>
                  <td><strong>TOI 1266 b</strong></td>
                  <td>Stable</td>
                  <td>✅ Likely Host</td>
                  <td>Supported by model</td>
                </tr>
                <tr>
                  <td>Earth (Test)</td>
                  <td>378,029 km</td>
                  <td>✅ Moon stable</td>
                  <td>Verified</td>
                </tr>
                <tr>
                  <td>Jupiter – Europa</td>
                  <td>628,900 km</td>
                  <td>✅ Moon stable</td>
                  <td>Verified</td>
                </tr>
                <tr>
                  <td>Saturn – Titan</td>
                  <td>1,140,000 km</td>
                  <td>✅ Moon stable</td>
                  <td>Verified</td>
                </tr>
              </tbody>
            </table>
          </div>

          <div style="display:flex; gap:12px; margin-top:12px; align-items:center;">
            <div class="visual" style="flex:1;">Correlation Matrix (saved in results/visualizations)</div>
            <div class="visual" style="width:220px;">MSZ Chart</div>
          </div>

          <div style="margin-top:12px; color:var(--muted);">
            <strong>Model performance:</strong> Decision Tree — ~80% accuracy with emphasis on F2 / recall to minimize false negatives.
          </div>
        </section>

        <section class="card" style="margin-top:16px;" aria-labelledby="references">
          <h3 id="references" class="section-title">References</h3>
          <ul style="color:var(--muted); margin:0; padding-left:18px;">
            <li><a href="https://exoplanetarchive.ipac.caltech.edu/" style="color:var(--accent-2)">NASA Exoplanet Archive</a></li>
            <li>Harris et al. (2020). Array Programming with NumPy.</li>
            <li>McKinney, W. (2010). Data Structures for Statistical Computing in Python.</li>
            <li>Kipping, D.M. (2011). Transit Timing Effects Due to an Exomoon. MNRAS.</li>
            <li>Murray & Dermott (1999). Solar System Dynamics. Cambridge University Press.</li>
          </ul>
        </section>
      </div>

      <aside>
        <div class="card" aria-labelledby="contrib">
          <h4 id="contrib" class="section-title">Repository Structure</h4>
          <div class="info-list" style="margin-top:8px;">
            <div><strong>scripts/</strong> — analysis scripts (moon_stability_zone.py)</div>
            <div><strong>notebooks/</strong> — interactive workflow & experiments</div>
            <div><strong>results/</strong> — visualizations, tables and exports</div>
            <div><strong>requirements.txt</strong> — Python dependencies</div>
            <div><strong>LICENSE</strong> — MIT License</div>
          </div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h4 class="section-title">How to Cite</h4>
          <div style="color:var(--muted); margin-top:8px;">
            S. S. Sikarwar et al., “Discovery of Potential Moons Around Exoplanets: Data Analysis Using Python and Development of a Moon Stability Zone Formula”, DOI: <a href="https://doi.org/10.5281/zenodo.17366586" style="color:var(--accent-2)">10.5281/zenodo.17366586</a>
          </div>
        </div>

        <div class="card" style="margin-top:12px;">
          <h4 class="section-title">Authors & Acknowledgements</h4>
          <div class="authors" style="margin-top:8px;">
            <div class="author"><strong>Swayam Singh Sikarwar</strong><span class="small-note">Lead Researcher & Developer — SDBCE, Indore</span></div>
            <div class="author"><strong>Jagriti Singh Thakur</strong><span class="small-note">Research Co-Author — SDBCE, Indore</span></div>
          </div>

          <div style="margin-top:10px; color:var(--muted); font-size:0.92rem;">
            Thanks to NASA Exoplanet Science Institute, the Python scientific community and Zenodo.
          </div>
        </div>

        <div class="card" style="margin-top:12px; display:flex; flex-direction:column; gap:10px;">
          <div class="section-title" style="font-size:0.95rem;">Quick Links</div>
          <a href="https://github.com/swayamsikarwar/MoonHabitableZone" class="btn" style="justify-content:center;">GitHub Repo</a>
          <a href="https://doi.org/10.5281/zenodo.17366586" class="btn secondary" style="justify-content:center;">Zenodo DOI</a>
        </div>
      </aside>
    </main>

    <footer>
      <div>Released under the MIT License — <a href="LICENSE" style="color:var(--accent-2)">LICENSE</a></div>
      <div style="color:var(--muted)">“Exploring the unseen moons of distant worlds — one dataset at a time.” 🌙</div>
    </footer>
  </div>
</body>
</html>
