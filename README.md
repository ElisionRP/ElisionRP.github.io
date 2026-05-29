<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Elision Role Play</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg: #05070b;
      --bg-alt: #0b0f18;
      --accent: #1e90ff;
      --accent-soft: #1e90ff22;
      --text: #f5f7ff;
      --muted: #9aa3c2;
      --danger: #ff4b6a;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background: radial-gradient(circle at top, #10172a 0, #05070b 55%);
      color: var(--text);
      min-height: 100vh;
    }

    a {
      color: var(--accent);
      text-decoration: none;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 20;
      backdrop-filter: blur(16px);
      background: linear-gradient(to right, #05070bcc, #05070b00);
      border-bottom: 1px solid #1b2236;
    }

    .nav {
      max-width: 1120px;
      margin: 0 auto;
      padding: 0.9rem 1.5rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 1.5rem;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 0.6rem;
    }

    .brand-logo {
      width: 32px;
      height: 32px;
      border-radius: 10px;
      background: radial-gradient(circle at 20% 0, #4fd1ff, #1e90ff 40%, #05070b 100%);
      box-shadow: 0 0 18px #1e90ff66;
    }

    .brand-text {
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      font-size: 0.8rem;
      color: var(--muted);
    }

    .brand-text span {
      color: var(--accent);
    }

    .nav-links {
      display: flex;
      gap: 1.25rem;
      font-size: 0.9rem;
    }

    .nav-links a {
      color: var(--muted);
      padding-bottom: 0.2rem;
      border-bottom: 2px solid transparent;
    }

    .nav-links a:hover {
      color: var(--text);
      border-bottom-color: var(--accent);
    }

    .nav-cta {
      display: flex;
      gap: 0.75rem;
    }

    .btn {
      border-radius: 999px;
      padding: 0.45rem 1.1rem;
      font-size: 0.85rem;
      border: 1px solid transparent;
      cursor: pointer;
      transition: 0.18s ease-out;
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      background: none;
      color: var(--text);
    }

    .btn-outline {
      border-color: #28324a;
      color: var(--muted);
    }

    .btn-outline:hover {
      border-color: var(--accent);
      color: var(--text);
      background: #1b223633;
    }

    .btn-primary {
      background: linear-gradient(135deg, #1e90ff, #4f46e5);
      box-shadow: 0 0 18px #1e90ff66;
    }

    .btn-primary:hover {
      transform: translateY(-1px);
      box-shadow: 0 0 26px #1e90ff88;
    }

    main {
      max-width: 1120px;
      margin: 0 auto;
      padding: 2.5rem 1.5rem 3.5rem;
    }

    /* Hero */

    .hero {
      display: grid;
      grid-template-columns: minmax(0, 3fr) minmax(0, 2.5fr);
      gap: 2.5rem;
      align-items: center;
      padding-top: 1.5rem;
    }

    .hero-kicker {
      font-size: 0.75rem;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 0.75rem;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
    }

    .hero-kicker span {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: var(--accent);
      box-shadow: 0 0 10px #1e90ff;
    }

    .hero-title {
      font-size: clamp(2.4rem, 3vw + 1.4rem, 3.4rem);
      line-height: 1.05;
      margin-bottom: 0.9rem;
    }

    .hero-title span {
      color: var(--accent);
      text-shadow: 0 0 18px #1e90ff55;
    }

    .hero-subtitle {
      color: var(--muted);
      font-size: 0.98rem;
      max-width: 32rem;
      line-height: 1.6;
      margin-bottom: 1.4rem;
    }

    .hero-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;
      margin-bottom: 1.6rem;
      font-size: 0.8rem;
      color: var(--muted);
    }

    .hero-meta-pill {
      padding: 0.25rem 0.7rem;
      border-radius: 999px;
      background: #10172a;
      border: 1px solid #28324a;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;
      align-items: center;
      margin-bottom: 1.2rem;
    }

    .hero-footnote {
      font-size: 0.75rem;
      color: var(--muted);
    }

    .hero-footnote strong {
      color: var(--accent);
      font-weight: 600;
    }

    /* Hero visual */

    .hero-card {
      background: radial-gradient(circle at top, #1e293b, #020617);
      border-radius: 1.4rem;
      border: 1px solid #28324a;
      padding: 1.2rem 1.2rem 1.1rem;
      box-shadow: 0 24px 60px #000000aa;
      position: relative;
      overflow: hidden;
    }

    .hero-card::before {
      content: "";
      position: absolute;
      inset: -40%;
      background:
        radial-gradient(circle at 0 0, #1e90ff33 0, transparent 55%),
        radial-gradient(circle at 100% 0, #4f46e533 0, transparent 55%);
      opacity: 0.8;
      pointer-events: none;
    }

    .hero-card-inner {
      position: relative;
      border-radius: 1rem;
      border: 1px solid #1f2937;
      padding: 1rem;
      background: linear-gradient(145deg, #020617, #020617ee);
    }

    .hero-card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 0.9rem;
      font-size: 0.8rem;
      color: var(--muted);
    }

    .status-pill {
      padding: 0.18rem 0.6rem;
      border-radius: 999px;
      background: #16a34a22;
      color: #4ade80;
      border: 1px solid #16a34a55;
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
    }

    .hero-city {
      position: relative;
      border-radius: 0.9rem;
      overflow: hidden;
      height: 210px;
      background:
        linear-gradient(to top, #020617 0, transparent 40%),
        url("https://images.pexels.com/photos/313782/pexels-photo-313782.jpeg?auto=compress&cs=tinysrgb&w=1200")
        center/cover no-repeat;
      filter: saturate(1.2) contrast(1.05);
    }

    .hero-city-overlay {
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 10% 0, #1e90ff33, transparent 55%);
      mix-blend-mode: screen;
    }

    .hero-city-footer {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      padding: 0.7rem 0.9rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.75rem;
      background: linear-gradient(to top, #020617ee, transparent);
      color: var(--muted);
    }

    .hero-city-footer strong {
      color: var(--text);
      font-weight: 600;
    }

    .hero-tag-row {
      display: flex;
      gap: 0.4rem;
      margin-top: 0.4rem;
      flex-wrap: wrap;
    }

    .hero-tag {
      padding: 0.15rem 0.55rem;
      border-radius: 999px;
      border: 1px solid #1f2937;
      background: #020617aa;
      font-size: 0.7rem;
    }

    .hero-card-badge {
      position: absolute;
      top: 0.9rem;
      right: 1.1rem;
      padding: 0.3rem 0.7rem;
      border-radius: 999px;
      background: #020617dd;
      border: 1px solid #1e90ff55;
      font-size: 0.7rem;
      color: var(--muted);
      display: flex;
      align-items: center;
      gap: 0.35rem;
    }

    .hero-card-badge span {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 10px #22c55eaa;
    }

    /* Sections */

    section {
      margin-top: 3rem;
    }

    .section-label {
      font-size: 0.75rem;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 0.4rem;
    }

    .section-title {
      font-size: 1.4rem;
      margin-bottom: 0.9rem;
    }

    .section-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
      gap: 1.1rem;
    }

    .card {
      background: var(--bg-alt);
      border-radius: 0.9rem;
      border: 1px solid #1f2937;
      padding: 0.9rem 1rem;
      font-size: 0.9rem;
    }

    .card h3 {
      font-size: 1rem;
      margin-bottom: 0.35rem;
    }

    .card p {
      color: var(--muted);
      font-size: 0.85rem;
      line-height: 1.5;
      margin-bottom: 0.5rem;
    }

    .pill-row {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 0.3rem;
    }

    .pill {
      padding: 0.15rem 0.55rem;
      border-radius: 999px;
      border: 1px solid #28324a;
      font-size: 0.7rem;
      color: var(--muted);
    }

    /* Rules list */

    .rules-list {
      list-style: none;
      display: grid;
      gap: 0.6rem;
      font-size: 0.85rem;
      color: var(--muted);
    }

    .rules-list li {
      padding: 0.55rem 0.7rem;
      border-radius: 0.6rem;
      background: #020617;
      border: 1px solid #111827;
    }

    .rules-list strong {
      color: var(--text);
      font-weight: 600;
    }

    /* CTA strip */

    .cta-strip {
      margin-top: 3rem;
      border-radius: 1rem;
      padding: 1.1rem 1.2rem;
      background: radial-gradient(circle at 0 0, #1e90ff33, transparent 55%), #020617;
      border: 1px solid #1f2937;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.9rem;
      font-size: 0.9rem;
    }

    .cta-strip p {
      color: var(--muted);
      max-width: 26rem;
    }

    footer {
      border-top: 1px solid #111827;
      margin-top: 3rem;
      padding: 1.2rem 1.5rem 2rem;
      font-size: 0.75rem;
      color: var(--muted);
      text-align: center;
    }

    @media (max-width: 800px) {
      .hero {
        grid-template-columns: minmax(0, 1fr);
      }
      .hero-card {
        order: -1;
      }
      .nav-links {
        display: none;
      }
    }
  </style>
</head>
<body>
  <header>
    <nav class="nav">
      <div class="brand">
        <div class="brand-logo"></div>
        <div class="brand-text"><span>ELISION</span>&nbsp;ROLE PLAY</div>
      </div>
      <div class="nav-links">
        <a href="#about">About</a>
        <a href="#features">Features</a>
        <a href="#rules">Rules</a>
        <a href="#join">Join</a>
      </div>
      <div class="nav-cta">
        <button class="btn btn-outline">Discord</button>
        <button class="btn btn-primary">Apply Now</button>
      </div>
    </nav>
  </header>

  <main>
    <!-- Hero -->
    <section class="hero">
      <div>
        <div class="hero-kicker">
          <span></span> Los Santos · Serious RP
        </div>
        <h1 class="hero-title">
          Elision Role Play<br />
          <span>Where stories own the streets.</span>
        </h1>
        <p class="hero-subtitle">
          A curated Los Santos role play experience focused on character, consequence, and cinematic moments—
          not chaos lobbies. Build your story, earn your reputation, and leave a mark that actually matters.
        </p>

        <div class="hero-meta">
          <div class="hero-meta-pill">Whitelisted · 18+</div>
          <div class="hero-meta-pill">Serious / Semi-Serious RP</div>
          <div class="hero-meta-pill">Custom Framework</div>
        </div>

        <div class="hero-actions">
          <button class="btn btn-primary">Join the Discord</button>
          <button class="btn btn-outline">View Server Rules</button>
        </div>

        <div class="hero-footnote">
          <strong>Elision Report:</strong> transparent staff actions, ban logs, and community updates—publicly visible, no smoke and mirrors.
        </div>
      </div>

      <aside class="hero-card">
        <div class="hero-card-badge">
          <span></span> Live server status
        </div>
        <div class="hero-card-inner">
          <div class="hero-card-header">
            <div>
              <div style="font-size:0.8rem;color:#e5e7eb;">Elision Report</div>
              <div style="font-size:0.7rem;color:#9ca3af;">Staff actions · Community transparency</div>
            </div>
            <div class="status-pill">Online</div>
          </div>

          <div class="hero-city">
            <div class="hero-city-overlay"></div>
            <div class="hero-city-footer">
              <div>
                <strong>Los Santos</strong><br />
                <span>Active scenes · Night patrols · City stories</span>
              </div>
              <div style="text-align:right;">
                <strong>128</strong> / 200<br />
                <span>Players in city</span>
              </div>
            </div>
          </div>

          <div class="hero-tag-row">
            <div class="hero-tag">Ban & warning logs</div>
            <div class="hero-tag">Staff decisions explained</div>
            <div class="hero-tag">Appeal outcomes</div>
          </div>
        </div>
      </aside>
    </section>

    <!-- About -->
    <section id="about">
      <div class="section-label">About</div>
      <h2 class="section-title">What is Elision Role Play?</h2>
      <div class="section-grid">
        <div class="card">
          <h3>Story-first Los Santos</h3>
          <p>
            Elision is built for players who care about immersion, continuity, and character development.
            Every scene should feel like it belongs in a series, not a random highlight reel.
          </p>
          <div class="pill-row">
            <span class="pill">Long-term characters</span>
            <span class="pill">Consequences matter</span>
            <span class="pill">Cinematic pacing</span>
          </div>
        </div>
        <div class="card">
          <h3>Transparent staff culture</h3>
          <p>
            The Elision Report is our public-facing log of staff actions, bans, warnings, and major decisions.
            No shadow decisions, no mystery bans—if it affects the community, it’s documented.
          </p>
          <div class="pill-row">
            <span class="pill">Public logs</span>
            <span class="pill">Explained decisions</span>
            <span class="pill">Appeal visibility</span>
          </div>
        </div>
        <div class="card">
          <h3>Curated player base</h3>
          <p>
            We’d rather have 80 great roleplayers than 200 randoms. Applications are reviewed by staff who
            actually play, and we prioritize fit over numbers.
          </p>
          <div class="pill-row">
            <span class="pill">Application-based</span>
            <span class="pill">18+ focus</span>
            <span class="pill">Quality over quantity</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Features -->
    <section id="features">
      <div class="section-label">Features</div>
      <h2 class="section-title">City features & systems</h2>
      <div class="section-grid">
        <div class="card">
          <h3>Legal & illegal balance</h3>
          <p>
            From PD and EMS to gangs, crews, and solo operators—both sides of the city get tools, depth,
            and reasons to interact beyond shootouts.
          </p>
          <div class="pill-row">
            <span class="pill">PD & EMS frameworks</span>
            <span class="pill">Investigations</span>
            <span class="pill">Organized crime</span>
          </div>
        </div>
        <div class="card">
          <h3>Economy with weight</h3>
          <p>
            Money means something. Jobs, businesses, and crime all feed into an economy where progression
            takes effort and smart play, not just grinding.
          </p>
          <div class="pill-row">
            <span class="pill">Player jobs</span>
            <span class="pill">Businesses</span>
            <span class="pill">Risk vs reward</span>
          </div>
        </div>
        <div class="card">
          <h3>Events & story arcs</h3>
          <p>
            Staff and storytellers run arcs that shape the city—elections, turf wars, investigations,
            and long-form plots that respond to player choices.
          </p>
          <div class="pill-row">
            <span class="pill">Planned events</span>
            <span class="pill">Reactive storytelling</span>
            <span class="pill">Community input</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Rules / Elision Report angle -->
    <section id="rules">
      <div class="section-label">Rules & report</div>
      <h2 class="section-title">Core rules & Elision Report</h2>
      <div class="section-grid">
        <div class="card">
          <h3>Core server rules</h3>
          <ul class="rules-list">
            <li><strong>1. Character over ego.</strong> Win or lose, your character’s story comes first.</li>
            <li><strong>2. No fail RP.</strong> Don’t ignore fear, injury, or obvious consequences.</li>
            <li><strong>3. No OOC toxicity.</strong> Disagreements stay respectful and in the right channels.</li>
            <li><strong>4. No random chaos.</strong> RDM/VDM and troll behavior are zero-tolerance.</li>
          </ul>
        </div>
        <div class="card">
          <h3>The Elision Report</h3>
          <p>
            The Elision Report is a living log of staff actions. Major bans, warnings, and appeals are
            documented with short context so the community understands what’s happening and why.
          </p>
          <p>
            This keeps staff accountable, sets clear precedent, and helps players learn from past cases
            instead of repeating them.
          </p>
          <div class="pill-row">
            <span class="pill">Ban reports</span>
            <span class="pill">Warning history</span>
            <span class="pill">Appeal outcomes</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Join -->
    <section id="join">
      <div class="section-label">Join</div>
      <h2 class="section-title">Ready to step into Elision?</h2>
      <div class="section-grid">
        <div class="card">
          <h3>Step 1 · Join Discord</h3>
          <p>
            Join our Discord to access applications, announcements, and live support. This is where
            everything starts.
          </p>
          <p style="font-size:0.8rem;color:var(--muted);">
            Replace this text with your actual Discord invite link.
          </p>
          <button class="btn btn-primary">Join Discord</button>
        </div>
        <div class="card">
          <h3>Step 2 · Submit application</h3>
          <p>
            Tell us who you are, what you enjoy in RP, and the kind of character you want to bring
            into the city.
          </p>
          <button class="btn btn-outline">View Application Form</button>
        </div>
        <div class="card">
          <h3>Step 3 · Get onboarded</h3>
          <p>
            If accepted, you’ll receive onboarding info, rule confirmations, and starter resources
            to help you hit the ground running.
          </p>
          <div class="pill-row">
            <span class="pill">Onboarding guide</span>
            <span class="pill">Role setup</span>
            <span class="pill">First steps in city</span>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA strip -->
    <div class="cta-strip">
      <div>
        <strong>Elision Report · Public staff log</strong>
        <p>
          Want a community where staff decisions aren’t hidden? Bookmark the Elision Report page and
          stay up to date on bans, warnings, and appeals.
        </p>
      </div>
      <div>
        <button class="btn btn-outline">View Elision Report</button>
      </div>
    </div>
  </main>

  <footer>
    © <span id="year"></span> Elision Role Play · Los Santos RP community
  </footer>

  <script>
    document.getElementById("year").textContent = new Date().getFullYear();
  </script>
</body>
</html>

