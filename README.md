# StreamXMap 🗺️🎥⚡

StreamXMap is a real-time, high-performance geospatial streaming platform that maps live broadcasters (YouTube & Twitch) onto an interactive global map. It features automated stream state detection, spatial database indexing, and over-the-air (OTA) mobile updates.

---

## 🛠️ Complete Technical Architecture & Tech Stack

### **1. Frontend Mobile Client (Flutter / Dart)**
* **Core Framework:** **Flutter SDK** (Dart) compiled for native Android performance.
* **Geospatial UI:** **`google_maps_flutter`** plugin for rendering vector maps, custom marker styling, and live camera movements.
* **Location Services:** **`geolocator`** package for high-accuracy GPS hardware polling and coordinate retrieval.
* **In-App Navigation & OTA:** **`url_launcher`** for opening external links and handling direct APK download intents.
* **Authentication Flow:** Custom deep-link URL scheme handler (`streamxmap://callback`) parsing incoming JWT payloads from OAuth redirects.
* **Version Control Client:** Static runtime configuration comparing local build versions against remote JSON metadata payloads.

### **2. Backend Server (Node.js & TypeScript)**
* **Runtime Environment:** **Node.js** executed with **TypeScript** for compile-time type safety.
* **Web Framework:** **Express.js** routing engine managing RESTful endpoints:
  * `POST /api/streams/golive` — Triggers automated YouTube checks and spatial coordinate updates.
  * `GET /api/version` — Serves current APK version metadata for OTA mobile checks.
* **Real-Time Communication:** **WebSockets** (or Socket-based architecture) for bidirectional, low-latency live location and stream state broadcasting across connected clients.
* **HTTP Client:** **Axios** managing external REST calls to Google/YouTube APIs with bearer token injection.
* **Security & Environment:** **Dotenv** for secure runtime secret management.

### **3. Database & Spatial Indexing (PostgreSQL & PostGIS)**
* **Relational Database:** **PostgreSQL** hosted on Render.
* **Geospatial Engine:** **PostGIS** extension utilizing native spatial types and functions:
  * `geography(POINT, 4326)` — Spatial column type utilizing WGS 84 latitude/longitude coordinates.
  * `ST_SetSRID()` & `ST_MakePoint()` — Geometrical constructor functions for precise coordinate wrapping.
* **Automated Migration Layer:** On-boot asynchronous `initDB()` schema validator executing conditional `CREATE TABLE IF NOT EXISTS` and `ALTER TABLE ADD COLUMN IF NOT EXISTS` queries for zero-downtime evolution.

### **4. Authentication & Security Layer**
* **Auth Middleware:** **Passport.js** authentication framework.
* **OAuth 2.0 Strategy:** **`passport-google-oauth20`** handling Google account consent screens and profile extraction.
* **Token Issuance:** **`jsonwebtoken` (JWT)** generating stateless 7-day session tokens (`jwt.sign` / verification middleware).
* **Token Persistence:** Secure database storage and refresh handling of Google OAuth Access and Refresh tokens.

### **5. External APIs & Third-Party Integrations**
* **YouTube Data API v3:**
  * **Search API (`/search`):** Queries user's active live broadcasts (`eventType='live'`) to catch standard and OBS-streamed events.
  * **Broadcasts API:** Fetches live stream IDs, video metadata, and titles.
* **Twitch API:** Stream state verification and channel metadata parsing.

### **6. Deployment & Distribution Infrastructure**
* **Cloud Hosting:** **Render** cloud platform with integrated auto-deploy CI/CD pipeline from GitHub.
* **Binary Distribution:** **GitHub Releases** acting as a dedicated artifact repository hosting compiled `app-release.apk` binaries.

---

## ✨ Core Features

* **Live Geospatial Pins:** Real-time markers pinned to exact GPS coordinates of active broadcasters.
* **Smart Go-Live Automation:** One-tap action that queries the YouTube API, extracts active stream metadata, and anchors it to the user's live position.
* **Instant OTA Updates:** Automatic startup version checking that prompts users with an in-app dialog to download fresh APK builds straight from GitHub Releases.

---

## 📲 Download & Installation

Grab the latest production-ready Android APK directly from the [GitHub Releases Page](https://github.com/PythonicPete/streamsXmap/releases/latest).

1. Download `app-release.apk`.
2. Tap to install on your Android device.
3. Sign in with Google and broadcast your stream live to the map!
