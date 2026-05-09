# CoreMaths Hub — Full Website Blueprint

## Tech Stack

* React + Vite
* Tailwind CSS
* Firebase Authentication
* Firestore Database
* Framer Motion
* React Router

---

# Features Included

## Dashboard Homepage

* Welcome section
* Exam countdown (May 2026)
* Revision progress tracker
* Recently viewed topics
* Quick access cards
* Daily revision goals

## Authentication

* Sign up
* Login
* Logout
* Password reset
* Saved progress per account

## Revision Notes

Topics:

* Finance
* Statistics
* Critical Analysis
* Fermi Estimation
* Graphs & Modelling
* Risk
* Probability
* Spreadsheets
* Personal Finance

Each topic contains:

* Summary notes
* Key formulas
* Worked examples
* Practice questions

## Flashcards

* Interactive flip cards
* Saved mastery progress
* Topic filtering
* Smart revision mode

## Quizzes

* Multiple choice
* Timed quizzes
* Instant marking
* Leaderboard system
* Topic-based quizzes

## Past Papers

Embedded PDFs:

* 2020
* 2021
* 2022
* 2023
* 2024
* 2025
* Specimen papers

Includes:

* Question papers
* Mark schemes
* Examiner reports

## Mobile Responsive

* Fully responsive navigation
* Touch-friendly design
* Dark modern UI
* Fast loading

---

# Folder Structure

```txt
coremaths-hub/
├── public/
│   ├── papers/
│   ├── markschemes/
│   └── icons/
│
├── src/
│   ├── components/
│   │   ├── Navbar.jsx
│   │   ├── Sidebar.jsx
│   │   ├── Flashcard.jsx
│   │   ├── QuizCard.jsx
│   │   ├── ProgressChart.jsx
│   │   └── Countdown.jsx
│   │
│   ├── pages/
│   │   ├── Home.jsx
│   │   ├── Dashboard.jsx
│   │   ├── Notes.jsx
│   │   ├── Flashcards.jsx
│   │   ├── Quizzes.jsx
│   │   ├── PastPapers.jsx
│   │   ├── Login.jsx
│   │   └── Register.jsx
│   │
│   ├── firebase/
│   │   └── config.js
│   │
│   ├── data/
│   │   ├── flashcards.js
│   │   ├── quizzes.js
│   │   └── notes.js
│   │
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
│
├── tailwind.config.js
├── package.json
└── vite.config.js
```

---

# Installation

## Create Project

```bash
npm create vite@latest coremaths-hub
cd coremaths-hub
```

## Install Dependencies

