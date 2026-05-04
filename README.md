# Priorities — ParaguAI Operations Base

Single source of truth for all clients, repos, websites, cron jobs, and infra.

## Quick Index

| # | Category | Count |
|---|----------|-------|
| 1 | [Live Websites](#live-websites) | 19 |
| 2 | [Client Repos](#client-repos) | 30+ |
| 3 | [Infrastructure](#infrastructure) | Docker Swarm + Traefik + CF |
| 4 | [Cron Jobs](#cron-jobs) | 22 active |
| 5 | [Active Projects](#active-projects) | ~12 |

---

## Live Websites

All hosted on `*.paragu-ai.com` domain, Docker Swarm, Traefik + Cloudflare.

### ParaguAI Internal
| URL | Service | Status |
|-----|---------|--------|
| paragu-ai.com | paragu-ai-builder (3 replicas) | LIVE |
| www.paragu-ai.com | paragu-ai-builder | LIVE |

### Client Sites (Live)
| URL | Client | Repo | Notes |
|-----|--------|------|-------|
| dayah.paragu-ai.com | Dayah LitWorks | /root/dayah-litworks-deploy | 7 client books, 239 unnamed covers |
| viajero.paragu-ai.com | El Viajero Comercio | /root/elviajero-comercio | Also el-viajero.paragu-ai.com |
| nexa.paragu-ai.com | Nexa Paraguay | /root/sites/nexa-paraguay | Has content resolver |
| nudo.paragu-ai.com | Nudo | /root/nudo/repo | Also xn--ndo-hoa.paragu-ai.com |
| ozmontania.paragu-ai.com | Oz Montania | /root/ozmontania-website | 7 pages, no real images |
| fun4me.paragu-ai.com | Fun4Me (Bram+Rach) | /root/fun4me-store | Auth fixed 2026-05-04 (bcryptjs+JWT) |
| superspuma.paragu-ai.com | Superspuma | /root/superspuma | 24 products, 12 pages. Leticia Roig. WA: Sarah |
| goldenvisa.paragu-ai.com | Golden Visa Advisory | /root/golden-visa-advisory | Raul Fretes. 7 langs, Residency/Business |
| cabral.paragu-ai.com | Granja Cabral | /root/granja-cabral | 8762 hens, 242 eggs/day |
| duerksen.paragu-ai.com | Clinica Duerksen | /root/clinica-duerksen | Dental clinic |
| mant ra-spa.paragu-ai.com | Mantra Spa | /root/mantra-spa | Spa services |
| magnolia-peluqueria.paragu-ai.com | Magnolia Peluqueria | /root/magnolia-peluqueria | Hair salon |
| maiyu.paragu-ai.com | Maiyu Atelier | /tmp/maiyu-atelier | Fashion/atelier |
| villamayor.paragu-ai.com | Villamayor & Asociados | /tmp/villamayor-asociados | Law firm |
| 30vcs.paragu-ai.com | 30vcs | /root/30vcs | Unknown/placeholder |
| brahm.paragu-ai.com | Brahm the Racoon | /root/brahm-the-racoon | Brand/entertainment |
| nicolas-duarte.paragu-ai.com | Nicolas Duarte Portfolio | /root/repos/nicolas-duarte-site | Nestlé HR IT analyst, static Next.js |

### Sites (/root/sites/ — paragu-ai-builder output)
| Directory | Client | Status |
|-----------|--------|--------|
| bufete-mendez | Bufete Mendez | Static |
| de-abasto-a-casa | De Abasto a Casa | Static |
| granja-cabral | Granja Cabral | Static (duplicate) |
| nexa-paraguay | Nexa Paraguay | Static |
| nexa-propiedades | Nexa Propiedades | Static |
| polki-squad | Polki Squad | Static |
| stoicfinch | Stoicfinch | Static |
| superspuma | Superspuma | Static (duplicate) |

### Extra Infra Services
| URL | Service | Notes |
|-----|---------|-------|
| space.sunstein.cloud | Space Agent | Browser-first AI agent |
| gyro.sunstein.cloud | Gyro | ghcr.io/ai-whisperers/gyro |

---

## All Repos

### Client Websites (Active)
| Repo | Client | Type |
|------|--------|------|
| 30vcs | 30vcs | Next.js |
| brahm-the-racoon | Brahm the Racoon | Next.js |
| clinica-duerksen | Clinica Duerksen | Next.js |
| dayah-litworks-deploy | Dayah LitWorks | Next.js |
| depiflash | Depiflash | Next.js |
| elviajero-comercio | El Viajero Comercio | Next.js |
| fun4me-store | Fun4Me | Next.js (custom pg auth) |
| golden-visa-advisory | Golden Visa | Next.js 16 |
| granja-cabral | Granja Cabral | Next.js (egg farm) |
| laura-egg-business | Laura Egg Business | Data/analysis |
| luis-de-leon-concept | Luis de Leon | Concept site |
| magnolia-peluqueria | Magnolia Peluqueria | Next.js |
| mantra-spa | Mantra Spa | Next.js |
| nudo/repo | Nudo | Next.js |
| ozmontania-website | Oz Montania | Next.js |
| superspuma | Superspuma | Next.js 15 static |
| vete | Vete | Unknown |
| repos/nicolas-duarte-site | Nicolas Duarte | Next.js static |
| 3md-website | 3MD | Client template |

### Internal / Platform
| Repo | Purpose |
|------|---------|
| paragu-ai-builder | Multi-tenant website generator |
| paragu-ai-leads | Lead extraction/data |
| paraguay-beauty-data | Beauty industry data |
| client-leads | Client lead management |
| solstein | Solstein devtools (AST/guardrails) |
| space-agent | Browser-first AI agent |
| clawpanel | OpenClaw management panel (Tauri) |
| bdsm-py-toolkit | BDSM Paraguay toolkit |
| bichos-gym | Gym/health related |
| awesome-opencode | OpenCode resource list |

### Hermes / AI Infra
| Repo | Purpose |
|------|---------|
| .hermes/hermes-agent | Main Hermes Agent (NousResearch fork) |
| .hermes/hermes-agent-self-evolution | Self-evolution module |
| hermes-incident-commander | Autonomous infra healing |
| hermes-ui | Hermes UI (legacy) |
| hermes-web-ui | Self-hosted AI chat dashboard |
| hermes-webui | Hermes UI (docker-compose) |
| cocodrilo-fitness | Fitness app |

### Research / Misc
| Repo | Purpose |
|------|---------|
| repos/paraguay-cannabis-analysis | Cannabis ecosystem research |
| refugio-animal-paraguay | Animal shelter (docker-compose) |
| stroopwafel-huis | Stroopwafel concept |
| maps-extractor | Map data extraction |
| ai-research | AI research docs |

---

## Infrastructure

### Docker Swarm
- 1 manager node (this VPS)
- 22 services running
- Traefik v3.5.3 as reverse proxy + SSL
- All sites on `agent-net` network

### Cloudflare
- DNS for *.paragu-ai.com
- CF token: READ-ONLY (user adds A records)

### Monitoring
- Prometheus + node-exporter
- IC health check (every 5 min)
- IC hourly audit
- IC morning briefing (daily 08:00)
- ~~Grafana~~ (check status)

### Postgres
- /root/stacks/postgres/ — shared DB for apps

---

## Cron Jobs (22 total)

### Solstein Pipeline (16 jobs — 8 RED-GREEN, 8 FEATURE)
Every 3 hours, round the clock. All currently ERROR state.
- `sol-rg-{00,03,06,09,12,15,18,21}` — Fix failing tests
- `sol-ft-{00,03,06,09,12,15,18,21}` — Implement features
- `sol-planning` — Weekly planning (Sun 02:00)
- `sol-metrics` — Weekly metrics (Sun 08:00)

### Incident Commander (3 jobs)
- `ic-health-check` — Every 5 min
- `ic-hourly-audit` — Every hour
- `ic-morning-briefing` — Daily 08:00

### Business (1 job)
- `lead-scout-weekly` — Every Monday 08:00 → WhatsApp

### Hermes Cron
- 22 cron jobs total, all using claude-sonnet-4 via OpenRouter

---

## Active Projects & Priority Areas

### 🥇 Tier 1 — Revenue / Active Clients
1. **Superspuma** — Missing: real product photos, product finder quiz, bundle builder (+Gs 1.17M), B2B portal (2300 clients). Contact: Leticia Roig via Sarah (WA)
2. **Golden Visa Advisory** — Raul Fretes. Live at goldenvisa.paragu-ai.com. Needs continued support.
3. **Granja Cabral / Laura** — 8762 hens, 242 eggs/day. WhatsApp group.

### 🥈 Tier 2 — Development Active
4. **Fun4Me** — Auth fixed, push pending. Bram+Rach project.
5. **Dayah LitWorks** — 7 clients with books, 239 unnamed covers.
6. **Nexa** — Live with content resolver.
7. **Nudo** — Live.
8. **Oz Montania** — Live but no real images.
9. **El Viajero Comercio** — Live.

### 🥉 Tier 3 — Infra / Maintenance
10. **Solstein pipeline** — 16 cron jobs all in error state, investigate.
11. **IC cron jobs** — All erroring, check.
12. **VPS cleanup** — Ongoing maintenance.
13. **All sites/ repos** — Verify all /root/sites/ sites are up-to-date.

### 🔄 Pending
- villamayor-asociados (built from /tmp)
- maiyu-atelier (built from /tmp)
- Lead enrichment pipeline
- New lead generation
- paragu-ai-builder tenant improvements

---

## Key Contacts

| Name | Role | Via |
|------|------|-----|
| Ivan (you) | Founder, ParaguAI | This chat |
| Sarah | Leticia Roig's daughter, Superspuma contact | WA 113090817425545 |
| Leticia Roig | Gerente General, Superspuma | Via Sarah |
| José Campuzano | Director, Superspuma | |
| Raul Fretes | Golden Visa client | |
| Bram | Fun4Me partner (concise, strategic) | |
| Rach | Fun4Me partner | |

---

## Communications Rules
- WhatsApp: max 3 sentences, no markdown, bullet points, zero fluff, one actionable per message
- Telegram: primary channel
- Group chats: English only in Gallinas Oviedo

---

*Generated 2026-05-04. Update this file when adding new clients or infra changes.*
