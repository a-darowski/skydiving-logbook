# Product Requirements Document (PRD) - Skydiving Logbook

## 1. Product Overview

A desktop-oriented web application that replaces traditional paper logbooks for skydivers. The system streamlines jump recording by auto-incrementing jump numbers and pre-filling repetitive fields, allowing users to log multiple jumps quickly and accurately. The application is built with Astro 5, React 19, TypeScript 5, Tailwind 4, shadcn/ui, and Supabase, and is deployed via GitHub Actions.

## 2. User Problem

Skydivers currently spend significant time manually transcribing repetitive data (jump number, aircraft, location, canopy details) into physical logbooks. This process is error-prone, time-consuming, and lacks data-driven insights. Users need a reliable, accessible solution that automates repetitive entry, preserves data integrity, and simplifies record keeping.

## 3. Functional Requirements

1. Account creation and login with username and password.
2. Optional guided onboarding (profile, weight, canopies, default dropzone) with skippable steps.
3. Core jump logging with server-side auto-incremented jump numbers.
4. Jump entry fields: date, jump type (solo, tandem, AFF, formation, other), canopy model & size, aircraft, location, altitude, free-fall time.
5. Batch logging workflow that opens a centered modal table for review, inline edit, and delete before confirmation.
6. Full edit and delete capabilities for saved jumps.
7. Logbook view displaying jumps in a sortable (date, jump number) and filterable (date range, jump type, location) table.
8. Locations stored in Supabase with a default aircraft; users can override aircraft per jump.
9. Data persistence secured with Supabase row-level security (RLS).
10. Continuous integration and deployment via GitHub Actions with Supabase secrets stored in repository settings.

## 4. Product Boundaries

● In Scope

- Desktop-first responsive design
- Authentication using Supabase credentials
- Auto-incremented jump numbering enforced server-side
- Batch entry modal with inline editing
- Sort and filter functions on the logbook table
- Guided onboarding (optional and skippable)

● Out of Scope (MVP)

- Mobile-first layout
- Import/export of logbook data
- Statistics and analytics dashboards
- Offline usage
- Social or sharing features

## 5. User Stories

| ID     | Title                    | Description                                                                                                             | Acceptance Criteria                                                                                                                               |
| ------ | ------------------------ | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| US-001 | Secure Authentication    | As a skydiver, I want to create an account and log in securely so that my logbook is private.                           | • User can sign up with a unique username and password. <br>• Passwords are stored securely in Supabase. <br>• Login rejects invalid credentials. |
| US-002 | Guided Onboarding        | As a new user, I want an optional setup flow so I can enter my profile, weight, canopies, and default dropzone quickly. | • On first login, user is offered onboarding. <br>• Each step can be skipped. <br>• Data entered is saved to Supabase.                            |
| US-003 | Log Single Jump          | As a user, I want to log an individual jump with all required fields so that my record is accurate.                     | • Form includes all jump fields. <br>• Jump number auto-increments from highest existing. <br>• Form validation prevents empty mandatory fields.  |
| US-004 | Batch Log Jumps          | As a user, I want to enter multiple jumps at once and review them before saving so I can log faster.                    | • User specifies number of jumps. <br>• Modal review table lists generated rows. <br>• Inline edit and delete are available before save.          |
| US-005 | Edit Jump                | As a user, I need to edit any saved jump to correct mistakes.                                                           | • Edit opens a form populated with current values. <br>• Changes are saved to Supabase. <br>• Validation rules match create form.                 |
| US-006 | Delete Jump              | As a user, I need to remove an incorrect jump entry.                                                                    | • Delete action prompts confirmation. <br>• Jump is removed from database and UI updates instantly.                                               |
| US-007 | View Logbook             | As a user, I want to see my jumps in a sortable table.                                                                  | • Default sort is by date descending. <br>• Clicking headers toggles sort by date or jump number.                                                 |
| US-008 | Filter Logbook           | As a user, I want filters for date range, jump type, and location so I can locate specific entries.                     | • Filter controls appear above table. <br>• Applying filters updates results without page reload.                                                 |
| US-009 | Manage Locations         | As a user, I want to add or select locations with default aircraft data.                                                | • Location dropdown lists existing locations. <br>• Users can add a new location with aircraft.                                                   |
| US-010 | Override Aircraft        | As a user, I can override the default aircraft for a specific jump.                                                     | • Aircraft field pre-fills from location but is editable.                                                                                         |
| US-011 | Auto-Number Integrity    | As a user, I trust that jump numbers are unique and sequential even in concurrent sessions.                             | • Jump numbers generated server-side. <br>• No duplicate numbers observed in tests.                                                               |
| US-012 | CI/CD Deployment         | As a developer, I want automatic deployment on merge to master.                                                         | • GitHub Actions workflow runs tests and deploys.                                                                                                 |
| US-013 | Accessibility Compliance | As a user, I need the interface to meet basic accessibility guidelines.                                                 | • Modal is focus-trapped. <br>• All inputs have accessible labels.                                                                                |
| US-014 | Error Handling           | As a user, I expect clear error messages if saving fails.                                                               | • API errors display non-technical messages.                                                                                                      |
