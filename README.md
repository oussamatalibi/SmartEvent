# SmartEvent
A full-stack event-management platform that lets organisers publish events, attendees self-register, and admins track everything in one place. Built with ASP.NET Core 7, Identity + JWT, React 18, and Syncfusion UI in a clean, layered architecture.
## ✨ Key Features

| Domain | What you get |
| ------ | ------------ |
| **Authentication & RBAC** | ASP.NET Identity + JWT, role‑based guards (`Admin`, `Organiser`, `User`). |
| **Event Lifecycle** | Create / update / delete events (title, description, category, capacity, pricing, schedule). Prevention of double‑booking via overlapping‑time validation. |
| **Participants** | REST endpoint streams participants; React renders them in a Syncfusion Grid with filtering, paging & export to Excel. |
| **Categories** | Enum‑backed (Tech, Media, Sports …) and instantly filterable on both API and UI. |
| **API‑first** | Versioned controllers, DTO mapping with AutoMapper, live Swagger / OpenAPI docs. |
| **Dev & Ops** | Docker‑compose for local spin‑up (API + MySQL + pgAdmin). GitHub Actions CI runs tests & publishes Docker images. |

---

## 🗂️ Project Structure

```
SmartEvent/
├── src/
│   ├── API/                # ASP.NET Core Web API
│   ├── Core/               # Domain models, DTOs, interfaces
│   ├── Infrastructure/     # EF Core, repositories, migrations
│   └── WebApp/             # React 18 front‑end
├── docker-compose.yml
├── .github/workflows/ci.yml
└── README.md               # (this file)
```

---

## 🚀 Quick Start

> **Prerequisites**: .NET 8 SDK, Node 18+, Docker & Docker Compose.

```bash
# 1. Clone repository
git clone https://github.com/your-user/SmartEvent.git
cd SmartEvent

# 2. Apply DB migrations
dotnet ef database update -p src/Infrastructure

# 3. Spin up full stack
docker compose up --build -d

# 4. Open in browser
# API docs:  https://localhost:5001/swagger
# Frontend:  http://localhost:5173
```

---

## 🛠️ Tech Stack

- **Backend**: ASP.NET Core 7, Entity Framework Core, AutoMapper, Swashbuckle
- **Frontend**: React 18, React Router DOM, Syncfusion UI, Axios
- **Auth**: ASP.NET Identity, JWT (stored client‑side, to be migrated to http‑only cookies)
- **Database**: MySQL 8
- **CI/CD**: GitHub Actions, Docker, docker‑compose

---

## 🔌 API Reference (excerpt)

| Method | Route | Auth | Description |
| ------ | ----- | ---- | ----------- |
| `POST` | `/api/auth/login` | – | Obtain JWT token |
| `GET`  | `/api/events` | Public | List / filter events |
| `POST` | `/api/events` | Admin, Organiser | Create new event |
| `GET`  | `/api/events/{id}/participants` | Admin, Organiser | List participants for given event |
| `GET`  | `/api/users/me` | Authenticated | Current user profile |

_Full contract available at `/swagger`._

---

## 🧭 Roadmap

- **AuthContext** in React for automatic token refresh  
- **Payment gateway** module for paid events  
- **React Query** for data caching and optimistic updates  
- **OpenTelemetry** integration → Grafana dashboards  
- **SaaS multi‑tenant mode** (organisation‑scoped data)

---

## 🤝 Contributing

1. Fork the repo & create your branch (`git checkout -b feature/amazing`).
2. Commit your changes (`git commit -m 'feat: add amazing'`).
3. Push to the branch (`git push origin feature/amazing`).
4. Open a pull request.

Please run `dotnet test` and `npm test` before sending a PR.

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

## 🙋 Author

**Lghadanfar (Oussama Talibi)** — _Computer Science & Network Engineering student, chess coach, and security enthusiast._

Feel free to reach out on [LinkedIn](https://www.linkedin.com/in/your-profile) for questions or collaboration!

---

> _“Plans are nothing; planning is everything.” — Dwight D. Eisenhower_
