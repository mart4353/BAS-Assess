# BAS-Assess

**Spondylitis Patient Self-Assessment Form**  
BASDAI · BASFI · Emotional Well-being

> A single-file, client-side web application for patients with Ankylosing Spondylitis (AS) to complete standardised self-assessments and send results directly to their doctor by email — no server, no login, no data stored anywhere.

**[▶ Open the assessment form](https://mart4353.github.io/BAS-Assess/)**

---

## Background

### What is Ankylosing Spondylitis?

Ankylosing Spondylitis (AS) — also called **axial spondyloarthritis (axSpA)** — is a chronic inflammatory arthritis that primarily affects the spine and sacroiliac joints. It causes pain and stiffness, and in advanced cases can lead to fusion of the vertebrae. AS affects approximately 0.1–1.4 % of the population and most commonly begins in young adults between ages 17 and 35.

**Common symptoms include:**

- Persistent lower back and hip pain, typically worse in the morning or after inactivity
- Stiffness that improves with movement and exercise
- Inflammation of tendons and ligaments where they attach to bone (enthesitis)
- Fatigue
- In some cases: peripheral joint involvement, eye inflammation (uveitis), and bowel inflammation

AS is a lifelong condition. Treatment focuses on reducing inflammation, managing symptoms, and preventing structural damage — typically combining physiotherapy, NSAIDs, and for moderate–severe disease, biologic therapies (TNF inhibitors, IL-17 inhibitors).

---

## Assessment Indices

Regular monitoring with validated patient-reported outcome measures is central to AS management. This tool implements three complementary assessments.

### Part 1 — BASDAI (Bath Ankylosing Spondylitis Disease Activity Index)

The **BASDAI** is the most widely used self-reported measure of disease activity in AS. It was developed at the Royal National Hospital for Rheumatic Diseases in Bath, UK, and validated in 1994.

It consists of **6 questions** covering the past week, each scored on a **0–10 numerical rating scale**:

| # | Domain |
|---|--------|
| 1 | Fatigue / tiredness |
| 2 | Neck, back or hip pain |
| 3 | Pain or swelling in joints other than neck, back and hips |
| 4 | Discomfort from areas tender to touch or pressure (Enthesitis) |
| 5 | Morning stiffness — intensity |
| 6 | Morning stiffness — duration (0 = 0 h, 10 = ≥ 2 h) |

**Formula:**

```
BASDAI = ( Q1 + Q2 + Q3 + Q4 + mean(Q5, Q6) ) / 5
```

**Interpretation:**

| Score | Interpretation |
|-------|---------------|
| 0 – 3.9 | Low disease activity |
| **≥ 4** | **High disease activity — treatment review recommended** |

A BASDAI ≥ 4 on two occasions at least 4 weeks apart is one of the criteria for initiating biologic therapy under most national guidelines (NICE, EULAR).

---

### Part 2 — BASFI (Bath Ankylosing Spondylitis Functional Index)

The **BASFI** measures physical function and the degree of disability caused by AS. Also developed in Bath and validated in 1994.

It consists of **10 questions** covering the patient's ability to perform daily activities over the past week, each scored on a **0–10 numerical rating scale** (0 = Easy, 10 = Impossible):

| # | Activity |
|---|----------|
| 1 | Putting on socks or tights without help |
| 2 | Bending forward to pick up a pen from the floor |
| 3 | Reaching up to a high shelf |
| 4 | Getting up from an armless chair |
| 5 | Getting up off the floor from lying on your back |
| 6 | Standing unsupported for 10 minutes without discomfort |
| 7 | Climbing 12–15 steps one foot per step, no handrail |
| 8 | Looking over your shoulder without turning your body |
| 9 | Doing physically demanding activities |
| 10 | Doing a full day's activities at home or work |

**Formula:**

```
BASFI = mean( Q1 … Q10 )
```

**Interpretation:** Higher scores indicate greater functional limitation. The BASFI is sensitive to change and widely used to monitor response to treatment over time. A score above 4 generally reflects significant functional impairment.

---

### Part 3 — Emotional Well-being

Chronic pain conditions have a well-documented impact on mental health. Studies show that patients with AS have higher rates of anxiety and depression than the general population. Poor sleep quality — a common consequence of nocturnal pain and stiffness — further compounds fatigue and psychological burden.

This section includes **3 self-reflection questions** on:

1. **Emotional wellbeing** — has the condition affected mood, motivation, or sense of self?
2. **Sleep quality** — assessing restorative sleep over the past week
3. **Social impact** — whether pain has led to withdrawal from relationships or social activities

Answers are presented to the treating doctor alongside the clinical indices to support a holistic consultation.

**Estonian patients** are also directed to [peaasi.ee](https://peaasi.ee), the leading Estonian mental health resource.

---

## Features

- **Single HTML file** — no build step, no dependencies, works offline
- **Three languages** — English, Estonian (Eesti), Russian (Русский); switch any time and the form re-renders instantly
- **URL pre-fill** — patient details and language can be encoded into the link so the form opens ready for a specific patient (useful for clinic workflows)
- **Live score calculation** — BASDAI and BASFI scores update in real time as sliders are moved; BASDAI score box turns red at ≥ 4
- **Progress indicator** — header progress bar tracks completion
- **Mailto submission** — clicking *Confirm and Send to Doctor* opens the native email client with a fully formatted plain-text report pre-loaded (subject line, all scores, all individual answers)
- **No data ever leaves the device** — no analytics, no backend, no cookies

---

## How to Use

### Option A — GitHub Pages (online)

Open **[https://mart4353.github.io/BAS-Assess/](https://mart4353.github.io/BAS-Assess/)** in any browser. No installation required.

### Option B — Local file

Download [`index.html`](index.html) and open it directly in a browser. Everything is self-contained.

### Workflow

1. Select language (EN / ET / RU)
2. Enter patient name, personal ID, and doctor's email address
3. Complete Parts 1, 2 and 3
4. Click **Confirm and Send to Doctor** — your email client opens with the completed report

---

## URL Parameters

The form accepts query parameters to pre-populate patient details. This lets clinics generate a personalised link for each patient.

| Parameter | Description | Example |
|-----------|-------------|---------|
| `lang` | Language (`en`, `et`, `ru`) | `?lang=et` |
| `name` | Patient name (URL-encoded) | `&name=Mari+Tamm` |
| `id` | Personal ID / Isikukood | `&id=49001010000` |
| `email` | Doctor's email address | `&email=arst@haigla.ee` |

**Example pre-filled URL:**

```
https://mart4353.github.io/BAS-Assess/?lang=et&name=Mari%20Tamm&id=49001010000&email=arst@haigla.ee
```

The **Copy Pre-filled URL** button on the form generates and copies this link automatically.

---

## Email Report Format

The report sent to the doctor is structured plain text:

```
PATIENT INFORMATION
Name:  Mari Tamm
ID:    49001010000

PART 1 — BASDAI (Disease Activity)
BASDAI Score: 5.30 / 10  [HIGH DISEASE ACTIVITY]

Q1: Fatigue / tiredness             → 6.0 / 10
Q2: AS neck, back or hip pain       → 7.5 / 10
...

PART 2 — BASFI (Functional Index)
BASFI Score: 3.40 / 10

Q1: Putting on socks or tights      → 2.0 / 10
...

PART 3 — EMOTIONAL WELL-BEING
Q1: Emotional wellbeing             → Moderately
Q2: Sleep quality                   → Poor
Q3: Social impact of pain           → Significantly
```

---

## Scoring Reference

| Index | Formula | High threshold |
|-------|---------|----------------|
| BASDAI | `(Q1+Q2+Q3+Q4 + avg(Q5,Q6)) / 5` | ≥ 4 (highlighted in red) |
| BASFI | `mean(Q1…Q10)` | — (tracked over time) |

---

## References

- Garrett S, et al. (1994). *A new approach to defining disease status in ankylosing spondylitis: the Bath Ankylosing Spondylitis Disease Activity Index.* J Rheumatol. 21(12):2286–91.
- Calin A, et al. (1994). *A new approach to defining functional ability in ankylosing spondylitis: the development of the Bath Ankylosing Spondylitis Functional Index.* J Rheumatol. 21(12):2281–5.
- NICE guideline NG65 (2017). *Spondyloarthritis in over 16s: diagnosis and management.*
- EULAR recommendations for the management of ankylosing spondylitis (updated 2022).

---

## License

[MIT](LICENSE) © 2026 mart4353
