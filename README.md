# NavSmart — AIU Campus Navigation

**A full-stack campus navigation platform built from the ground up as my Final Year Project at Albukhary International University (AIU).**

[Live Demo](https://nav-smart.vercel.app/) · [GitHub Profile](https://github.com/Leroy-laboe) · [LinkedIn](https://www.linkedin.com/in/leroy-nyasha-mangwarara-86185a302/)

> **Source code is private.** This repository is a public product and engineering case study for NavSmart. It documents the problem, user experience, system design, routing approach, and selected interfaces without exposing the full implementation.

---

![NavSmart campus navigation experience](./imagies/navsmart_01_route_finder_hero.png)

## Overview

NavSmart is a campus navigation system designed to help students, staff, and visitors move around Albukhary International University more easily.

Instead of treating the campus as a static map, NavSmart represents locations and walkable connections as a **weighted graph**. A routing engine uses **Dijkstra's shortest-path algorithm** to calculate a route between selected locations, while the frontend combines that route with an interactive campus map and immersive location views.

I designed and built NavSmart as my Final Year Project, working across the product experience, routing logic, frontend, backend, database structure, administration tools, and deployment.

---

## The Problem

Large campuses can be difficult to navigate for:

- new students;
- visitors;
- event attendees;
- staff moving between unfamiliar facilities;
- users who recognise buildings visually more easily than from a traditional map.

A static map can show where a building is, but it does not necessarily explain **how to get there**, what the destination looks like, or how navigation data can be maintained as the campus changes.

NavSmart explores a more interactive approach by combining **route computation, map-based guidance, destination discovery, and immersive campus views**.

---

## Product Experience

### 1. Navigate the Campus

The main experience combines the real campus environment with route discovery and an interactive map.

![NavSmart route finder](./imagies/navsmart_01_route_finder_hero.png)

Users can select destinations, view campus locations, and follow route information through a map-based interface.

---

### 2. Campus Map & Route Visualisation

![NavSmart campus map](./imagies/navsmart_02_campus_map_widget.png)

The map represents buildings and navigation points as connected locations. Route results can then be visualised as an ordered path between the selected start and destination.

---

### 3. Campus Directory

![NavSmart campus directory](./imagies/navsmart_05_campus_directory_mobile.png)

The directory gives users a more direct way to discover buildings and facilities before starting navigation.

---

### 4. Location Exploration

![NavSmart location explorer](./imagies/navsmart_07_library_explorer_modal.png)

Destination views can provide richer context around a campus location instead of reducing it to a map marker alone.

---

## Routing Engine

NavSmart models the campus as a graph:

```text
Campus Locations
      │
      ▼
Navigation Nodes
      │
      ▼
Weighted Connections
      │
      ▼
Dijkstra's Algorithm
      │
      ▼
Shortest Path
      │
      ▼
Ordered Coordinates
      │
      ▼
Route Rendered on the Map
```

The routing engine builds an adjacency structure from stored connections and applies Dijkstra's algorithm to find the lowest-cost path between the selected start and destination nodes.

The resulting node sequence is converted back into geographic coordinates for the frontend to display.

---

## System Architecture

```text
┌──────────────────────────────┐
│       React + Vite UI        │
│                              │
│ Directory / Map / Tour /     │
│ Route Finder / Admin Tools   │
└──────────────┬───────────────┘
               │ REST API
               ▼
┌──────────────────────────────┐
│     Node.js + Express API    │
│                              │
│ Auth / Campus Data / Routes  │
└──────────────┬───────────────┘
               │
       ┌───────┴────────┐
       ▼                ▼
┌───────────────┐  ┌───────────────────┐
│  PostgreSQL   │  │ Navigation Engine │
│               │  │                   │
│ Nodes         │  │ Dijkstra          │
│ Connections   │  │ shortest path     │
│ Hotspots      │  └───────────────────┘
│ Admins        │
│ Announcements │
└───────────────┘
```

---

## Admin & Campus Management

NavSmart also includes administrative tools for maintaining the system rather than requiring navigation data to remain hard-coded.

### Admin Portal

![NavSmart admin login](./imagies/navsmart_03_admin_login_portal.png)

### Admin Dashboard

![NavSmart admin dashboard](./imagies/navsmart_04_admin_dashboard.png)

### Map Editor

![NavSmart map editor](./imagies/navsmart_06_map_editor_dashboard.png)

The management experience is designed around maintaining campus information, navigation nodes, path connections, and announcements.

---

## Engineering Highlights

### Real campus → navigation graph

One of the main challenges was translating physical campus movement into a graph that software could reason about.

Buildings alone were not enough. The navigation model also required meaningful intermediate waypoints and weighted connections so that route calculations followed realistic walkable paths.

### Shortest-path routing

I implemented Dijkstra's algorithm for route calculation, including support for weighted edges and directional relationships.

### Data-driven navigation

Navigation data was moved into PostgreSQL so locations and connections could be managed independently of the frontend rather than permanently embedded in UI code.

### Map + immersive exploration

The project combines 2D map navigation with panorama/location exploration so users can recognise destinations visually as well as geographically.

### Administration tools

I also built management interfaces for maintaining parts of the navigation system and campus content.

---

## Tech Stack

| Area | Technologies |
| --- | --- |
| **Frontend** | React, Vite, JavaScript |
| **Mapping** | Leaflet, React Leaflet |
| **Backend** | Node.js, Express |
| **Database** | PostgreSQL |
| **Authentication** | JWT, bcrypt |
| **Routing** | Dijkstra's shortest-path algorithm |
| **UI / Motion** | Tailwind CSS, Framer Motion, GSAP |
| **Immersive Views** | Panorama / 360° viewer tooling |
| **Deployment** | Vercel + deployed API configuration |

---

## My Role

**Final Year Project — BSc Computer Science (Data Science)**

I built NavSmart from the ground up.

My work included:

- defining the product concept and navigation experience;
- modelling the AIU campus as a graph;
- implementing Dijkstra's shortest-path logic;
- building the React/Vite frontend;
- integrating Leaflet for map rendering;
- developing the Node.js/Express backend;
- designing and working with the PostgreSQL navigation schema;
- building administrator authentication and management workflows;
- connecting route results to map coordinates;
- integrating immersive campus/location views;
- testing navigation paths and refining campus data;
- deploying and iterating on the product.

---

## Selected UI Showcase

> **Presentation note:** the visuals below are polished presentation versions based directly on real NavSmart screens. The UI styling, spacing, typography, and framing were refined for this case study; they are not intended to represent additional functionality that does not exist in the project.

![NavSmart case study overview](./imagies/navsmart_08_case_study_overview.png)

| Product Area | Preview |
| --- | --- |
| Route Finder | ![Route Finder](./imagies/navsmart_01_route_finder_hero.png) |
| Campus Map | ![Campus Map](./imagies/navsmart_02_campus_map_widget.png) |
| Admin Dashboard | ![Admin Dashboard](./imagies/navsmart_04_admin_dashboard.png) |
| Campus Directory | ![Campus Directory](./imagies/navsmart_05_campus_directory_mobile.png) |
| Map Editor | ![Map Editor](./imagies/navsmart_06_map_editor_dashboard.png) |
| Location Explorer | ![Location Explorer](./imagies/navsmart_07_library_explorer_modal.png) |

---

## Future Direction

NavSmart began as a university navigation project, but the underlying approach can extend beyond a single campus.

Potential future directions include:

- accessibility-aware routing;
- indoor navigation;
- real-time path closures;
- mobile positioning;
- configurable deployments for other campuses or facilities;
- stronger map-management tooling;
- route preferences;
- navigation analytics.

I am keeping the implementation repository private while I continue exploring the project's future direction.

---

## Live Demo

### [Open NavSmart →](https://nav-smart.vercel.app/)

---

## Contact

**Leroy Nyasha Mangwarara**

Software Engineering · Full-Stack · Applied AI · Data

[LinkedIn](https://www.linkedin.com/in/leroy-nyasha-mangwarara-86185a302/) · [GitHub](https://github.com/Leroy-laboe) · [Email](mailto:mangwararaleroy@gmail.com)
