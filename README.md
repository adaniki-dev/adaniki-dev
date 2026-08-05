<div align="center">

# Adam Iki Yoshikai

**Software Engineer** · Full-stack · Platform & cloud-native infrastructure

Building and operating SaaS platforms end-to-end, from the interface down to the cluster it runs on.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/adaniki)
[![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:ikiyoshikai@gmail.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/5535988376411)

</div>

---

## About Me

Software Engineer from Minas Gerais, Brazil, with over 7 years of experience building SaaS products and web platforms. I work the full path: React and Next.js on the front, NestJS and Node/Bun APIs on the back, Kubernetes with ArgoCD carrying it to production. What I care about most is the space *between* those layers, where the contracts live, where the failure modes hide, and where a decision made six months ago starts charging interest.

Most of my recent work is on a multi-tenant SaaS platform I build and operate: container orchestration across multiple Kubernetes clusters, identity and SSO, a payment layer spanning several gateways, and a server-side tracking pipeline. Owning it end-to-end means there's no other team to hand a problem to. I debug the FreeMarker login template, the Prisma query, and the autoscaler's behavior in the same afternoon, and I've learned to like that.

My deepest specialization is an unusual one: **server-side tracking infrastructure**. Server-side GTM on Cloud Run, custom tag templates, first-party serving through custom domains and loaders, cookie durability under browser privacy restrictions, Consent Mode, and conversion ingestion into Google and Meta. It's a domain where the browser is actively working against you, the vendor docs go stale every quarter, and nothing works until you measure it in production.

I also spend real time on **LLM tooling**: MCP servers, multi-agent orchestration with scoped permissions, and retrieval-backed memory systems. It's the area I'm betting on next, alongside going deeper on cloud architecture (AWS/GCP).

I work best in small, direct teams where people own their work. Always up for a good technical conversation.

---

## What I've Built

### Multi-cluster container platform

Container lifecycle orchestration across multiple Kubernetes clusters: provisioning, suspend/resume, scaling, and continuous reconciliation of desired versus actual workload state. I built the convergence engine, the placement logic that maps tenants onto cluster cells, and plan-driven autoscaling. Delivery is GitOps with ArgoCD, observability is cross-cluster via Thanos, edge and DNS through Cloudflare.

Most of the hard work here wasn't the happy path. It was the operational reality: eviction and OOMKill under memory pressure, a message broker's state after an unclean restart, and the difference between "the port is open" and "the service actually works."

### Server-side tracking infrastructure

A server-side GTM platform offered as a product. Custom sGTM tag templates authored against the sandboxed template API (`getGoogleAuth`, `sendHttpRequest`, scoped permissions), running on Cloud Run with workload identity instead of service-account key files. I migrated the Google side off the Measurement Protocol, which entered maintenance mode at the end of 2025, onto the **Google Data Manager API**, and I handle the Meta side through the Conversions API.

The layer below that is anti-adblock serving: custom tracking domains, custom loaders, cookie durability against ITP and similar browser restrictions, and Consent Mode v2. Plus offline conversion ingestion into Google Ads, and a Shopify embedded app (Remix + Prisma) that installs a clean data layer on a merchant's storefront.

### Tracking maturity scanner

A product that audits a website's tracking stack and explains what's missing. The core is a deterministic detection engine over a live scan, mapped onto a linear **capability ladder** (client-side GTM → server-side → custom domain → custom loader → cookie keeper → enhanced protection → Consent Mode v2), each rung carrying the mechanism, the invisible cost of not having it, and what it unlocks.

The design constraint was the interesting part: the report has three audiences (the client, the sales team, and the consultant), and none of them is a developer. That meant killing the dev dialect in the output and writing the detection results as an explanation instead of a score.

### Multi-gateway billing

A payment layer abstracting several providers (Stripe, Iugu, Pagar.me, WHMCS) behind a single contract: subscriptions, invoices, coupons and affiliate attribution, currency routing with locking rules, SCA/3DS, and card handling with an explicit PCI boundary. Built the gateway resolver and the provider adapters in TDD, and also a payment module on the WHMCS side.

One lesson from this one stuck: a fake anchored to your own adapter gives you a **false green**. The fake's shape has to come from production code or the gateway's docs, never from whatever makes the test pass.

### Identity & authentication

Keycloak in production: custom login and account themes (FreeMarker, multi-realm, i18n), OIDC integration, social login, and JIT provisioning that wires the identity provider to the application's user model. Migrated an application's auth from a separate BFF service into the platform itself, and moved a client from ROPC onto the Authorization Code flow.

### Contract-driven admin platform

An internal admin panel on Next.js 16 (App Router, RSC, Turbopack) with React 19, TypeScript strict, Tailwind v4, Zod, Zustand, and TanStack Query, organized in **Feature-Sliced Design** (app → widgets → features → entities → shared). Feature boundaries are declared as YAML contracts and checked by a dedicated linter, so a feature's public surface is a reviewable artifact rather than whatever happened to get exported.

### AI tooling & agents

An always-on assistant runtime in Bun. MCP servers exposing tools to LLM clients, multi-agent workflows where each role's toolset is scoped at the boundary (the planner and the reviewer physically cannot write files, so role separation is enforced rather than requested), and a **spec-anchored gate**: every acceptance criterion has to map to a named test that actually ran green, because a passing suite proves the suite passed, not that the requirement was met.

Underneath: a markdown-native memory layer with a typed relationship graph and retrieval-backed recall, and a real-time voice pipeline (STT, TTS, voice conversion, and DF3 denoising) running through ONNX Runtime with DirectML, because the GPU in that machine is AMD and CUDA was never an option.

---

## How I Work

**Measured, not assumed.** If a claim isn't verified, I label it a guess out loud. The recurring problem is never not knowing something; it's not knowing that you don't know it.

**Simplicity over cleverness.** I'd rather cut a feature than ship an abstraction nobody can change later. I'll flag overengineering and YAGNI in a review, including in my own code.

**Architecture before the first line.** I think a design through, write down the decision *and its reason*, and revisit it when reality disagrees.

**Direct feedback.** I'd rather be told I'm wrong early than be agreed with politely. I give the same in return, with the reasoning attached.

---

## Tech Stack

### Languages

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

### Frontend

![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![Remix](https://img.shields.io/badge/Remix-000000?style=for-the-badge&logo=remix&logoColor=white)
![Svelte](https://img.shields.io/badge/Svelte-FF3E00?style=for-the-badge&logo=svelte&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router_v7-CA4245?style=for-the-badge&logo=react-router&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![TanStack Query](https://img.shields.io/badge/TanStack_Query-FF4154?style=for-the-badge&logo=reactquery&logoColor=white)
![Zod](https://img.shields.io/badge/Zod-3E67B1?style=for-the-badge&logo=zod&logoColor=white)

### Backend

![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Bun](https://img.shields.io/badge/Bun-000000?style=for-the-badge&logo=bun&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white)

### DevOps & Infrastructure

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Google Cloud](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![Grafana](https://img.shields.io/badge/Prometheus_%2F_Thanos-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)

### Identity, Payments & Tracking

![Keycloak](https://img.shields.io/badge/Keycloak-008AAA?style=for-the-badge&logo=keycloak&logoColor=white)
![Stripe](https://img.shields.io/badge/Stripe-635BFF?style=for-the-badge&logo=stripe&logoColor=white)
![Google Tag Manager](https://img.shields.io/badge/Server--side_GTM-246FDB?style=for-the-badge&logo=googletagmanager&logoColor=white)
![Google Ads](https://img.shields.io/badge/Google_Ads_API-4285F4?style=for-the-badge&logo=googleads&logoColor=white)
![Meta](https://img.shields.io/badge/Meta_CAPI-0866FF?style=for-the-badge&logo=meta&logoColor=white)
![Shopify](https://img.shields.io/badge/Shopify-7AB55C?style=for-the-badge&logo=shopify&logoColor=white)

### AI & Tooling

![Anthropic](https://img.shields.io/badge/MCP_%2F_LLM_tooling-D97757?style=for-the-badge&logo=anthropic&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX_Runtime-005CED?style=for-the-badge&logo=onnx&logoColor=white)

---

## GitHub Stats

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats-sigma-five.vercel.app/api?username=adaniki-dev&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" />
  <img height="170" src="https://github-readme-stats-sigma-five.vercel.app/api?username=adaniki-dev&show_icons=true&theme=default&hide_border=true&count_private=true" alt="GitHub Stats" />
</picture>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=adaniki-dev&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" />
  <img height="170" src="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=adaniki-dev&layout=compact&theme=default&hide_border=true&langs_count=8" alt="Top Languages" />
</picture>

</div>

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com/?user=adaniki-dev&theme=tokyonight&hide_border=true" />
  <img src="https://streak-stats.demolab.com/?user=adaniki-dev&theme=default&hide_border=true" alt="GitHub Streak" />
</picture>

</div>

---

<div align="center">

**Open to collaborations, freelance projects, and new opportunities.**

Let's build something great together.

</div>
