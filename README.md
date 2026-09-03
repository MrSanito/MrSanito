<div align="center"> 
  
<!-- Dynamic Header -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:00D9FF,100:0D1117&height=200&section=header&text=Hey,%20I'm%20mrsanito%20👋&fontSize=42&fontColor=ffffff&fontAlignY=38&desc=Full%20Stack%20Developer%20%7C%20Cloud%20Enthusiast%20%7C%20Open%20Source%20Lover&descAlignY=58&descSize=16&animation=fadeIn" />

<!-- Typing Animation -->
<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=3000&pause=1000&color=00D9FF&center=true&vCenter=true&multiline=false&width=600&height=50&lines=Building+the+web%2C+one+commit+at+a+time+%F0%9F%9A%80;React+%2B+Node+%2B+Cloud+%3D+My+Stack+%E2%9A%A1;Turning+coffee+into+scalable+apps+%E2%98%95;Always+learning%2C+always+shipping+%F0%9F%93%A6" alt="Typing SVG" />
 
<br/>

<!-- Profile Views & Followers -->
![Profile Views](https://komarev.com/ghpvc/?username=mrsanito&color=00d9ff&style=flat-square&label=Profile+Views)
[![GitHub followers](https://img.shields.io/github/followers/mrsanito?label=Followers&style=flat-square&color=00d9ff)](https://github.com/mrsanito?tab=followers)
[![GitHub Stars](https://img.shields.io/github/stars/mrsanito?label=Total%20Stars&style=flat-square&color=00d9ff)](https://github.com/mrsanito)

</div>

---
 
## 🛠️ Tech Stack

### 🎨 Frontend
<p>
  <img src="https://skillicons.dev/icons?i=html,css,js,ts,react,nextjs,tailwind&theme=dark" />
</p>

### ⚙️ Backend
<p>
  <img src="https://skillicons.dev/icons?i=nodejs,express,prisma&theme=dark" />
</p>

### 🗄️ Databases
<p>
  <img src="https://skillicons.dev/icons?i=mongodb,postgresql,redis&theme=dark" />
</p>

### ☁️ Cloud & DevOps
<p>
  <img src="https://skillicons.dev/icons?i=docker,git,github&theme=dark" />
</p>

---

## 📊 GitHub Analytics

<div align="center">

<img height="180em" src="https://github-readme-stats.vercel.app/api?username=mrsanito&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&include_all_commits=true" />
<img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=mrsanito&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" />

</div>

<div align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=mrsanito&theme=tokyonight&hide_border=true&date_format=M%20j%5B%2C%20Y%5D" />

</div>

<div align="center">

<img src="https://github-profile-trophy.vercel.app/?username=mrsanito&theme=tokyonight&no-frame=true&no-bg=false&column=7&margin-w=4" />

</div>

---

## 🔥 Activity Graph

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=mrsanito&theme=tokyo-night&hide_border=true&area=true" />
</div>

---

## 🚀 Featured Project — QuizMaster Turbo

<div align="center">

### 🎮 Real-Time Multiplayer Quiz Platform — *MCA Major Project*

<p>
  <img src="https://skillicons.dev/icons?i=react,nodejs,ts,redis,docker&theme=dark" />
</p>

</div>

QuizMaster Turbo is a **full-scale real-time multiplayer quiz platform**, architected as a proper **Turborepo monorepo** with independent services, a custom real-time engine, and a from-scratch authentication system built to production-grade security standards — not a weekend project.

### ⚡ Real-Time Multiplayer Engine

- Live quiz rooms powered by a **Socket.IO microservice** running independently of the main API, so gameplay traffic never blocks core business logic
- Supports **multiple concurrent rooms** with isolated game state per room (players, scores, current question, timers)
- Server-authoritative **question timer & scoring sync** — every player's clock is reconciled against the server so no one can cheat by manipulating client-side timers
- **Event-driven architecture** for room lifecycle: create room → join → ready-up → question broadcast → answer submission → live leaderboard update → next round
- Built for **low-latency state broadcasting** across all connected clients in a room simultaneously
- Designed to scale horizontally — the socket layer is decoupled so more instances can be added behind the service as load grows

### 🔐 Auth2 — Custom Authentication System

The auth layer (internally called **Auth2**) was built from the ground up instead of dropping in an off-the-shelf auth library. Here's what it uses and how the pieces fit together:

- **JWT access tokens** — short-lived tokens used for actual API authorization, kept deliberately short-lived to limit the damage window if one leaks
- **DPoP (Demonstrating Proof-of-Possession)** — every request is bound to a private key held by the client, so even a stolen access token is useless without the matching key; this is layered on top of the standard bearer-token model
- **Rotating refresh tokens** — every time a refresh token is used to get a new access token, it's invalidated and replaced with a new one; if an old/used refresh token ever gets replayed, the system can detect it and kill the whole session chain
- **Passwordless login flow (OTP-based)** — no passwords stored at all; users authenticate via a one-time code, removing password database breaches as an attack surface entirely
- **Session chain tracking** — refresh token rotation is tracked per-device/session so a compromised session can be revoked without logging the user out everywhere
- **Redis-backed token/session store** — fast lookups for token validation and revocation checks without hammering the primary database

### 📦 Monorepo & Infrastructure

- Built on **Turborepo** — frontend, backend, and the socket microservice all live as separate packages sharing common types/utilities, with cached, parallelized builds
- Clear separation of concerns: `apps/` for deployable services, `packages/` for shared logic (types, auth utils, UI components)
- **Docker**-ready service setup for consistent local dev and deployment
- **MCA project report** generated programmatically using Python + ReportLab, pulling structure straight from the codebase for academic submission

| 🎯 Project | 💡 Description | 🔧 Stack |
|:-----------|:---------------|:---------|
| **[QuizMaster Turbo](#)** | Real-time multiplayer quiz platform (MCA major project) with a Socket.IO-based multiplayer engine and a custom-built JWT/OTP/DPoP authentication system | React, Node.js, Socket.IO, WebSockets, Turborepo, Redis, Docker, JWT/OTP/DPoP Auth |

> 📌 *This is my MCA major project — a full-scale build with a real-time multiplayer engine and a hardened, from-scratch auth system (Auth2). Check the pinned repo for source code!*

---

## 🐍 Contribution Snake

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/mrsanito/mrsanito/output/github-contribution-grid-snake-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/mrsanito/mrsanito/output/github-contribution-grid-snake.svg">
    <img alt="GitHub Contribution Snake" src="https://raw.githubusercontent.com/mrsanito/mrsanito/output/github-contribution-grid-snake.svg" width="100%">
  </picture>
</div>

---

 
## 📬 Let's Connect

<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-0D1117?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mrsanito)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/vishal-nishad-03a690229/)
[![Twitter](https://img.shields.io/badge/Twitter-1D9BF0?style=for-the-badge&logo=twitter&logoColor=white)](https://x.com/satoru34176)
[![Portfolio](https://img.shields.io/badge/Portfolio-FF6B6B?style=for-the-badge&logo=firefox&logoColor=white)](https://zynito.in)
[![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:vishalni2004@gmail.com)

<br/>

**💼 Open to:** Freelance projects · Full-time roles · Open-source collaboration · Tech consultations

</div>

---

<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:00D9FF,100:0D1117&height=120&section=footer&animation=fadeIn" />

**✨ Thanks for visiting! If you like what you see, drop a ⭐ on something — it means a lot!**

</div>
