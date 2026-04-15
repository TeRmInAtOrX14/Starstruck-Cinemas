<p align="center">
  <img src="webapp/assets/icon.png" alt="Starstruck Cinemas Logo" width="120" />
</p>

<h1 align="center">🎬 Starstruck Cinemas</h1>

<p align="center">
  <strong>An AI-Enhanced Multi-Cinema Theater Management Platform</strong>
  <br />
  Built with Next.js, Supabase, and custom algorithmic engines
</p>

<p align="center">
  <img alt="Next.js" src="https://img.shields.io/badge/Next.js-15-black?logo=next.js" />
  <img alt="Supabase" src="https://img.shields.io/badge/Supabase-PostgreSQL-3FCF8E?logo=supabase" />
  <img alt="React" src="https://img.shields.io/badge/React-18-61DAFB?logo=react" />
  <img alt="License" src="https://img.shields.io/badge/License-MIT-blue" />
</p>

---

## 📖 Overview

Starstruck Cinemas is a full-stack cinema management web application that manages 5 cinema locations across New York City. It features an algorithmic AI chatbot, dynamic surge pricing, BFS-powered seat grouping, a tiered seat pricing model, a user reward system, and downloadable PDF tickets with QR codes.

> **Live Demo:** _Deploy on Vercel and add your URL here_

---

## ✨ Features

### 🎥 Multi-Cinema Management
- **5 Cinema Locations** — Central (NY), Luxe (LA), IMAX (Queens), Hub (Brooklyn), North (Bronx)
- Browse movies filtered by cinema location
- Genre-based mood filtering (Action, Sci-Fi, Comedy, Drama)

### 🤖 AI-Powered Chatbot
- **NLP Tokenizer** with stopword removal for natural language understanding
- **Entity Scoring Algorithm** — O(N × T) complexity matching for movie name, genre, and location
- **Intent Detection Engine** — recognizes review, pricing, timing, and greeting intents
- Users can submit movie reviews directly through the chatbot, which are saved to the database

### 💰 Dynamic Surge Pricing
- Algorithmic price surge (+Rs. 300) when a movie exceeds **70% seat capacity**
- Real-time "High Demand 📈" badge on affected movies

### 🪑 Interactive Seat Selection
- **8×8 Visual Seat Map** with three pricing tiers:
  - 🟡 **VIP** (Rows A–B) → +Rs. 500
  - 🔵 **Regular** (Rows C–F) → Base price
  - 🟢 **Economy** (Rows G–H) → -Rs. 200
- 🔴 Already-booked seats are locked in real-time
- **BFS Auto-Group** — Radial Breadth-First Search algorithm finds the best grouped seats closest to center-screen

### 🎟️ PDF Ticket Generation
- Professional ticket with movie details, seat assignments, and total price
- **QR Code** generated dynamically for each booking
- Download as PDF via `html2pdf.js`
- Native share support on Android via Capacitor

### 👤 User System
- Email/password signup and login
- **Reward Points** — Earn 10% of ticket price as loyalty points on every booking
- Personalized "Because You Watched" recommendations based on booking history

### 🔐 Admin Panel
- Secure admin login (default: `admin` / `admin123`)
- Add new movies with poster URL, genre, showtime, and cinema assignment
- View all movies with booking counts in a dashboard table

### 💡 AI Review Summarization
- Algorithmic keyword extraction from all user reviews
- Generates consensus summaries displayed on each movie card (e.g., _"Audiences praise stunning visuals and great action, but note slow pacing"_)

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, Next.js 15 |
| **Backend** | Next.js API Routes (Serverless) |
| **Database** | Supabase (PostgreSQL) |
| **Styling** | Custom CSS with glassmorphism, gradients, dark theme |
| **PDF Export** | html2pdf.js |
| **Mobile Bridge** | Capacitor (Android APK support) |
| **QR Codes** | QR Server API |

---

## 📂 Project Structure

```
Starstruck-Cinemas/
├── webapp/
│   ├── src/
│   │   ├── app/
│   │   │   ├── page.js              # Main movie listing + booking flow
│   │   │   ├── layout.js            # Root layout with metadata
│   │   │   ├── globals.css           # Design system + dark theme
│   │   │   ├── admin/page.js         # Admin control panel
│   │   │   ├── login/page.js         # User login page
│   │   │   ├── signup/page.js        # User signup page
│   │   │   └── api/
│   │   │       ├── movies/route.js   # GET all movies, POST new movie
│   │   │       ├── book/route.js     # POST seat booking
│   │   │       ├── auth/route.js     # POST admin authentication
│   │   │       ├── user/auth/route.js # POST user signup/login
│   │   │       └── ai-recommend/route.js # POST AI chatbot
│   │   └── lib/
│   │       └── db.js                 # Supabase client singleton
│   ├── public/                       # Static assets
│   ├── assets/                       # App icons
│   ├── android/                      # Capacitor Android project
│   ├── supabase_setup.sql            # One-time DB setup script
│   ├── .env.local                    # Supabase credentials (gitignored)
│   ├── package.json
│   └── next.config.mjs
├── presentation.html                 # Project presentation slides
├── Presentation_Script.md            # Presentation talking points
├── Starstruck-Cinemas-Technical-Report.md
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** 18+
- A **Supabase** project ([supabase.com](https://supabase.com))

### 1. Clone the Repository

```bash
git clone https://github.com/TeRmInAtOrX14/Starstruck-Cinemas.git
cd Starstruck-Cinemas/webapp
```

### 2. Set Up Supabase

1. Create a new project at [supabase.com](https://supabase.com)
2. Go to **SQL Editor → New Query**
3. Paste the contents of `webapp/supabase_setup.sql` and click **Run**
4. This creates all tables and seeds movies, reviews, cinemas, and the admin account

### 3. Configure Environment Variables

Create `webapp/.env.local`:

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project-id.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key_here
```

Find these values in **Supabase → Settings → API**.

### 4. Install & Run

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## ☁️ Deployment (Vercel)

1. Push the repo to GitHub
2. Go to [vercel.com](https://vercel.com) → **Add New Project** → Import your repo
3. Set **Root Directory** to `webapp`
4. Add environment variables:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`
5. Click **Deploy** 🚀

---

## 🔑 Default Credentials

| Role | Username/Email | Password |
|---|---|---|
| Admin | `admin` | `admin123` |

---

## 🧠 Algorithms Used

| Algorithm | Purpose | Complexity |
|---|---|---|
| **BFS (Breadth-First Search)** | Radial seat grouping from screen center | O(R × C) |
| **Entity Scoring** | NLP movie matching from user prompts | O(N × T) |
| **Surge Pricing** | Dynamic pricing at >70% capacity | O(1) per movie |
| **Keyword Extraction** | Review summarization via pattern matching | O(R × K) |
| **Personalized Sort** | "Because You Watched" genre-based reordering | O(N log N) |

---

## 📱 Mobile (Android)

The app includes a Capacitor project in `webapp/android/` for building a native Android APK. PDF tickets use native file system and share APIs on mobile.

---

## 👥 Contributors

- **TeRmInAtOrX14** — Lead Developer

---

## 📄 License

This project is licensed under the MIT License.
