# SmartEvent
A full-stack event-management platform that lets organisers publish events, attendees self-register, and admins track everything in one place. Built with ASP.NET Core 7, Identity + JWT, React 18, and Syncfusion UI in a clean, layered architecture.
✨ Core Features
Domain	Highlights
Authentication & RBAC	ASP.NET Identity, JWT stored in localStorage, role-based guards (Admin, Organiser, User).
Event Lifecycle	CRUD for events (title, description, category, pricing, capacity, schedule). Overlapping-time validation prevents double-booking.
Participant Management	REST endpoint streams all participants; React lists them in a Syncfusion Grid with sorting, paging, and Excel export.
Category System	Flexible enum-backed categories (Tech, Media, Sports …) used for filtering and analytics.
Responsive Front-End	React + React Router; reusable components for Navbar, Sidebar, modals; dark-mode ready.
API-first	Clear Swagger / OpenAPI spec auto-generated; versioned controllers; DTO mapping via AutoMapper.
Dev & Ops	Docker-compose for local spin-up (API + MySQL + pgAdmin); GitHub Actions CI pipeline with unit tests and simple Docker publish.
