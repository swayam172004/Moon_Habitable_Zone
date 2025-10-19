<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MoonHabitableZone — Exomoon Detection Toolkit</title>
  
  <!-- 🧭 SEO & Social Meta -->
  <meta name="description" content="MoonHabitableZone — A Python toolkit for detecting exomoons using Hill radius, Roche limit & Moon Stability Zone (MSZ) formula.">
  <meta property="og:title" content="MoonHabitableZone — Exomoon Detection Toolkit">
  <meta property="og:description" content="A scientific toolkit for exomoon detection using orbital mechanics, Hill sphere, Roche limit and MSZ formula.">
  <meta property="og:image" content="https://yourdomain.com/preview.png">
  <meta property="og:url" content="https://yourdomain.com">
  <meta name="twitter:card" content="summary_large_image">

  <link rel="icon" href="favicon.ico" />
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" />

  <style>
    :root {
      --bg: #0a0a0a;
      --fg: #f1f1f1;
      --accent: #4ac1ff;
      --gradient: linear-gradient(90deg, #4ac1ff, #9b59b6);
    }

    body {
      background-color: var(--bg);
      color: var(--fg);
      font-family: 'Inter', sans-serif;
      margin: 0;
      padding: 0;
      line-height: 1.6;
    }

    header {
      padding: 1.5rem;
      text-align: center;
      background: var(--gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    header h1 {
      font-size: 2.5rem;
      font-weight: 800;
    }

    .hero {
      text-align: center;
      padding: 3rem 1rem;
    }

    .hero p {
      max-width: 650px;
      margin: 1rem auto;
      font-size: 1.2rem;
      color: #ccc;
    }

    .cta-buttons {
      display: flex;
      justify-content: center;
      gap: 1rem;
      margin-top: 1rem;
    }

    .cta-buttons a {
      background: var(--gradient);
      padding: 0.8rem 1.5rem;
      color: white;
      text-decoration: none;
      font-weight: 600;
      border-radius: 8px;
      transition: transform 0.2s ease;
    }

    .cta-buttons a:hover {
      transform: scale(1.05);
    }

    section {
      max-width: 900px;
      margin: 2rem auto;
      padding: 1rem;
    }

    .section-title {
      font-size: 1.8rem;
      margin-bottom: 1rem;
      text-align: center;
      background: var(--gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .card {
      background: #111;
      padding: 1.5rem;
      margin-top: 1rem;
      border-radius: 12px;
      border: 1px solid #222;
    }

    footer {
      text-align: center;
      padding: 1rem;
      font-size: 0.9rem;
      border-top: 1px solid #222;
      color: #777;
    }

    /* Orbit Animation */
    #orbitCanvas {
      display: block;
      margin: 0 auto;
      background: #0f0f0f;
      border-radius: 50%;
      border: 1px solid #222;
    }

    /* Calculator styling */
    .calculator label {
      display: block;
      margin-top: 0.5rem;
      color: #ccc;
    }

    .calculator input {
      width: 100%;
      padding: 0.5rem;
      margin-top: 0.2rem;
      background: #222;
      border: none;
      color: #fff;
      border-radius: 6px;
    }

    .calculator button {
      margin-top: 1rem;
      background: var(--gradient);
      border: none;
      padding: 0.7rem 1.5rem;
      color: #fff;
      font-weight: 600;
      border-radius: 8px;
      cursor: pointer;
    }

    pre.code {
      background: #000;
      padding: 1rem;
      color: #4ac1ff;
      border-radius: 8px;
      overflow-x: auto;
    }

    @media (max-width: 600px) {
      .cta-buttons {
        flex-direction: column;
        align-items: center;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>MoonHabitableZone</h1>
    <p>Exomoon Detection & Moon Stability Zone Toolkit</p>
  </header>

  <section class="hero">
    <p>
      A research-grade open-source toolkit that combines <strong>Hill radius</strong>, 
      <strong>Roche limit</strong>, and a newly derived <strong>Moon Stability Zone</strong> (MSZ) formula
      to detect potential exomoons around exoplanets.
    </p>
    <div class="cta-buttons">
      <a href="https://github.com/yourusername/MoonHabitableZone" target="_blank">View on GitHub</a>
      <a href="https://doi.org/10.5281/zenodo.17366586" target="_blank">View DOI</a>
    </div>
  </section>

  <section>
    <h2 class="section-title">🔭 Orbital Visualization</h2>
    <div class="card">
      <canvas id="orbitCanvas" width="300" height="300"></canvas>
    </div>
  </section>

  <section>
    <h2 class="section-title">🧮 MSZ Calculator</h2>
    <div class="card calculator">
      <label for="mass">Planetary Mass (in kg)</label>
      <input type="number" id="mass" placeholder="e.g. 5.972e24">
      
      <label for="radius">Planetary Radius (in m)</label>
      <input type="number" id="radius" placeholder="e.g. 6.371e6">

      <label for="a">Semi-major axis (in m)</label>
      <input type="number" id="a" placeholder="e.g. 1.5e11">

      <label for="starMass">Star Mass (in kg)</label>
      <input type="number" id="starMass" placeholder="e.g. 1.989e30">

      <button onclick="calculateMSZ()">Calculate MSZ</button>
      <p id="result"></p>
    </div>
  </section>

  <section>
    <h2 class="section-title">📜 Citation</h2>
    <div class="card">
<pre class="code">
@software{swayam_2025_moonhabitablezone,
  author       = {Swayam Sikarwar},
  title        = {MoonHabitableZone: Exomoon Detection & Moon Stability Zone Formula},
  year         = 2025,
  doi          = {10.5281/zenodo.17366586},
  url          = {https://doi.org/10.5281/zenodo.17366586}
}
</pre>
    </div>
  </section>

  <footer>
    © 2025 MoonHabitableZone — Built with ❤️ by Swayam Sikarwar  
    <div>
      <a href="https://github.com/yourusername/MoonHabitableZone" target="_blank">GitHub</a> · 
      <a href="https://doi.org/10.5281/zenodo.17366586" target="_blank">DOI</a>
    </div>
  </footer>

  <script>
    // Orbit animation
    const canvas = document.getElementById('orbitCanvas');
    const ctx = canvas.getContext('2d');
    let angle = 0;

    function drawOrbit() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      const cx = canvas.width / 2;
      const cy = canvas.height / 2;
      const r = 100;

      // orbit path
      ctx.beginPath();
      ctx.arc(cx, cy, r, 0, 2 * Math.PI);
      ctx.strokeStyle = '#333';
      ctx.stroke();

      // planet
      ctx.beginPath();
      ctx.arc(cx, cy, 10, 0, 2 * Math.PI);
      ctx.fillStyle = '#4ac1ff';
      ctx.fill();

      // moon
      const mx = cx + r * Math.cos(angle);
      const my = cy + r * Math.sin(angle);
      ctx.beginPath();
      ctx.arc(mx, my, 6, 0, 2 * Math.PI);
      ctx.fillStyle = '#9b59b6';
      ctx.fill();

      angle += 0.02;
      requestAnimationFrame(drawOrbit);
    }
    drawOrbit();

    // MSZ Calculator
    function calculateMSZ() {
      const G = 6.67430e-11;
      const mass = parseFloat(document.getElementById('mass').value);
      const radius = parseFloat(document.getElementById('radius').value);
      const a = parseFloat(document.getElementById('a').value);
      const starMass = parseFloat(document.getElementById('starMass').value);

      if (isNaN(mass) || isNaN(radius) || isNaN(a) || isNaN(starMass)) {
        document.getElementById('result').innerText = '⚠️ Please fill in all fields correctly.';
        return;
      }

      const hillRadius = a * Math.cbrt(mass / (3 * starMass));
      const rocheLimit = 2.44 * radius;
      const mszInner = rocheLimit;
      const mszOuter = 0.5 * hillRadius;

      document.getElementById('result').innerHTML = `
        🪐 Hill Radius: <strong>${hillRadius.toExponential(3)}</strong> m<br>
        🌑 Roche Limit: <strong>${rocheLimit.toExponential(3)}</strong> m<br>
        📏 MSZ: <strong>${mszInner.toExponential(3)} m - ${mszOuter.toExponential(3)} m</strong>
      `;
    }
  </script>
</body>
</html>