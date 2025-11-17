<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Tampilan Coklat — Contoh</title>
  <style>
    :root{
      --brown-1: #3b2f2f;
      --brown-2: #6b4f3a;
      --brown-3: #a67b5b;
      --cream: #f6efe6;
      --shadow: rgba(17,12,7,0.35);
    }

    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
      background: linear-gradient(180deg, var(--brown-1) 0%, #2f2424 50%);
      color:var(--cream);
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:40px;
    }

    .container{
      width:100%;
      max-width:1000px;
      background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(0,0,0,0.06));
      border-radius:18px;
      padding:28px;
      box-shadow: 0 10px 30px var(--shadow);
      display:grid;
      grid-template-columns: 1fr 420px;
      gap:24px;
      align-items:center;
    }

    .left{
      padding:10px 18px;
    }
    h1{
      margin:0 0 8px 0;
      font-size:28px;
      letter-spacing:0.4px;
      color:var(--cream);
    }
    p.lead{
      margin:0 0 18px 0;
      color: #e9dacb;
      line-height:1.5;
    }

    .btn-row{
      display:flex;
      gap:12px;
      margin-top:18px;
    }
    .btn{
      background: linear-gradient(180deg,var(--brown-2),var(--brown-3));
      border: none;
      padding:10px 16px;
      border-radius:10px;
      color:var(--cream);
      font-weight:600;
      cursor:pointer;
      box-shadow: 0 6px 14px rgba(0,0,0,0.25);
    }
    .btn.ghost{
      background:transparent;
      border:1px solid rgba(255,255,255,0.06);
      color: #f0e7de;
    }

    .card-right{
      background: linear-gradient(180deg,#5a4436 0%, #442e22 100%);
      border-radius:14px;
      padding:18px;
      box-shadow: inset 0 -6px 20px rgba(0,0,0,0.2), 0 8px 24px rgba(0,0,0,0.35);
      display:flex;
      flex-direction:column;
      gap:12px;
      align-items:center;
      justify-content:center;
    }

    .cig-card{
      width:100%;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.08));
      padding:14px;
      border-radius:10px;
      display:flex;
      gap:14px;
      align-items:center;
    }

    /* Stylized cigarette (SVG inside) */
    .cig-visual{
      width:130px;
      height:60px;
      display:flex;
      align-items:center;
      justify-content:center;
    }

    .cig-info{
      flex:1;
      color:#f3e9dd;
    }
    .muted{color:#e0cdbf; font-size:14px}

    footer{
      margin-top:8px;
      font-size:12px;
      color:#cfbdae;
      opacity:0.9;
    }

    /* responsive */
    @media (max-width:900px){
      .container{grid-template-columns:1fr; padding:18px}
      .cig-visual{width:100%; height:90px}
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="left">
      <h1>Tampilan Coklat — Desain Rapi</h1>
      <p class="lead">Desain ini menggunakan palet coklat hangat, tipografi modern, dan elemen visual sederhana. Di sebelah kanan ada ilustrasi rokok bergaya vektor (bukan foto) sehingga bebas hak cipta — cocok untuk mockup atau demo UI.</p>

      <div class="btn-row">
        <button class="btn">Lihat Detail</button>
        <button class="btn ghost">Download</button>
      </div>

      <div style="margin-top:22px; background:rgba(0,0,0,0.12); padding:12px; border-radius:10px;">
        <p style="margin:0; font-size:14px; color:#f1e7db">Catatan: Jika kamu ingin menampilkan <strong>gambar rokok nyata</strong> (foto), kirim gambarnya atau saya bisa ambil dari sumber bebas lisensi dan saya pasang ke desain.</p>
      </div>

      <footer>Contoh UI • Tema Coklat • 2025</footer>
    </div>

    <aside class="card-right">
      <div class="cig-card">
        <div class="cig-visual" aria-hidden="true">
          <!-- Inline SVG: stylized cigarette -->
          <svg width="220" height="80" viewBox="0 0 220 80" xmlns="http://www.w3.org/2000/svg" role="img">
            <!-- Filter / shadow -->
            <defs>
              <filter id="soft" x="-20%" y="-20%" width="140%" height="140%">
                <feDropShadow dx="0" dy="6" stdDeviation="8" flood-color="#000" flood-opacity="0.25"/>
              </filter>
            </defs>

            <!-- cigarette body -->
            <rect x="6" y="22" rx="10" ry="10" width="150" height="22" fill="#fff" stroke="#e6ddd2" />

            <!-- tobacco end -->
            <rect x="156" y="22" rx="8" ry="8" width="44" height="22" fill="#b97b4a" stroke="#9a5f37" />

            <!-- filter tip -->
            <rect x="198" y="22" rx="6" ry="6" width="12" height="22" fill="#cfa57b" stroke="#a77b4f" />

            <!-- ash (subtle) -->
            <ellipse cx="154" cy="33" rx="10" ry="4" fill="#3b2b2b" opacity="0.08" />

            <!-- glow/inner lines -->
            <line x1="20" y1="30" x2="140" y2="30" stroke="#f6efe6" stroke-opacity="0.06" stroke-width="2"/>

            <!-- small smoke curls -->
            <g transform="translate(-16,-20)" fill="none" stroke="#e9dccf" stroke-opacity="0.18" stroke-width="1.4">
              <path d="M120 40 C118 36, 114 34, 112 30" />
              <path d="M126 36 C125 32, 120 30, 118 26" />
            </g>

            <!-- subtle highlight -->
            <rect x="12" y="24" rx="8" ry="8" width="8" height="18" fill="#fff3e8" opacity="0.06" />
          </svg>
        </div>

        <div class="cig-info">
          <div style="font-weight:700; font-size:16px;">Ilustrasi Rokok (Vektor)</div>
          <div class="muted">Gaya minimal &amp; estetik — cocok untuk mockup, presentasi, atau demo UI.</div>
        </div>
      </div>

      <div style="width:100%; display:flex; gap:10px; margin-top:8px;">
        <div style="flex:1; background:rgba(255,255,255,0.03); padding:10px; border-radius:8px; text-align:center;">
          <div style="font-weight:700;">Estetika</div>
          <div class="muted">Coklat hangat</div>
        </div>
        <div style="flex:1; background:rgba(255,255,255,0.03); padding:10px; border-radius:8px; text-align:center;">
          <div style="font-weight:700;">Lisensi</div>
          <div class="muted">Vektor gratis</div>
        </div>
      </div>

    </aside>
  </div>
</body>
</html>
