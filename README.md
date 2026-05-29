# Metodo-BIC
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Método BIC — Kinbai·Cora · Creatividad Aplicada</title>
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@300;400;700;900&family=Syne:wght@400;600;700;800&family=Newsreader:ital,wght@0,300;0,400;1,300;1,400&display=swap" rel="stylesheet">
<style>
/* ============================================
   RESET & BASE
   ============================================ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
 
:root {
  --cream: #f5f0e8;
  --cream-dark: #e8e0d0;
  --ink: #1a1410;
  --ink-soft: #3d352c;
  --gold: #c8921a;
  --gold-light: #f0c04a;
  --rust: #b84a2a;
  --forest: #2d5a3d;
  --sky: #2a5f82;
  --wine: #6b2040;
  --sand: #d4b896;
  --paper: #faf7f0;
 
  --dato-color: #2d5a3d;
  --anec-color: #b84a2a;
  --reflex-color: #c8921a;
  --emoc-color: #2a5f82;
 
  --font-display: 'Unbounded', sans-serif;
  --font-head: 'Syne', sans-serif;
  --font-body: 'Newsreader', serif;
}
 
html { scroll-behavior: smooth; }
 
body {
  font-family: var(--font-body);
  background-color: var(--cream);
  color: var(--ink);
  line-height: 1.7;
  overflow-x: hidden;
}
 
/* Grain texture overlay */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 1000;
  opacity: 0.025;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}
 
/* ============================================
   TYPOGRAPHY
   ============================================ */
h1, h2, h3 { font-family: var(--font-head); font-weight: 800; line-height: 1.1; }
h4, h5 { font-family: var(--font-head); font-weight: 700; }
 
.display { font-family: var(--font-display); font-weight: 900; line-height: 1; }
.mono { font-family: 'Courier New', monospace; font-size: 0.75em; letter-spacing: 0.12em; text-transform: uppercase; }
 
/* ============================================
   HERO HEADER
   ============================================ */
.hero {
  background: var(--ink);
  color: var(--cream);
  min-height: 100vh;
  display: grid;
  grid-template-rows: 1fr auto;
  padding: 0;
  position: relative;
  overflow: hidden;
}
 
.hero-bg-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: var(--font-display);
  font-weight: 900;
  font-size: clamp(100px, 22vw, 320px);
  color: rgba(255,255,255,0.03);
  white-space: nowrap;
  pointer-events: none;
  user-select: none;
  letter-spacing: -0.05em;
}
 
.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0;
  min-height: 100vh;
  position: relative;
  z-index: 1;
}
 
.hero-left {
  padding: 80px 60px 80px 80px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  border-right: 1px solid rgba(255,255,255,0.08);
}
 
.hero-right {
  padding: 80px 80px 80px 60px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}
 
.hero-tag {
  display: inline-block;
  font-family: 'Courier New', monospace;
  font-size: 10px;
  letter-spacing: 4px;
  text-transform: uppercase;
  color: var(--gold);
  border: 1px solid var(--gold);
  padding: 6px 16px;
  border-radius: 0;
  margin-bottom: 32px;
  width: fit-content;
}
 
.hero-title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: clamp(42px, 7vw, 96px);
  line-height: 0.95;
  letter-spacing: -0.03em;
  margin-bottom: 24px;
}
 
.hero-title em {
  font-style: normal;
  color: var(--gold);
}
 
.hero-subtitle {
  font-size: 15px;
  color: rgba(255,255,255,0.55);
  max-width: 380px;
  line-height: 1.8;
  font-style: italic;
}
 
.hero-meta {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1px;
  background: rgba(255,255,255,0.08);
  border: 1px solid rgba(255,255,255,0.08);
  margin-top: 40px;
}
 
.hero-meta-item {
  padding: 20px 24px;
  background: var(--ink);
}
 
.hero-meta-item .label {
  font-size: 9px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.35);
  font-family: 'Courier New', monospace;
  display: block;
  margin-bottom: 4px;
}
 
.hero-meta-item .value {
  font-size: 13px;
  font-family: var(--font-head);
  font-weight: 600;
  color: rgba(255,255,255,0.85);
}
 
.hero-nav {
  display: flex;
  flex-direction: column;
  gap: 2px;
  margin-bottom: 60px;
}
 
.hero-nav a {
  display: flex;
  align-items: center;
  gap: 16px;
  text-decoration: none;
  color: rgba(255,255,255,0.4);
  font-family: 'Courier New', monospace;
  font-size: 11px;
  letter-spacing: 2px;
  text-transform: uppercase;
  padding: 12px 0;
  border-bottom: 1px solid rgba(255,255,255,0.05);
  transition: color 0.2s, gap 0.2s;
}
 
.hero-nav a:hover { color: var(--gold); gap: 24px; }
 
.hero-nav a .nav-num {
  color: rgba(255,255,255,0.2);
  font-size: 9px;
}
 
.hero-scroll {
  display: flex;
  align-items: center;
  gap: 12px;
  color: rgba(255,255,255,0.3);
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 3px;
  text-transform: uppercase;
}
 
.hero-scroll::before {
  content: '';
  width: 40px;
  height: 1px;
  background: rgba(255,255,255,0.2);
}
 
/* ============================================
   SECTION WRAPPERS
   ============================================ */
.section {
  padding: 120px 80px;
  max-width: 1400px;
  margin: 0 auto;
}
 
.section-narrow {
  padding: 120px 80px;
  max-width: 1100px;
  margin: 0 auto;
}
 
.section-full {
  padding: 120px 0;
}
 
.section-divider {
  height: 1px;
  background: var(--ink);
  opacity: 0.1;
  margin: 0 80px;
}
 
.chapter-header {
  display: flex;
  align-items: flex-start;
  gap: 24px;
  margin-bottom: 64px;
}
 
.chapter-number {
  font-family: var(--font-display);
  font-size: 72px;
  font-weight: 900;
  line-height: 1;
  color: var(--cream-dark);
  flex-shrink: 0;
  margin-top: -8px;
  user-select: none;
}
 
.chapter-info {}
.chapter-tag {
  display: block;
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 8px;
}
 
.chapter-title {
  font-size: clamp(28px, 4vw, 48px);
  font-family: var(--font-display);
  font-weight: 900;
  letter-spacing: -0.02em;
  line-height: 1.05;
}
 
.chapter-desc {
  margin-top: 12px;
  font-size: 15px;
  color: var(--ink-soft);
  max-width: 600px;
  font-style: italic;
}
 
/* ============================================
   AUTORES STRIP
   ============================================ */
.autores-strip {
  background: var(--ink);
  color: var(--cream);
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  border-top: 3px solid var(--gold);
}
 
.autor-block {
  padding: 40px 48px;
  border-right: 1px solid rgba(255,255,255,0.08);
  position: relative;
}
 
