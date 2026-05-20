---
title: "How We Work"
url: "/how-we-work/"
badge: "Company Info"
description: "Learn how Plotkai Interactive builds premium products with zero technical debt."
---

<style>
  .timeline-container {
    position: relative;
    padding: 32px 0;
    margin-top: 24px;
  }
  
  .timeline-line {
    position: absolute;
    left: 24px;
    top: 0;
    bottom: 0;
    width: 2px;
    background: linear-gradient(to bottom, #00e5a0 0%, var(--teal) 33%, var(--coral) 66%, #00c853 100%);
    opacity: 0.25;
  }

  .timeline-item {
    position: relative;
    display: flex;
    gap: 32px;
    margin-bottom: 56px;
  }

  .timeline-item:last-child {
    margin-bottom: 0;
  }

  .timeline-node {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background: var(--dark-surface);
    border: 2px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 800;
    font-size: 18px;
    color: white;
    z-index: 2;
    flex-shrink: 0;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    box-shadow: 0 0 15px rgba(0, 0, 0, 0.5);
  }

  .timeline-card {
    flex-grow: 1;
    background: var(--dark-card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 32px;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    position: relative;
    overflow: hidden;
    backdrop-filter: blur(12px);
  }

  .timeline-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    background: transparent;
    transition: background 0.3s ease;
  }

  /* Phase 01: Teal Glow */
  .item-teal .timeline-node {
    border-color: #00e5a0;
    box-shadow: 0 0 15px rgba(0, 229, 160, 0.15);
    color: #00e5a0;
  }
  .item-teal .timeline-card::before {
    background: linear-gradient(90deg, #00e5a0, transparent);
  }
  .item-teal:hover .timeline-card {
    border-color: rgba(0, 229, 160, 0.35);
    box-shadow: 0 12px 40px rgba(0, 229, 160, 0.08);
    transform: translateX(6px);
  }
  .item-teal:hover .timeline-node {
    box-shadow: 0 0 25px rgba(0, 229, 160, 0.5);
    background: #00e5a0;
    color: var(--dark-surface);
  }

  /* Phase 02: Gold Glow */
  .item-gold .timeline-node {
    border-color: var(--teal);
    box-shadow: 0 0 15px rgba(218, 165, 32, 0.15);
    color: var(--teal);
  }
  .item-gold .timeline-card::before {
    background: linear-gradient(90deg, var(--teal), transparent);
  }
  .item-gold:hover .timeline-card {
    border-color: rgba(218, 165, 32, 0.35);
    box-shadow: 0 12px 40px rgba(218, 165, 32, 0.08);
    transform: translateX(6px);
  }
  .item-gold:hover .timeline-node {
    box-shadow: 0 0 25px rgba(218, 165, 32, 0.5);
    background: var(--teal);
    color: var(--dark-surface);
  }

  /* Phase 03: Coral Glow */
  .item-coral .timeline-node {
    border-color: var(--coral);
    box-shadow: 0 0 15px rgba(255, 127, 80, 0.15);
    color: var(--coral);
  }
  .item-coral .timeline-card::before {
    background: linear-gradient(90deg, var(--coral), transparent);
  }
  .item-coral:hover .timeline-card {
    border-color: rgba(255, 127, 80, 0.35);
    box-shadow: 0 12px 40px rgba(255, 127, 80, 0.08);
    transform: translateX(6px);
  }
  .item-coral:hover .timeline-node {
    box-shadow: 0 0 25px rgba(255, 127, 80, 0.5);
    background: var(--coral);
    color: var(--dark-surface);
  }

  /* Phase 04: Emerald Glow */
  .item-emerald .timeline-node {
    border-color: #00c853;
    box-shadow: 0 0 15px rgba(0, 200, 83, 0.15);
    color: #00c853;
  }
  .item-emerald .timeline-card::before {
    background: linear-gradient(90deg, #00c853, transparent);
  }
  .item-emerald:hover .timeline-card {
    border-color: rgba(0, 200, 83, 0.35);
    box-shadow: 0 12px 40px rgba(0, 200, 83, 0.08);
    transform: translateX(6px);
  }
  .item-emerald:hover .timeline-node {
    box-shadow: 0 0 25px rgba(0, 200, 83, 0.5);
    background: #00c853;
    color: var(--dark-surface);
  }

  .timeline-badge {
    display: inline-block;
    padding: 5px 12px;
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 50px;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(255, 255, 255, 0.55);
    margin-bottom: 14px;
  }

  .timeline-card h3 {
    font-size: 24px;
    font-weight: 800;
    color: white;
    margin: 0 0 12px 0 !important;
    font-family: 'Space Grotesk', sans-serif;
  }

  .timeline-card p {
    font-size: 16px !important;
    line-height: 1.7 !important;
    color: rgba(255, 255, 255, 0.65) !important;
    margin-bottom: 24px !important;
  }

  .timeline-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
    gap: 14px;
    margin-top: 20px;
  }

  .timeline-grid-item {
    background: rgba(255, 255, 255, 0.02);
    border: 1px solid rgba(255, 255, 255, 0.05);
    border-radius: 10px;
    padding: 14px 18px;
    font-size: 14.5px;
    color: rgba(255, 255, 255, 0.85);
    display: flex;
    align-items: center;
    gap: 12px;
    transition: all 0.2s ease;
  }

  .timeline-grid-item:hover {
    background: rgba(255, 255, 255, 0.05);
    border-color: rgba(255, 255, 255, 0.1);
  }

  .timeline-grid-item svg {
    flex-shrink: 0;
    transition: transform 0.2s ease;
  }

  .timeline-grid-item:hover svg {
    transform: scale(1.15);
  }

  /* Specific color SVG icons in grid items */
  .item-teal .timeline-grid-item svg { color: #00e5a0; }
  .item-gold .timeline-grid-item svg { color: var(--teal); }
  .item-coral .timeline-grid-item svg { color: var(--coral); }
  .item-emerald .timeline-grid-item svg { color: #00c853; }

  @media (max-width: 680px) {
    .timeline-line {
      left: 18px;
    }
    .timeline-item {
      gap: 20px;
    }
    .timeline-node {
      width: 38px;
      height: 38px;
      font-size: 15px;
    }
    .timeline-card {
      padding: 24px;
    }
    .timeline-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="timeline-container">
  <div class="timeline-line"></div>

  <!-- PHASE 01 -->
  <div class="timeline-item item-teal reveal">
    <div class="timeline-node">01</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 01 / Research &amp; Blueprint</span>
      <h3>Discovery &amp; Strategy</h3>
      <p>
        Every great project starts with understanding. We deep-dive into your product vision, target market, and strategic goals to design a neat, purpose-driven blueprint before writing a single line of code.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
          Proper Research &amp; Insights
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 2 7 12 12 22 7 12 2"></polygon><polyline points="2 17 12 22 22 17"></polyline><polyline points="2 12 12 17 22 12"></polyline></svg>
          Technical Feasibility (POC)
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path><circle cx="9" cy="7" r="4"></circle><path d="M23 21v-2a4 4 0 0 0-3-3.87"></path><path d="M16 3.13a4 4 0 0 1 0 7.75"></path></svg>
          User-Centric Goal Definition
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="20" x2="18" y2="10"></line><line x1="12" y1="20" x2="12" y2="4"></line><line x1="6" y1="20" x2="6" y2="14"></line></svg>
          Strategic Product Mapping
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 02 -->
  <div class="timeline-item item-gold reveal">
    <div class="timeline-node">02</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 02 / Concept &amp; Validation</span>
      <h3>Prototype &amp; Validate</h3>
      <p>
        We build fast, high-fidelity prototypes and proof of concepts to put your ideas to the test. By ranking features based on user experience (UX), Artificial Intelligence Integration, and technical feasibility, we validate the path forward with clarity.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z"></path><path d="M8 14C9.5 16 14.5 16 16 14"></path><line x1="9" y1="9" x2="9.01" y2="9"></line><line x1="15" y1="9" x2="15.01" y2="9"></line></svg>
          Ranked Features (UX vs POC)
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"></path></svg>
          Functional Proof of Concept
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="4" y="4" width="16" height="16" rx="2" ry="2"></rect><rect x="9" y="9" width="6" height="6"></rect><line x1="9" y1="1" x2="9" y2="4"></line><line x1="15" y1="1" x2="15" y2="4"></line><line x1="9" y1="20" x2="9" y2="23"></line><line x1="15" y1="20" x2="15" y2="23"></line><line x1="20" y1="9" x2="23" y2="9"></line><line x1="20" y1="15" x2="23" y2="15"></line><line x1="1" y1="9" x2="4" y2="9"></line><line x1="1" y1="15" x2="4" y2="15"></line></svg>
          Artificial Intelligence Integration
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21.5 2v6h-6M21.34 15.57a10 10 0 1 1-.57-8.38l5.67-5.67"/></svg>
          Rapid User Validation Loops
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 03 -->
  <div class="timeline-item item-coral reveal">
    <div class="timeline-node">03</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 03 / Agile Development</span>
      <h3>Build with Precision</h3>
      <p>
        Engineering excellence is our signature. We follow rigorous 2-week agile sprint ceremonies to ensure seamless execution. By adhering to clean modular architecture, we guarantee robust, zero-technical-debt products.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="23 4 23 10 17 10"></polyline><path d="M20.49 15a9 9 0 1 1-2.12-9.36L23 10"></path></svg>
          Agile Sprint Ceremonies
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M4 15s1-1 4-1 5 2 8 2 4-1 4-1V3s-1 1-4 1-5-2-8-2-4 1-4 1z"></path><line x1="4" y1="22" x2="4" y2="15"></line></svg>
          Feature-Based Milestones
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 2 7 12 12 22 7 12 2"></polygon><polyline points="2 17 12 22 22 17"></polyline><polyline points="2 12 12 17 22 12"></polyline></svg>
          Zero Tech Debt Clean Code
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>
          Precision Engineering Standards
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 04 -->
  <div class="timeline-item item-emerald reveal">
    <div class="timeline-node">04</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 04 / Launch &amp; Scale</span>
      <h3>Launch &amp; Grow Together</h3>
      <p>
        We launch a highly-polished, market-ready MVP in weeks, not months. We believe in purpose-driven results, keeping systems user-centric and simple while scaling cloud infrastructure hand-in-hand with your startup.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 2L11 13M22 2l-7 20-4-9-9-4 20-7z"/></svg>
          Market-Ready MVP in Weeks
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 7 13.5 15.5 8.5 10.5 2 17"></polyline><polyline points="16 7 22 7 22 13"></polyline></svg>
          Purpose-Driven Growth
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2a10 10 0 0 1 10 10c0 5.523-4.477 10-10 10S2 17.523 2 12 6.477 2 12 2z"/><path d="M12 6v6l4 2"/></svg>
          Simple &amp; User-Centric Focus
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"/></svg>
          High-Scale Cloud Operations
        </div>
      </div>
    </div>
  </div>
</div>
<div style="display:flex;gap:16px;justify-content:center;flex-wrap:wrap;margin-top:56px;margin-bottom:32px;">
  <a href="/contact/" class="btn-outline" id="about-schedule-consultation">
    Schedule a Free Consultation
  </a>
</div>