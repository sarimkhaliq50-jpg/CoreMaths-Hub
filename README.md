# CoreMaths Hub

A modern AQA Core Maths revision platform built for the 2026 May exams and future years.

## Features

* User authentication (login/register)
* Saved revision progress
* Interactive dashboard
* Embedded past papers and mark schemes
* Revision notes
* Flashcards
* Topic quizzes
* Mobile + desktop responsive
* Modern black & white UI
* Fast and scalable React architecture

---

# Tech Stack

* React
* Vite
* Tailwind CSS
* Firebase Authentication
* Firestore Database
* React Router
* Framer Motion

---

# Installation

## Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/coremaths-hub.git
cd coremaths-hub
```

---

# Install Dependencies

```bash
npm install
```

---

# Run Development Server

```bash
npm run dev
```

The app will run locally on:

```txt
http://localhost:5173
```

---

# Build For Production

```bash
npm run build
```

---

# Firebase Setup

1. Create a project on:

[Firebase](https://firebase.google.com?utm_source=chatgpt.com)

2. Enable:

* Authentication
* Firestore Database

3. Add your Firebase config to:

```txt
src/firebase/config.js
```

Example:

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

---

# Deployment

## Deploy With Vercel

1. Push project to GitHub
2. Open:

[Vercel](https://vercel.com?utm_source=chatgpt.com)

3. Import repository
4. Click Deploy

You will receive a live website URL.

---

# Folder Structure

```txt
src/
├── components/
├── pages/
├── firebase/
├── data/
├── App.jsx
├── main.jsx
└── index.css
```

---

# Included Sections

## Dashboard

* Exam countdown
* Revision tracking
* Daily goals
* Quick navigation

## Notes

* Finance
* Statistics
* Probability
* Risk
* Modelling
* Personal Finance

## Flashcards

* Interactive cards
* Topic filters
* Progress saving

## Quizzes

* Multiple choice
* Instant marking
* Score tracking

## Past Papers

* Embedded PDFs
* Mark schemes
* Examiner reports

---

# Future Features

* AI tutor
* Smart revision planner
* Weak-topic analysis
* XP and streak system
* Leaderboards
* Study timer

---

# Design

* Minimal black & white theme
* Glassmorphism cards
* Responsive layouts
* Smooth animations

---

# License

MIT License

---

# Author

CoreMaths Hub — built for AQA Core Maths students preparing for 2026 exams and beyond.
