# 🐛 BugNotes

### *The Premium, Distraction-Free Workspace for Bug Bounty Hunters & Security Researchers*

[![Local-First](https://img.shields.io/badge/Architecture-100%25%20Local--First-eb5e28?style=flat-square)](#)
[![Security](https://img.shields.io/badge/Security-Zero--Knowledge%20Sandbox-2ec4b6?style=flat-square)](#)
[![Storage](https://img.shields.io/badge/Storage-IndexedDB%20Engine-0077b6?style=flat-square)](#)
[![Design](https://img.shields.io/badge/UI-Claude--Inspired%20Minimalism-f4f3ee?style=flat-square&labelColor=252422)](#)

---

## 1. Product Identity & Core Philosophy

**BugNotes** is an ultra-minimalist, distraction-free Markdown scratchpad and note-taking workspace purpose-built for **security researchers, bug bounty hunters, and ethical hackers**. 

When you are deep in an overnight target recon session, tracing a complex exploit chain, or logging volatile zero-day payloads, the last thing you should worry about is your note-taking tool. BugNotes strips away the clutter, tracking, and latency of traditional cloud-based applications, replacing them with a fluid, high-performance canvas that operates entirely inside your browser's native sandbox.

### The Problem We Solve
Traditional note-taking applications present severe liabilities for security professionals:

| **Traditional Note Apps** | **The Security Risk** | **The BugNotes Mitigation** |
| :--- | :--- | :--- |
| **Public Cloud Sync** | Accidental leaks of sensitive targets, private scopes, or zero-days. | **100% Local-First Architecture.** Data never leaves your machine. |
| **Server Logs / APIs** | Third-party tracking or interception of critical exploit code. | **Zero Centralized Endpoints.** Completely decoupled from external backends. |
| **Clunky Configurations** | Wasting hours setting up databases, self-hosted Docker containers, or sync keys. | **Zero-Setup.** Open the URL and immediately start hacking. |

---

## 2. Architecture & Zero-Knowledge Security

BugNotes eliminates the attack surface by discarding the backend entirely. It operates with a **Zero-Knowledge Architecture** driven by a native client-side storage engine.

```
                   +---------------------------------------+
                   |           User Browser Sandbox         |
                   |                                       |
                   |   [ BugNotes UI Canvas (Warm Cream) ] |
                   |                    |                  |
                   |                    v                  |
                   |   [ CodeMirror 6 Markdown Engine ]   |
                   |                    |                  |
                   |                    v                  |
                   |   [ Asynchronous Transactional ]      |
                   +--------------------+------------------+
                                        |
                                        v (Direct Local Write)
                   +---------------------------------------+
                   |     IndexedDB Native Hard Drive       |
                   |      (Refresh-Proof Persistence)      |
                   +---------------------------------------+
```

### 🔒 100% Local-First
There are no backend database connection strings, centralized servers, or API endpoints. BugNotes is entirely decoupled from Firebase, Supabase, GitHub REST APIs, and AWS. Your markdown text, raw HTTP logs, and private scope configurations stay inside your local environment.

### 🛡️ Browser Sandbox Storage
Powered entirely by **IndexedDB**—a high-capacity, transactional, object-oriented database embedded natively inside your browser sandbox. The application writes directly to your local hard drive, enabling massive storage limits far exceeding standard `localStorage` restrictions.

### 🚫 Anti-Flooding & DoS Protection
Because there is no centralized database server or shared network state, malicious actors cannot run automated scripts to inspect, flood, or trigger Denial of Service (DoS) attacks against your project data. Your infrastructure is as secure as your operating system.

---

## 3. Anti-Data-Loss Shield (Client-Side Backups)

Security testing environments often demand aggressive hygiene—including frequent browser history wipes, cookie purges, and automated site cache clearances. Under standard conditions, this risks destroying local browser databases. BugNotes builds a permanent physical defense against this vector.

### 📦 Export Backup (`.json`)
With a single click or shortcut, the application compiles your complete notebook state into a unified, lightweight offline payload:
* Unique record IDs (`UUIDv4`)
* Precise epoch time-metadata (`createdAt`, `updatedAt`)
* Raw Markdown content strings and directory schemas

### 📥 Import Backup
Dropped your site cache? Switched to a clean, hardened burner laptop? Simply drag and drop your `.json` offline backup file back into a fresh BugNotes browser window. The system instantly parses the structure, fully restoring your exact workspace layout, notes, and hierarchical history in milliseconds.

---

## 🗄️ IndexedDB Storage Policy & Data Safety Guide (Must Read)

Since BugNotes runs entirely as a **local-first browser application** without an external cloud database, your notes are bound to your browser's private sandbox storage (**IndexedDB**). To prevent accidental data loss, here is everything you need to know about how your browser treats your notebook:

### 🟢 What is Safe?
- **Clearing Browsing History:** Safely clear your regular browsing history, downloads, or search logs. Your IndexedDB database **will not be touched**, and your notes will remain perfectly intact.
- **System Restarts:** Shutting down your machine or quitting your browser will never delete your notes.

### 🔴 When can Data be Wiped Out? (Precautions)
Your local database can be completely cleared under these specific browser and system conditions:
1. **Clearing "Cookies and Site Data":** If you manually clear your browser data and explicitly check the box for **"Cookies and other site data"** or click **"Clear Site Data"** in Developer Tools, your database will be purged.
2. **Incognito / Private Browsing:** If you open BugNotes inside an Incognito window, it spins up a temporary temporary database in your RAM. **Closing the Private Window destroys all notes instantly.**
3. **Critical Hard Drive Congestion:** If your computer's main drive (`C: Drive` or root volume) drops to nearly 0% free space, modern browsers (Chrome/Brave) will automatically initiate *Automated Eviction* to free up system space, which may clear offline databases.
4. **The Safari 7-Day Inactivity Rule:** If you access this tool via **Apple Safari** (macOS or iOS) and do not interact with the application for **7 consecutive days**, Apple's tracking prevention policy will automatically wipe out the IndexedDB container. *(This restriction does not apply to Chrome, Brave, or Firefox).*

---
- **Pro-Tip For Hunters:** Make it a strict habit to click **Export Backup (.json)** at the end of every active hacking session. Keep that lightweight file on your local machine or an encrypted drive. If your browser cache gets wiped, dragging that file back into the **Import Backup** module fully reconstructs your entire note structure and content tree in less than a second!

---

## 4. Premium UI Canvas & Code-Editor Features

The visual design is meticulously structured around prolonged, high-cognitive work sessions where eye strain and interface friction must be minimized.

```
+-----------------------------------------------------------------+
| 📂 My-Targets > src > exploit.md                       [ ][-]   |
+-----------------------------------------------------------------+
|  1 | # Zero-Day Payload POC                                    |
|  2 |                                                            |
|  3 | Let's trace the memory corruption vulnerability here:     |
|  4 |                                                            |
|  5 | ```http                                                   |
|  6 | POST /vulnerable-endpoint HTTP/1.1                        |
|  7 | Host: target.internal                                     |
|  8 | Content-Length: 42                                        |
|  9 |                                                           |
| 10 | AAAAAAAA...AAA                                            |
| 11 | ```                                                       |
|    |                                                           |
+-----------------------------------------------------------------+
```

### ☕ Claude-Inspired Aesthetics
Designed with a calming, eye-friendly, anti-glare warm cream and dark charcoal color palette (`#f4f3ee`). Optimized specifically for grueling overnight target recon sessions, replacing harsh high-contrast blacks and blinding whites with organic, readable tones.

### 🔲 Collapsible Workspace Focus
Featuring a borderless UI toggle that instantly hides the navigational sidebars and index panels. This transforms the editor into a fluid, edge-to-edge focal canvas, isolating your code and notes from all external visual noise.

### 🚀 CodeMirror 6 Engine
Integrated with an elite, industrial-grade code-editor engine that drives:
* **Live Inline Parsing:** Clean, real-time rendering of markdown syntax, headers, and codeblocks.
* **Vertical Line Numbering:** Standard code gutters to maintain direct layout reference lines when pasting massive HTTP request/response payloads.
* **Horizontal Cursor Line-Shadows:** Active highlight tracking to keep your place instantly visible in dense text documents.

### 🗺️ Dynamic Path Tracking
Features real-time state listeners where updating an active heading or title instantly modifies the top-left breadcrumb trail dynamically. Your location in complex multi-folder target structures remains crystal clear at all times.

---

## 5. Getting Started

Since BugNotes requires **absolute zero-setup out of the box**, you can spin up your workspace in seconds:

1. **Launch:** Access the live deployment link in any modern, sandboxed browser.
2. **Hack:** Immediately start dropping private scopes, raw logs, or scripts.
3. **Backup:** Download an offline `.json` backup before clearing your environment caches.

---

*Built for hackers, by hackers. Keep your notes local. Keep your data safe.*
