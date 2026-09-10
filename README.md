<div align="center">

# 🌍 StreamXMap
**The Real-Time Geospatial Live Streaming Network**

[![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white)](https://flutter.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![YouTube API](https://img.shields.io/badge/YouTube_API-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://developers.google.com/youtube)

StreamXMap bridges the gap between the digital broadcast and the physical world. <br> Discover active YouTube and Twitch creators broadcasting live, mapped instantly to their real-world coordinates.

[**📥 Download Latest APK**](https://github.com/PythonicPete/streamsXmap/releases/latest) • [**Report Bug**](#) • [**Request Feature**](#)

</div>

<br/>

## 🎯 The Real-World Impact

**The Problem:** Traditional street performances, local flash mobs, and spontaneous public talents rely entirely on immediate foot traffic. A talented musician or street artist might be performing just two streets over, but unless people happen to walk right past them, they remain completely unaware that something amazing is happening right in their neighborhood.

**The Solution:** StreamXMap solves the local discovery gap. By opening the map, users can instantly scan a 2km radius to see if anyone is broadcasting a live event nearby. 

**Who Benefits Most?**
- 🎸 **Street Performers & Buskers:** Instantly broadcast your exact location to draw a larger, localized crowd. Turn digital viewers into a real-world audience walking over to tip and engage.
- 🚶 **Local Explorers:** Never miss out on neighborhood pop-up events, street shows, or live talents happening just around the corner.
- 🤝 **Community Builders:** Turn localized, spontaneous moments into highly engaging, well-attended real-world gatherings.

---

## ✨ The Vision

Traditional platforms bury live streams behind algorithms and endless scrolling. **StreamXMap** changes the paradigm by placing streams exactly where they are happening. Whether it's a walking tour in Tokyo or a street magician in Kolkata, you see the broadcast exactly where it originates.

### 🚀 Core Features
- **📍 Real-Time Spatial Mapping:** Watch live broadcasters pop up on a global, interactive vector map the second they go live.
- **⚡ Zero-Touch Go-Live:** One tap dynamically queries the YouTube API, extracts your active stream, and binds it to your GPS coordinates.
- **🔄 Invisible OTA Updates:** The app automatically cross-references version payloads on startup, delivering fresh APK updates via an elegant in-app dialog.
- **🛡️ Secure OAuth Handshake:** Frictionless Google sign-in using custom deep links (`streamxmap://callback`) for a seamless app-to-browser-to-app flow.

---

## 🏗️ Architecture & Tech Stack

<details>
<summary><b>📱 Client-Side: Mobile App (Flutter)</b></summary>
<br>

- **Framework:** `Flutter SDK` (Dart) compiled for native Android performance.
- **Geospatial UI:** `google_maps_flutter` for dynamic vector maps, custom marker rendering, and camera kinematics.
- **Hardware Integration:** `geolocator` for high-precision GPS polling.
- **Deep Linking:** Custom URL scheme parser handling stateless JWT handoffs from the backend.
- **OTA Engine:** `url_launcher` coupled with a REST check comparing local binaries against remote JSON metadata.
</details>

<details>
<summary><b>⚙️ Server-Side: Node.js Backend</b></summary>
<br>

- **Runtime:** `Node.js` + `TypeScript` for bulletproof, strongly-typed endpoints.
- **API Layer:** `Express.js` managing high-frequency REST routes (`/api/streams/golive`, `/api/version`).
- **Real-Time Sync:** WebSockets engine broadcasting spatial coordinate shifts to connected clients with sub-second latency.
- **External Communications:** `Axios` managing authenticated requests to Google/YouTube API v3.
</details>

<details>
<summary><b>🗄️ Database: PostGIS & Spatial Indexing</b></summary>
<br>

- **Core Engine:** `PostgreSQL` (Hosted on Render).
- **Spatial Extension:** `PostGIS` leveraging `geography(POINT, 4326)` for WGS 84 coordinate mapping.
- **Geometries:** Native `ST_SetSRID()` & `ST_MakePoint()` constructors for lightning-fast spatial queries.
- **Auto-Migrations:** Custom, asynchronous `initDB()` schema validator executing on-boot to ensure zero-downtime column evolution (`CREATE TABLE IF NOT EXISTS`).
</details>

<details>
<summary><b>🔐 Security & Authentication</b></summary>
<br>

- **Strategy:** `Passport.js` with `passport-google-oauth20`.
- **Session State:** Stateless `jsonwebtoken` (JWT) issuing 7-day cryptographically signed payloads.
- **Token Vault:** Secure PostgreSQL persistence for Google Access and Refresh tokens to enable background API queries.
</details>

---

## 📦 Installation & Usage

StreamXMap is distributed directly to users via GitHub Releases to ensure rapid deployment and bypass app store delays.

### 1. Install the App
1. Navigate to the **[Releases Page](https://github.com/PythonicPete/streamsXmap/releases/latest)**.
2. Download the `app-release.apk` asset.
3. Open the file on your Android device and tap **Install** *(Note: You may need to allow "Install from unknown sources" in your settings)*.

### 2. Broadcast to the Map
1. Launch the app and authenticate securely via Google.
2. Start your live stream on YouTube (via OBS, mobile, or desktop).
3. Tap **Go Live** in StreamXMap. The app will automatically detect your stream, grab your GPS location, and pin you to the global map for viewers to discover.

---
<div align="center">
  <i>Engineered with precision for the next generation of live streaming.</i>
</div>
