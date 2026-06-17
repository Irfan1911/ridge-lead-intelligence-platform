# RIDGE — Relations & Internship Discovery Generation Engine

**Live:** [dynamis-ai.com](https://www.dynamis-ai.com)

RIDGE is a lead generation tool that converts a Google Maps search into a 
spreadsheet of companies with contact emails extracted automatically from 
their websites. Paste a search URL, get a contact-ready spreadsheet 
delivered to your inbox — no login, no setup.

## What It Does

1. **Search** — User submits a Google Maps search URL and email address
2. **Scrape** — Backend extracts up to 200 companies (name, industry, 
   phone, website, address, rating, hours) via SerpAPI
3. **Enrich** — Each company's website is visited and contact emails are 
   extracted automatically in the background
4. **Deliver** — A Google Sheet is created per request and emailed to 
   the user, populating progressively as enrichment completes

## Tech Stack

**Frontend:** Next.js, React, Tailwind CSS  
**Backend automation:** n8n (workflow orchestration)  
**Data source:** SerpAPI (Google Maps)  
**Storage & delivery:** Google Sheets API, Gmail  
**Hosting:** Vercel

## Architecture Highlights
- **Ping-pong workflow pattern** — two coordinated n8n workflows 
  (Email Enricher + Enricher Manager) recursively process leads in 
  batches of 15–20, avoiding execution timeouts on large datasets 
  (tested up to 200 companies per run)
- **Per-user dynamic spreadsheet creation** — each request generates 
  an isolated Google Sheet rather than writing to a shared dataset
- **Frontend-only architecture** — this repository contains the 
  Next.js frontend. The automation backend runs on a self-hosted 
  n8n instance and is not included in this repo

## Screenshots

### Landing Page
![RIDGE Homepage](<img width="1763" height="4446" alt="image" src="https://github.com/user-attachments/assets/3cc3f95e-f4ba-4c16-979e-ef8ccf4fa978" />)

### Generate Leads
![Generate Leads Form](<img width="1763" height="1411" alt="image" src="https://github.com/user-attachments/assets/bedda732-9e2d-44aa-b9d7-00d1c6be37a2" />)

### Example Output
![Spreadsheet Output](<img width="1919" height="915" alt="image" src="https://github.com/user-attachments/assets/c094da74-9a1e-4ead-8874-e96e0d1b9856" />)

## Validated Results

Tested across multiple Malaysian industries (architecture, accounting, 
digital marketing, logistics):
- Up to 200 companies processed per search
- 55–67% contact email extraction rate on companies with websites
- Full pipeline (search → enriched spreadsheet) completes in 
  20–30 minutes for 150–200 company datasets

## Note
This repository serves as a project showcase. The live tool can be tested directly at the link above.
