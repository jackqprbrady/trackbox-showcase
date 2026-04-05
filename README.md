# TrackBox

**A music social platform. Log albums. Rate and review. Follow people. Build your music identity.**

Think Letterboxd, but for music.

**Live:** [trackbox-one.vercel.app](https://trackbox-one.vercel.app)

---

## What it is

TrackBox is a full-stack social platform built solo from scratch. Users log albums and songs, write reviews with half-star ratings, follow other listeners, build curated playlists, and browse a social feed of what people around them are listening to.

The core idea: your music taste is part of your identity. TrackBox gives it somewhere to live.

---

**[Try the live app](https://trackbox-one.vercel.app)** — runs on web, iOS, and Android.

---

## Tech stack

| Layer | Technology |
|-------|------------|
| Mobile/Web | React Native (Expo 54), Expo Router 6 |
| Language | TypeScript |
| State | TanStack Query 5, Zustand 5 |
| Forms | React Hook Form + Zod |
| Backend | Supabase (PostgreSQL 17, Row-Level Security, Edge Functions/Deno, Auth) |
| Music APIs | Spotify API (OAuth), Apple Music (MusicKit JS) |
| Deployment | Vercel (web), EAS (iOS + Android native) |
| Testing | Playwright (end-to-end) |

---

## Architecture

```
UI (React Native / Expo Router)
  └── React Query hooks
        └── Service layer (src/services/)
              └── Supabase SDK / Edge Functions (Deno)
                    └── PostgreSQL 17 with Row-Level Security
```

**Backend breakdown:**
- 19 Supabase Edge Functions (feed ranking, social graph, Spotify token refresh, etc.)
- 53+ production migrations
- Full RLS policies on every table
- Real-time-ready data model

**Key services:** feed, artist, catalog, social, profile, search, notifications, playlists, logging, reviews

---

## Features

- **Social feed** — Latest / For You / Radio modes, social activity from followed users
- **Logging** — Log albums and songs with timestamps and notes
- **Reviews** — Half-star ratings (0.5 to 5.0), written reviews, likes and comments
- **Profiles** — Music identity page, favorites 2x2 grid, follower/following counts
- **Playlists** — Curated lists of albums, songs, and live performances
- **Search** — Full-text search across artists, albums, songs, and users
- **Communities** — Artist-based community spaces
- **Onboarding** — Genre selection, artist seeding, Spotify OAuth connect
- **Notifications** — Likes, comments, follows, mentions

---

## Data model

```
profiles · artists · albums · songs · performances
logs · reviews · gigs · gig_reviews
follows · likes · comments · feed_events
lists · list_items · community_posts
artist_community_memberships · profile_favorites
notifications · user_settings · recent_searches
```

---

## Testing

19 Playwright end-to-end tests covering:
- Auth shell and session handling
- Core identity loop (log, rate, review)
- Onboarding flow
- Social interactions (follow, like, comment)
- Destructive actions (account deletion, log removal)
- Spotify degradation path

---

## Design system

Custom dark-mode design system built from scratch.

- Background: `#0C0B0F` / Text: `#F4F1EC`
- Gold ratings: `#F0B429` / Like red: `#E8355A`
- Typography: Space Grotesk (display), Plus Jakarta Sans (body/UI)
- Even-only spacing tokens, consistent border radius scale

---

## Status

Live and in active development. Web + iOS + Android (via EAS). App Store submission in progress.

Built solo. No team. No framework boilerplate beyond Expo.

---

*Source code is private. For enquiries: jack@jackbradyfilm.co.uk*
