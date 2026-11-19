# MF Chat (Make Friends Chat)

> **"Meet people. Make friends."**  
> Adults (18+) meeting new people, chatting privately, and connecting face to face through live WebRTC video.

---

## 🌟 Overview & Key Features

MF Chat is a responsive, privacy-first web application designed for adults aged 18 and over to find friends, message in real time, and connect face-to-face via WebRTC live video.

- **18+ Verification & Clean Onboarding**: Strict 18+ declaration during sign-up, age validation, display name, username, bio, and interest tags.
- **Discover with Privacy-Preserving Geolocation**:
  - Filter by Gender, Age range (18–99), Interests, and Distance (km).
  - **1 km Coordinate Rounding**: Locations are automatically rounded to ~1 km grids before storing. Users only see approximate distances like *"About 5 km away"*, never exact coordinates.
  - Online presence toggle (*"Show other people when I am online"*).
- **Private Messaging & Auto-Resized Photos**:
  - Instant 1-on-1 chats.
  - Snap photos with device camera/webcam or pick from device files/gallery.
  - Client-side auto-downscaling/compression ensures quick image transfers on any connection.
- **Live WebRTC Video Calling**:
  - **Direct Calls**: Call anyone from their profile or chat with an incoming call ringing dialog (Accept/Decline).
  - **Random Video Matching**: One-tap matching with another active adult, featuring instant **Next** skip controls.
  - **Call Saved People**: Call your bookmarked friends directly from the Video Hub.
  - **In-Call Controls**: Mute microphone, camera on/off, camera flipping (mobile front/back), report, block, and end call.
  - Echo cancellation, noise suppression, and auto gain control enabled by default.
- **Safety, Respect & Moderation**:
  - **One-tap Block**: Immediately removes users from Discover, messages, and video matching.
  - **Moderation Reports**: Categorized reporting (harassment, underage, scam, inappropriate content) routed to administration.
  - **Kenya Emergency numbers** (999 & 112) and admin contact (`kelvinkirui1528@gmail.com`).

---

## 🚀 Quick Start

### Option A: Instant Zero-Install Preview
You can test the full user experience right away without running any terminal commands:
1. Open [`standalone-preview.html`](file:///c:/Users/hp/Documents/project%20kkk/standalone-preview.html) directly in any web browser (Google Chrome, Microsoft Edge, Safari, Firefox).
2. Explore Discover filters, messaging, live WebRTC camera/audio calls, and random video matching!

---

### Option B: Running the Vite React Application

1. Open your terminal in this project directory:
   ```bash
   cd "c:\Users\hp\Documents\project kkk"
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the local development server:
   ```bash
   npm run dev
   ```

4. Open the displayed URL in your browser (usually `http://localhost:5173`).

---

## 🗄️ Supabase Backend Setup

MF Chat is built to work seamlessly with **Supabase** for database, authentication, realtime messaging, and storage.

1. Create a free project at [supabase.com](https://supabase.com).
2. Open the **SQL Editor** in your Supabase dashboard.
3. Copy and run the entire contents of [`supabase/schema.sql`](file:///c:/Users/hp/Documents/project%20kkk/supabase/schema.sql).
   * This creates all tables (`profiles`, `messages`, `saved_users`, `blocks`, `reports`, `random_queue`), RLS policies, helper functions (Haversine distance calculation), and user triggers.
4. Create two storage buckets in the Supabase Storage dashboard:
   * `avatars` (Public bucket)
   * `chat_media` (Public bucket)
5. Rename `.env.example` to `.env` and fill in your project credentials:
   ```env
   VITE_SUPABASE_URL=https://your-project-id.supabase.co
   VITE_SUPABASE_ANON_KEY=your-anon-public-key-here
   ```

*(Note: If no Supabase credentials are configured, the app runs in interactive demo/preview mode with realistic mock Kenyan/international profiles and simulated messaging).*

---

## 📁 Project Structure

```
project kkk/
├── index.html                   # Vite HTML entry point
├── standalone-preview.html      # Zero-install single-file browser runner
├── package.json                 # Dependencies and build scripts
├── vite.config.ts               # Vite configuration
├── tailwind.config.js           # Tailwind color scheme & typography
├── tsconfig.json                # TypeScript compiler config
├── supabase/
│   └── schema.sql               # Full PostgreSQL tables, RLS & functions
└── src/
    ├── types/                   # TypeScript interfaces (UserProfile, Chat, WebRTC)
    ├── services/
    │   ├── supabase.ts          # Supabase client & local mock storage fallback
    │   ├── webrtc.ts            # WebRTC peer connection, STUN servers & media
    │   ├── mockData.ts          # Realistic initial profiles & interest tags
    │   └── imageUtils.ts        # Client-side photo resizing & Haversine distance
    ├── context/
    │   └── AuthContext.tsx      # Auth state, call state, block/save management
    ├── components/
    │   ├── Navbar.tsx           # Responsive desktop top bar & mobile tab bar
    │   ├── DiscoverView.tsx     # Filterable member discovery & distance cards
    │   ├── ChatView.tsx         # Real-time messaging with webcam/gallery photos
    │   ├── VideoHubView.tsx     # Random matching & saved people calling hub
    │   ├── RandomVideoChat.tsx  # Omegle-style 1-on-1 video with "Next" button
    │   ├── VideoCallModal.tsx   # Direct WebRTC call screen with PiP & controls
    │   ├── IncomingCallModal.tsx# Incoming call ring dialog with Accept/Decline
    │   ├── PhotoCaptureModal.tsx# Webcam snapshot & file compressor
    │   ├── SavedView.tsx        # Bookmarked contacts with instant call/chat
    │   ├── AccountView.tsx      # Profile editing, privacy toggles & unblock list
    │   ├── SafetyView.tsx       # Safety guidelines, 18+ rules & emergency contacts
    │   ├── ReportModal.tsx      # Moderation report submission dialog
    │   └── AuthModal.tsx        # 18+ Sign in & registration modal
    ├── App.tsx                  # Root application coordinator
    ├── main.tsx                 # React DOM mount point
    └── index.css                # Global styles & Tailwind layers
```

---

## 🛡️ Safety & Contact

- **Strict 18+ Policy**: All users must self-declare adulthood upon registration.
- **Kenyan Emergency Contacts**: Police & Emergency: **999** or **112**.
- **Administrator Email**: For questions, moderation reports, or account deletion requests:
  **`kelvinkirui1528@gmail.com`**
