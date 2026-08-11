<img width="40" src="https://cdn.simpleicons.org/googlesummerofcode" /> &nbsp;[<img width="230" src="https://cdn.prod.website-files.com/611a19b9853b7414a0f6b3f6/611bbb87319adfd903b90f24_logoRC.svg" />](#)  
### Google Summer of Code 2026 for Rocket.Chat

# 🚀 Agenda Jobs Admin Page

Hi, I'm **Khizar Shah**. This repository is my final work product hub for Google Summer of Code 2026 with Rocket.Chat. it showcases the work I delivered on the Agenda Jobs Admin page.

## 💡 Work Highlights
1. [Pull Request](https://github.com/RocketChat/Rocket.Chat/pull/40699)

## 🧠 About the Project

_Background jobs in Rocket.Chat are powered by Agenda (system cron, app schedulers, and omnichannel schedulers). Before this work, administrators had no visibility into which jobs exist, whether they are running or failing, or what happened in past executions._

This project adds an admin page at **Workspace → Background Jobs** so admins can:

- list jobs across **System**, **Apps**, and **Omnichannel**
- search by name and filter by status
- inspect **execution history** in a contextual bar
- **Run Now / Enable / Disable** system jobs (apps & omnichannel remain managed by their own subsystems)

## 🎯 Project Milestones

- [x] Implement `CronJobsService` (core, app, omnichannel listing)
- [x] Add job `status` field + `deriveStatus` / `resolveStatus`
- [x] Lifecycle / create hooks to keep status updated (system & app; create status for omni)
- [x] Database models for Agenda collections
- [x] REST APIs: list, single job, history, enable, disable, trigger
- [x] Permission `manage-scheduled-jobs`
- [x] Execution history logging (system, app, omnichannel)
- [x] Admin UI with tabs + omnichannel sub-tabs
- [x] Contextual bar for job detail + history
- [x] Server-side search + status filter
- [x] Unit / API smoke tests
- [ ] Migration to backfill `status` on existing jobs
- [ ] Orphan app jobs after app uninstall

## 📚 Commit Timeline

Key commits from the pull request (highlights only):

| Commit | Short description |
|--------|-------------------|
| [b5d03b4](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/b5d03b4b9b) | Implement CronJobs service and status derivation
| [482c86e](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/482c86e418) | Add history logging for system and app jobs |
| [fb887e3](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/fb887e3a2d) | Add history logging for omnichannel schedulers |
| [64fe771](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/64fe771b2f) | Add cron.jobs API endpoint |
| [9a7b922](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/9a7b922aca) | Add enable and disable API endpoints |
| [2db2305](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/2db23054b6) | Add cron.trigger endpoint |
| [b4ddf7b](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/b4ddf7b721) | Add Background Jobs admin page with tabs |
| [a758423](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/a758423a29) | Contextual bar for job detail and actions |
| [c274e84](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/c274e842f5) | Fix duplicate jobs on manual trigger |
| [a0112f2](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/a0112f20dd) | Omnichannel scheduler models |
| [a096872](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/a096872d23) | cron.omnichanneljobs endpoint |
| [9fd9eee](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/9fd9eee9f7) | Omnichannel sub-tabs in admin UI |
| [097dc3e](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/097dc3e42d) | Set status on job create when missing |
| [07b6a70](https://github.com/RocketChat/Rocket.Chat/pull/40699/commits/07b6a70dd3) | Fix failed status derivation |

## 📽️ Project Showcase

https://github.com/user-attachments/assets/6c36f97c-dbbf-4b80-aaf2-65d47493d67f



## 🏄‍♂️ Challenges

- Agenda does not own a first-class admin `status`; we combined a stored `status` field with derivation from Agenda fields for correctness and stale “running” cases.
- Manual trigger originally used `agenda.now()`, which created **duplicate** job documents. so i fixed by rescheduling the existing job.

## 🔮 Future Goals

- Investigate orphan app scheduler jobs after uninstall
- Deeper automated tests for actions and filters

## ☀️ Mentors

Grateful to my mentors for guidance, prioritization (documentation first, then migration), and review support.

1. **Douglas Gubert** – Mentor
   [Rocket.Chat](https://open.rocket.chat/direct/douglas.gubert) · [GitHub](https://github.com/d-gubert)
   
3. **Kevin Aleman** – Mentor
      [Rocket.Chat](https://open.rocket.chat/direct/kaleman) . [GitHub](https://github.com/KevLehman)
   
## 🤝 Further Thanks

Rocket.Chat community, and everyone who help me and gave feedback on the PR.
