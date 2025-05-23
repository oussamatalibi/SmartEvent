# SmartEvent
A full-stack event-management platform that lets organisers publish events, attendees self-register, and admins track everything in one place. Built with ASP.NET Core 7, Identity + JWT, React 18, and Syncfusion UI in a clean, layered architecture.

![image](https://github.com/user-attachments/assets/b5e61b2d-e97a-4b56-8d01-88d08525a93c)

## ✨ Key Features

| Domain | What you get |
| ------ | ------------ |
| **Authentication & RBAC** | ASP.NET Identity + JWT, role‑based guards (`Admin`, `Organiser`, `User`). |
| **Event Lifecycle** | Create / update / delete events (title, description, category, capacity, pricing, schedule). Prevention of double‑booking via overlapping‑time validation. |
| **Participants** | REST endpoint streams participants; React renders them in a Syncfusion Grid with filtering, paging & export to Excel. |
| **Categories** | Enum‑backed (Tech, Media, Sports …) and instantly filterable on both API and UI. |
| **API‑first** | Versioned controllers, DTO mapping with AutoMapper, live Swagger / OpenAPI docs. |


---

## 🗂️ Project Structure

```
SmartEvent/
├── SmartEvent.API/ # ASP.NET Core Web API (entry point)
├── SmartEvent.Core/ # Domain entities, DTOs, interfaces
├── SmartEvent.Data/ # EF Core DbContext & migrations
├── SmartEvent.Services/ # Business-logic services
├── SmartEvent.RegistrationServices/ # Email, QR code, registration utilities
├── Migrations/ # EF Core migration snapshots (dotnet-ef)
├── wwwroot/ # Static files (Swagger UI assets, logos …)
├── appsettings.json
└── README.md # (this file)
```

---

## 🚀 Quick Start

> **Prerequisites**: .NET 8 SDK (or 7), local MySQL 8 server (or update `appsettings.json` for your DB).

```bash
# 1. Clone repository
git clone https://github.com/oussamatalibi/SmartEvent.git
cd SmartEvent

# 2. Restore & build
dotnet restore
dotnet build

# 3. Apply latest DB migrations
dotnet ef database update --project SmartEvent.Data

# 4. Run the API
dotnet run --project SmartEvent.API
```

---

## 🛠️ Tech Stack

- **Backend**: ASP.NET Core 7, Entity Framework Core, AutoMapper, Swashbuckle
- **Frontend**: React 18, React Router DOM, Syncfusion UI, Axios
- **Auth**: ASP.NET Identity, JWT (stored client‑side, to be migrated to http‑only cookies)
- **Database**: MySQL 8

---

## 🔌 API Reference (excerpt)

> All endpoints are version-neutral (`/api/...`) and return JSON.  
> **Auth:** 🔒 = JWT required | 🔓 = Public

### Events
| Method | Route | Auth | Purpose |
| ------ | ----- | ---- | ------- |
| `GET`  | `/api/events` | 🔓 | List & filter events |
| `POST` | `/api/events` | 🔒 (`Admin`) | Create a new event |
| `GET`  | `/api/events/{id}` | 🔒 | Get event by ID |
| `PUT`  | `/api/events/{id}` | 🔒 (`Admin`) | Update event |

### Registration
| Method | Route | Auth | Purpose |
| ------ | ----- | ---- | ------- |
| `POST` | `/api/registration` | 🔒 (`User`) | Register current user to an event |
| `GET`  | `/api/registration/user-events` | 🔒 (`User`) | List events the current user joined |
| `GET`  | `/api/registration/check/{evenementId}` | 🔒 (`User`) | Check eligibility (already registered? capacity left?) |
| `GET`  | `/api/registration/event-participants/{eventId}` | 🔒 (`Admin`) | Get participants of a specific event |

### Cancellation
| Method | Route | Auth | Purpose |
| ------ | ----- | ---- | ------- |
| `GET`  | `/api/cancellation/user-cancellations` | 🔒 (`User`) | List cancellations made by current user |
| `POST` | `/api/cancellation/cancel/{eventId}` | 🔒 (`User`) | Cancel current user’s registration |
| `POST` | `/api/cancellation/remove-blacklist/{userId}` | 🔒 (`Admin`) | Remove user from blacklist |
| `GET`  | `/api/cancellation/user-status` | 🔒 (`User`) | Get current user’s cancellation status (e.g., blacklisted) |

### Auth
| Method | Route | Auth | Purpose |
| ------ | ----- | ---- | ------- |
| `GET`  | `/api/auth/all` | 🔒 (`Admin`) | List **all** users |
| `POST` | `/api/auth/login` | 🔓 | Login & receive JWT |
| `POST` | `/api/auth/register` | 🔓 | Create new account |
| `POST` | `/api/auth/logout` | 🔒 | Invalidate current token (client-side) |
| `GET`  | `/api/auth/current-user` | 🔒 | Get profile of current user |

---



## 🤝 Contributing

1. Fork the repo & create your branch (`git checkout -b feature/amazing`).
2. Commit your changes (`git commit -m 'feat: add amazing'`).
3. Push to the branch (`git push origin feature/amazing`).
4. Open a pull request.

Please run `dotnet test` and `npm test` before sending a PR.

---


## 🙋 Author

**Oussama Talibi** — _Computer Science & Network Engineering student._

Feel free to reach out on [LinkedIn](https://www.linkedin.com/in/oussama-talibi-87ab2821b/) for questions or collaboration!

---