```bash
npm install react-router-dom firebase framer-motion react-icons recharts
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

---

# Tailwind Setup

## tailwind.config.js

```js
export default {
  content: [
    './index.html',
    './src/**/*.{js,ts,jsx,tsx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

## src/index.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  background: #000;
  color: white;
  font-family: Inter, sans-serif;
}
```

---

# Firebase Authentication Setup

## firebase/config.js

```js
import { initializeApp } from 'firebase/app';
import { getAuth } from 'firebase/auth';
import { getFirestore } from 'firebase/firestore';

const firebaseConfig = {
  apiKey: 'YOUR_API_KEY',
  authDomain: 'YOUR_AUTH_DOMAIN',
  projectId: 'YOUR_PROJECT_ID',
  storageBucket: 'YOUR_STORAGE_BUCKET',
  messagingSenderId: 'YOUR_SENDER_ID',
  appId: 'YOUR_APP_ID'
};

const app = initializeApp(firebaseConfig);

export const auth = getAuth(app);
export const db = getFirestore(app);
```

---

# Main App.jsx

```jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Dashboard from './pages/Dashboard';
import Notes from './pages/Notes';
import Flashcards from './pages/Flashcards';
import Quizzes from './pages/Quizzes';
import PastPapers from './pages/PastPapers';
import Login from './pages/Login';
import Register from './pages/Register';
import Navbar from './components/Navbar';

function App() {
  return (
    <BrowserRouter>
      <div className='min-h-screen bg-black text-white'>
        <Navbar />

        <Routes>
          <Route path='/' element={<Dashboard />} />
          <Route path='/notes' element={<Notes />} />
          <Route path='/flashcards' element={<Flashcards />} />
          <Route path='/quizzes' element={<Quizzes />} />
          <Route path='/pastpapers' element={<PastPapers />} />
          <Route path='/login' element={<Login />} />
          <Route path='/register' element={<Register />} />
        </Routes>
      </div>
    </BrowserRouter>
  );
}

export default App;
```

---

# Modern Navbar

```jsx
import { Link } from 'react-router-dom';

export default function Navbar() {
  return (
    <nav className='border-b border-gray-800 p-4 flex justify-between items-center'>
      <h1 className='text-2xl font-bold'>CoreMaths Hub</h1>

      <div className='flex gap-6'>
        <Link to='/'>Dashboard</Link>
        <Link to='/notes'>Notes</Link>
        <Link to='/flashcards'>Flashcards</Link>
        <Link to='/quizzes'>Quizzes</Link>
        <Link to='/pastpapers'>Past Papers</Link>
      </div>
    </nav>
  );
}
```

---

# Dashboard Page

```jsx
import Countdown from '../components/Countdown';

export default function Dashboard() {
  return (
    <div className='p-8'>
      <h1 className='text-5xl font-bold mb-6'>Welcome Back</h1>

      <div className='grid md:grid-cols-3 gap-6'>
        <div className='bg-zinc-900 rounded-3xl p-6'>
          <h2 className='text-2xl mb-2'>Exam Countdown</h2>
          <Countdown />
        </div>

        <div className='bg-zinc-900 rounded-3xl p-6'>
          <h2 className='text-2xl mb-2'>Revision Progress</h2>
          <p>67% Complete</p>
        </div>

        <div className='bg-zinc-900 rounded-3xl p-6'>
          <h2 className='text-2xl mb-2'>Daily Goal</h2>
          <p>2 Topics + 1 Quiz</p>
        </div>
      </div>
    </div>
  );
}
```

---

# Countdown Component

```jsx
import { useEffect, useState } from 'react';

export default function Countdown() {
  const calculate = () => {
    const examDate = new Date('2026-05-01');
    const now = new Date();
    const diff = examDate - now;

    const days = Math.floor(diff / (1000 * 60 * 60 * 24));

    return days;
  };

  const [days, setDays] = useState(calculate());

  useEffect(() => {
    const timer = setInterval(() => {
      setDays(calculate());
    }, 1000);

    return () => clearInterval(timer);
  }, []);

  return <h1 className='text-5xl font-bold'>{days} Days</h1>;
}
```

---

# Flashcards Page

```jsx
import { useState } from 'react';

const cards = [
  {
    question: 'What is probability?',
    answer: 'Likelihood of an event occurring'
  },
  {
    question: 'Mean formula?',
    answer: 'Total ÷ Frequency'
  }
];

export default function Flashcards() {
  const [flipped, setFlipped] = useState(null);

  return (
    <div className='p-8 grid md:grid-cols-2 gap-6'>
      {cards.map((card, index) => (
        <div
          key={index}
          onClick={() => setFlipped(index)}
          className='bg-zinc-900 p-8 rounded-3xl cursor-pointer min-h-[200px] flex items-center justify-center text-center text-2xl'
        >
          {flipped === index ? card.answer : card.question}
        </div>
      ))}
    </div>
  );
}
```

---

# Quiz Page

```jsx
import { useState } from 'react';

export default function Quizzes() {
  const [score, setScore] = useState(0);

  const question = {
    text: 'What is 10% of 200?',
    answers: ['10', '20', '30'],
    correct: '20'
  };

  const handleAnswer = answer => {
    if (answer === question.correct) {
      setScore(score + 1);
    }
  };

  return (
    <div className='p-8'>
      <h1 className='text-4xl mb-6'>Quiz</h1>

      <div className='bg-zinc-900 p-8 rounded-3xl'>
        <h2 className='text-2xl mb-4'>{question.text}</h2>

        <div className='flex flex-col gap-4'>
          {question.answers.map(answer => (
            <button
              key={answer}
              onClick={() => handleAnswer(answer)}
              className='bg-white text-black p-4 rounded-2xl'
            >
              {answer}
            </button>
          ))}
        </div>

        <p className='mt-6'>Score: {score}</p>
      </div>
    </div>
  );
}
```

---

# Embedded Past Papers

```jsx
export default function PastPapers() {
  return (
    <div className='p-8'>
      <h1 className='text-4xl mb-8'>Past Papers</h1>

      <div className='grid gap-8'>
        <div>
          <h2 className='text-2xl mb-4'>2025 Paper</h2>

          <iframe
            src='/papers/2025-paper.pdf'
            className='w-full h-[700px] rounded-3xl'
          />
        </div>

        <div>
          <h2 className='text-2xl mb-4'>2025 Mark Scheme</h2>

          <iframe
            src='/markschemes/2025-ms.pdf'
            className='w-full h-[700px] rounded-3xl'
          />
        </div>
      </div>
    </div>
  );
}
```

---

# Login Page

```jsx
import { useState } from 'react';
import { signInWithEmailAndPassword } from 'firebase/auth';
import { auth } from '../firebase/config';

export default function Login() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const login = async () => {
    await signInWithEmailAndPassword(auth, email, password);
  };

  return (
    <div className='flex justify-center items-center min-h-screen'>
      <div className='bg-zinc-900 p-8 rounded-3xl w-[400px]'>
        <h1 className='text-4xl mb-6'>Login</h1>

        <input
          type='email'
          placeholder='Email'
          className='w-full p-4 rounded-xl bg-black mb-4'
          onChange={e => setEmail(e.target.value)}
        />

        <input
          type='password'
          placeholder='Password'
          className='w-full p-4 rounded-xl bg-black mb-4'
          onChange={e => setPassword(e.target.value)}
        />

        <button
          onClick={login}
          className='bg-white text-black w-full p-4 rounded-xl'
        >
          Login
        </button>
      </div>
    </div>
  );
}
```

---

# Future Features

## AI Features

* AI tutor chatbot
* Automatic quiz generation
* Weak-topic detection
* Smart revision planner

## Gamification

* XP system
* Revision streaks
* Achievements
* Leaderboards

## Productivity

* Pomodoro timer
* Study planner
* Revision calendar
* Task manager

---

# Deployment

## Upload to GitHub

```bash
git init
git add .
git commit -m "CoreMaths Hub"
```

## Deploy Free

### Vercel

1. Upload project to GitHub
2. Open Vercel
3. Import repository
4. Deploy
5. Receive live website link

Official website:
[https://vercel.com](https://vercel.com)

---

# Recommended Design Style

## Colours

* Black: #000000
* Dark Gray: #111111
* White: #FFFFFF
* Light Gray: #999999

## Fonts

* Inter
* Poppins

## Design Style

* Rounded corners
* Large spacing
* Glassmorphism cards
* Smooth animations
* Minimalist UI

---

# Final Result

CoreMaths Hub will look similar to a premium modern learning platform with:

* Sleek dashboard
* Fast navigation
* Smooth animations
* Fully responsive layout
* Secure authentication
* Saved progress tracking
* Embedded papers
* Interactive learning tools

This structure is fully scalable and ready for future AQA Core Maths exam years.
