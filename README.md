<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#071326">
  <meta id="meta-description" name="description" content="CamToVault est une caméra privée avec coffre-fort chiffré pour protéger vos photos et vidéos sensibles.">
  <meta property="og:type" content="website">
  <meta property="og:title" content="CamToVault — Caméra privée. Coffre-fort chiffré.">
  <meta property="og:description" content="Protégez vos photos et vidéos sensibles avec CamToVault.">
  <meta property="og:image" content="assets/camtovault-private-camera-encrypted-vault.png">
  <meta property="og:locale" content="fr_FR">
  <link rel="icon" type="image/png" href="assets/camtovault-icon.png">
  <link rel="apple-touch-icon" href="assets/camtovault-icon.png">
  <title>CamToVault — Caméra privée. Coffre-fort chiffré.</title>
  <style>
    :root {
      --bg: #050c18;
      --bg-soft: #081426;
      --panel: rgba(12, 29, 52, 0.72);
      --panel-solid: #0b1c34;
      --text: #f5f8ff;
      --muted: #a8b8ce;
      --primary: #25cde2;
      --primary-soft: rgba(37, 205, 226, 0.14);
      --border: rgba(171, 205, 255, 0.16);
      --shadow: 0 24px 70px rgba(0, 0, 0, 0.35);
      --radius: 24px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      color: var(--text);
      background:
        radial-gradient(circle at 82% 4%, rgba(14, 101, 173, 0.22), transparent 30rem),
        radial-gradient(circle at 8% 20%, rgba(0, 185, 210, 0.09), transparent 24rem),
        linear-gradient(180deg, #050c18 0%, #071426 52%, #050d1b 100%);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      min-height: 100vh;
      overflow-x: hidden;
    }

    body::before {
      content: "";
      position: fixed;
      inset: 0;
      pointer-events: none;
      opacity: 0.28;
      background-image:
        linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
      background-size: 56px 56px;
      mask-image: linear-gradient(to bottom, black, transparent 88%);
    }

    a { color: inherit; text-decoration: none; }
    button, select, a { -webkit-tap-highlight-color: transparent; }
    img { max-width: 100%; display: block; }

    .container {
      width: min(1160px, calc(100% - 40px));
      margin: 0 auto;
    }

    .navbar {
      position: sticky;
      top: 0;
      z-index: 20;
      border-bottom: 1px solid transparent;
      transition: 0.25s ease;
    }

    .navbar.scrolled {
      background: rgba(5, 13, 27, 0.88);
      backdrop-filter: blur(18px);
      border-color: var(--border);
    }

    .nav-inner {
      min-height: 76px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 18px;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-size: 1.05rem;
      font-weight: 850;
      letter-spacing: -0.04em;
    }

    .brand img {
      width: 48px;
      height: 48px;
      object-fit: contain;
      filter: drop-shadow(0 10px 18px rgba(0, 194, 220, 0.2));
    }

    .nav-right, .nav-links {
      display: flex;
      align-items: center;
    }

    .nav-right { gap: 18px; }
    .nav-links { gap: 24px; }
    .nav-links a { color: var(--muted); font-size: 0.91rem; transition: color 0.2s ease; }
    .nav-links a:hover { color: var(--text); }

    .language-select {
      min-height: 40px;
      padding: 0 30px 0 11px;
      border: 1px solid var(--border);
      border-radius: 11px;
      color: var(--text);
      background: rgba(255,255,255,0.04);
      font: inherit;
      font-size: 0.86rem;
      cursor: pointer;
    }

    .language-select option { color: #0a1728; background: white; }

    .btn {
      min-height: 46px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 0 18px;
      border: 1px solid transparent;
      border-radius: 13px;
      font: inherit;
      font-size: 0.93rem;
      font-weight: 780;
      cursor: pointer;
      transition: 0.22s ease;
    }

    .btn-primary {
      color: #001b22;
      background: linear-gradient(135deg, #4ae7ed, #22c1e8);
      box-shadow: 0 14px 34px rgba(21, 184, 218, 0.24);
    }

    .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 18px 38px rgba(21, 184, 218, 0.33); }

    .btn-secondary {
      color: var(--text);
      border-color: var(--border);
      background: rgba(255,255,255,0.045);
    }

    .btn-secondary:hover { transform: translateY(-2px); background: rgba(255,255,255,0.085); }

    .mobile-toggle {
      display: none;
      border: 0;
      color: var(--text);
      background: transparent;
      font-size: 1.55rem;
      cursor: pointer;
    }

    .hero { padding: 74px 0 58px; }
    .hero-grid {
      display: grid;
      grid-template-columns: 0.9fr 1.1fr;
      align-items: center;
      gap: 48px;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 8px 12px;
      border: 1px solid var(--border);
      border-radius: 999px;
      color: #cef7ff;
      background: rgba(255,255,255,0.035);
      font-size: 0.8rem;
      font-weight: 750;
    }

    .dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--primary);
      box-shadow: 0 0 0 5px rgba(37, 205, 226, 0.14);
    }

    h1 {
      margin: 21px 0 17px;
      font-size: clamp(3.15rem, 6vw, 5.75rem);
      line-height: 0.98;
      letter-spacing: -0.075em;
    }

    .gradient-text {
      color: transparent;
      background: linear-gradient(135deg, #f8fcff 6%, #68edf2 60%, #46a4ff);
      background-clip: text;
      -webkit-background-clip: text;
    }

    .hero-copy {
      max-width: 650px;
      margin: 0;
      color: var(--muted);
      font-size: 1.05rem;
      line-height: 1.75;
    }

    .hero-actions { display: flex; flex-wrap: wrap; gap: 11px; margin-top: 29px; }
    .trust-row { display: flex; flex-wrap: wrap; gap: 16px; margin-top: 30px; color: #d1deed; font-size: 0.87rem; }
    .trust-row span { display: inline-flex; align-items: center; gap: 7px; }
    .check { color: #58e5ec; font-weight: 900; }

    .visual-frame {
      position: relative;
      border: 1px solid rgba(170, 205, 255, 0.17);
      border-radius: 27px;
      overflow: hidden;
      background: #061123;
      box-shadow: var(--shadow);
      isolation: isolate;
    }

    .visual-frame::after {
      content: "";
      position: absolute;
      inset: 0;
      pointer-events: none;
      box-shadow: inset 0 0 0 1px rgba(255,255,255,0.04);
      border-radius: inherit;
    }

    .visual-frame img { width: 100%; height: auto; }

    section { padding: 84px 0; }
    .section-head { max-width: 720px; margin-bottom: 34px; }
    .section-head h2, .security-content h2, .cta-box h2 {
      margin: 14px 0 11px;
      font-size: clamp(2rem, 4vw, 3.35rem);
      letter-spacing: -0.06em;
      line-height: 1.05;
    }
    .section-head p, .security-content p, .cta-box p { margin: 0; color: var(--muted); line-height: 1.75; }

    .cards, .steps {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .card {
      padding: 25px;
      border: 1px solid var(--border);
      border-radius: var(--radius);
      background: var(--panel);
      box-shadow: 0 14px 32px rgba(0,0,0,0.13);
      transition: 0.24s ease;
    }

    .card:hover { transform: translateY(-5px); border-color: rgba(37,205,226,0.36); }
    .card-tag {
      display: grid;
      width: 43px;
      height: 43px;
      place-items: center;
      border: 1px solid rgba(37,205,226,0.2);
      border-radius: 14px;
      color: #75edf1;
      background: var(--primary-soft);
      font-size: 0.84rem;
      font-weight: 850;
    }
    .card h3 { margin: 18px 0 9px; font-size: 1.03rem; }
    .card p { margin: 0; color: var(--muted); font-size: 0.93rem; line-height: 1.7; }

    .steps { counter-reset: step; }
    .step { padding: 26px; border-top: 1px solid var(--border); counter-increment: step; }
    .step::before {
      content: "0" counter(step);
      display: inline-block;
      margin-bottom: 27px;
      color: #6aeaf0;
      font-size: 0.8rem;
      font-weight: 850;
      letter-spacing: 0.15em;
    }
    .step h3 { margin: 0 0 9px; font-size: 1rem; }
    .step p { margin: 0; color: var(--muted); font-size: 0.93rem; line-height: 1.7; }

    .security { padding-top: 22px; }
    .security-box {
      display: grid;
      grid-template-columns: 1fr 0.72fr;
      align-items: center;
      gap: 30px;
      padding: 38px;
      border: 1px solid var(--border);
      border-radius: 30px;
      background:
        radial-gradient(circle at 88% 7%, rgba(27, 187, 218, 0.16), transparent 18rem),
        linear-gradient(135deg, rgba(13,38,67,0.96), rgba(7,23,44,0.94));
      box-shadow: var(--shadow);
    }

    .security-list { display: grid; gap: 12px; margin-top: 21px; }
    .security-list div { display: flex; gap: 10px; color: #d6e4f3; font-size: 0.93rem; }
    .security-logo { display: grid; place-items: center; min-height: 280px; }
    .security-logo img { width: min(310px, 82%); filter: drop-shadow(0 24px 30px rgba(0, 181, 222, 0.22)); }

    .cta { padding: 94px 0; }
    .cta-box {
      padding: 57px 24px;
      border: 1px solid var(--border);
      border-radius: 30px;
      text-align: center;
      background:
        radial-gradient(circle at 22% 0, rgba(37,205,226,0.14), transparent 17rem),
        radial-gradient(circle at 82% 100%, rgba(50,119,220,0.14), transparent 19rem),
        rgba(255,255,255,0.025);
    }
    .cta-box h2 { max-width: 790px; margin-inline: auto; }
    .cta-box p { max-width: 680px; margin-inline: auto; }
    .cta-box .hero-actions { justify-content: center; }

    footer { padding: 26px 0 34px; border-top: 1px solid var(--border); }
    .footer-inner { display: flex; justify-content: space-between; gap: 18px; color: var(--muted); font-size: 0.85rem; }
    .footer-links { display: flex; flex-wrap: wrap; gap: 17px; }
    .footer-links a:hover { color: var(--text); }

    @media (max-width: 970px) {
      .hero-grid, .security-box { grid-template-columns: 1fr; }
      .hero { padding-top: 55px; }
      .visual-frame { margin-top: 4px; }
      .cards, .steps { grid-template-columns: 1fr; }
      .security-logo { min-height: 210px; }
      .security-logo img { width: min(240px, 70%); }
      .nav-links {
        display: none;
        position: absolute;
        top: 76px;
        left: 20px;
        right: 20px;
        padding: 16px;
        flex-direction: column;
        align-items: stretch;
        gap: 5px;
        border: 1px solid var(--border);
        border-radius: 17px;
        background: rgba(5, 14, 28, 0.98);
        box-shadow: var(--shadow);
      }
      .nav-links.open { display: flex; }
      .nav-links a { padding: 10px; }
      .mobile-toggle { display: block; }
      .desktop-cta { display: none; }
    }

    @media (max-width: 560px) {
      .container { width: min(100% - 28px, 1160px); }
      h1 { font-size: 3.55rem; }
      section { padding: 68px 0; }
      .nav-inner { gap: 8px; }
      .brand img { width: 42px; height: 42px; }
      .brand span { display: none; }
      .nav-right { gap: 8px; }
      .language-select { max-width: 127px; }
      .security-box { padding: 26px; }
      .footer-inner { flex-direction: column; }
    }
  </style>
</head>
<body>
  <header class="navbar" id="navbar">
    <div class="container nav-inner">
      <a class="brand" href="#home" aria-label="CamToVault">
        <img src="assets/camtovault-logo-transparent.png" alt="" aria-hidden="true">
        <span>CamToVault</span>
      </a>

      <div class="nav-right">
        <nav class="nav-links" id="navLinks" aria-label="Navigation principale">
          <a href="#features" data-i18n="nav.features">Fonctionnalités</a>
          <a href="#how-it-works" data-i18n="nav.how">Fonctionnement</a>
          <a href="#security" data-i18n="nav.security">Sécurité</a>
        </nav>

        <select class="language-select" id="languageSelect" aria-label="Choisir la langue">
          <option value="fr">Français</option>
          <option value="en">English</option>
          <option value="pt">Português</option>
          <option value="de">Deutsch</option>
          <option value="es">Español</option>
        </select>

        <a class="btn btn-primary desktop-cta" href="#features" data-i18n="nav.cta">Découvrir l’application</a>
        <button class="mobile-toggle" id="mobileToggle" type="button" aria-label="Ouvrir le menu" aria-expanded="false">☰</button>
      </div>
    </div>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="container hero-grid">
        <div>
          <div class="eyebrow"><span class="dot"></span><span data-i18n="hero.eyebrow">Caméra privée et coffre-fort chiffré</span></div>
          <h1><span data-i18n="hero.line1">Capturez en privé.</span><br><span class="gradient-text" data-i18n="hero.line2">Conservez en sécurité.</span></h1>
          <p class="hero-copy" data-i18n="hero.copy">CamToVault vous aide à protéger vos photos et vidéos sensibles dans un coffre-fort privé. Créez votre code PIN, capturez votre contenu et gardez le contrôle de vos médias.</p>
          <div class="hero-actions">
            <a class="btn btn-primary" href="#features" data-i18n="hero.primary">Découvrir CamToVault</a>
            <a class="btn btn-secondary" href="#how-it-works" data-i18n="hero.secondary">Voir le fonctionnement</a>
          </div>
          <div class="trust-row">
            <span><b class="check">✓</b><span data-i18n="hero.trust1">Accès protégé par PIN</span></span>
            <span><b class="check">✓</b><span data-i18n="hero.trust2">Coffre-fort privé</span></span>
            <span><b class="check">✓</b><span data-i18n="hero.trust3">Expérience simple</span></span>
          </div>
        </div>

        <div class="visual-frame">
          <img src="assets/camtovault-private-camera-encrypted-vault.png" alt="Présentation de CamToVault avec smartphone, caméra privée et coffre-fort chiffré" data-i18n-alt="hero.imageAlt">
        </div>
      </div>
    </section>

    <section id="features">
      <div class="container">
        <div class="section-head">
          <div class="eyebrow" data-i18n="features.eyebrow">Confidentialité par conception</div>
          <h2 data-i18n="features.title">Une application pensée pour garder vos médias privés.</h2>
          <p data-i18n="features.copy">CamToVault réunit une caméra dédiée et un espace de stockage privé afin de limiter la circulation inutile de vos photos et vidéos sensibles.</p>
        </div>

        <div class="cards">
          <article class="card">
            <div class="card-tag">01</div>
            <h3 data-i18n="features.card1Title">Caméra privée</h3>
            <p data-i18n="features.card1Copy">Prenez vos photos et vidéos depuis une interface dédiée, conçue pour les contenus que vous souhaitez conserver à l’écart de votre galerie habituelle.</p>
          </article>
          <article class="card">
            <div class="card-tag">02</div>
            <h3 data-i18n="features.card2Title">Protection par code PIN</h3>
            <p data-i18n="features.card2Copy">Créez un code PIN pour protéger l’accès à votre coffre-fort et renforcer la confidentialité de vos contenus enregistrés.</p>
          </article>
          <article class="card">
            <div class="card-tag">03</div>
            <h3 data-i18n="features.card3Title">Coffre-fort chiffré</h3>
            <p data-i18n="features.card3Copy">Conservez vos médias sensibles dans un espace privé pensé pour réduire les accès non souhaités.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="how-it-works">
      <div class="container">
        <div class="section-head">
          <div class="eyebrow" data-i18n="how.eyebrow">Simple à utiliser</div>
          <h2 data-i18n="how.title">Trois étapes pour protéger vos captures.</h2>
          <p data-i18n="how.copy">Une expérience volontairement simple : sécurisez l’accès, capturez vos médias et retrouvez-les dans votre espace privé.</p>
        </div>

        <div class="steps">
          <article class="step">
            <h3 data-i18n="how.step1Title">Créez votre code PIN</h3>
            <p data-i18n="how.step1Copy">Configurez votre accès personnel dès l’ouverture de l’application afin de protéger votre coffre-fort.</p>
          </article>
          <article class="step">
            <h3 data-i18n="how.step2Title">Prenez vos photos et vidéos</h3>
            <p data-i18n="how.step2Copy">Utilisez la caméra CamToVault pour créer les médias que vous ne souhaitez pas laisser dans une galerie classique.</p>
          </article>
          <article class="step">
            <h3 data-i18n="how.step3Title">Consultez votre coffre-fort</h3>
            <p data-i18n="how.step3Copy">Retrouvez vos captures dans un espace privé et gardez une expérience claire au quotidien.</p>
          </article>
        </div>
      </div>
    </section>

    <section class="security" id="security">
      <div class="container security-box">
        <div class="security-content">
          <div class="eyebrow" data-i18n="security.eyebrow">Une priorité : la confidentialité</div>
          <h2 data-i18n="security.title">Vos captures privées méritent un espace dédié.</h2>
          <p data-i18n="security.copy">CamToVault est conçu pour séparer vos médias sensibles de votre galerie habituelle et vous offrir un accès protégé dans une interface sobre et intuitive.</p>
          <div class="security-list">
            <div><span class="check">✓</span><span data-i18n="security.item1">Accès personnel protégé par votre code PIN</span></div>
            <div><span class="check">✓</span><span data-i18n="security.item2">Espace dédié à vos photos et vidéos privées</span></div>
            <div><span class="check">✓</span><span data-i18n="security.item3">Interface pensée pour une utilisation quotidienne simple</span></div>
          </div>
        </div>
        <div class="security-logo" aria-hidden="true">
          <img src="assets/camtovault-logo-transparent.png" alt="">
        </div>
      </div>
    </section>

    <section class="cta" id="about">
      <div class="container cta-box">
        <h2 data-i18n="cta.title">Une caméra privée. Un coffre-fort chiffré. Un seul objectif : protéger vos médias.</h2>
        <p data-i18n="cta.copy">CamToVault est en cours de développement. Cette page présente les principes essentiels de l’application et son approche centrée sur la confidentialité.</p>
        <div class="hero-actions">
          <a class="btn btn-primary" href="#features" data-i18n="cta.primary">Découvrir les fonctionnalités</a>
          <a class="btn btn-secondary" href="#home" data-i18n="cta.secondary">Retour en haut</a>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="container footer-inner">
      <div>© <span id="year"></span> CamToVault. <span data-i18n="footer.rights">Tous droits réservés.</span></div>
      <div class="footer-links">
        <a href="https://sites.google.com/view/camtovault/accueil/privacy-policy" target="_blank" rel="noopener noreferrer" data-i18n="footer.privacy">Politique de confidentialité</a>
      </div>
    </div>
  </footer>

  <script>
    const translations = {
      fr: {
        meta: { title: "CamToVault — Caméra privée. Coffre-fort chiffré.", description: "CamToVault est une caméra privée avec coffre-fort chiffré pour protéger vos photos et vidéos sensibles." },
        nav: { features: "Fonctionnalités", how: "Fonctionnement", security: "Sécurité", cta: "Découvrir l’application" },
        hero: { eyebrow: "Caméra privée et coffre-fort chiffré", line1: "Capturez en privé.", line2: "Conservez en sécurité.", copy: "CamToVault vous aide à protéger vos photos et vidéos sensibles dans un coffre-fort privé. Créez votre code PIN, capturez votre contenu et gardez le contrôle de vos médias.", primary: "Découvrir CamToVault", secondary: "Voir le fonctionnement", trust1: "Accès protégé par PIN", trust2: "Coffre-fort privé", trust3: "Expérience simple", imageAlt: "Présentation de CamToVault avec smartphone, caméra privée et coffre-fort chiffré" },
        features: { eyebrow: "Confidentialité par conception", title: "Une application pensée pour garder vos médias privés.", copy: "CamToVault réunit une caméra dédiée et un espace de stockage privé afin de limiter la circulation inutile de vos photos et vidéos sensibles.", card1Title: "Caméra privée", card1Copy: "Prenez vos photos et vidéos depuis une interface dédiée, conçue pour les contenus que vous souhaitez conserver à l’écart de votre galerie habituelle.", card2Title: "Protection par code PIN", card2Copy: "Créez un code PIN pour protéger l’accès à votre coffre-fort et renforcer la confidentialité de vos contenus enregistrés.", card3Title: "Coffre-fort chiffré", card3Copy: "Conservez vos médias sensibles dans un espace privé pensé pour réduire les accès non souhaités." },
        how: { eyebrow: "Simple à utiliser", title: "Trois étapes pour protéger vos captures.", copy: "Une expérience volontairement simple : sécurisez l’accès, capturez vos médias et retrouvez-les dans votre espace privé.", step1Title: "Créez votre code PIN", step1Copy: "Configurez votre accès personnel dès l’ouverture de l’application afin de protéger votre coffre-fort.", step2Title: "Prenez vos photos et vidéos", step2Copy: "Utilisez la caméra CamToVault pour créer les médias que vous ne souhaitez pas laisser dans une galerie classique.", step3Title: "Consultez votre coffre-fort", step3Copy: "Retrouvez vos captures dans un espace privé et gardez une expérience claire au quotidien." },
        security: { eyebrow: "Une priorité : la confidentialité", title: "Vos captures privées méritent un espace dédié.", copy: "CamToVault est conçu pour séparer vos médias sensibles de votre galerie habituelle et vous offrir un accès protégé dans une interface sobre et intuitive.", item1: "Accès personnel protégé par votre code PIN", item2: "Espace dédié à vos photos et vidéos privées", item3: "Interface pensée pour une utilisation quotidienne simple" },
        cta: { title: "Une caméra privée. Un coffre-fort chiffré. Un seul objectif : protéger vos médias.", copy: "CamToVault est en cours de développement. Cette page présente les principes essentiels de l’application et son approche centrée sur la confidentialité.", primary: "Découvrir les fonctionnalités", secondary: "Retour en haut" },
        footer: { rights: "Tous droits réservés.", privacy: "Politique de confidentialité" }
      },
      en: {
        meta: { title: "CamToVault — Private Camera. Encrypted Vault.", description: "CamToVault is a private camera with an encrypted vault designed to protect your sensitive photos and videos." },
        nav: { features: "Features", how: "How it works", security: "Security", cta: "Discover the app" },
        hero: { eyebrow: "Private camera and encrypted vault", line1: "Capture privately.", line2: "Store securely.", copy: "CamToVault helps protect your sensitive photos and videos in a private vault. Create your PIN, capture your content and stay in control of your media.", primary: "Discover CamToVault", secondary: "See how it works", trust1: "PIN-protected access", trust2: "Private vault", trust3: "Simple experience", imageAlt: "CamToVault presentation featuring a smartphone, a private camera and an encrypted vault" },
        features: { eyebrow: "Privacy by design", title: "An app designed to keep your media private.", copy: "CamToVault combines a dedicated camera and a private storage space to help avoid unnecessary exposure of your sensitive photos and videos.", card1Title: "Private camera", card1Copy: "Take photos and videos from a dedicated interface designed for content you prefer to keep away from your usual gallery.", card2Title: "PIN protection", card2Copy: "Create a PIN to protect access to your vault and strengthen the privacy of your saved content.", card3Title: "Encrypted vault", card3Copy: "Keep your sensitive media in a private space designed to reduce unwanted access." },
        how: { eyebrow: "Easy to use", title: "Three steps to protect your captures.", copy: "A deliberately simple experience: secure access, capture your media and find it in your private space.", step1Title: "Create your PIN", step1Copy: "Set up your personal access when opening the app to protect your vault.", step2Title: "Take your photos and videos", step2Copy: "Use the CamToVault camera to create media you do not want to leave in a standard gallery.", step3Title: "Access your vault", step3Copy: "Find your captures in a private space and keep a clear everyday experience." },
        security: { eyebrow: "One priority: privacy", title: "Your private captures deserve a dedicated space.", copy: "CamToVault is designed to separate your sensitive media from your usual gallery and give you protected access through a clean, intuitive interface.", item1: "Personal access protected by your PIN", item2: "Dedicated space for your private photos and videos", item3: "Interface designed for simple everyday use" },
        cta: { title: "A private camera. An encrypted vault. One goal: protecting your media.", copy: "CamToVault is currently under development. This page presents the app’s core principles and its privacy-focused approach.", primary: "Discover the features", secondary: "Back to top" },
        footer: { rights: "All rights reserved.", privacy: "Privacy Policy" }
      },
      pt: {
        meta: { title: "CamToVault — Câmara privada. Cofre encriptado.", description: "CamToVault é uma câmara privada com cofre encriptado para proteger as suas fotos e vídeos sensíveis." },
        nav: { features: "Funcionalidades", how: "Como funciona", security: "Segurança", cta: "Descobrir a aplicação" },
        hero: { eyebrow: "Câmara privada e cofre encriptado", line1: "Capture em privado.", line2: "Guarde em segurança.", copy: "O CamToVault ajuda a proteger as suas fotos e vídeos sensíveis num cofre privado. Crie o seu PIN, capture o seu conteúdo e mantenha o controlo dos seus ficheiros multimédia.", primary: "Descobrir CamToVault", secondary: "Ver como funciona", trust1: "Acesso protegido por PIN", trust2: "Cofre privado", trust3: "Experiência simples", imageAlt: "Apresentação do CamToVault com smartphone, câmara privada e cofre encriptado" },
        features: { eyebrow: "Privacidade desde a conceção", title: "Uma aplicação pensada para manter os seus ficheiros multimédia privados.", copy: "O CamToVault combina uma câmara dedicada e um espaço de armazenamento privado para limitar a exposição desnecessária das suas fotos e vídeos sensíveis.", card1Title: "Câmara privada", card1Copy: "Capture fotos e vídeos numa interface dedicada, concebida para os conteúdos que pretende manter separados da galeria habitual.", card2Title: "Proteção por código PIN", card2Copy: "Crie um PIN para proteger o acesso ao seu cofre e reforçar a privacidade do conteúdo guardado.", card3Title: "Cofre encriptado", card3Copy: "Mantenha os seus ficheiros multimédia sensíveis num espaço privado pensado para reduzir acessos indesejados." },
        how: { eyebrow: "Simples de utilizar", title: "Três passos para proteger as suas capturas.", copy: "Uma experiência deliberadamente simples: proteja o acesso, capture os seus ficheiros e encontre-os no seu espaço privado.", step1Title: "Crie o seu PIN", step1Copy: "Configure o seu acesso pessoal ao abrir a aplicação para proteger o seu cofre.", step2Title: "Capture as suas fotos e vídeos", step2Copy: "Utilize a câmara CamToVault para criar conteúdos que não pretende deixar numa galeria convencional.", step3Title: "Consulte o seu cofre", step3Copy: "Encontre as suas capturas num espaço privado e mantenha uma experiência simples no dia a dia." },
        security: { eyebrow: "Uma prioridade: a privacidade", title: "As suas capturas privadas merecem um espaço dedicado.", copy: "O CamToVault foi concebido para separar os seus ficheiros sensíveis da galeria habitual e proporcionar um acesso protegido através de uma interface simples e intuitiva.", item1: "Acesso pessoal protegido pelo seu PIN", item2: "Espaço dedicado às suas fotos e vídeos privados", item3: "Interface pensada para uma utilização diária simples" },
        cta: { title: "Uma câmara privada. Um cofre encriptado. Um único objetivo: proteger os seus ficheiros.", copy: "O CamToVault está em desenvolvimento. Esta página apresenta os princípios essenciais da aplicação e a sua abordagem centrada na privacidade.", primary: "Descobrir as funcionalidades", secondary: "Voltar ao topo" },
        footer: { rights: "Todos os direitos reservados.", privacy: "Política de privacidade" }
      },
      de: {
        meta: { title: "CamToVault — Private Kamera. Verschlüsselter Tresor.", description: "CamToVault ist eine private Kamera mit verschlüsseltem Tresor zum Schutz sensibler Fotos und Videos." },
        nav: { features: "Funktionen", how: "So funktioniert es", security: "Sicherheit", cta: "App entdecken" },
        hero: { eyebrow: "Private Kamera und verschlüsselter Tresor", line1: "Privat aufnehmen.", line2: "Sicher aufbewahren.", copy: "CamToVault hilft Ihnen dabei, sensible Fotos und Videos in einem privaten Tresor zu schützen. Erstellen Sie Ihre PIN, nehmen Sie Inhalte auf und behalten Sie die Kontrolle über Ihre Medien.", primary: "CamToVault entdecken", secondary: "Funktionsweise ansehen", trust1: "PIN-geschützter Zugriff", trust2: "Privater Tresor", trust3: "Einfache Bedienung", imageAlt: "CamToVault-Präsentation mit Smartphone, privater Kamera und verschlüsseltem Tresor" },
        features: { eyebrow: "Datenschutz von Anfang an", title: "Eine App, die Ihre Medien privat hält.", copy: "CamToVault kombiniert eine eigene Kamera mit einem privaten Speicherbereich, um die unnötige Verbreitung sensibler Fotos und Videos zu begrenzen.", card1Title: "Private Kamera", card1Copy: "Nehmen Sie Fotos und Videos über eine eigene Oberfläche auf, die für Inhalte gedacht ist, die nicht in Ihrer üblichen Galerie erscheinen sollen.", card2Title: "PIN-Schutz", card2Copy: "Erstellen Sie eine PIN, um den Zugriff auf Ihren Tresor zu schützen und die Privatsphäre Ihrer gespeicherten Inhalte zu stärken.", card3Title: "Verschlüsselter Tresor", card3Copy: "Bewahren Sie sensible Medien in einem privaten Bereich auf, der unerwünschte Zugriffe reduzieren soll." },
        how: { eyebrow: "Einfach zu verwenden", title: "Drei Schritte zum Schutz Ihrer Aufnahmen.", copy: "Bewusst unkompliziert: Zugriff sichern, Medien aufnehmen und im privaten Bereich wiederfinden.", step1Title: "PIN erstellen", step1Copy: "Richten Sie beim Öffnen der App Ihren persönlichen Zugang ein, um Ihren Tresor zu schützen.", step2Title: "Fotos und Videos aufnehmen", step2Copy: "Nutzen Sie die CamToVault-Kamera für Medien, die nicht in einer herkömmlichen Galerie verbleiben sollen.", step3Title: "Tresor öffnen", step3Copy: "Finden Sie Ihre Aufnahmen in einem privaten Bereich und behalten Sie im Alltag den Überblick." },
        security: { eyebrow: "Eine Priorität: Datenschutz", title: "Ihre privaten Aufnahmen verdienen einen eigenen Bereich.", copy: "CamToVault trennt sensible Medien von Ihrer üblichen Galerie und bietet einen geschützten Zugriff über eine übersichtliche, intuitive Oberfläche.", item1: "Persönlicher Zugriff, geschützt durch Ihre PIN", item2: "Eigener Bereich für private Fotos und Videos", item3: "Oberfläche für eine unkomplizierte tägliche Nutzung" },
        cta: { title: "Eine private Kamera. Ein verschlüsselter Tresor. Ein Ziel: Schutz Ihrer Medien.", copy: "CamToVault befindet sich in der Entwicklung. Diese Seite stellt die Grundprinzipien der App und ihren datenschutzorientierten Ansatz vor.", primary: "Funktionen entdecken", secondary: "Nach oben" },
        footer: { rights: "Alle Rechte vorbehalten.", privacy: "Datenschutzerklärung" }
      },
      es: {
        meta: { title: "CamToVault — Cámara privada. Bóveda cifrada.", description: "CamToVault es una cámara privada con bóveda cifrada para proteger tus fotos y vídeos sensibles." },
        nav: { features: "Funciones", how: "Cómo funciona", security: "Seguridad", cta: "Descubrir la aplicación" },
        hero: { eyebrow: "Cámara privada y bóveda cifrada", line1: "Captura en privado.", line2: "Guarda con seguridad.", copy: "CamToVault te ayuda a proteger tus fotos y vídeos sensibles en una bóveda privada. Crea tu PIN, captura tu contenido y mantén el control de tus archivos multimedia.", primary: "Descubrir CamToVault", secondary: "Ver cómo funciona", trust1: "Acceso protegido por PIN", trust2: "Bóveda privada", trust3: "Experiencia sencilla", imageAlt: "Presentación de CamToVault con smartphone, cámara privada y bóveda cifrada" },
        features: { eyebrow: "Privacidad desde el diseño", title: "Una aplicación pensada para mantener tus archivos multimedia privados.", copy: "CamToVault combina una cámara dedicada y un espacio de almacenamiento privado para limitar la exposición innecesaria de tus fotos y vídeos sensibles.", card1Title: "Cámara privada", card1Copy: "Toma fotos y vídeos desde una interfaz dedicada, diseñada para el contenido que prefieres mantener separado de tu galería habitual.", card2Title: "Protección mediante PIN", card2Copy: "Crea un PIN para proteger el acceso a tu bóveda y reforzar la privacidad de tu contenido guardado.", card3Title: "Bóveda cifrada", card3Copy: "Guarda tus archivos multimedia sensibles en un espacio privado pensado para reducir accesos no deseados." },
        how: { eyebrow: "Fácil de usar", title: "Tres pasos para proteger tus capturas.", copy: "Una experiencia deliberadamente sencilla: protege el acceso, captura tus archivos y encuéntralos en tu espacio privado.", step1Title: "Crea tu PIN", step1Copy: "Configura tu acceso personal al abrir la aplicación para proteger tu bóveda.", step2Title: "Toma tus fotos y vídeos", step2Copy: "Utiliza la cámara de CamToVault para crear contenido que no quieres dejar en una galería convencional.", step3Title: "Consulta tu bóveda", step3Copy: "Encuentra tus capturas en un espacio privado y disfruta de una experiencia clara en el día a día." },
        security: { eyebrow: "Una prioridad: la privacidad", title: "Tus capturas privadas merecen un espacio dedicado.", copy: "CamToVault está diseñado para separar tus archivos multimedia sensibles de tu galería habitual y ofrecerte un acceso protegido mediante una interfaz clara e intuitiva.", item1: "Acceso personal protegido por tu PIN", item2: "Espacio dedicado para tus fotos y vídeos privados", item3: "Interfaz pensada para un uso diario sencillo" },
        cta: { title: "Una cámara privada. Una bóveda cifrada. Un único objetivo: proteger tus archivos.", copy: "CamToVault está en desarrollo. Esta página presenta los principios esenciales de la aplicación y su enfoque centrado en la privacidad.", primary: "Descubrir las funciones", secondary: "Volver arriba" },
        footer: { rights: "Todos los derechos reservados.", privacy: "Política de privacidad" }
      }
    };

    const localeMap = { fr: "fr_FR", en: "en_US", pt: "pt_PT", de: "de_DE", es: "es_ES" };
    const navbar = document.getElementById("navbar");
    const navLinks = document.getElementById("navLinks");
    const mobileToggle = document.getElementById("mobileToggle");
    const languageSelect = document.getElementById("languageSelect");
    const metaDescription = document.getElementById("meta-description");

    function getNestedValue(object, path) {
      return path.split(".").reduce((value, key) => value && value[key], object);
    }

    function applyLanguage(language) {
      const selectedLanguage = translations[language] ? language : "fr";
      const dictionary = translations[selectedLanguage];

      document.documentElement.lang = selectedLanguage;
      document.title = dictionary.meta.title;
      metaDescription.setAttribute("content", dictionary.meta.description);
      document.querySelector('meta[property="og:title"]').setAttribute("content", dictionary.meta.title);
      document.querySelector('meta[property="og:description"]').setAttribute("content", dictionary.meta.description);
      document.querySelector('meta[property="og:locale"]').setAttribute("content", localeMap[selectedLanguage]);

      document.querySelectorAll("[data-i18n]").forEach((element) => {
        const translatedText = getNestedValue(dictionary, element.dataset.i18n);
        if (translatedText) element.textContent = translatedText;
      });

      document.querySelectorAll("[data-i18n-alt]").forEach((element) => {
        const translatedText = getNestedValue(dictionary, element.dataset.i18nAlt);
        if (translatedText) element.setAttribute("alt", translatedText);
      });

      languageSelect.value = selectedLanguage;
      localStorage.setItem("camtovault-language", selectedLanguage);
    }

    function getInitialLanguage() {
      const savedLanguage = localStorage.getItem("camtovault-language");
      if (savedLanguage && translations[savedLanguage]) return savedLanguage;
      const browserLanguage = navigator.language.slice(0, 2).toLowerCase();
      return translations[browserLanguage] ? browserLanguage : "fr";
    }

    window.addEventListener("scroll", () => {
      navbar.classList.toggle("scrolled", window.scrollY > 16);
    });

    mobileToggle.addEventListener("click", () => {
      const isOpen = navLinks.classList.toggle("open");
      mobileToggle.setAttribute("aria-expanded", String(isOpen));
      mobileToggle.textContent = isOpen ? "✕" : "☰";
    });

    navLinks.querySelectorAll("a").forEach((link) => {
      link.addEventListener("click", () => {
        navLinks.classList.remove("open");
        mobileToggle.setAttribute("aria-expanded", "false");
        mobileToggle.textContent = "☰";
      });
    });

    languageSelect.addEventListener("change", (event) => applyLanguage(event.target.value));
    document.getElementById("year").textContent = new Date().getFullYear();
    applyLanguage(getInitialLanguage());
  </script>
</body>
</html>