.autor-block:last-child { border-right: none; }
 
.autor-num {
  font-family: var(--font-display);
  font-size: 80px;
  font-weight: 900;
  color: rgba(255,255,255,0.04);
  position: absolute;
  top: 16px;
  right: 24px;
  line-height: 1;
}
 
.autor-label {
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
  display: block;
  margin-bottom: 8px;
}
 
.autor-name {
  font-family: var(--font-head);
  font-size: 20px;
  font-weight: 800;
  margin-bottom: 4px;
}
 
.autor-role {
  font-size: 12px;
  color: rgba(255,255,255,0.4);
  font-style: italic;
}
 
/* ============================================
   B-DARE GRID
   ============================================ */
.bdare-layout {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 0;
  border: 1px solid rgba(26,20,16,0.15);
  margin-bottom: 48px;
  overflow: hidden;
}
 
.bdare-sidebar {
  background: var(--ink);
  color: var(--cream);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 40px 24px;
  position: sticky;
  top: 0;
}
 
.bdare-letter {
  font-family: var(--font-display);
  font-size: 88px;
  font-weight: 900;
  line-height: 1;
  margin-bottom: 12px;
}
 
.bdare-letter.d { color: #6fcf97; }
.bdare-letter.a { color: #f2994a; }
.bdare-letter.r { color: #f2c94c; }
.bdare-letter.e { color: #56ccf2; }
 
.bdare-name {
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 2px;
  text-transform: uppercase;
  opacity: 0.5;
  text-align: center;
}
 
.bdare-cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: rgba(26,20,16,0.08);
}
 
.bdare-card {
  background: var(--paper);
  padding: 28px 24px;
  position: relative;
}
 
.bdare-card-author {
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 12px;
  padding-bottom: 8px;
  border-bottom: 1px dashed rgba(26,20,16,0.15);
}
 
.bdare-card-author.yefer { color: var(--rust); }
.bdare-card-author.jose { color: var(--forest); }
.bdare-card-author.juan { color: var(--sky); }
 
.bdare-card ul {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
 
.bdare-card ul li {
  font-size: 13px;
  line-height: 1.5;
  color: var(--ink-soft);
  padding-left: 16px;
  position: relative;
}
 
.bdare-card ul li::before {
  content: '—';
  position: absolute;
  left: 0;
  color: var(--sand);
  font-size: 10px;
}
 
/* Color accent per D-A-R-E */
.bdare-layout.datos .bdare-card { border-top: 3px solid var(--forest); }
.bdare-layout.anecdotas .bdare-card { border-top: 3px solid var(--rust); }
.bdare-layout.reflexiones .bdare-card { border-top: 3px solid var(--gold); }
.bdare-layout.emociones .bdare-card { border-top: 3px solid var(--sky); }
 
/* ============================================
   PROBLEM STATEMENT
   ============================================ */
.problem-section {
  background: var(--ink);
  color: var(--cream);
  padding: 120px 80px;
}
 
.problem-inner {
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}
 
.problem-kicker {
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 24px;
  display: block;
}
 
.problem-q {
  font-family: var(--font-display);
  font-size: clamp(22px, 3.5vw, 38px);
  font-weight: 700;
  line-height: 1.2;
  letter-spacing: -0.02em;
  color: var(--cream);
}
 
.problem-q strong {
  color: var(--gold-light);
}
 
.problem-right {
  border-left: 1px solid rgba(255,255,255,0.08);
  padding-left: 80px;
}
 
.problem-note {
  font-size: 14px;
  color: rgba(255,255,255,0.5);
  font-style: italic;
  line-height: 1.8;
  margin-bottom: 40px;
}
 
.method-steps {
  display: flex;
  flex-direction: column;
  gap: 2px;
}
 
.method-step {
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 16px 20px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.05);
}
 
.step-icon {
  font-family: var(--font-display);
  font-size: 32px;
  font-weight: 900;
  color: var(--gold);
  flex-shrink: 0;
  line-height: 1;
}
 
.step-label {
  font-family: 'Courier New', monospace;
  font-size: 10px;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.4);
  display: block;
  margin-bottom: 2px;
}
 
.step-name {
  font-family: var(--font-head);
  font-size: 13px;
  font-weight: 700;
  color: rgba(255,255,255,0.85);
}
 
/* ============================================
   PRODUCTS — 3P
   ============================================ */
.products-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1px;
  background: rgba(26,20,16,0.1);
  border: 1px solid rgba(26,20,16,0.1);
}
 
.product-card {
  background: var(--paper);
  padding: 24px 20px;
  position: relative;
  transition: background 0.2s, transform 0.2s;
}
 
.product-card:hover {
  background: var(--ink);
  color: var(--cream);
  z-index: 2;
}
 
.product-card:hover .product-keyword { color: var(--gold); }
.product-card:hover .product-idea { color: rgba(255,255,255,0.75); }
 
.product-number {
  font-family: var(--font-display);
  font-size: 40px;
  font-weight: 900;
  color: var(--cream-dark);
  line-height: 1;
  margin-bottom: 8px;
  transition: color 0.2s;
}
 
.product-card:hover .product-number { color: rgba(255,255,255,0.08); }
 
.product-keyword {
  font-family: var(--font-head);
  font-size: 11px;
  font-weight: 800;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: var(--rust);
  margin-bottom: 8px;
  display: block;
  transition: color 0.2s;
}
 
.product-idea {
  font-size: 12px;
  line-height: 1.5;
  color: var(--ink-soft);
  transition: color 0.2s;
}
 
/* ============================================
   CUVA TABLE
   ============================================ */
.table-wrapper {
  overflow-x: auto;
  border: 1px solid rgba(26,20,16,0.12);
}
 
table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
  min-width: 700px;
}
 
thead {
  background: var(--ink);
  color: var(--cream);
}
 
thead th {
  padding: 16px 18px;
  text-align: left;
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 2px;
  text-transform: uppercase;
  font-weight: 700;
  border-right: 1px solid rgba(255,255,255,0.06);
}
 
thead th.r { text-align: right; }
 
tbody tr { border-bottom: 1px solid rgba(26,20,16,0.07); }
tbody tr:hover { background: rgba(200,146,26,0.04); }
 
tbody tr.winner {
  background: #fdf8ea;
  border-left: 3px solid var(--gold);
}
 
tbody tr.runner {
  background: #f0f7f2;
  border-left: 3px solid var(--forest);
}
 
tbody td {
  padding: 13px 18px;
  vertical-align: middle;
  color: var(--ink-soft);
  line-height: 1.4;
  border-right: 1px solid rgba(26,20,16,0.05);
}
 
tbody td.r {
  text-align: right;
  font-family: 'Courier New', monospace;
  font-size: 13px;
  font-weight: 700;
  color: var(--ink);
}
 
