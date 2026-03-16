# CAAASA Idea Wall — "Turn Your Ideas Into an AI App"

## Overview
A Firebase-powered real-time Idea Wall for the CAAASA x TRPEC 60-minute student workshop (ages 11-18). Students brainstorm AI app ideas, submit them to a live wall, build prototypes, and pitch.

**Created by:** The Right Path Educational Consulting (TRPEC)
**Team:** Dr. Marie Martin, Dr. Charles Martin

---

## Access & Accounts

### Firebase Project
- **Project name:** CAAASA Idea Wall
- **Project ID:** `caaasa-idea-wall`
- **Project number:** `698516642475`
- **Firestore location:** `us-west2` (Los Angeles)
- **Console:** https://console.firebase.google.com/project/caaasa-idea-wall

### Firebase Project Owners
| Email | Role |
|-------|------|
| ginjack2002@gmail.com | Owner (creator) |
| alexandriasworld1234@gmail.com | Owner |
| charlesmartinedd@gmail.com | Owner |

### Live URLs
- **App (students):** https://caaasa-idea-wall.web.app
- **Projector mode:** https://caaasa-idea-wall.web.app/?projector=true
- **Facilitator mode:** https://caaasa-idea-wall.web.app/?facilitator=true
- **Pitch template:** https://caaasa-idea-wall.web.app/?pitch=true

### GitHub Repository
- **Repo:** https://github.com/Alexandria-s-Design/caaasa-idea-wall
- **Org:** Alexandria-s-Design

### Gamma Facilitator Presentation
- **URL (FINAL):** https://gamma.app/docs/po36u3b1ovil3gq
- **Previous drafts:** https://gamma.app/docs/n3xsjwms6h4p967, https://gamma.app/docs/dwwrunrqeavukgv, https://gamma.app/docs/otvbzqazhjjiebc
- **Theme:** Aurora (dark purple/navy)
- **Slides:** 16 slides, structured around IDEO Human-Centered Design (Inspiration → Ideation → Implementation)
- **Intro video:** https://vimeo.com/106505300 (IDEO "What is Human-Centered Design?" — embedded on Slide 3)
- **No student-facing contact info** (removed by design)
- **Gamma account:** alexandriasworld1234@gmail.com

---

## App Modes (URL Parameters)

| URL Parameter | What It Does |
|---------------|-------------|
| *(none)* | Default student view — submit form + idea wall |
| `?projector=true` | Gallery Walk display — large cards, dot legend, QR code, no submit form |
| `?facilitator=true` | Facilitator tools — QR code, pitch template, clear wall button |
| `?pitch=true` | Shows micro-pitch template panel |
| `?view=wall` | Wall-only view (hides submit form) |

Modes can be combined: `?facilitator=true&projector=true`

---

## Workshop Flow (60 minutes)

### Structure: IDEO Human-Centered Design

| Phase | Time | Activity | Slides |
|-------|------|----------|--------|
| **OPENING** | 0-5 min | Title, Hook, HCD video (Vimeo) | 1-3 |
| **INSPIRATION** | 5-20 min | Design Justice, Power Check, Micro-Interviews, User Statement | 4-8 |
| **IDEATION** | 20-45 min | Choose Quest, Submit to Idea Wall, Prototype (15 min), AI Guardrails | 9-13 |
| **IMPLEMENTATION** | 45-60 min | Pitch to get partnerships, Gallery Walk + Dots, Micro-Pitches, Closing | 14-16 |

**Inspiration** = Listen, observe, empathize. Students write/draw ideas as they watch the IDEO video and discuss.
**Ideation** = Generate ideas, build prototypes. Firebase Idea Wall explained as real-world prototyping tool.
**Implementation** = Pitch your idea to get partnerships and get it into the world.

### Gallery Walk Dot Colors
- **Gold** = "I'd download this"
- **Blue** = "Smartest AI use"
- **Green** = "Most responsible design"

### Micro-Pitch Template (30-45 seconds)
1. "The problem at our school is..."
2. "My app is for..."
3. "It helps by..."
4. "The AI part is smart because..."
5. "We designed it responsibly by..."
6. "Next step: we need feedback from..."

### Choose Your Quest Tracks
| Track | Tool | What Students Create |
|-------|------|---------------------|
| Music | Suno AI | Original song or jingle for their app |
| Memes & Graphics | Media.io | AI-powered visuals and memes |
| Video | Google Gemini | Video prototype or commercial |

---

## Firebase Configuration

Firebase config is embedded in `public/index.html`. The API key is a **client-side identifier** (not a secret) — security is enforced by Firestore rules, not by hiding this key. See [Firebase docs on API key security](https://firebase.google.com/docs/projects/api-keys).

### Firestore Security Rules
- **Read:** Anyone can read ideas
- **Create/Update:** Anyone can submit and upvote
- **Delete:** Blocked (except via facilitator clear wall, which uses admin-level batch delete)

### Firestore Collection: `ideas`
| Field | Type | Description |
|-------|------|-------------|
| name | string | Student's first name/nickname |
| appName | string | Name of their app idea |
| category | string | homework, clubs, mental-health, language, school-spirit, other |
| userFor | string | "My app is for ___" |
| userStruggle | string | "who struggle with ___" |
| userSo | string | "so they can ___" |
| aiFeature | string | Optional AI feature description |
| fires | number | Upvote count |
| createdAt | timestamp | Server timestamp |

---

## Deployment

### Prerequisites
- Node.js installed
- `npm install -g firebase-tools`
- `firebase login` (with an Owner account listed above)

### Deploy
```bash
cd caaasa-idea-wall
firebase deploy
```

This deploys both hosting (the web app) and Firestore security rules.

### Between Workshop Sessions
Use facilitator mode (`?facilitator=true`) and click **"Clear All Ideas (Reset Wall)"** to wipe the board for the next group.

---

## Contact
- **TRPEC:** info@discoverycollective.com
- **Website:** modelitk12.com
