# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

## Search Sites

Primary (your market's job boards - scaffold one with `/add-portal`):
- **linkedin.com/jobs** - LinkedIn job listings (filter: Brasil / São Paulo); also covered by `linkedin-search` CLI - primary source for now
- **indeed.com.br** - general WebSearch fallback (no dedicated CLI yet)
- **Gupy / Catho / InfoJobs** - major Brazilian job boards, not yet scaffolded with a CLI; good `/add-portal` candidates if LinkedIn coverage proves insufficient

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies

## Query Categories

Queries are grouped by priority. Each query should be combined with your location terms (e.g. your city, region, or metro area) where the site supports it.

### Priority 1: Full-Stack Developer

These match your current hands-on experience (Next.js/microservices at NewLegal) and stated top career direction.

```
site:indeed.com.br "desenvolvedor full-stack" São Paulo
site:indeed.com.br "Next.js" OR "Nest.js" desenvolvedor São Paulo
site:linkedin.com/jobs "desenvolvedor full-stack" Brasil
site:linkedin.com/jobs "full-stack developer" remoto Brasil
```

### Priority 2: Power Platform / Data Analyst

These match your strongest track record (Junior to Lead Data Analyst progression at RS Aeron; Power BI/Power Apps skills).

```
site:indeed.com.br "Power BI" analista São Paulo OR "Grande São Paulo"
site:indeed.com.br "Power Apps" OR "Power Platform" especialista Brasil
site:linkedin.com/jobs "analista de dados" Power BI São Paulo Brasil
site:linkedin.com/jobs "Power Platform specialist" Brasil
```

### Priority 3: Business Analyst

Adjacent role you're targeting as a business-technology bridge.

```
site:indeed.com.br "business analyst" OR "analista de negócios" São Paulo
site:linkedin.com/jobs "business analyst" Python SQL Brasil
```

### Priority 4: Broader Technical / PropTech

Wider net, including PropTech/real-estate-tech companies (a stated differentiator) and general junior/estágio-level technical roles.

```
site:indeed.com.br "PropTech" desenvolvedor OR analista São Paulo
site:linkedin.com/jobs Python SQL desenvolvedor São Paulo Brasil
site:linkedin.com/jobs "automação de processos" analista OR desenvolvedor Brasil
```

## Location Filter

When evaluating results, verify the job location is within reasonable commute distance from your home, or fully remote. Define acceptable areas:
- São Paulo (city) and surrounding areas - ideal
- Fully remote (anywhere in Brasil) - ideal
- Hybrid roles requiring occasional office days in São Paulo - acceptable
- Grande São Paulo / ABC (Santo André, São Bernardo do Campo, São Caetano do Sul) - acceptable
- Campinas or Santos/Litoral (borderline - ~1-2h by transit/car, only if hybrid with limited office days)
- Other Brazilian states / on-site-only roles outside São Paulo (too far - would require relocation)

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
