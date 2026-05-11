---
title: "Yognishtha Trust: A Zero-Cost, Seamless Deployment Journey"
date: 2025-10-27
lastmod: 2025-10-27
category: "Client Projects"
tags: ["Web Development", "GCP", "Automation", "Deployment Pipeline"]
excerpt: "How Plotkai Interactive delivered a zero-cost, fully automated website for Yognishtha Trust — with a seamless build and deployment pipeline that required just one iteration."
featured: true
featuredImage: "https://yognishtha.in/images/yognishtha_50.jpeg"
featuredImageCaption: "A minimal, performance-optimized website built for Yognishtha Trust"
readTime: "4 min read"
---

At Plotkai Interactive, we take pride in building scalable and cost-efficient digital foundations for organizations doing meaningful work. One such collaboration was with Yognishtha Trust — a non-profit initiative focused on holistic wellbeing and community upliftment. Their goal was simple: to have a clean, fast, and sustainable website that communicated their mission effectively without recurring infrastructure costs.

## Building for Simplicity and Impact

Instead of over-engineering the stack, we focused on efficiency. The site was designed with a minimal front-end, static content generation, and a fully automated CI/CD pipeline. Everything runs on Google Cloud’s free-tier infrastructure — meaning Yognishtha Trust pays **zero ongoing cost** for hosting or maintenance.

## A Seamless Deployment Pipeline

The deployment process was fully automated using GitHub Actions connected to Google Cloud Run. Every commit to the main branch triggers a build, runs validations, and deploys instantly. No manual intervention. No downtime. This ensures the team can make updates anytime with confidence — the infrastructure takes care of itself.

* Fully automated build and deploy workflow
* Hosted on Google Cloud Run free tier
* Optimized for speed and low compute footprint
* Single-iteration delivery — ready from concept to launch in one cycle

## Negligible Cost, Maximum Value

The project was designed intentionally to minimize cost for the client. By leveraging Google Cloud’s always-free limits and an efficient deployment architecture, the ongoing cost remains **negligible to none**. Yognishtha Trust now has a sustainable digital presence that doesn’t depend on paid infrastructure or manual upkeep.

> “Our goal was to create a digital home for Yognishtha Trust that is as peaceful and enduring as the values it represents — lightweight, reliable, and cost-free.”
> <cite>— Plotkai Team</cite>

## From Commit to Production — Instantly

```yaml
# GitHub Actions Workflow for Cloud Run Deployment
name: Deploy to Cloud Run
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Set up gcloud
        uses: google-github-actions/setup-gcloud@v2
        with:
          project_id: ${{ secrets.GCP_PROJECT_ID }}
          service_account_key: ${{ secrets.GCP_SA_KEY }}
      - name: Deploy
        run: gcloud run deploy yognishtha --source . --region=asia-south2 --platform=managed
```

This pipeline ensures zero-touch deployment. The website is automatically rebuilt and redeployed whenever content or code changes — delivering a smooth experience both for the maintainers and the end users.

## One Iteration, One Vision

The project required only a single iteration to reach production — a testament to clear communication, focused design, and automation-driven engineering. For Yognishtha Trust, this meant instant launch with long-term reliability, all at no recurring cost.

At Plotkai Interactive, we believe every digital product — even a simple website — should be sustainable, fast, and effortless to maintain. The Yognishtha Trust project is a small but powerful example of how smart engineering choices can make technology affordable for everyone.
