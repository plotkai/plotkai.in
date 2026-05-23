---
title: "Our Methodology"
url: "/our-methodology/"
badge: "Company Info"
description: "Learn how Plotkai Interactive builds premium products with zero technical debt."
excerpt: "High level overview of the plotkai methodology"
---

<style>
  /* Override global reveal animations on this page for instant loading */
  .reveal {
    opacity: 1 !important;

  }

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
    background: linear-gradient(to bottom, #3b82f6 0%, #00e5a0 16%, #f59e0b 33%, var(--coral) 50%, #8b5cf6 66%, #f43f5e 83%, #00c853 100%);
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

  /* Phase 01: Blue Glow */
  .item-blue .timeline-node {
    border-color: #3b82f6;
    box-shadow: 0 0 15px rgba(59, 130, 246, 0.15);
    color: #3b82f6;
  }
  .item-blue .timeline-card::before {
    background: linear-gradient(90deg, #3b82f6, transparent);
  }
  .item-blue:hover .timeline-card {
    border-color: rgba(59, 130, 246, 0.35);
    box-shadow: 0 12px 40px rgba(59, 130, 246, 0.08);
    transform: translateX(6px);
  }
  .item-blue:hover .timeline-node {
    box-shadow: 0 0 25px rgba(59, 130, 246, 0.5);
    background: #3b82f6;
    color: var(--dark-surface);
  }

  /* Phase 02: Teal Glow */
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

  /* Phase 03: Amber Glow */
  .item-amber .timeline-node {
    border-color: #f59e0b;
    box-shadow: 0 0 15px rgba(245, 158, 11, 0.15);
    color: #f59e0b;
  }
  .item-amber .timeline-card::before {
    background: linear-gradient(90deg, #f59e0b, transparent);
  }
  .item-amber:hover .timeline-card {
    border-color: rgba(245, 158, 11, 0.35);
    box-shadow: 0 12px 40px rgba(245, 158, 11, 0.08);
    transform: translateX(6px);
  }
  .item-amber:hover .timeline-node {
    box-shadow: 0 0 25px rgba(245, 158, 11, 0.5);
    background: #f59e0b;
    color: var(--dark-surface);
  }

  /* Phase 04: Coral Glow */
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

  /* Phase 05: Purple Glow */
  .item-purple .timeline-node {
    border-color: #8b5cf6;
    box-shadow: 0 0 15px rgba(139, 92, 246, 0.15);
    color: #8b5cf6;
  }
  .item-purple .timeline-card::before {
    background: linear-gradient(90deg, #8b5cf6, transparent);
  }
  .item-purple:hover .timeline-card {
    border-color: rgba(139, 92, 246, 0.35);
    box-shadow: 0 12px 40px rgba(139, 92, 246, 0.08);
    transform: translateX(6px);
  }
  .item-purple:hover .timeline-node {
    box-shadow: 0 0 25px rgba(139, 92, 246, 0.5);
    background: #8b5cf6;
    color: var(--dark-surface);
  }

  /* Phase 06: Rose Glow */
  .item-rose .timeline-node {
    border-color: #f43f5e;
    box-shadow: 0 0 15px rgba(244, 63, 94, 0.15);
    color: #f43f5e;
  }
  .item-rose .timeline-card::before {
    background: linear-gradient(90deg, #f43f5e, transparent);
  }
  .item-rose:hover .timeline-card {
    border-color: rgba(244, 63, 94, 0.35);
    box-shadow: 0 12px 40px rgba(244, 63, 94, 0.08);
    transform: translateX(6px);
  }
  .item-rose:hover .timeline-node {
    box-shadow: 0 0 25px rgba(244, 63, 94, 0.5);
    background: #f43f5e;
    color: var(--dark-surface);
  }

  /* Phase 07: Emerald Glow */
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
  .item-blue .timeline-grid-item svg { color: #3b82f6; }
  .item-teal .timeline-grid-item svg { color: #00e5a0; }
  .item-amber .timeline-grid-item svg { color: #f59e0b; }
  .item-coral .timeline-grid-item svg { color: var(--coral); }
  .item-purple .timeline-grid-item svg { color: #8b5cf6; }
  .item-rose .timeline-grid-item svg { color: #f43f5e; }
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
  <div class="timeline-item item-blue">
    <div class="timeline-node">01</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 01 / Legal &amp; Client Onboarding</span>
      <h3>Secure Onboarding &amp; NDA</h3>
      <p>
        We build a foundation of absolute trust and security from day zero. Before exploring your concepts, we sign comprehensive Mutual Non-Disclosure Agreements (NDAs) and establish transparent Intellectual Property (IP) ownership frameworks so your ideas remain 100% yours.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect><path d="M7 11V7a5 5 0 0 1 10 0v4"></path></svg>
          Mutual NDA Execution
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="8" r="7"></circle><polyline points="8.21 13.89 7 23 12 20 17 23 15.79 13.88"></polyline></svg>
          Full IP Protection &amp; Transfer
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path></svg>
          Secure Client Portal Setup
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 11 12 14 22 4"></polyline><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"></path></svg>
          Legal &amp; Compliance Sign-off
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 02 -->
  <div class="timeline-item item-teal reveal">
    <div class="timeline-node">02</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 02 / Strategic Research &amp; Blueprint</span>
      <h3>Discovery &amp; Market Research</h3>
      <p>
        Every exceptional product is built on deep understanding. We perform exhaustive primary and secondary market research, define user demographics, map out competitor benchmarks, and execute early-stage Proof-of-Concepts (POCs) to mitigate technical risks.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
          Competitor Benchmark Tracking
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path><circle cx="9" cy="7" r="4"></circle><path d="M23 21v-2a4 4 0 0 0-3-3.87"></path><path d="M16 3.13a4 4 0 0 1 0 7.75"></path></svg>
          User Persona Profiling
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 2 7 12 12 22 7 12 2"></polygon><polyline points="2 17 12 22 22 17"></polyline><polyline points="2 12 12 17 22 12"></polyline></svg>
          Technical Feasibility POCs
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline><polyline points="17 6 23 6 23 12"></polyline></svg>
          Strategic Product Mapping
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 03 -->
  <div class="timeline-item item-amber reveal">
    <div class="timeline-node">03</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 03 / Commercial &amp; Growth Blueprint</span>
      <h3>Product Strategy &amp; GTM</h3>
      <p>
        Building the right features means aligning them with your commercial strategy. We synchronize product design with your Go-To-Market (GTM) strategy, model pricing models, plan sales &amp; marketing distribution funnels, and prioritize the backlog for growth.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="3 6 9 3 15 6 21 3 21 18 15 21 9 18 3 21"></polygon><line x1="9" y1="3" x2="9" y2="18"></line><line x1="15" y1="6" x2="15" y2="21"></line></svg>
          Go-To-Market (GTM) Strategy
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M11 5L6 9H2v6h4l5 4V5z"></path><path d="M19.07 4.93a10 10 0 0 1 0 14.14M15.54 8.46a5 5 0 0 1 0 7.07"></path></svg>
          Sales &amp; Marketing Alignment
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path></svg>
          Core Value Proposition Design
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="8" y1="6" x2="21" y2="6"></line><line x1="8" y1="12" x2="21" y2="12"></line><line x1="8" y1="18" x2="21" y2="18"></line><line x1="3" y1="6" x2="3.01" y2="6"></line><line x1="3" y1="12" x2="3.01" y2="12"></line><line x1="3" y1="18" x2="3.01" y2="18"></line></svg>
          Strategic Backlog Prioritization
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 04 -->
  <div class="timeline-item item-coral reveal">
    <div class="timeline-node">04</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 04 / Experience Design &amp; Validation</span>
      <h3>Prototype &amp; UX Validation</h3>
      <p>
        We build fast, high-fidelity prototypes to put design paradigms and ideas to the test. By ranking feature usability through hands-on clickable flows, testing onboarding micro-interactions, and designing advanced AI/LLM integration blueprints, we validate the solution.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect><line x1="3" y1="9" x2="21" y2="9"></line><line x1="9" y1="21" x2="9" y2="9"></line></svg>
          High-Fidelity UX Prototypes
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3l7.07 16.97 2.51-7.39 7.39-2.51L3 3z"></path><path d="M13 13l6 6"></path></svg>
          Interactive Clickable Journeys
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="4" y="4" width="16" height="16" rx="2" ry="2"></rect><rect x="9" y="9" width="6" height="6"></rect><line x1="9" y1="1" x2="9" y2="4"></line><line x1="15" y1="1" x2="15" y2="4"></line><line x1="9" y1="20" x2="9" y2="23"></line><line x1="15" y1="20" x2="15" y2="23"></line><line x1="20" y1="9" x2="23" y2="9"></line><line x1="20" y1="15" x2="23" y2="15"></line><line x1="1" y1="9" x2="4" y2="9"></line><line x1="1" y1="15" x2="4" y2="15"></line></svg>
          Artificial Intelligence Blueprint
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21.5 2v6h-6M21.34 15.57a10 10 0 1 1-.57-8.38l5.67-5.67"/></svg>
          Rapid User Validation Loops
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 05 -->
  <div class="timeline-item item-purple reveal">
    <div class="timeline-node">05</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 05 / Engineering Excellence</span>
      <h3>Agile Development &amp; Clean Code</h3>
      <p>
        Engineering excellence is our signature. We adhere to rigorous 2-week Agile sprint ceremonies, including sprint planning, daily standups, and retrospective loops. We write clean, modular code following strict architecture guidelines to ensure zero technical debt.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect><line x1="16" y1="2" x2="16" y2="6"></line><line x1="8" y1="2" x2="8" y2="6"></line><line x1="3" y1="10" x2="21" y2="10"></line></svg>
          2-Week Sprints &amp; Ceremonies
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"></polyline><polyline points="8 6 2 12 8 18"></polyline></svg>
          Zero Tech Debt Clean Code
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="18" cy="18" r="3"></circle><circle cx="6" cy="6" r="3"></circle><circle cx="6" cy="18" r="3"></circle><path d="M18 15V9a4 4 0 0 0-4-4H9"></path><line x1="6" y1="9" x2="6" y2="15"></line></svg>
          Automated CI/CD Pipelines
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>
          Precision Engineering QA
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 06 -->
  <div class="timeline-item item-rose reveal">
    <div class="timeline-node">06</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 06 / Trust, Protection &amp; Governance</span>
      <h3>Security &amp; Data Governance</h3>
      <p>
        Security is a core design criterion, not an afterthought. We implement multi-layered encryption protocols for data at rest and in transit, establish strict data governance pipelines, execute regular vulnerability threat modeling, and design for SOC 2, HIPAA, and GDPR compliance.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path></svg>
          SOC 2 &amp; GDPR Ready Standards
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 2l-2 2m-7.61 7.61a5.5 5.5 0 1 1-7.778 7.778 5.5 5.5 0 0 1 7.777-7.777zm0 0L15.5 7.5m0 0l3 3L22 7l-3-3m-3.5 3.5L19 4"></path></svg>
          End-to-End Advanced Encryption
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"></path><line x1="12" y1="9" x2="12" y2="13"></line><line x1="12" y1="17" x2="12.01" y2="17"></line></svg>
          Threat Modeling &amp; Pen Testing
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><ellipse cx="12" cy="5" rx="9" ry="3"></ellipse><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"></path><path d="M3 12c0 1.66 4 3 9 3s9-1.34 9-3"></path></svg>
          Role-Based Access Control (RBAC)
        </div>
      </div>
    </div>
  </div>

  <!-- PHASE 07 -->
  <div class="timeline-item item-emerald reveal">
    <div class="timeline-node">07</div>
    <div class="timeline-card">
      <span class="timeline-badge">Phase 07 / Commercial Launch &amp; Scale</span>
      <h3>Launch &amp; Scaled DevOps</h3>
      <p>
        We launch a highly-polished, market-ready MVP in weeks. We configure high-availability, multi-region autoscaling cloud operations (AWS/GCP), implement real-time analytics and metric collection dashboards, and provide hands-on post-launch support as your platform grows.
      </p>
      <div class="timeline-grid">
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"></line><polygon points="22 2 15 22 11 13 2 9 22 2"></polygon></svg>
          Market-Ready MVP in Weeks
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"></path></svg>
          Autoscaling Cloud DevOps
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="20" x2="18" y2="10"></line><line x1="12" y1="20" x2="12" y2="4"></line><line x1="6" y1="20" x2="6" y2="14"></line></svg>
          Real-Time Analytics &amp; Sentry
        </div>
        <div class="timeline-grid-item">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"></polyline></svg>
          24/7 Hypercare &amp; Scale Support
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