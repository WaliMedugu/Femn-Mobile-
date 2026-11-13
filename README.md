<p align="center">
  <img src="assets/femnlogotxt.png" alt="Femn" width="220">
</p>

<h1 align="center">Femn</h1>

<p align="center">
  <strong>Empowering women and marginalised communities</strong><br>
  A Flutter + Firebase mobile app for community, safety, wellbeing and activism.
</p>

<p align="center">
  <img src="public/app.jpg" alt="Femn home feed" width="280">
</p>

---

## Overview

Femn is a holistic digital ecosystem designed to **support, educate, connect and empower women and marginalised communities**. It brings community support, safety tools, educational resources and activist channels together, linking digital connection with real-world safety and collective impact.

Femn is more than a social app. It is a **multifaceted platform** for personal growth, safety, expression and activism in one user-centred environment.

> **Project status:** Femn is in active development. Each feature below is labelled from the current code:
> **Built** = working in the app · **In progress** = partly implemented · **Planned** = on the roadmap, not yet implemented.

---

## Features

### Community & Connection Hub
The heart of Femn, focused on fostering deep, supportive relationships.

| Feature | Status | Notes |
|---|---|---|
| **Spark Groups** (temporary discussions) | Built | Discussions are created as temporary groups and expire after 7 days (the original target was 24–72h). |
| **Permanent Circles** | Built | Long-term groups with group chat, typing indicators, age ratings, hashtags and a profanity-filter setting. Invite-only private groups are *planned*. |
| **Support Ecosystem** | In progress | Therapist discovery, session booking, a therapist dashboard (accept/complete sessions), ratings and therapist reporting are built. Sign-up includes support roles (Certified Therapist, Psych Student, Peer Listener, Volunteer). Moderated group therapy is *planned*. |
| **Direct messaging & Stories** | Built | One-to-one chats and stories. |
| **Polls** | Built | Create and vote on community polls. |
| **Buddy System** | Planned | Opt-in safety buddies for commutes, events or difficult moments. |
| **Anonymous Mode** | Planned | Toggle identity for sensitive sharing within support circles. |

### Safety & Wellbeing Toolkit
Practical tools for physical, mental and emotional security.

| Feature | Status | Notes |
|---|---|---|
| **LeakGuard** (anti-sextortion toolkit) | Built | Negotiation playbook, decoy "pending payment" receipt generator, Evidence Locker (biometric-locked, stored in private app storage), Social Airlock privacy guides, cease-and-desist PDF generator, and deepfake-defence statements. |
| **Health Tracker** | In progress | Period/cycle tracker with symptoms, calendar and charts; activity tracker; journal with mood filters, voice notes and streaks. On-device encryption is *planned*. |
| **Customisable wellness dashboard** | Built | Add, remove and resize wellness widgets; the layout is saved to the user's account. |
| **Community Safety Maps** | Planned | Crowd-sourced heatmap to pin and rate locations by safety and inclusivity (dashboard tile exists, feature not yet built). |
| **Proactive Safety (check-in timer)** | Planned | Timer that alerts buddies if not deactivated on arrival (dashboard tile only). |
| **Self-Defense Academy** | Planned | Video lessons on verbal de-escalation and physical self-defence (dashboard tile only). |

### Expression & Identity Corner
A creative space for identity, art and activism.

| Feature | Status | Notes |
|---|---|---|
| **The Stream** | Built | Visual-first, Pinterest-style masonry feed with *For You* and *Following* tabs, image/video posts and text-to-image posts. The *News* tab is under development. |
| **AI-assisted feed** | Built | New posts are analysed with Gemini 2.5 Flash (Firebase Vertex AI) for a safety check and content tags, which feed a personalised ranking. |
| **Twin Finder** | Built | A personality quiz that assigns one of 16 personality types and saves it to the profile. |
| **Inclusive Profiles** | In progress | Profile editing is built; pronouns, gender identity, cultural background and zodiac fields are *planned*. |
| **Mood Boards** | Planned | Personal and collaborative digital canvases. |

### Knowledge & Growth Academy
Education, skill-building and long-term growth.

| Feature | Status | Notes |
|---|---|---|
| **Daily quotes** | Built | Daily quote, also available as an Android home-screen widget. |
| **Feminist Library** | Planned | Curated social justice literature and theory (dashboard tile only). |
| **femn Academy** | Planned | Micro-courses on financial literacy, reproductive rights and digital safety. |
| **Career Mentorship** | Planned | Shown in the app as "coming in a future update". |

