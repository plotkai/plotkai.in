---
title: "Vitaran SMTP Orchestrator"
date: 2026-05-27
draft: false
category: "Product Launch"
tags: ["Vitaran","SMTP","Orchestrator"]
excerpt: "Vitaran is an operational communication gateway for email infrastructure, providing unified API, provider load balancing, template management, and inbound email broker."
featured: false
featuredImage: "/img/our-work/vitaran.png"
featuredImageCaption: "Vitaran Dashboard"
readTime: "2 min read"
---

## Overview

Vitaran is an **operational communication gateway** that acts as the central control plane for your entire application ecosystem's email infrastructure. By serving as a programmable middleware layer between your application logic and multiple third-party email providers (such as SMTP2GO or Brevo, etc), Vitaran eliminates infrastructure fragmentation. It empowers developers to seamlessly manage global user consent, maintain brand-consistent HTML templates, and dispatch cross-channel messages through a single, unified API.

Vitaran goes beyond merely sending emails; it handles bidirectional traffic. By linking outgoing transactional emails with incoming replies via an integrated Cloudflare-powered broker, Vitaran provides granular observability and compliance-as-code. This allows you to easily manage communication reputation and infrastructure across multiple disparate projects without the complexity of configuring distinct setups for each one.

## Core Features

- **Unified API Gateway**: Send emails through a single, standardized REST API regardless of the underlying SMTP provider.
- **Provider Load Balancing**: Configure multiple SMTP providers with daily usage limits and dynamic weighting to ensure reliable delivery.
- **Template Management**: Store and manage brand-consistent HTML templates with full Go template variable support.
- **Identity & Compliance Control**: Manage sender identities, configure 1x1 tracking pixels, enforce SMTP tracing, and handle global unsubscribes with automatic footer injection.
- **Bidirectional Email Broker**: Ingest inbound emails via Cloudflare Workers to capture replies directly within the dashboard.
- **Modern Dashboard**: A fully responsive, dark/light mode UI to visualize usage statistics, inspect mail queues, manage providers, and preview templates.

## Inbound Emails (Cloudflare Worker Setup)

To capture incoming emails and route them back to Vitaran, you can deploy a Cloudflare Worker using the Cloudflare Email Routing feature.

```javascript
export default {
  async email(message, env, ctx) {
    // 1. Get the full raw email content
    const rawEmail = await new Response(message.raw).text();

    // 2. Prepare the payload exactly as the API expects
    const payload = {
      from: message.from,
      to: message.to,
      subject: message.headers.get("subject") || "(No Subject)",
      body: rawEmail // This is the entire raw email stream
    };

    // 3. Send to the Vitaran Backend
    const response = await fetch("https://vitaran.your-company.com/api/v1/receive", {
      method: "POST",
      headers: {
        "X-API-Key": env.API_KEY, // Set this in Worker Settings > Variables
        "Content-Type": "application/json"
      },
      body: JSON.stringify(payload)
    });
  }
};
```

## Sending Emails (API)

To send an email through Vitaran from your applications, you must use the `POST /api/v1/send` endpoint.

### Obtaining your API Key

1. Log in to the Vitaran Dashboard.
2. Navigate to the **API Key** section in the sidebar.
3. If you haven't saved your key, click **Regenerate Key** (Note: this immediately invalidates your old key).
4. Copy the generated key.

### API Usage Example

Include the copied key in the `X-API-Key` header of your requests.

```bash
curl -X POST https://vitaran.your-company.com/api/v1/send \
  -H "X-API-Key: vt_your_key_here" \
  -H "Content-Type: application/json" \
  -d '{
    "from": "<identity_id_from_dashboard>",
    "to": "recipient@example.com",
    "template_slug": "welcome",
    "vars": {
      "name": "Alice",
      "company": "Acme Corp"
    }
  }'
```

**Payload Fields:**
* `from`: The ID of the Identity you configured in the dashboard.
* `to`: The email address of the recipient.
* `template_slug`: The slug of the HTML template you wish to use.
* `vars`: A JSON object of variables that will be injected into the Go template during rendering.


<!-- ==================== PREMIUM GLASSMORPHISM CTA BLOCK ==================== -->
<div class="reveal reveal-delay-4 my-10 p-8 rounded-2xl border border-brand-coral/20 bg-gradient-to-br from-brand-dark/95 via-brand-dark to-brand-coral/5 text-center relative overflow-hidden group">
  <div class="absolute -right-20 -bottom-20 w-60 h-60 rounded-full bg-brand-coral/5 blur-3xl pointer-events-none"></div>
  <div class="absolute -left-20 -top-20 w-60 h-60 rounded-full bg-brand-teal/5 blur-3xl pointer-events-none"></div>
  
  <div class="relative z-10 max-w-xl mx-auto">
    <div class="badge mb-4">Build for Scale</div>
    <h3 class="text-2xl font-extrabold text-white mb-2 leading-snug">Let's Engineer Your Scalable Mailer</h3>
    <p class="text-sm text-white/70 leading-relaxed mb-6">
      Is your engineering team struggling to design a fault-tolerant mailer infrastructure, optimize SMTP workflows, handle sudden traffic load spikes, or maintain compliance across projects? Let our system design and cloud architects perform a comprehensive <strong>Free Email Infrastructure Audit</strong>.
    </p>   
    <div style="display:flex;gap:16px;justify-content:center;flex-wrap:wrap;">
      <a href="/contact/" class="btn-outline" id="product-cta-secondary">
        Schedule a Free Demo & Pricing
      </a>
    </div>
  </div>
</div>