.badge {
  display: inline-block;
  padding: 3px 10px;
  border-radius: 2px;
  font-family: 'Courier New', monospace;
  font-size: 12px;
  font-weight: 700;
}
 
.badge-gold { background: var(--gold); color: white; }
.badge-green { background: var(--forest); color: white; }
.badge-gray { background: rgba(26,20,16,0.08); color: var(--ink-soft); }
 
/* ============================================
   VIDEO SECTION
   ============================================ */
.video-section {
  background: var(--ink);
  color: var(--cream);
  padding: 120px 80px;
  text-align: center;
  position: relative;
  overflow: hidden;
}
 
.video-bg {
  position: absolute;
  inset: 0;
  font-family: var(--font-display);
  font-size: 280px;
  font-weight: 900;
  color: rgba(255,255,255,0.02);
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
  letter-spacing: -0.05em;
}
 
.video-inner {
  position: relative;
  z-index: 1;
  max-width: 860px;
  margin: 0 auto;
}
 
.video-kicker {
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 4px;
  text-transform: uppercase;
  color: var(--gold);
  display: block;
  margin-bottom: 24px;
}
 
.video-title {
  font-family: var(--font-display);
  font-size: clamp(28px, 5vw, 56px);
  font-weight: 900;
  letter-spacing: -0.03em;
  margin-bottom: 16px;
}
 
.video-subtitle {
  font-size: 15px;
  color: rgba(255,255,255,0.45);
  font-style: italic;
  margin-bottom: 56px;
}
 
.video-link-box {
  display: inline-flex;
  align-items: center;
  gap: 16px;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.1);
  padding: 20px 32px;
  text-decoration: none;
  color: var(--cream);
  font-family: 'Courier New', monospace;
  font-size: 13px;
  letter-spacing: 1px;
  transition: background 0.2s, border-color 0.2s;
  margin-bottom: 48px;
}
 
.video-link-box:hover {
  background: rgba(200,146,26,0.12);
  border-color: var(--gold);
  color: var(--gold);
}
 
.video-play-icon {
  width: 40px;
  height: 40px;
  border: 1px solid rgba(255,255,255,0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
 
.video-play-icon svg {
  width: 14px;
  height: 14px;
  fill: currentColor;
  margin-left: 2px;
}
 
.video-result-box {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.08);
  padding: 40px;
  text-align: left;
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 40px;
  align-items: center;
  margin-top: 16px;
}
 
.result-score {
  font-family: var(--font-display);
  font-size: 80px;
  font-weight: 900;
  color: var(--gold);
  line-height: 1;
}
 
.result-info-label {
  font-family: 'Courier New', monospace;
  font-size: 9px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.35);
  display: block;
  margin-bottom: 8px;
}
 
.result-product {
  font-family: var(--font-head);
  font-size: 20px;
  font-weight: 800;
  color: rgba(255,255,255,0.9);
  margin-bottom: 8px;
}
 
.result-desc {
  font-size: 13px;
  color: rgba(255,255,255,0.45);
  font-style: italic;
  line-height: 1.7;
}
 
/* ============================================
   FOOTER
   ============================================ */
footer {
  background: var(--ink);
  border-top: 1px solid rgba(255,255,255,0.06);
  padding: 48px 80px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: rgba(255,255,255,0.3);
  font-family: 'Courier New', monospace;
  font-size: 10px;
  letter-spacing: 2px;
  text-transform: uppercase;
}
 
footer strong { color: var(--gold); }
 
/* ============================================
   REVEAL ANIMATIONS
   ============================================ */
