# 📚 StudyBuddy

A location-based social study app. Turn on your location only when you're *open to studying*, ping friends and classmates, and find study partners without the awkwardness.

---

## Core Features

| # | Feature | Status |
|---|---------|--------|
| 1 | **Friends** — add and manage study friends | 🔲 planned |
| 2 | **Study Mode** — location shares *only* while you're "open to studying" or "studying" | 🔲 planned |
| 3 | **Groups** — public (like a groupchat) or private (just for yourself) to invite people in one tap | 🔲 planned |
| 4 | **Classrooms** — join a class; studying for it turns on location for classmates and tags you | 🔲 planned |
| 5 | **Random Class Ping** — anonymously ping a classmate to study, keeping the nonchalant façade | 🔲 planned |

## Privacy First
Location is **off by default**. It only turns on when the user explicitly enters Study Mode, and is only visible to the scoped audience (friends, a group, or a classroom). See [`docs/PRIVACY.md`](docs/PRIVACY.md).

## Tech Stack
- **Mobile:** React Native + Expo (iOS & Android from one codebase)
- **Navigation:** React Navigation
- **Backend:** Python + FastAPI
- **DB:** PostgreSQL (+ PostGIS for geo) — swappable
- **Realtime:** WebSockets (presence + pings)
- **Auth:** JWT

## Getting Started
```bash
# Mobile app
npm install
npx expo start

# Backend
cd server
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --port 4000
```
Interactive API docs auto-generate at `http://localhost:4000/docs`.

See [`docs/SETUP.md`](docs/SETUP.md) for full setup.

## Repo Structure
```
src/          Mobile app (React Native)
  screens/    One file per screen (Map, Friends, Groups, Classrooms...)
  components/ Reusable UI
  services/   API + location + realtime clients
  context/    Auth & study-mode global state
server/       FastAPI backend
  app/
    main.py     App entry, router wiring, WebSocket endpoint
    core/       Config + JWT auth dependency
    routers/    One file per surface (auth, friends, groups...)
    models/     Pydantic schemas + SQL schema
docs/         Setup, privacy, architecture, roadmap
```

## Roadmap
See [`docs/ROADMAP.md`](docs/ROADMAP.md).

## License
MIT
