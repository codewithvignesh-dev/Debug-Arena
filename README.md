# Debug Arena (Flask + MySQL + Tailwind)

## cPanel deploy
1. MySQL Databases: create a database + user, give ALL privileges.
2. Upload this zip to your home folder and extract (e.g. ~/debug_arena).
3. Setup Python App: Python 3.9+, App root `debug_arena`, Startup file `passenger_wsgi.py`, Entry point `application`.
4. In that screen run pip install with requirements.txt.
5. Copy `.env.example` to `.env`, fill values (DB + admin password + SECRET_KEY). The .env admin account is the only admin; staff accounts are added from the Admin panel.
6. Restart the app. Tables are created automatically on first load.

## Event flow
1. Login at `/` as Admin -> Import students (`Name, RegNo` per line).
2. Admin -> Staff accounts: add / remove staff logins.
2b. Format: 10 questions x 90 sec each x 10 marks (100 total). Blank answers are skipped when the 90 sec ends.
3. Student password = first 3 letters of name + `@sngc#` + digits after K (Vigneshwaran P, 2526K1350 -> `Vig@sngc#1350`).
3. Set event to LIVE; waiting students enter automatically and their 15 min timer starts.
4. After the event set COMPLETED, then turn on "Show results" -> table + Excel export appear for staff/admin.
5. Use "Reset event" to wipe attempts after your dry run.

Local run: `pip install -r requirements.txt && python app.py`