### Activism & Impact Platform
Turning awareness into real-world change.

| Feature | Status | Notes |
|---|---|---|
| **Petition Engine** | Built | Draft and launch petitions, collect signatures against a goal, and manage them from a petitions dashboard. |
| **Petition home-screen widget** | Built | Android widget showing a petition's title and live signature progress. |
| **Campaign Tracker** | In progress | Live signature progress is built; fundraising metrics are *planned*. |
| **Events** | Built | Create and view community events. |
| **Volunteer Matchmaking** | Planned | Match with NGOs and activist groups by skills and location. |

### Economy & Engagement
A non-monetary, gamified reward system.

| Feature | Status | Notes |
|---|---|---|
| **Embers** | In progress | In-app balance stored on each account and spent to post stories. Ways to earn are not built yet. |
| **Pinks** | Planned | Earn by hosting skill-sharing circles, contributing to safety maps or completing mentorship cycles; spend on profile themes, petition boosts and early features. |

### Platform
- Push notifications (Firebase Cloud Messaging + local notifications)
- Deep links to posts (`/post/:postId`) via Android App Links and a Firebase Hosting fallback page
- Post analytics dashboard with charts
- Settings: privacy, security, notifications, accessibility, account deletion and a JSON data export
- Firebase App Check

---

## Tech stack

| Layer | Technology |
|---|---|
| App | Flutter (Dart SDK ^3.8.1), Provider |
| Backend | Firebase Authentication (email/password), Cloud Firestore, Firebase Storage |
| AI | Firebase Vertex AI (Gemini 2.5 Flash) |
| Notifications | Firebase Cloud Messaging, `flutter_local_notifications` |
| Security | Firebase App Check, `local_auth` (biometrics) |
| Media | `camera`, `image_picker`, `image_cropper`, `video_player`, `chewie`, `record`, `audioplayers` |
| Charts & docs | `fl_chart`, `table_calendar`, `pdf`, `printing` |
| Device | `home_widget` (Android home-screen widgets), `app_links` (deep links), `geolocator` |
| Web | Firebase Hosting (landing page, APK download page, App Links verification) |

## Project structure

```
lib/
├── main.dart, app.dart         App entry, Firebase init, navigation shell
├── auth/                       Sign-up / sign-in, account types
├── feed/                       Post creation, upload, AI analysis, personalised feed
├── hub_screens/                Feed/posts, profile, search, messaging, stories,
│                               notifications, settings, wellness dashboard
├── circle/                     Groups, discussions, polls, petitions, campaigns/events
├── wellness_widgets/           Period tracker, activity tracker, journal, Twin Finder,
│   └── leakguard/              Anti-sextortion toolkit
├── therapy/                    Therapist discovery, booking, therapist dashboard
├── analytics/                  Post analytics dashboard
├── services/                   Notifications, deep links, streaks, Embers, widgets
└── customization/              Theme, colours, fonts, layout
public/                         Firebase Hosting site (landing + download pages)
```

## Getting started

### Prerequisites
- Flutter SDK with Dart ^3.8.1
- A Firebase project with **Authentication (email/password)**, **Cloud Firestore**, **Storage**, **Cloud Messaging**, **App Check** and **Vertex AI in Firebase** enabled
- [FlutterFire CLI](https://firebase.google.com/docs/flutter/setup) (`dart pub global activate flutterfire_cli`)

### Installation

```bash
git clone https://github.com/WaliMedugu/Femn-Mobile-.git
cd Femn-Mobile-
flutter pub get

# Point the app at your own Firebase project
# (regenerates lib/firebase_options.dart and android/app/google-services.json)
flutterfire configure

flutter run
```

### Release builds (Android)
Release signing reads `android/key.properties` (`storeFile`, `storePassword`, `keyAlias`, `keyPassword`), which is not committed.

```bash
flutter build apk --release
```

### Website
The `public/` folder is a Firebase Hosting site (landing page, download page and `.well-known` files for App Links):

```bash
firebase deploy --only hosting
```

## Author

**Medugu Wali**, Blue Particle Studios

- GitHub: [github.com/WaliMedugu](https://github.com/WaliMedugu)
- LinkedIn: [linkedin.com/in/meduguwali](https://www.linkedin.com/in/meduguwali)
