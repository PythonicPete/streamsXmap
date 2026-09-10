StreamXMap 🗺️🎥
StreamXMap is a high-performance, real-time geospatial platform that bridges the gap between content creators and viewers. By combining interactive mapping with live stream monitoring, it allows users to discover active creators broadcasting live across YouTube and Twitch right on a live global map.

🛠️ The Tech Stack (Under the Hood)
Every component, library, and protocol powering the ecosystem:

Mobile Client (Flutter)
Framework: Flutter (Dart) for cross-platform mobile compilation.

Map Engine: Google Maps Flutter Plugin for real-time marker rendering and geospatial UI.

Navigation & Links: url_launcher for handling external redirects and APK updates.

App Architecture: Stateful widget lifecycle management, custom URL schemes (streamxmap://callback) for secure OAuth handoffs.

Versioning System: Client-side OTA version verification comparing local builds against remote payloads.

Backend Server (Node.js & TypeScript)
Runtime: Node.js powered by TypeScript for strict typing and scalable execution.

Framework: Express.js for handling high-frequency RESTful endpoints (/api/streams/golive, /api/version).

HTTP Client: Axios for robust external API communication with Google/YouTube services.

Environment Configuration: Dotenv for secure runtime secret management.

Database & Geospatial Engine
Primary Database: PostgreSQL relational database hosted on Render.

Geospatial Extension: PostGIS utilizing geography(POINT, 4326) data types, ST_SetSRID, and ST_MakePoint for precise coordinate indexing and spatial queries.

Automated Migration: Custom on-boot initDB() schema validation layer ensuring zero-downtime table and column evolution.

Authentication & Security
Auth Framework: Passport.js utilizing passport-google-oauth20 strategy.

Session Management: Stateless JSON Web Tokens (JWT) issued via jsonwebtoken for secure API authorization.

Token Lifecycle: Secure handling and database persistence of Google OAuth Access Tokens and Refresh Tokens.

External APIs & Integrations
YouTube Data API v3: Leveraged via both the Search API (to dynamically catch OBS and standard RTMP streams) and the Live Broadcasts API.

Twitch API Integration: Stream state verification and metadata extraction.

Deployment & Distribution
Backend Hosting: Render cloud platform with automated CI/CD pipeline.

App Distribution: GitHub Releases for direct APK hosting, version control, and seamless OTA updates.

✨ Core Features
Live Geospatial Pins: Creators broadcast their coordinates, placing a live-updating marker directly on the map.

Smart Go-Live Automation: One-tap detection automatically queries the YouTube API, extracts the active stream ID and title, and anchors it to the user's GPS coordinates.

In-App OTA Updates: Built-in update checker detects newer version tags on startup and prompts users to download fresh APK builds instantly.

📲 Download & Installation
Grab the latest production-ready Android APK directly from the GitHub Releases Page.

Download app-release.apk.

Tap to install on your Android device.

Sign in with Google and broadcast your stream to the map!
