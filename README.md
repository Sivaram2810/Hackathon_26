# NEXUS — Multi-Agent Hospital Emergency Resource Intelligence Platform

NEXUS is a single-file, browser-based simulation of a hospital emergency
resource management system. It models bed occupancy, patient triage,
ambulance dispatch coordination, and clinical staff workflows across
doctors, nurses, receptionists, and paramedics — all within one
self-contained HTML file.

## Overview

The platform demonstrates how a multi-role hospital operations dashboard
can coordinate patient placement, staff visibility, and diagnostic data in
real time. It ships as a single `.html` file with no build step: open it
in a browser and it runs.

## Features

### 🔄 Persistent Client-Side State
All application state (patients, beds, staff activity, and session data)
is synchronized to the browser's `localStorage`, so data survives page
refreshes and browser restarts without requiring a backend database.

### 🔑 Bring Your Own Key (BYOK)
An in-app **API Configuration Panel** lets you connect your own OpenAI,
Anthropic, or custom-endpoint API key.
- **With an active key:** the system makes live LLM calls to reason
  about patient placement using current simulated clinical variables.
- **Without a key:** the system falls back to deterministic, simulated
  agent telemetry, so the app remains fully functional in demo mode.

### 🗄️ Embedded SQL Query Console
A built-in relational query console lets users run SQL-style queries
directly against the live application state — inspecting patient
records, bed assignments, and diagnostic schemas without leaving the
browser.

### 👥 Role-Based Access
The app includes seeded demo accounts spanning:
- **Doctors** across specialties (Emergency Medicine, ICU, Cardiothoracic
  Surgery, Neurosurgery, General Surgery, Internal Medicine, Orthopedics,
  Pulmonology, Nephrology, Gastroenterology)
- **Nurses** across wards
- **Receptionists**
- **Ambulance / Paramedic** command view

Each role sees a tailored dashboard (patient intake, triage boards,
capacity diagnostics, ambulance divert alerts, etc.).

### 🚑 Ambulance Command & Divert Logic
A dedicated Ambulance Command tab surfaces live bed occupancy and
automatically flags a hospital divert protocol when occupancy crosses a
critical threshold, recommending an alternate branch for incoming
patients.

## Getting Started

No installation required.

1. Download `nexus.html` (or whichever filename you saved this as).
2. Open it directly in any modern browser (Chrome, Edge, Firefox, Safari).
3. Log in using one of the seeded demo accounts (see below), or configure
   your own credentials as needed.

There is no server, package manager, or build process — it is a single
static HTML file using React and Babel loaded from CDN.

## Demo Accounts

| Role | Example ID | Password |
|---|---|---|
| Doctor | `DR-2025-001` | `Anjali@123` |
| Nurse | `NR-2025-001` | `Nurse1@123` |
| Receptionist | `RC-2025-001` | `Recep1@123` |
| Ambulance | `AM-2025-001` | `Ambu@123` |

> ⚠️ These are demo credentials for local testing only. Replace or remove
> them before any real deployment, and never reuse these values for actual
> systems handling real patient data.

## Configuring BYOK

1. Open the **API Configuration Panel** from the dashboard.
2. Enter your API key for OpenAI, Anthropic, or a custom endpoint.
3. Save — the system will begin routing placement decisions through live
   LLM calls. Clearing the key reverts to simulated telemetry.

Your key is stored client-side only, alongside the rest of the app's
`localStorage` state.

## Tech Stack

- **React 18** (via CDN, no bundler)
- **Babel Standalone** for in-browser JSX transpilation
- **Google Fonts** (Inter, DM Mono)
- **localStorage** for persistence
- Vanilla CSS with CSS custom properties for theming

## Project Status / Notes

This is a demonstration / prototype build intended for internal review,
UX exploration, and workflow simulation. It uses entirely fictional
patient and staff data and is **not** connected to any real hospital
system, EHR, or database. It should not be used to store, process, or
simulate handling of real patient health information.

## License
