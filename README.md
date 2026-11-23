# MediFlow — Hospital Digital Notes & Patient Care System

MediFlow is a local, mock-data hospital workflow demo built from the supplied Google Stitch screens. It uses no database, authentication service, API key, or paid integration.

## Run

```bash
npm install
npm run dev
```

Open http://localhost:5173. The Vite interface runs on port 5173 and the Express mock API runs on port 3001. All changes are persisted locally in `apps/mediflow/server/mock-data.json` after the first change.

## Test the demo

1. Select **Doctor** in the header, choose a patient, use Start recording (or type into the structured note), then Save draft or Submit & approve.
2. Select **Hospital Admin** to approve pending orders, or **Nurse** to record administered, missed, refused, or withheld doses and their notes.
3. Open **Records**, select a patient and date, then print the daily report. It reflects the local data immediately.
4. Select **Patient** to see the restricted mock patient view.

Voice recognition is browser-native (`SpeechRecognition` / `webkitSpeechRecognition`) and stays in the browser. If it is unavailable or microphone access is denied, the structured note fields remain the manual fallback. Browser language availability determines English/Hindi support.

## Safety

Demo records are fictional. Prescribed orders and actual administration are separate local records.

---

# Legacy Smart Crop Advisory System

Production-ready MVP scaffold for an AI-powered multilingual advisory platform serving farmers, agriculture officers, and admins.

## Stack

- Mobile: Expo React Native, Android-first responsive layout
- Web: Next.js 14 App Router with TypeScript
- Backend: Next.js API routes with Supabase-ready database contracts
- Database: PostgreSQL / Supabase schema and seed files
- Shared domain layer: reusable TypeScript types, translations, and sample data
- AI-ready architecture: advisory engine, pest detection adapter, and notification hooks

## Monorepo Structure

```text
apps/
  mobile/        Expo app for farmers
  web/           Responsive dashboard for farmer, officer, and admin workflows
packages/
  shared/        Types, sample data, translations, constants
supabase/
  schema.sql     PostgreSQL schema
  seed.sql       Dummy seed data
```

## Key MVP Capabilities

- Farmer onboarding with language preference, farm profile, and voice-first hints
- Personalized crop, fertilizer, and irrigation advisory cards
- Pest and disease detection upload flow with treatment suggestions
- Weather forecast, rainfall trend, and extreme alert widgets
- Market price tracking with nearby mandi recommendations
- Officer dashboard for farmer monitoring and advisory broadcast
- Admin dashboard for analytics and user management
- Offline-ready mobile architecture with sync queue placeholder
- Dark mode tokens, low bandwidth optimization notes, and push notification hooks

## UI Preview Summary

- Login: large segmented role entry and quick demo access
- Language Selection: five-card grid with native language labels
- Farmer Registration: large input panels with icon cues and voice action
- Farmer Dashboard: today's advisory, weather summary, alerts, prices, and voice button
- Advisory Screen: crop, fertilizer, irrigation, and explain-in-simple-language sections
- Pest Flow: upload image card, diagnosis panel, treatment plan, organic alternative
- Weather Screen: today card, seven-day strip, and alert banner
- Market Screen: mandi price table, trend chips, and best market recommendation
- Officer Dashboard: farmer overview cards, risk flags, and alert composer
- Admin Panel: KPI cards, adoption trend, language mix, and operational summary

## API Surface

- `GET /api/farmers`
- `POST /api/farmers`
- `GET /api/advisory/:farmerId`
- `GET /api/weather`
- `GET /api/market-prices`
- `POST /api/pest-detect`
- `POST /api/officer/broadcast`

## Local Setup

### 1. Install dependencies

```bash
npm install
```

### 2. Run the web dashboard

```bash
npm run dev:web
```

Open [http://localhost:3000](http://localhost:3000)

### 3. Run the mobile app

```bash
npm run dev:mobile
```

Use Expo Go on Android or an emulator.

## Supabase Setup

1. Create a Supabase project.
2. Run [`schema.sql`](/Users/kabeeraa/Documents/New project/supabase/schema.sql).
3. Run [`seed.sql`](/Users/kabeeraa/Documents/New project/supabase/seed.sql).
4. Replace mock repositories with live Supabase clients in `apps/web/src/lib/repositories` and `apps/mobile/src/services`.

## Production Hardening Checklist

- Add auth with Supabase Auth or Firebase Auth
- Replace mock weather and mandi feeds with live integrations
- Plug in CV model for pest detection and LLM-backed advisory explanation
- Add E2E tests, observability, rate limiting, and audit logs
- Configure Firebase Cloud Messaging or OneSignal for notifications
- Add encrypted local storage and conflict-aware offline sync
