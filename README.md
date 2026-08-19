# Dragon-Table-Tennis-Club-System

A digital membership and payment system built for a table tennis club, replacing manual tracking with a two-sided web platform. Members can self-register, choose between walk-in access or table rentals, and pay cashlessly through DuitNow/FPX integration. Payments sync in real time across both the client and owner dashboards, while the owner retains the ability to manually log cash payments for renewals, walk-ins, or rentals. The system also generates automated monthly earnings reports and sends renewal reminders to members before their membership lapses.



#### Tech Stack:

* Frontend: React, Next.js, Tailwind CSS
* Backend: Next.js (API Routes / Server Actions), Node.js
* Database \& Auth: Supabase (PostgreSQL)
* Payments: Billplz / ToyyibPay API
* Hosting: Vercel (app), Supabase Cloud (database)
* Version control: Git, GitHub



#### Sprints:

* \[Sprint 0: Setup](devlog/sprint-00-setup.md) - Repo, devlog, project board
* Sprint 1: Registration - Auth, Supabase, role-based portals
* Sprint 2: Walk-in \& Rental - Booking flows
* Sprint 3: Payments - Billplz/ToyyibPay integration
* Sprint 4: Owner Dashboard - Manual entry, tracking
* Sprint 5: Reports \& Testing - Monthly reports, QA



#### Features:

##### Client Portal (Members)



* Self-registration via email/phone OTP (no admin approval needed)
* Membership fee payment via cashless gateway (DuitNow/FPX through Billplz/ToyyibPay)
* Payment history view — list of all past months with status
* Visual monthly payment chart (heatmap-style, paid vs. unpaid per month)
* Accurate handling of late payments (e.g. June's fee paid in July still shows under June, not July)



##### Guest Access (Non-members)



* No account required — pay as guest
* Walk-in payment (flat entry fee)
* Table rental payment (RM20/hour, tied to a specific table)
* Cashless payment through the same gateway



##### Owner Portal



* Dashboard overview of members and recent activity
* Manual payment entry for cash payments — covers membership renewal, walk-in, and table rental, each scoped to the exact member/month or transaction so it can't overwrite unrelated records
* Full member list with search/filter
* Real-time sync — any payment (cashless or manually entered) instantly reflects on both the owner's and the relevant client's dashboard
* Monthly earnings report — aggregated totals at month-end, broken down by membership dues, walk-ins, and rentals
* Renewal reminders — automated nudge sent to a member if their membership is unpaid as the month closes, so it doesn't fall through the cracks



##### System-level



* Role-based access — separate, secured routes for client vs. owner, enforced at the database level via Row Level Security
* Two independent data domains — member subscriptions vs. guest transactions — kept separate but both feeding into the same owner-facing reports
* Audit trail — manual cash entries are tagged with which owner account logged them

