!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#764ba2">
  <title>Android Apps</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #667eea, #764ba2);
      min-height: 100vh;
      margin: 0;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .card {
      background: white;
      padding: 40px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }
    h1 { margin-top: 0; color: #333; }
    #count {
      font-size: 64px;
      font-weight: bold;
      color: #764ba2;
      margin: 20px 0;
    }
    button {
      font-size: 20px;
      padding: 12px 24px;
      margin: 5px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      color: white;
    }
    #plus { background: #27ae60; }
    #minus { background: #e67e22; }
    #reset { background: #c0392b; }
    button:hover { opacity: 0.85; }
  </style>
</head>
<body>
  <div class="card">
    <h1>Android Apps</h1>
    <div id="count">0</div>
    <button id="plus" onclick="change(1)">+ Increase</button>
    <button id="minus" onclick="change(-1)">- Decrease</button>
    <button id="reset" onclick="reset()">Reset</button>
  </div>

  <script>
    // ---------- Counter logic (saved on the phone) ----------
    let count = parseInt(localStorage.getItem('count') || '0', 10);
    const display = document.getElementById('count');
    display.textContent = count;

    function save() {
      localStorage.setItem('count', count);
      display.textContent = count;
    }
    function change(n) { count += n; save(); }
    function reset() { count = 0; save(); }

    // ---------- Make it installable (PWA) ----------
    // Draw a simple app icon with canvas
    function makeIcon(size) {
      const c = document.createElement('canvas');
      c.width = c.height = size;
      const ctx = c.getContext('2d');
      const g = ctx.createLinearGradient(0, 0, size, size);
      g.addColorStop(0, '#667eea');
      g.addColorStop(1, '#764ba2');
      ctx.fillStyle = g;
      ctx.fillRect(0, 0, size, size);
      ctx.fillStyle = 'white';
      ctx.font = 'bold ' + (size * 0.6) + 'px Arial';
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';
      ctx.fillText('+1', size / 2, size / 2);
      return c.toDataURL('image/png');
    }

    // Build the manifest inside the page
    const manifest = {
      name: 'Android Apps',
      short_name: 'Counter',
      start_url: '.',
      display: 'standalone',
      background_color: '#764ba2',
      theme_color: '#764ba2',
      icons: [
        { src: makeIcon(192), sizes: '192x192', type: 'image/png' },
        { src: makeIcon(512), sizes: '512x512', type: 'image/png' }
      ]
    };
    const link = document.createElement('link');
    link.rel = 'manifest';
    link.href = URL.createObjectURL(
      new Blob([JSON.stringify(manifest)], { type: 'application/json' })
    );
    document.head.appendChild(link);
  </script>
</body>
</html>
What changed from your version
• The counter number is now saved on the phone, so it stays after you close the app.
• The page builds its own icon and install information, so no extra files are needed.
• It opens full screen without the browser address bar once installed.