.reveal {
  opacity: 0;
  transform: translateY(32px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
 
.reveal.visible {
  opacity: 1;
  transform: none;
}
 
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
 
/* ============================================
   RESPONSIVE
   ============================================ */
@media (max-width: 1024px) {
  .hero-content { grid-template-columns: 1fr; min-height: auto; }
  .hero-left { padding: 80px 40px 40px; border-right: none; border-bottom: 1px solid rgba(255,255,255,0.08); }
  .hero-right { padding: 40px 40px 80px; }
  .autores-strip { grid-template-columns: 1fr; }
  .autor-block { border-right: none; border-bottom: 1px solid rgba(255,255,255,0.08); }
  .bdare-layout { grid-template-columns: 1fr; }
  .bdare-sidebar { flex-direction: row; padding: 24px 32px; gap: 16px; }
  .bdare-letter { font-size: 48px; }
  .bdare-cards { grid-template-columns: 1fr; }
  .problem-inner { grid-template-columns: 1fr; }
  .problem-right { border-left: none; border-top: 1px solid rgba(255,255,255,0.08); padding-left: 0; padding-top: 48px; }
  .products-grid { grid-template-columns: repeat(3, 1fr); }
  .section, .section-narrow { padding: 80px 40px; }
  .section-divider { margin: 0 40px; }
  .video-section { padding: 80px 40px; }
  footer { padding: 40px; flex-direction: column; gap: 12px; text-align: center; }
  .problem-section { padding: 80px 40px; }
  .video-result-box { grid-template-columns: 1fr; gap: 24px; text-align: center; }
}
 
@media (max-width: 640px) {
  .products-grid { grid-template-columns: repeat(2, 1fr); }
  .hero-meta { grid-template-columns: 1fr; }
}
</style>
</head>
<body>
 
<!-- ===========================
     HERO
     =========================== -->
<header class="hero">
  <div class="hero-bg-text">BIC</div>
  <div class="hero-content">
    <div class="hero-left">
      <span class="hero-tag">Método BIC · Banco de Ideas Creativas</span>
      <h1 class="hero-title">KINBAI<br><em>·CORA</em></h1>
      <p class="hero-subtitle">Bitácora completa de creatividad aplicada. Sensibilización en campo, ideas divergentes y evaluación CUVA Free para innovación en desarrollo social y personal universitario.</p>
      <div class="hero-meta">
        <div class="hero-meta-item">
          <span class="label">Lugar</span>
          <span class="value">Parque Kinbái, Cundinamarca</span>
        </div>
        <div class="hero-meta-item">
          <span class="label">Fecha</span>
          <span class="value">17–18 de Abril</span>
        </div>
        <div class="hero-meta-item">
          <span class="label">Método</span>
          <span class="value">BIC — Carolina Pinzón H.</span>
        </div>
        <div class="hero-meta-item">
          <span class="label">Autores</span>
          <span class="value">3 integrantes</span>
        </div>
      </div>
    </div>
    <div class="hero-right">
      <nav class="hero-nav">
        <a href="#bdare"><span class="nav-num">01</span> B-DARE — Datos, Anécdotas, Reflexiones, Emociones</a>
        <a href="#problema"><span class="nav-num">02</span> Definición del Problema</a>
        <a href="#productos"><span class="nav-num">03</span> Generación de Ideas — 3P</a>
        <a href="#cuva"><span class="nav-num">04</span> Evaluación CUVA Free</a>
        <a href="#resultado"><span class="nav-num">05</span> Resultado Final — Video</a>
      </nav>
      <div class="hero-scroll">Desplazar para explorar</div>
    </div>
  </div>
</header>
 
<!-- AUTORES -->
<div class="autores-strip">
  <div class="autor-block">
    <div class="autor-num">1</div>
    <span class="autor-label">Autor 01</span>
    <div class="autor-name">Yefer Hinestroza Rodríguez</div>
    <div class="autor-role">Bitácora narrativa · Kinbai-Cora</div>
  </div>
  <div class="autor-block">
    <div class="autor-num">2</div>
    <span class="autor-label">Autor 02</span>
    <div class="autor-name">Jose David Pinzon</div>
    <div class="autor-role">Diario de expedición · esquema visual</div>
  </div>
  <div class="autor-block">
    <div class="autor-num">3</div>
    <span class="autor-label">Autor 03</span>
    <div class="autor-name">Juan David Rojas</div>
    <div class="autor-role">Infografía · Equipo Azteca</div>
  </div>
</div>
 
<!-- ===========================
     SECTION 01 — B-DARE
     =========================== -->
<section id="bdare" class="section">
 
  <div class="chapter-header reveal">
    <div class="chapter-number">01</div>
    <div class="chapter-info">
      <span class="chapter-tag">Técnica B-DARE · Organización de la Bitácora</span>
      <h2 class="chapter-title">Datos · Anécdotas<br>Reflexiones · Emociones</h2>
      <p class="chapter-desc">Interpretación de las bitácoras narrativas de los tres autores, organizadas por criterio. Cada celda recoge las palabras clave más potentes para la ideación.</p>
    </div>
  </div>
 
  <!-- DATOS -->
  <div class="bdare-layout datos reveal">
    <div class="bdare-sidebar">
      <div class="bdare-letter d">D</div>
      <div class="bdare-name">Datos</div>
    </div>
    <div class="bdare-cards">
      <div class="bdare-card">
        <div class="bdare-card-author yefer">Yefer Hinestroza</div>
        <ul>
          <li>Parque Kinbái — km 30 vía Bogotá-La Vega</li>
          <li>Certificación europea de seguridad</li>
          <li>Tirolesa, escalada, cuerdas altas, bungee trampolín</li>
          <li>2 días y 1 noche (17–18 abril)</li>
          <li>Juego de memoria, cánticos, actividades en equipo</li>
          <li>Zonas de acampe, pesca deportiva, caminatas ecológicas</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author jose">Jose David Pinzon</div>
        <ul>
          <li>~40 personas transportadas en bus</li>
          <li>Carpas de 3–4 personas por grupo</li>
          <li>3 tipos de pases: Roble y otros, 28 actividades</li>
          <li>Llegada viernes a la mañana</li>
          <li>Primer día: equipos en competencia de triki, tubos, ping pong</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author juan">Juan David Rojas</div>
        <ul>
          <li>Temperatura: 14°C — clima frío de montaña</li>
          <li>Altitud: 2.500 msnm — bosque nuboso</li>
          <li>Carpas expuestas a lluvia nocturna intensa</li>
          <li>Equipo de desafío: "AZTECA"</li>
          <li>Dos días de expedición en alta montaña</li>
        </ul>
      </div>
    </div>
  </div>
 
  <!-- ANÉCDOTAS -->
  <div class="bdare-layout anecdotas reveal">
    <div class="bdare-sidebar">
      <div class="bdare-letter a">A</div>
      <div class="bdare-name">Anécdotas</div>
    </div>
    <div class="bdare-cards">
      <div class="bdare-card">
        <div class="bdare-card-author yefer">Yefer Hinestroza</div>
        <ul>
          <li>Inundación de carpas — planificación ante contingencias</li>
          <li>Cris y Nicolás durmieron en zona de refugio grupal</li>
          <li>La "parranda" terminó cuando llegó la lluvia</li>
          <li>Grupos aislados no mitigaron el daño de sus carpas</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author jose">Jose David Pinzon</div>
        <ul>
          <li>Fiesta en la cabaña con goteras — la más divertida del viaje</li>
          <li>Varias carpas inundadas — compañeros durmieron en cabaña</li>
          <li>El bus de vuelta: conocer compañeros de una perspectiva nueva</li>
          <li>El circuito Banana — pensó que era primero, al final lo logró</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author juan">Juan David Rojas</div>
        <ul>
          <li>Música, baile con altavoz Bose en plena tormenta</li>
          <li>Caída inesperada sobre roca húmeda en el lodo</li>
          <li>Dinámica grupal bajo lluvia que fortaleció al equipo</li>
        </ul>
      </div>
    </div>
  </div>
 
  <!-- REFLEXIONES -->
  <div class="bdare-layout reflexiones reveal">
    <div class="bdare-sidebar">
      <div class="bdare-letter r">R</div>
      <div class="bdare-name">Reflexiones</div>
    </div>
    <div class="bdare-cards">
      <div class="bdare-card">
        <div class="bdare-card-author yefer">Yefer Hinestroza</div>
        <ul>
          <li>Cada lugar tiene su mística — mirada holística y emprendedora frente a los retos</li>
          <li>Probar experiencias nuevas obliga a adaptarse y aprender de quienes nos rodean</li>
          <li>Los retos permiten convertirnos en mejores personas y profesionales</li>
          <li>La banana fue lo más difícil — pero decidí no tomar el camino fácil</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author jose">Jose David Pinzon</div>
        <ul>
          <li>Disfrutar cada momento con quienes quiero — son instantes que nunca apreciamos suficiente</li>
          <li>Hacer siempre lo que me represente — el viaje enseñó que con ellos podía confiar plenamente</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author juan">Juan David Rojas</div>
        <ul>
          <li>El trabajo en equipo facilita el desarrollo en entornos naturales</li>
          <li>Los retos físicos fortalecen el carácter y la capacidad de adaptación</li>
          <li>Escuchar perspectivas ajenas luego de la adversidad hace mejores personas</li>
          <li>Me adapté al enfrentar nuevos retos como escalar</li>
        </ul>
      </div>
    </div>
  </div>
 
  <!-- EMOCIONES -->
  <div class="bdare-layout emociones reveal">
    <div class="bdare-sidebar">
      <div class="bdare-letter e">E</div>
      <div class="bdare-name">Emociones</div>
    </div>
    <div class="bdare-cards">
      <div class="bdare-card">
        <div class="bdare-card-author yefer">Yefer Hinestroza</div>
        <ul>
          <li>Cierta adicción a las actividades del primer día</li>
          <li>Desconexión inicial con las dinámicas planteadas</li>
          <li>Resistencia que fue cambiando hacia el disfrute genuino</li>
          <li>Relajación profunda en almuerzos y desayunos compartidos</li>
          <li>Dificultad en la banana — interés en superarlo</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author jose">Jose David Pinzon</div>
        <ul>
          <li>Entusiasmo inicial — expectativas altas del parque</li>
          <li>Disfrute — felicidad compartiendo en la fiesta bajo la lluvia</li>
          <li>Impotencia e incomodidad — frío y humedad al dormir</li>
          <li>Tranquilidad final — viaje compartido con personas queridas</li>
        </ul>
      </div>
      <div class="bdare-card">
        <div class="bdare-card-author juan">Juan David Rojas</div>
        <ul>
          <li>Amor al compartir experiencias intensas con el equipo</li>
          <li>Paz al estar rodeado de naturaleza de alta montaña</li>
          <li>Sentido de logro al superar los retos físicos del circuito</li>
        </ul>
      </div>
    </div>
  </div>
 
</section>
 
<div class="section-divider"></div>
 
<!-- ===========================
     SECTION 02 — PROBLEMA
     =========================== -->
<section id="problema" class="problem-section">
  <div class="problem-inner">
    <div class="reveal">
      <span class="problem-kicker">Sección 02 · Definición del Problema</span>
      <h2 class="problem-q">¿Cómo transformar la incomodidad, el reto y la convivencia en una guía creativa para desarrollar <strong>seguridad personal, autenticidad y atractivo social</strong> en jóvenes universitarios?</h2>
    </div>
    <div class="problem-right reveal reveal-delay-1">
      <p class="problem-note">El problema fue formulado a partir de las palabras más potentes extraídas de las bitácoras mediante la técnica B-DARE, conectando la experiencia sensibilizadora de Kinbái con una oportunidad real de innovación en el sector panelero colombiano.</p>
      <div class="method-steps">
        <div class="method-step">
          <div class="step-icon">P</div>
          <div>
            <span class="step-label">Componente</span>
            <span class="step-name">Palabra — extraída de la bitácora</span>
          </div>
        </div>
        <div class="method-step">
          <div class="step-icon">P</div>
          <div>
            <span class="step-label">Componente</span>
            <span class="step-name">Problema — la pregunta formulada</span>
          </div>
        </div>
        <div class="method-step">
          <div class="step-icon">P</div>
          <div>
            <span class="step-label">Componente</span>
            <span class="step-name">Propuesta — idea creativa de solución</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
 
<!-- ===========================
     SECTION 03 — PRODUCTOS 3P
     =========================== -->
<section id="productos" class="section-narrow">
 
  <div class="chapter-header reveal">
    <div class="chapter-number">03</div>
    <div class="chapter-info">
      <span class="chapter-tag">Técnica 3P · Palabra – Problema – Propuesta</span>
      <h2 class="chapter-title">35 Ideas Creativas</h2>
      <p class="chapter-desc">Cada palabra extraída de la experiencia en Kinbái se conecta directamente con una propuesta de innovación social y educativa para jóvenes universitarios.</p>
    </div>
  </div>
 
  <div class="products-grid reveal">
    <div class="product-card">
      <div class="product-number">01</div>
      <span class="product-keyword">Desbloqueo</span>
      <p class="product-idea">Portafolio de propuestas para jóvenes que les permitan realizar desbloqueos cognitivos a partir de experiencias de incomodidad, reto y reflexión personal.</p>
    </div>
    <div class="product-card">
      <div class="product-number">02</div>
      <span class="product-keyword">Equipo</span>
      <p class="product-idea">Aplicación digital que conecta a jóvenes con inseguridades similares y con el deseo de construir autenticidad, seguridad personal y atractivo social a través de experiencias compartidas.</p>
    </div>
    <div class="product-card">
      <div class="product-number">03</div>
      <span class="product-keyword">Memoria</span>
      <p class="product-idea">Museo virtual interactivo donde se recopilen experiencias, aprendizajes, errores y transformaciones de los participantes del programa, resignificando la incomodidad como parte del crecimiento personal.</p>
    </div>
    <div class="product-card">
      <div class="product-number">04</div>
      <span class="product-keyword">Creativo</span>
      <p class="product-idea">Guía del "papucho" adaptable (práctica y reflexiva) que ayude a jóvenes universitarios a desarrollar seguridad personal, adaptabilidad y atractivo integral mediante la gestión consciente de situaciones imprevistas.</p>
    </div>
    <div class="product-card">
      <div class="product-number">05</div>
      <span class="product-keyword">Certificación</span>
      <p class="product-idea">Diplomados modulares orientados al desarrollo personal y social de jóvenes universitarios, basados en experiencias vivenciales, reflexión guiada y aprendizaje aplicado.</p>
    </div>
    <div class="product-card">
      <div class="product-number">06</div>
      <span class="product-keyword">Aprendizaje</span>
      <p class="product-idea">Cursos extracurriculares mediante los cuales expertos en psicología y temas sociales generen aprendizajes al momento de enfrentar retos y desafíos en las relaciones interpersonales.</p>
    </div>
    <div class="product-card">
      <div class="product-number">07</div>
      <span class="product-keyword">Decisión</span>
      <p class="product-idea">Colección de experiencias reales donde otros jóvenes aprendan a partir de decisiones mal tomadas, actitudes y consecuencias. Formatos: videos, podcast, textos.</p>
    </div>
    <div class="product-card">
      <div class="product-number">08</div>
      <span class="product-keyword">Actitud</span>
      <p class="product-idea">Programa de retos "21 retos" de autenticidad documentada, donde los jóvenes universitarios puedan aprender de experiencias poco habituales.</p>
    </div>
    <div class="product-card">
      <div class="product-number">09</div>
      <span class="product-keyword">Consecuencia</span>
      <p class="product-idea">Kits de autoexploración para jóvenes universitarios que buscan conocerse mejor a través de actividades guiadas de introspección.</p>
    </div>
    <div class="product-card">
      <div class="product-number">10</div>
      <span class="product-keyword">Experiencia</span>
      <p class="product-idea">Manual de 21 días con recomendaciones y consejos a los jóvenes universitarios para que puedan aprender las diferentes dinámicas sociales.</p>
    </div>
    <div class="product-card">
      <div class="product-number">11</div>
      <span class="product-keyword">Indiferencia</span>
      <p class="product-idea">Micro-retos de sensibilidad para romper la apatía hacia actividades diferentes y con alta carga creativa.</p>
    </div>
    <div class="product-card">
      <div class="product-number">12</div>
      <span class="product-keyword">Desconexión</span>
      <p class="product-idea">Aplicación que bloquea temporalmente redes sociales durante actividades universitarias para fomentar la interacción presencial.</p>
    </div>
    <div class="product-card">
      <div class="product-number">13</div>
      <span class="product-keyword">Resistencia</span>
      <p class="product-idea">Programa de entrenamiento emocional para ayudar a estudiantes a afrontar rechazo, críticas y situaciones incómodas.</p>
    </div>
    <div class="product-card">
      <div class="product-number">14</div>
      <span class="product-keyword">Disfrute</span>
      <p class="product-idea">Membresía universitaria que da acceso a actividades recreativas y sociales para mejorar la experiencia estudiantil.</p>
    </div>
    <div class="product-card">
      <div class="product-number">15</div>
      <span class="product-keyword">Melancolía</span>
      <p class="product-idea">Espacios creativos de memoria y escritura que permitan procesar emociones y mejorar la relación con uno mismo y con el entorno.</p>
    </div>
    <div class="product-card">
      <div class="product-number">16</div>
      <span class="product-keyword">Retos</span>
      <p class="product-idea">Plataforma que lanza desafíos semanales para desarrollar habilidades sociales y liderazgo en entornos universitarios.</p>
    </div>
    <div class="product-card">
      <div class="product-number">17</div>
      <span class="product-keyword">Adaptar</span>
      <p class="product-idea">Servicio de acompañamiento para estudiantes nuevos que buscan integrarse a la vida universitaria de forma auténtica.</p>
    </div>
    <div class="product-card">
      <div class="product-number">18</div>
      <span class="product-keyword">Dificultad</span>
      <p class="product-idea">Herramienta digital que identifica áreas donde un estudiante tiene problemas para relacionarse y propone rutas de mejora personalizadas.</p>
    </div>
    <div class="product-card">
      <div class="product-number">19</div>
      <span class="product-keyword">Intentarlo</span>
      <p class="product-idea">Aplicación que propone una acción diaria para vencer la timidez o el miedo social, con seguimiento de progreso.</p>
    </div>
    <div class="product-card">
      <div class="product-number">20</div>
      <span class="product-keyword">Reto</span>
      <p class="product-idea">Programa guiado para fortalecer la seguridad personal mediante pequeñas acciones diarias de exposición progresiva.</p>
    </div>
    <div class="product-card">
      <div class="product-number">21</div>
      <span class="product-keyword">Amor</span>
      <p class="product-idea">Caja de herramientas físicas y digitales enfocadas en autoestima y autoconocimiento para jóvenes universitarios.</p>
    </div>
    <div class="product-card">
      <div class="product-number">22</div>
      <span class="product-keyword">Paz</span>
      <p class="product-idea">Espacio dentro de la universidad diseñado para reducir estrés y ansiedad social, con actividades de bienestar integradas.</p>
    </div>
    <div class="product-card">
      <div class="product-number">23</div>
      <span class="product-keyword">Confort</span>
      <p class="product-idea">Salas de conversación seguras donde los estudiantes practican habilidades sociales sin presión ni juicio.</p>
    </div>
    <div class="product-card">
      <div class="product-number">24</div>
      <span class="product-keyword">Diversión</span>
      <p class="product-idea">Organización de eventos universitarios diseñados para generar nuevas amistades de forma espontánea y auténtica.</p>
    </div>
    <div class="product-card">
      <div class="product-number">25</div>
      <span class="product-keyword">Desafío</span>
      <p class="product-idea">Experiencia gamificada donde los estudiantes acumulan puntos al enfrentar situaciones incómodas que amplían su zona de confort.</p>
    </div>
    <div class="product-card">
      <div class="product-number">26</div>
      <span class="product-keyword">Perspectiva</span>
      <p class="product-idea">Plataforma que permite conocer historias y experiencias de otros estudiantes para ampliar la visión personal y reducir la sensación de soledad.</p>
    </div>
    <div class="product-card">
      <div class="product-number">27</div>
      <span class="product-keyword">Grupo</span>
      <p class="product-idea">Sistema que conecta estudiantes con intereses similares para formar comunidades universitarias significativas y duraderas.</p>
    </div>
    <div class="product-card">
      <div class="product-number">28</div>
      <span class="product-keyword">Competencia</span>
      <p class="product-idea">Competencia entre facultades basada en trabajo en equipo, liderazgo y comunicación para desarrollar habilidades blandas.</p>
    </div>
    <div class="product-card">
      <div class="product-number">29</div>
      <span class="product-keyword">Categorías</span>
      <p class="product-idea">Test interactivo que clasifica estilos de personalidad e interacción social para orientar el desarrollo personal del estudiante.</p>
    </div>
    <div class="product-card">
      <div class="product-number">30</div>
      <span class="product-keyword">División</span>
      <p class="product-idea">Programa que agrupa estudiantes según fortalezas para desarrollar proyectos colaborativos que potencien sus habilidades.</p>
    </div>
    <div class="product-card">
      <div class="product-number">31</div>
      <span class="product-keyword">Parque</span>
      <p class="product-idea">Espacio al aire libre con estaciones de actividades para fomentar la interacción espontánea entre estudiantes de distintas facultades.</p>
    </div>
    <div class="product-card">
      <div class="product-number">32</div>
      <span class="product-keyword">Entusiasmo</span>
      <p class="product-idea">Plataforma que recompensa la participación en eventos y actividades universitarias con beneficios tangibles y reconocimiento social.</p>
    </div>
    <div class="product-card">
      <div class="product-number">33</div>
      <span class="product-keyword">Tranquilidad</span>
      <p class="product-idea">Servicio de acompañamiento para estudiantes con ansiedad o inseguridad social, conectando con pares y mentores capacitados.</p>
    </div>
    <div class="product-card">
      <div class="product-number">34</div>
      <span class="product-keyword">Incomodidad</span>
      <p class="product-idea">Caja de retos diseñada para que los estudiantes enfrenten situaciones fuera de su zona de confort de forma progresiva y guiada.</p>
    </div>
    <div class="product-card">
      <div class="product-number">35</div>
      <span class="product-keyword">Disfrute</span>
      <p class="product-idea">Aplicación que recomienda actividades universitarias según gustos e intereses personales para maximizar el bienestar estudiantil.</p>
    </div>
  </div>
 
</section>
 
<div class="section-divider"></div>
 
<!-- ===========================
     SECTION 04 — CUVA FREE
     =========================== -->
<section id="cuva" class="section">
 
  <div class="chapter-header reveal">
    <div class="chapter-number">04</div>
    <div class="chapter-info">
      <span class="chapter-tag">Evaluación CUVA Free · Creatividad 40 · Utilidad 20 · Viabilidad 20 · Apropiada 20</span>
      <h2 class="chapter-title">Tabla CUVA Free</h2>
      <p class="chapter-desc">Evaluación de las 35 propuestas bajo criterios ponderados libremente. La puntuación máxima es 100. Ninguna idea puede empatar en creatividad.</p>
    </div>
  </div>
 
  <div class="table-wrapper reveal">
    <table>
      <thead>
        <tr>
          <th style="width:48%">Propuesta creativa</th>
          <th class="r">C (40)</th>
          <th class="r">U (20)</th>
          <th class="r">V (20)</th>
          <th class="r">A (20)</th>
          <th class="r">Total</th>
        </tr>
      </thead>
      <tbody>
        <tr class="winner">
          <td><strong>Creativo: Guía del "papucho" adaptable para desarrollar seguridad personal, adaptabilidad y atractivo integral</strong></td>
          <td class="r">40</td><td class="r">20</td><td class="r">20</td><td class="r">20</td>
          <td class="r"><span class="badge badge-gold">100</span></td>
        </tr>
        <tr class="runner">
          <td>Equipo: Aplicación digital que conecta a jóvenes con inseguridades similares para construir autenticidad y atractivo social</td>
          <td class="r">35</td><td class="r">18</td><td class="r">19</td><td class="r">18</td>
          <td class="r"><span class="badge badge-green">90</span></td>
        </tr>
        <tr class="runner">
          <td>Memoria: Museo virtual interactivo de experiencias, aprendizajes y transformaciones resignificando la incomodidad</td>
          <td class="r">38</td><td class="r">19</td><td class="r">13</td><td class="r">19</td>
          <td class="r"><span class="badge badge-green">89</span></td>
        </tr>
        <tr>
          <td>Desbloqueo: Portafolio de propuestas para desbloqueos cognitivos a partir de experiencias de incomodidad y reto</td>
          <td class="r">30</td><td class="r">15</td><td class="r">18</td><td class="r">20</td>
          <td class="r"><span class="badge badge-gray">83</span></td>
        </tr>
        <tr>
          <td>Actitud: Programa de retos "21 retos" de autenticidad documentada para jóvenes universitarios</td>
          <td class="r">29</td><td class="r">18</td><td class="r">17</td><td class="r">17</td>
          <td class="r"><span class="badge badge-gray">81</span></td>
        </tr>
        <tr>
          <td>Amor: Caja de herramientas físicas y digitales enfocadas en autoestima y autoconocimiento</td>
          <td class="r">25</td><td class="r">19</td><td class="r">20</td><td class="r">12</td>
          <td class="r"><span class="badge badge-gray">76</span></td>
        </tr>
        <tr>
          <td>Indiferencia: Micro-retos de sensibilidad para romper la apatía hacia actividades con alta carga creativa</td>
          <td class="r">26</td><td class="r">19</td><td class="r">15</td><td class="r">12</td>
          <td class="r"><span class="badge badge-gray">72</span></td>
        </tr>
        <tr>
          <td>Resistencia: Programa de entrenamiento emocional para afrontar rechazo, críticas y situaciones incómodas</td>
          <td class="r">20</td><td class="r">18</td><td class="r">18</td><td class="r">13</td>
          <td class="r"><span class="badge badge-gray">69</span></td>
        </tr>
        <tr>
          <td>Dificultad: Herramienta digital que identifica áreas donde un estudiante tiene problemas para relacionarse</td>
          <td class="r">30</td><td class="r">18</td><td class="r">13</td><td class="r">8</td>
          <td class="r"><span class="badge badge-gray">69</span></td>
        </tr>
        <tr>
          <td>Incomodidad: Caja de retos para que los estudiantes enfrenten situaciones fuera de su zona de confort</td>
          <td class="r">15</td><td class="r">18</td><td class="r">16</td><td class="r">17</td>
          <td class="r"><span class="badge badge-gray">66</span></td>
        </tr>
        <tr>
          <td>Paz: Espacio dentro de la universidad diseñado para reducir estrés y ansiedad social</td>
          <td class="r">17</td><td class="r">16</td><td class="r">16</td><td class="r">14</td>
          <td class="r"><span class="badge badge-gray">63</span></td>
        </tr>
        <tr>
          <td>Desafío: Experiencia gamificada donde los estudiantes acumulan puntos al enfrentar situaciones incómodas</td>
          <td class="r">20</td><td class="r">18</td><td class="r">8</td><td class="r">17</td>
          <td class="r"><span class="badge badge-gray">63</span></td>
        </tr>
        <tr>
          <td>Consecuencia: Kits de autoexploración para jóvenes universitarios</td>
          <td class="r">15</td><td class="r">18</td><td class="r">19</td><td class="r">10</td>
          <td class="r"><span class="badge badge-gray">62</span></td>
        </tr>
        <tr>
          <td>Adaptar: Servicio de acompañamiento para estudiantes nuevos que buscan integrarse a la vida universitaria</td>
          <td class="r">21</td><td class="r">16</td><td class="r">17</td><td class="r">8</td>
          <td class="r"><span class="badge badge-gray">62</span></td>
        </tr>
        <tr>
          <td>Tranquilidad: Servicio de acompañamiento para estudiantes con ansiedad o inseguridad social</td>
          <td class="r">12</td><td class="r">19</td><td class="r">17</td><td class="r">14</td>
          <td class="r"><span class="badge badge-gray">62</span></td>
        </tr>
        <tr>
          <td>Diversión: Organización de eventos universitarios para generar nuevas amistades de forma espontánea</td>
          <td class="r">17</td><td class="r">16</td><td class="r">14</td><td class="r">15</td>
          <td class="r"><span class="badge badge-gray">62</span></td>
        </tr>
        <tr>
          <td>Decisión: Colección de experiencias reales de decisiones mal tomadas — videos, podcast, textos</td>
          <td class="r">24</td><td class="r">14</td><td class="r">8</td><td class="r">15</td>
          <td class="r"><span class="badge badge-gray">61</span></td>
        </tr>
        <tr>
          <td>Competencia: Competencia entre facultades basada en trabajo en equipo, liderazgo y comunicación</td>
          <td class="r">30</td><td class="r">15</td><td class="r">6</td><td class="r">10</td>
          <td class="r"><span class="badge badge-gray">61</span></td>
        </tr>
        <tr>
          <td>Aprendizaje: Cursos extracurriculares con expertos en psicología y temas sociales</td>
          <td class="r">24</td><td class="r">12</td><td class="r">9</td><td class="r">15</td>
          <td class="r"><span class="badge badge-gray">60</span></td>
        </tr>
        <tr>
          <td>Grupo: Sistema que conecta estudiantes con intereses similares para formar comunidades universitarias</td>
          <td class="r">28</td><td class="r">15</td><td class="r">12</td><td class="r">5</td>
          <td class="r"><span class="badge badge-gray">60</span></td>
        </tr>
        <tr>
          <td>Disfrute (membresía): Membresía universitaria de acceso a actividades recreativas y sociales</td>
          <td class="r">18</td><td class="r">12</td><td class="r">15</td><td class="r">14</td>
          <td class="r"><span class="badge badge-gray">59</span></td>
        </tr>
        <tr>
          <td>Parque: Espacio al aire libre con estaciones de actividades para fomentar la interacción entre estudiantes</td>
          <td class="r">19</td><td class="r">17</td><td class="r">14</td><td class="r">9</td>
          <td class="r"><span class="badge badge-gray">59</span></td>
        </tr>
        <tr>
          <td>Certificación: Diplomados modulares de desarrollo personal y social para jóvenes universitarios</td>
          <td class="r">20</td><td class="r">10</td><td class="r">11</td><td class="r">16</td>
          <td class="r"><span class="badge badge-gray">57</span></td>
        </tr>
        <tr>
          <td>Categorías: Test interactivo que clasifica estilos de personalidad e interacción social</td>
          <td class="r">16</td><td class="r">19</td><td class="r">16</td><td class="r">6</td>
          <td class="r"><span class="badge badge-gray">57</span></td>
        </tr>
        <tr>
          <td>Desconexión: Aplicación que bloquea temporalmente redes sociales para fomentar interacción presencial</td>
          <td class="r">12</td><td class="r">20</td><td class="r">14</td><td class="r">9</td>
          <td class="r"><span class="badge badge-gray">55</span></td>
        </tr>
        <tr>
          <td>Disfrute (app): Aplicación que recomienda actividades universitarias según gustos e intereses personales</td>
          <td class="r">19</td><td class="r">17</td><td class="r">15</td><td class="r">3</td>
          <td class="r"><span class="badge badge-gray">54</span></td>
        </tr>
        <tr>
          <td>Entusiasmo: Plataforma que recompensa la participación en eventos y actividades universitarias</td>
          <td class="r">19</td><td class="r">14</td><td class="r">12</td><td class="r">7</td>
          <td class="r"><span class="badge badge-gray">52</span></td>
        </tr>
        <tr>
          <td>Melancolía: Espacios creativos de memoria y escritura para procesar emociones y mejorar</td>
          <td class="r">18</td><td class="r">10</td><td class="r">14</td><td class="r">11</td>
          <td class="r"><span class="badge badge-gray">53</span></td>
        </tr>
        <tr>
          <td>Confort: Salas de conversación seguras donde los estudiantes practican habilidades sociales sin presión</td>
          <td class="r">19</td><td class="r">9</td><td class="r">11</td><td class="r">7</td>
          <td class="r"><span class="badge badge-gray">46</span></td>
        </tr>
        <tr>
          <td>División: Programa que agrupa estudiantes según fortalezas para proyectos colaborativos</td>
          <td class="r">18</td><td class="r">19</td><td class="r">6</td><td class="r">4</td>
          <td class="r"><span class="badge badge-gray">47</span></td>
        </tr>
        <tr>
          <td>Perspectiva: Plataforma de historias y experiencias de otros estudiantes para ampliar la visión personal</td>
          <td class="r">28</td><td class="r">18</td><td class="r">16</td><td class="r">16</td>
          <td class="r"><span class="badge badge-gray">78</span></td>
        </tr>
        <tr>
          <td>Retos: Plataforma que lanza desafíos semanales para desarrollar habilidades sociales y liderazgo</td>
          <td class="r">22</td><td class="r">11</td><td class="r">13</td><td class="r">16</td>
          <td class="r"><span class="badge badge-gray">62</span></td>
        </tr>
        <tr>
          <td>Intentarlo: Aplicación que propone una acción diaria para vencer la timidez o el miedo social</td>
          <td class="r">21</td><td class="r">16</td><td class="r">14</td><td class="r">10</td>
          <td class="r"><span class="badge badge-gray">61</span></td>
        </tr>
        <tr>
          <td>Reto: Programa guiado para fortalecer la seguridad personal mediante pequeñas acciones diarias</td>
          <td class="r">20</td><td class="r">17</td><td class="r">15</td><td class="r">12</td>
          <td class="r"><span class="badge badge-gray">64</span></td>
        </tr>
        <tr>
          <td>Experiencia: Manual de 21 días con recomendaciones para aprender diferentes dinámicas sociales</td>
          <td class="r">23</td><td class="r">15</td><td class="r">13</td><td class="r">14</td>
          <td class="r"><span class="badge badge-gray">65</span></td>
        </tr>
      </tbody>
    </table>
  </div>
 
</section>
 
<!-- ===========================
     SECTION 05 — VIDEO / RESULTADO
     =========================== -->
<section id="resultado" class="video-section">
  <div class="video-bg">3P</div>
  <div class="video-inner">
    <span class="video-kicker">Sección 05 · Resultado Final · 3P</span>
    <h2 class="video-title">Producto Ganador</h2>
    <p class="video-subtitle">La idea con mayor puntuación CUVA Free (100 pts) materializada en video</p>
 
    <div class="video-result-box reveal">
      <div class="result-score">100</div>
      <div>
        <span class="result-info-label">Propuesta seleccionada · Puntaje máximo</span>
        <div class="result-product">Guía del "papucho" adaptable: seguridad personal, adaptabilidad y atractivo integral</div>
        <p class="result-desc">Una guía práctica y reflexiva que ayuda a jóvenes universitarios a desarrollar seguridad personal, adaptabilidad y atractivo integral mediante la gestión consciente de situaciones imprevistas y experiencias de incomodidad. La propuesta más creativa, útil, viable y apropiada de la evaluación CUVA Free con puntaje perfecto de 100.</p>
      </div>
    </div>
 
    <div style="margin-top: 48px;">
      <span class="video-kicker">Video de exposición no convencional</span>
      <a class="video-link-box" href="https://youtu.be/BH1J6ZdgVQY" target="_blank" rel="noopener">
        <div class="video-play-icon">
          <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M8 5v14l11-7z"/></svg>
        </div>
        <div style="text-align:left;">
          <div style="font-size:9px; letter-spacing:3px; color:rgba(255,255,255,0.4); margin-bottom:4px;">YOUTUBE · MÉTODO BIC</div>
          <div>youtu.be/BH1J6ZdgVQY — Bitácora Kinbai-Cora · Yefer Hinestroza Rodríguez</div>
        </div>
      </a>
    </div>
 
  </div>
</section>
 
<!-- FOOTER -->
<footer>
  <div>
    <strong>Yefer Hinestroza · Jose David Pinzon · Juan David Rojas</strong>
  </div>
  <div>Método BIC · <strong>Carolina Pinzón Hernández</strong> · Kinbái, Cundinamarca · Abril 2025</div>
</footer>
 
<script>
// Scroll reveal
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
      obs.unobserve(e.target);
    }
  });
}, { threshold: 0.06 });
 
document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
 
// Smooth nav
document.querySelectorAll('a[href^="#"]').forEach(a => {
  a.addEventListener('click', e => {
    const t = document.querySelector(a.getAttribute('href'));
    if (t) { e.preventDefault(); t.scrollIntoView({ behavior: 'smooth', block: 'start' }); }
  });
});
</script>
</body>
</html>
