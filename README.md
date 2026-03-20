<p align="center">
  <img src="docs/assets/kamai-kavach-banner.png" alt="KamaiKavach Banner" width="800"/>
</p>

<h1 align="center">KamaiKavach</h1>
<h3 align="center">AI-Powered Parametric Income Shield for India's Q-Commerce Delivery Partners</h3>

<p align="center">
  <b>Team AeroFyta</b> | Guidewire DEVTrails 2026 — Unicorn Chase
</p>

<p align="center">
  Danish A G (Lead) &bull; Sanjay N &bull; Athishaya K &bull; Vishal C B &bull; Hariharan C V
</p>

---

## Table of Contents

1. [The Problem — Why This Matters](#1-the-problem--why-this-matters)
2. [Our Persona — The 10-Minute Sprinter](#2-our-persona--the-10-minute-sprinter)
3. [Persona-Based Scenarios & Workflow](#3-persona-based-scenarios--workflow)
4. [Weekly Premium Model](#4-weekly-premium-model)
5. [Parametric Triggers — What Fires a Payout](#5-parametric-triggers--what-fires-a-payout)
6. [AI/ML Integration Plan](#6-aiml-integration-plan)
7. [Adversarial Defense & Anti-Spoofing Strategy](#7-adversarial-defense--anti-spoofing-strategy)
8. [Zero-Touch Claims — The User Experience](#8-zero-touch-claims--the-user-experience)
9. [Platform Choice — Web vs Mobile](#9-platform-choice--web-vs-mobile)
10. [Tech Stack & Architecture](#10-tech-stack--architecture)
11. [Financial Viability — Unit Economics](#11-financial-viability--unit-economics)
12. [Development Roadmap (Phase 2 & 3)](#12-development-roadmap-phase-2--3)
13. [Why KamaiKavach Wins](#13-why-kamaikavach-wins)

---

## 1. The Problem — Why This Matters

India's 12.7 million gig workers are the backbone of the digital economy. Yet **80% have zero formal insurance**, and **no existing product covers income loss from external disruptions**.

When Mumbai floods for three days, when Delhi's AQI hits 828, when a Cloudflare outage kills Blinkit for hours — delivery partners who can't work simply **lose income with no recourse**.

**The gap we fill**: Platform-provided insurance covers accidents and health. Government schemes cover hospitalization. But when external disruptions halt work, riders bear 100% of the financial loss. KamaiKavach eliminates this gap.

### The Numbers That Define the Crisis

| Metric | Data Point | Source |
|--------|-----------|--------|
| Gig workers with zero savings | 90% | NITI Aayog |
| Earnings drop during heatwave days | 40% | Nature 2024 (Das & Somanathan) |
| Income loss per 1°C wet-bulb rise | 19% | Nature 2024 |
| Q-Commerce GMV (2024) | $6-7 Billion | RedSeer / Bain |
| Annual heatwave days (India, 2024) | 536 nationally | CII / IMD |
| Delhi AQI > 400 days per winter | 30-50 days | CPCB |

---

## 2. Our Persona — The 10-Minute Sprinter

### Why Q-Commerce (Blinkit / Zepto / Instamart) — Not Food Delivery

Most teams will default to Zomato/Swiggy food delivery. We chose Q-Commerce because it is **structurally more vulnerable** to external disruptions:

| Factor | Food Delivery | Q-Commerce (Our Pick) |
|--------|--------------|----------------------|
| Delivery SLA | 30-45 min | **10-15 min** |
| Radius | Up to 7 km | **2-3 km (dark store)** |
| Impact of 30 min heavy rain | Orders delayed | **Entire dark store paused, income = 0** |
| Algorithmic response to disruption | Reduced orders | **Instant zone shutdown** |
| Measurability of disruption | Moderate | **High** (tight geofence around dark stores) |

Q-Commerce operates on an ultra-condensed supply chain. When a localized disruption hits — a flooded intersection near a dark store, a sudden AQI spike — the platform's algorithm **instantly disables the zone**. The rider's earning potential drops to zero within minutes. This "SLA brittleness" makes Q-Commerce the ideal candidate for parametric insurance.

### Meet Ravi — Our Target User

> **Ravi, 27, Blinkit rider in Koramangala, Bangalore. Rides a 2-wheeler. Works peak + late shift (6 PM - 2 AM) from a dark store cluster. Nets ~₹18,000-21,000/month after fuel. Has zero savings and no insurance.**

**Ravi's Reality:**
- Completes 2.3-2.5 deliveries/hour (vs 1.8-2.0 for food delivery)
- Gross monthly: ₹16,000-31,000 | Net after fuel/maintenance (20%): **₹12,000-24,000**
- Peak hours: 7-11 AM (groceries/milk) + 6-11 PM (snacks/household)
- During Bangalore's October 2024 flooding (157mm in 6 hours), Q-commerce operations were **completely halted** — Ravi earned ₹0 for 2 days
- During the December 2025 Cloudflare outage, Blinkit/Zomato/Swiggy went down simultaneously — **riders were stranded in zones for hours without pay**

**What makes Ravi actually pay ₹49/week:**
- **Micro-pricing**: ₹49/week = less than the cost of one delivery order. Framed as "less than one order per week to protect all your earnings"
- **Loss-aversion framing**: "Your income is at risk this week" — riders are more motivated to avoid losses than chase gains
- **Default renewal via UPI AutoPay**: Status quo bias keeps them subscribed
- **Instant value**: "You are covered for tonight's shift" displayed immediately after payment
- **Deterministic rules**: Payout triggers a rider can verify externally (check IMD rainfall data themselves)

---

## 3. Persona-Based Scenarios & Workflow

### Scenario 1: Monsoon Flooding (High Frequency)

> **Tuesday, 7:45 PM**: Ravi starts his evening shift at the Koramangala dark store. At 8:30 PM, torrential rain begins — 72mm in 90 minutes. The dark store algorithm pauses all outgoing orders. Ravi is stuck under a shop awning.

**KamaiKavach Response (Zero-Touch):**
1. `8:35 PM` — Our trigger engine detects rainfall > 64.5mm (IMD "Heavy Rain" threshold) in Ravi's H3 zone via OpenWeatherMap API
2. `8:36 PM` — Cross-validates with IMD API data (dual-source confirmation)
3. `8:37 PM` — Fraud engine checks: Ravi's GPS is in the affected zone, his device sensors show outdoor conditions, his accelerometer confirms he was mobile before the rain started
4. `8:38 PM` — Claim auto-approved. ₹300 payout initiated via RazorpayX to Ravi's UPI
5. `8:40 PM` — WhatsApp notification: *"Heavy Rain detected in Koramangala. Deliveries are paused. KamaiKavach has credited ₹300 to your account for lost shift time. Stay safe!"*

**Total time from disruption to money-in-account: ~5 minutes. Zero buttons pressed by Ravi.**

### Scenario 2: Platform Outage (Novel — Most Teams Will Miss This)

> **Saturday, 1:15 PM** (Peak lunch demand): Cloudflare experiences a global outage. Blinkit, Zepto, and Swiggy APIs return HTTP 503 errors. 200,000+ riders nationwide are instantly unable to receive orders.

**KamaiKavach Response:**
1. `1:18 PM` — Our synthetic monitoring probes detect Blinkit's partner-facing API returning 503 errors for >3 minutes across 5 geographically distributed endpoints
2. `1:20 PM` — Cross-validates with secondary signals: Downdetector spike, social media mentions via GDELT
3. `1:25 PM` — After 10-minute sustained outage confirmation, all active policyholders with "shift active" heartbeat signals receive automatic payout
4. `1:30 PM` — ₹300 credited to each affected rider's UPI

### Scenario 3: Severe Air Pollution (Seasonal, Delhi-Specific)

> **November 15, Delhi**: AQI hits 485 ("Severe"). GRAP Stage IV activated. Ravi's counterpart Amit in Dwarka sees reduced order flow as restaurants close tandoors and customers self-restrict.

**KamaiKavach Response:**
1. WAQI API + CPCB station both report AQI > 400 for 24 continuous hours
2. Dual-source validation confirms the event
3. Riders in affected pincodes with active shift history receive partial-day payout (₹150) reflecting ~20-30% income impact

### Scenario 4: Coordinated Fraud Attempt (Market Crash Compliance)

> **500 riders in Mumbai organize via Telegram**. They install GPS-spoofing apps and fake their locations into a red-alert weather zone while sitting at home.

**KamaiKavach Response:** See [Section 7 — Adversarial Defense & Anti-Spoofing Strategy](#7-adversarial-defense--anti-spoofing-strategy)

### End-to-End Application Workflow

```
┌──────────────┐     ┌───────────────┐     ┌──────────────────┐
│   ONBOARDING │────▶│ RISK PROFILING │────▶│ POLICY CREATION   │
│  (3 screens) │     │   (AI/ML)     │     │ (Weekly Premium)  │
└──────────────┘     └───────────────┘     └──────────────────┘
                                                    │
                     ┌──────────────────────────────┘
                     ▼
┌──────────────────────────────┐     ┌────────────────────┐
│  REAL-TIME TRIGGER MONITORING │────▶│  CLAIM AUTO-TRIGGER │
│  (Weather, AQI, Outage APIs) │     │  (Parametric Event) │
└──────────────────────────────┘     └────────────────────┘
                                              │
                     ┌────────────────────────┘
                     ▼
┌──────────────────────────────┐     ┌────────────────────┐
│  4-LAYER FRAUD DETECTION     │────▶│  INSTANT UPI PAYOUT │
│  (Anti-Spoofing Pipeline)    │     │  (RazorpayX)       │
└──────────────────────────────┘     └────────────────────┘
                                              │
                     ┌────────────────────────┘
                     ▼
┌──────────────────────────────┐
│  ANALYTICS DASHBOARD         │
│  Workers: Earnings protected │
│  Insurers: Loss ratios, AI   │
└──────────────────────────────┘
```

---

## 4. Weekly Premium Model

### Why Weekly — Not Monthly or Annual

Gig workers operate week-to-week. Their platform payouts settle weekly. A ₹200/month premium triggers loss aversion. A ₹49/week premium — deducted automatically on payout day via UPI AutoPay — feels like a platform fee, not an insurance bill.

### Coverage Tiers

| Tier | Weekly Premium | Triggers Covered | Max Daily Payout | Max Weekly Payout | Target User |
|------|---------------|-----------------|-----------------|-------------------|-------------|
| **Basic Shield** | ₹29 | AQI > 400, Heat > 45°C | ₹300 | ₹600 | Part-time riders, low-risk cities |
| **Standard Guard** | ₹49 | Basic + Heavy Rain, Traffic Gridlock | ₹600 | ₹1,200 | Full-time riders, average-risk cities |
| **Pro Armor** | ₹89 | Standard + Platform Outages, Civil Disruption | ₹1,000 | ₹2,000 | High-risk weeks (monsoon/pollution season) |

### How Dynamic Pricing Works

Premiums are **not static**. Our AI recalculates every Monday based on:

```
Weekly Premium = (Expected Loss / Target Loss Ratio) + Risk Loading

Where:
  Expected Loss = Σ P(trigger_t | zone, week) × E(payout_t | tier)
  Target Loss Ratio = 62% (portfolio-level)
  Risk Loading = f(season, zone_risk_score, rider_claim_history)
```

**Example: How Ravi's premium changes across seasons**

| Season | Zone Risk Score | Weather Forecast | Premium (Standard) | Rationale |
|--------|----------------|-----------------|-------------------|-----------|
| Winter (Dec) | 0.25 | Clear, low AQI | ₹39 | Low disruption probability |
| Pre-Monsoon (May) | 0.45 | Heatwave advisory | ₹49 | Moderate heat risk |
| Peak Monsoon (Jul) | 0.72 | Heavy rain forecast | ₹69 | High rain + flood probability |
| Post-Monsoon (Oct) | 0.35 | Residual rain | ₹45 | Declining risk |

**Affordability Guardrail**: Premium is hard-capped at **0.8% of estimated weekly net income** — ensuring it never becomes unaffordable for the lowest-earning riders.

**Resilience Streak Discount**: If a rider operates 3 consecutive weeks without a disruption claim, their premium decreases by 10% — incentivizing genuine engagement and reducing moral hazard.

---

## 5. Parametric Triggers — What Fires a Payout

Every trigger must be: (a) **objectively measurable** via public APIs, (b) **directly correlated with income loss**, and (c) **independently verifiable** to resist fraud.

### Trigger Table

| # | Trigger | Threshold (Official Indian Standard) | Data Source / API | Income Loss Estimate | Historical Frequency | Anti-Fraud Check |
|---|---------|--------------------------------------|-------------------|---------------------|---------------------|-----------------|
| 1 | **Heavy Rainfall** | ≥ 64.5 mm/24hr (IMD "Heavy Rain") | OpenWeatherMap + IMD API (dual-source) | 40-90% of shift income | Mumbai: 15-25 days/monsoon; Bangalore: 5-10 days | GPS in zone + dual-source weather match + active shift proof |
| 2 | **Extreme Rain / Flooding** | ≥ 204.5 mm/24hr (IMD "Extremely Heavy") OR NDMA Red Alert | NDMA SACHET CAP API + GDACS | 70-100% of daily earnings | Mumbai: ~4 events/year; Chennai: 3-7 events/year | GDACS + IMD + rainfall consensus; geofenced to flood polygons |
| 3 | **Severe Heatwave** | Max temp ≥ 45°C for ≥ 2 consecutive days (IMD criteria) | OpenWeatherMap + IMD Heatwave Bulletins | 20-40% weekly loss | Delhi: 10-25 days/year; Hyderabad: 8-15 days/year | Shift declaration + local temp threshold match + baseline activity |
| 4 | **Hazardous Air Quality** | AQI ≥ 401 ("Severe") for 24 continuous hours | WAQI API + CPCB CAAQMS stations (dual-source) | 15-30% weekly loss | Delhi: 30-50 Severe days/winter; Mumbai: up to 28 Poor/VP days | Dual AQI source consensus + location proof + episode cap |
| 5 | **Platform / Cloud Outage** | Partner-facing API returns HTTP 503/504 for > 15 min across 3+ probes | Synthetic monitoring probes + Downdetector correlation | ~100% for outage duration | Cloudflare Dec 2025 outage paralyzed Blinkit/Zomato/Swiggy | Active session heartbeat required; cross-check with public reports |
| 6 | **Civil Disruption** | Section 144 / Curfew order active in rider's police jurisdiction for ≥ 4 hours | GDELT Project + NewsAPI + Government gazette feeds | 60-80% of daily income | Multiple incidents 2023-2025; Dec 2025 nationwide gig strike (200K+ workers) | Government order geofence + platform order suspension confirmation |

### Innovative Triggers Most Teams Will Miss

**Digital Infrastructure Disruption Index**: Beyond weather, we monitor:
- **Platform outages** (our synthetic probes + public reporting)
- **Payment rail failures** (UPI/IMPS downtime affecting payout settlement)
- **Internet shutdowns** (government-mandated, tracked via GDELT + IP traffic analysis)

This is credible because:
- Blinkit nationwide outage (Feb 2024) and Swiggy Instamart outage (Oct 2024) are documented
- The Cloudflare Dec 2025 outage simultaneously killed Blinkit, Zerodha, Groww, and other platforms
- Human Rights Watch documents that internet shutdowns directly remove access to app-mediated gig work

---

## 6. AI/ML Integration Plan

### 6.1 Dynamic Premium Pricing Engine

**Architecture**: Tweedie GLM + XGBoost Ensemble

| Component | Model | Purpose |
|-----------|-------|---------|
| Base Rate | Tweedie GLM | Actuarially interpretable base premium |
| Risk Adjustment | XGBoost Regressor | Non-linear risk factors (zone, season, rider history) |
| Explainability | SHAP Values | Waterfall charts showing why a premium is ₹X |

**Feature Space (All measurable in hackathon):**

| Category | Features |
|----------|----------|
| Geospatial | Rider's operational pincode, H3 cell (Res 7-8), elevation proxy, distance to coast/floodplain |
| Temporal | Week-of-year, monsoon flag, festival indicator, day-length |
| Environmental | 7-day weather forecast, trailing AQI averages, seasonal pollution patterns |
| Rider Behavior | Declared shift window, avg active hours, claim history, "online but stationary" ratio |
| Integrity | Device attestation status, GPS accuracy radius, spoof-risk score |

**Output**: Personalized weekly premium constrained to ₹29-₹89 range.

### 6.2 Intelligent Fraud Detection (4-Layer Pipeline)

**Layer 1 — Real-Time Telemetry Validation (Isolation Forest)**
- Cross-references GPS coordinates against Wi-Fi BSSIDs, cell tower triangulation, and IP geolocation
- Detects "impossible travel" (device teleporting 15km in 2 seconds) and VPN routing
- Catches basic GPS spoofing within sub-seconds

**Layer 2 — Behavioral Anomaly Detection (Autoencoder + LSTM)**
- Autoencoder architecture: Input → 64 → 32 → 16 → 32 → 64 → Output
- Trained on legitimate claim patterns; high reconstruction error = anomaly
- LSTM analyzes accelerometer/gyroscope time-series: a rider "trapped in flood" whose sensor data shows them sitting motionless indoors for hours gets flagged

**Layer 3 — Network Collusion Analysis (Graph Neural Networks)**
- Builds a graph: nodes = riders, edges = shared device IDs, IP subnets, bank accounts, referral codes
- Louvain community detection identifies suspicious clusters
- If 40 riders sharing the same IP subnet simultaneously claim from the same zone → syndicate alert

**Layer 4 — Historical Cross-Referencing (XGBoost Classifier)**
- Final arbiter: checks that IMD weather data, CPCB AQI data, GDACS alerts, and TomTom traffic data ALL reflect the claimed disruption
- Multi-source consensus required — a "rainstorm" claim with no corresponding IMD/OpenWeather data = rejected

### 6.3 Predictive Risk Engine (Competitive Moat)

**Purpose**: Forecast next week's disruption probability per H3 zone — enabling proactive premium adjustment and rider alerts.

**Architecture**: LSTM (48-hour lookback, 7 features, 2 layers of 64+32 units) + XGBoost ensemble

**Inputs**: Multi-model weather forecasts, seasonal climatology, historical trigger counts, AQI seasonal signals, NDMA alert patterns

**Two strategic outputs:**
1. **Underwriting discipline** — premiums adjust BEFORE monsoon spikes, protecting the loss ratio
2. **Preventive intelligence alerts** — when the model forecasts 44°C tomorrow, push a WhatsApp alert: *"Heatwave expected in your zone tomorrow. Your income protection auto-activates. Consider the evening shift instead."*

**Preventive Payouts (Unicorn Feature)**: If severe heat is predicted 48 hours ahead, auto-disburse ₹50 to the rider's wallet earmarked for ORS (Oral Rehydration Salts) and water. By investing ₹50 proactively, we prevent the much larger ₹600 loss-of-income claim — transforming insurance from reactive to proactive.

---

## 7. Adversarial Defense & Anti-Spoofing Strategy

> *Market Crash Compliance: Addressing the coordinated GPS-spoofing syndicate of 500 delivery workers exploiting parametric insurance via fake locations while resting at home.*

### 7.1 The Differentiation — Genuine Worker vs. Bad Actor

Simple GPS verification is dead. A spoofed GPS coordinate is indistinguishable from a real one at the data layer. Our system therefore **never trusts GPS alone** — it builds a **multi-signal authenticity score** from orthogonal data sources that are progressively harder to fake simultaneously.

**The Authenticity Scoring Matrix:**

| Signal | What It Detects | Why Spoofers Can't Fake It | Weight |
|--------|----------------|---------------------------|--------|
| **GPS Coordinates** | Basic location | Easily spoofed — baseline only | 10% |
| **Wi-Fi BSSID Fingerprint** | Nearby Wi-Fi networks visible to device | Spoofing GPS doesn't change which Wi-Fi routers your phone can see. A rider "in Andheri" whose device sees only home Wi-Fi SSIDs from Thane is caught. | 20% |
| **Cell Tower ID (CID/LAC)** | Which cell towers the device connects to | Cell tower IDs are hardware-level; GPS spoofing apps don't alter cellular connections. A rider claiming to be in Zone A but connected to a tower 12km away in Zone B is flagged. | 20% |
| **IP Geolocation** | Approximate location via ISP routing | If device GPS says "flood zone in Andheri" but IP resolves to a residential ISP in Thane, the signals disagree. | 10% |
| **Accelerometer + Gyroscope** | Physical motion patterns | A genuinely stranded rider shows micro-movements (standing, walking to shelter, adjusting phone). A rider at home shows flat-line sedentary patterns. LSTM-based kinematic profiling detects this. | 20% |
| **Barometric Pressure Sensor** | Altitude + weather correlation | During a genuine rainstorm, barometric pressure drops measurably. A spoofer's phone in a dry apartment registers normal indoor pressure — inconsistent with the claimed "severe weather zone." | 10% |
| **Network Latency Pattern** | Connection quality fingerprint | Genuine bad-weather zones show degraded cellular signal quality (increased jitter, packet loss). A spoofer on stable home Wi-Fi shows pristine network metrics — contradicting the "stranded in storm" narrative. | 10% |

**Composite Authenticity Score**: Each claim receives a score from 0-100. The system auto-approves above 75, flags for review between 45-75, and auto-rejects below 45.

**How this catches the 500-rider syndicate**: Even if all 500 spoof GPS perfectly, they CANNOT simultaneously fake:
- Wi-Fi BSSIDs matching the target zone's routers
- Cell tower connections to towers in the claimed zone
- Barometric pressure drops consistent with a rainstorm
- Accelerometer patterns of a rider outdoors in rain
- Degraded network latency matching storm conditions

The multi-signal approach ensures that **faking even 3 of 7 signals requires physical presence** — at which point the rider isn't faking.

### 7.2 The Data — Detecting a Coordinated Fraud Ring

Beyond individual spoofing detection, the 500-rider syndicate scenario requires **network-level pattern analysis**:

**Graph-Based Collusion Detection:**

```
Rider Nodes ──── Edges (Suspicious Connections) ──── Community Detection
    │                                                        │
    ├── Shared Device ID / IMEI                              │
    ├── Same IP Subnet (home Wi-Fi)                          ├── Louvain Algorithm
    ├── Shared Bank Account / UPI VPA                        ├── Label Propagation
    ├── Co-registration within 48 hours                      └── Anomaly Score
    ├── Identical referral chain
    └── Simultaneous claim timestamps (< 60 sec spread)
```

**Syndicate Detection Signals:**

| Signal | Normal Pattern | Fraud Ring Pattern | Detection Method |
|--------|---------------|-------------------|-----------------|
| Claim timing | Spread across hours | 500 claims within 60-second window | Statistical burst detection |
| IP addresses | Diverse ISPs/locations | Cluster on same subnet | IP entropy analysis |
| Device fingerprints | Unique per rider | Shared IMEI/device IDs, app cloners | Device fingerprint hashing |
| Referral chains | Organic, varied | Linear chain from single source | Graph depth analysis |
| Claim-to-registration ratio | Claims after weeks of activity | Claims within days of signup | Velocity scoring |
| Geographic clustering | Diverse dark stores | All "in" same 500m radius | Spatial density anomaly |
| Behavioral similarity | Varied shift patterns | Identical login/logout times | Time-series correlation |

**The Telegram Coordination Signal**: If 500 riders all submit claims from the "same zone" within a 60-second window — and their cell tower data shows they're actually in 200+ different locations — the system flags the entire cluster. A genuine weather event causes claims to trickle in over 30-60 minutes as different riders are progressively affected. Instantaneous mass claims are a statistical impossibility in organic disruption.

### 7.3 The UX Balance — Protecting Honest Workers

The hardest challenge: **how do you catch 500 fraudsters without rejecting the 1 genuine rider who has a dead GPS signal in a real storm?**

**Graduated Response Protocol (Never Binary):**

| Authenticity Score | Action | Rider Experience |
|-------------------|--------|-----------------|
| **75-100** (High Confidence) | Auto-approve, instant payout | *"₹300 credited to your account. Stay safe!"* |
| **45-74** (Medium Confidence) | Payout held in escrow (2 hours), enhanced verification | *"Your claim is being processed. We'll confirm within 2 hours."* + Request for optional selfie-in-rain or screenshot of delivery app showing "zone paused" |
| **25-44** (Low Confidence) | Manual review queue (24 hours) | *"We need a bit more time to verify conditions in your area. You'll hear from us within 24 hours."* |
| **0-24** (Fraud Likely) | Soft block + investigation | *"We couldn't verify the disruption in your area. If this is an error, tap here to request a review."* |

**Critical UX Principles:**

1. **Never punish network drops**: If a rider's phone loses connectivity during a genuine storm (a common scenario), they shouldn't be penalized for missing telemetry data. The system uses **last-known-good location** + **zone-level disruption confirmation** to bridge data gaps. If weather APIs confirm heavy rain in the rider's last-known zone, the claim proceeds.

2. **Benefit-of-the-doubt buffer**: First-time flagged riders with clean history (>4 weeks of legitimate activity, no prior flags) receive payouts with a soft flag rather than a hold. Trust is earned and tracked.

3. **Appeal mechanism**: Every rejected or held claim includes a one-tap "Request Review" button. A human reviewer (in production) or escalation queue (in hackathon) examines the evidence bundle. Wrongful rejections are compensated with a 10% bonus payout.

4. **Transparency**: Riders can view their own "Trust Score" (simplified, 3 levels: Trusted / Verified / New) and understand that maintaining consistent, genuine usage improves their score over time.

5. **Syndicate isolation, not collateral damage**: When a fraud ring is detected, only the graph-connected cluster is suspended. Other riders in the same geographic zone who are NOT part of the network continue receiving payouts normally. The system punishes the network, not the neighborhood.

---

## 8. Zero-Touch Claims — The User Experience

### Onboarding (3 Screens, < 60 Seconds)

**Screen 1 — "Protect This Week's Earnings"**
- Auto-detect city and zone via GPS
- OTP login (mobile number)
- Language selection (Hindi, English, Kannada, Tamil, Telugu, Marathi)
- One toggle: "I mostly work evenings/nights"

**Screen 2 — Coverage Selection (No Insurance Jargon)**
- Three cards: Basic / Standard / Pro
- Each shows: "Covers up to ₹600 / ₹1,200 / ₹2,000 lost income per week — from ₹29/week"
- Social proof: *"82% of riders in Koramangala chose Standard Guard this week"*
- Plain explanation: "If heavy rain, severe pollution, or app outage happens in your area during your shift, we pay automatically. No forms. No calls."

**Screen 3 — Payout Setup**
- Enter UPI ID or bank account
- UPI AutoPay mandate (single biometric confirmation)
- *"You're Protected"* badge with coverage dates (Mon-Sun)

### Claims Flow (Completely Invisible to Rider)

```
Disruption Occurs (e.g., rainfall > 64.5mm)
         │
         ▼
Trigger Engine detects via dual-source API polling (every 5 min)
         │
         ▼
Policy DB query: which riders have active coverage in affected H3 zone?
         │
         ▼
Fraud Pipeline: 4-layer authenticity scoring (< 2 min)
         │
         ▼
Score ≥ 75 ──▶ Auto-approve ──▶ RazorpayX UPI Payout ──▶ WhatsApp notification
Score 45-74 ──▶ Escrow hold ──▶ Enhanced verification (2 hrs) ──▶ Resolve
Score < 45 ──▶ Flag + review ──▶ Manual queue (24 hrs) ──▶ Appeal available
```

**Target Latency**: Disruption → Money-in-account: **< 30 minutes** for auto-approved claims.

---

## 9. Platform Choice — Web vs Mobile

### Decision: Mobile-First PWA + WhatsApp Integration

| Audience | Platform | Why |
|----------|----------|-----|
| **Riders** | Progressive Web App (PWA) + WhatsApp Bot | Zero-install, works on low-end Android, no Play Store friction. WhatsApp has 500M+ Indian users — notifications land where riders already live. |
| **Insurers / Admin** | Web Dashboard | Loss ratio monitoring, fraud analytics, trigger feed, premium volume — judges see the business intelligence layer. |

**Why PWA over Native App:**
- No 50MB download for a storage-constrained phone
- Instant updates without app store approval cycles
- Works offline for basic coverage status display
- Sharable via WhatsApp link (viral distribution among rider groups)

**WhatsApp Integration via Cloud API:**
- Onboarding flow can run entirely in WhatsApp (1,000 free service conversations/month)
- Claim notifications delivered as rich WhatsApp messages
- Policy renewal reminders with one-tap payment links
- Multi-language support via India's Bhashini API (government-built, free)

---

## 10. Tech Stack & Architecture

### System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        FRONTEND LAYER                           │
│  React PWA (Rider App)  │  React Dashboard (Admin/Insurer)      │
│  WhatsApp Cloud API     │  Deck.gl + H3 Risk Visualization      │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────┴──────────────────────────────────────┐
│                      API GATEWAY (FastAPI)                       │
│  Auth │ Policy Mgmt │ Premium Engine │ Claims │ Payouts │ Admin │
└──────────────────────────┬──────────────────────────────────────┘
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐
│  ML Services │  │ Trigger Engine│  │  Fraud Detection     │
│  (Python)    │  │ (Event-Driven)│  │  Pipeline            │
│              │  │              │  │                      │
│ • XGBoost    │  │ • API Poller │  │ • Isolation Forest   │
│ • LightGBM   │  │ • Kafka/     │  │ • Autoencoder        │
│ • LSTM       │  │   Redis      │  │ • GNN (Louvain)      │
│ • SHAP       │  │   Streams    │  │ • XGBoost Classifier │
└──────────────┘  └──────────────┘  └──────────────────────┘
                           │
┌──────────────────────────┴──────────────────────────────────────┐
│                        DATA LAYER                               │
│  PostgreSQL + PostGIS + h3-pg  │  Redis (real-time cache)       │
│  (Policies, Claims, Audit)     │  (Zone risk scores, sessions)  │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────┴──────────────────────────────────────┐
│                    EXTERNAL INTEGRATIONS                         │
│  OpenWeatherMap │ WAQI/CPCB │ NDMA SACHET │ GDELT │ RazorpayX  │
│  IMD API        │ OpenAQ    │ GDACS      │ NewsAPI│ WhatsApp   │
└─────────────────────────────────────────────────────────────────┘
```

### Tech Stack Summary

| Layer | Technology | Why This Choice |
|-------|-----------|----------------|
| **Frontend (Rider)** | React + Tailwind CSS (PWA) | Fast, mobile-first, installable, offline-capable |
| **Frontend (Admin)** | React + Deck.gl + H3 | H3 hexagonal risk maps rendered beautifully in WebGL |
| **Backend** | Python FastAPI | Async, high-performance, native ML ecosystem integration |
| **ML/AI** | XGBoost, LightGBM, scikit-learn, PyTorch (LSTM/Autoencoder) | Gradient boosting for tabular pricing; PyTorch for sequence models |
| **Explainability** | SHAP | Waterfall charts showing premium breakdown — satisfies judges + IRDAI |
| **Database** | PostgreSQL + PostGIS + h3-pg | Geospatial queries on H3 grids, ACID compliance for financial records |
| **Cache** | Redis | Real-time zone risk scores, rate limiting, session management |
| **Event Streaming** | Redis Streams (hackathon) / Kafka (production) | Lightweight event-driven trigger processing |
| **Payments** | RazorpayX (Test Mode) | UPI payouts with idempotency; sandbox for demo |
| **Notifications** | WhatsApp Cloud API | 500M+ Indian users; rich message templates |
| **Monitoring** | OpenTelemetry + Grafana | Observability for trigger latency and system health |
| **Deployment** | Docker + Railway/Render (free tier) | Fast deployment, zero infrastructure management |

### External APIs (All Free/Freemium)

| API | Free Tier | Use Case |
|-----|-----------|----------|
| OpenWeatherMap One Call 3.0 | 1,000 calls/day | Precipitation, temperature, severe weather alerts |
| WeatherAPI.com | 1M calls/month | Backup weather source, built-in AQI |
| WAQI (aqicn.org) | 1,000 req/sec | Real-time AQI from CPCB stations |
| OpenAQ v3 | Unlimited | Historical air quality data for model training |
| NDMA SACHET | Free (RSS/JSON) | Cyclone, flood, earthquake CAP alerts |
| GDACS | Free (RSS, 6-min updates) | International disaster alerts, flood severity |
| GDELT Project | Free (BigQuery) | Civil disruption, protest, curfew detection |
| NewsAPI | 100 req/day (free) | Strike/curfew news corroboration |
| RazorpayX | Test mode (free) | UPI payout simulation with idempotency |
| WhatsApp Cloud API | 1,000 conversations/month | Rider notifications and onboarding |

---

## 11. Financial Viability — Unit Economics

### Sample Weekly P&L — 10,000 Riders

**Tier Mix Assumption**: 50% Basic, 35% Standard, 15% Pro

| Tier | Riders | Weekly Premium | Weekly Collection |
|------|--------|---------------|-------------------|
| Basic Shield | 5,000 | ₹29 | ₹1,45,000 |
| Standard Guard | 3,500 | ₹49 | ₹1,71,500 |
| Pro Armor | 1,500 | ₹89 | ₹1,33,500 |
| **Total** | **10,000** | — | **₹4,50,000** |

**Expected Weekly Claims (Normal Season)**

| Tier | Trigger Probability | Avg Payout | Expected Claims |
|------|-------------------|------------|----------------|
| Basic | 10% | ₹150 | ₹75,000 |
| Standard | 15% | ₹300 | ₹1,57,500 |
| Pro | 20% | ₹500 | ₹1,50,000 |
| **Total** | — | — | **₹2,82,500** |

**Loss Ratio**: ₹2,82,500 / ₹4,50,000 = **62.8%** (within target range of 60-65%)

**Weekly Gross Margin**: ₹1,67,500 — covers technology costs, API subscriptions, and operations.

### Monsoon Stress Test

During peak monsoon, trigger probability rises to 25-35%. The dynamic pricing engine responds:
- Premium auto-adjusts upward (Standard: ₹49 → ₹69 for high-risk zones)
- Episode caps limit consecutive payouts (max 4 disruption windows/week)
- Winter-month surplus funds a smart-reserve pool to subsidize monsoon payouts

### Unit Economics

| Metric | Value |
|--------|-------|
| Customer Acquisition Cost (CAC) | ₹45 (WhatsApp referral loops + dark-store partnerships) |
| Average Weekly Premium (blended) | ₹45 |
| Average Retention | 26 weeks (conservative, given 65% annual gig attrition) |
| Lifetime Value (LTV) | ₹45 × 26 × (1 - 0.628) = **₹435** |
| **LTV / CAC Ratio** | **9.7x** (benchmark: >3x is venture-scale) |
| Break-even Subscribers | ~5,000 active riders |

---

## 12. Development Roadmap (Phase 2 & 3)

### Phase 2: Automation & Protection (Weeks 3-4, Mar 21 - Apr 4)
- [ ] Registration and onboarding flow (3-screen PWA)
- [ ] Insurance policy management (CRUD + weekly renewal engine)
- [ ] Dynamic premium calculation (XGBoost pricing model)
- [ ] 5 automated parametric triggers with real API integrations
- [ ] Basic claims management with fraud Layer 1 (GPS validation)
- [ ] RazorpayX test-mode payout integration
- [ ] 2-minute demo video

### Phase 3: Scale & Optimize (Weeks 5-6, Apr 5 - 17)
- [ ] Advanced fraud detection (all 4 layers — Autoencoder, LSTM, GNN, XGBoost)
- [ ] Instant payout system (simulated end-to-end)
- [ ] Predictive risk engine with next-week forecasting
- [ ] Worker dashboard (earnings protected, active coverage, trust score)
- [ ] Admin dashboard (loss ratios, trigger feed, fraud flags, predictive analytics)
- [ ] Evidence Bundle for every claim (multi-source proof card)
- [ ] 5-minute demo video + final pitch deck (PDF)

---

## 13. Why KamaiKavach Wins

### What Makes This a 5-Star, Not a 3-Star

| Dimension | 3-Star (Meets Brief) | 5-Star (KamaiKavach) |
|-----------|---------------------|---------------------|
| **Architecture** | Single weather trigger, cron polling, monolithic backend | Multi-source event-driven pipeline, H3 spatial grid, 4-layer fraud ML, Kafka streaming |
| **UX** | Download app, fill forms, press "Claim Now" | Zero-install PWA + WhatsApp, 3-screen onboarding, zero-touch claims, money in 5 minutes |
| **Logic** | "It rained, so pay everyone" | IMD/CPCB official thresholds, dynamic weekly pricing with SHAP explainability, 62% target loss ratio, LTV/CAC 9.7x |

### Our 5 Unicorn Differentiators

1. **Platform Outage Insurance** — We insure digital infrastructure downtime. No other team will think of this. The Cloudflare Dec 2025 outage proves it's real and devastating.

2. **Preventive Payouts** — AI predicts heatwave 48hrs ahead, sends ₹50 for ORS proactively. Prevents the larger ₹600 claim. Insurance becomes proactive, not reactive.

3. **Evidence Bundle Claims** — Every payout shows a "Proof Card" combining 2+ weather sources, AQI data, zone match, and timestamped logs. Directly addresses basis risk and builds trust.

4. **H3 Hexagonal Risk Map** — Hyper-local zone-level risk visualization using Uber's H3 grid + Deck.gl WebGL rendering. Visually stunning, technically impressive, and genuinely useful.

5. **Adversarial-Grade Anti-Spoofing** — 7-signal authenticity scoring, graph-based syndicate detection, graduated response that protects honest workers. Built to survive the Market Crash scenario and beyond.

---

<p align="center">
  <b>KamaiKavach</b> — Because every delivery matters. Every rider deserves a safety net.
</p>

<p align="center">
  <i>Built with conviction by Team AeroFyta for Guidewire DEVTrails 2026</i>
</p>
