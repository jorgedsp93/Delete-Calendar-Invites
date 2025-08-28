elete "Away" All-Day Events from Google Calendar

This Google Apps Script deletes all **all-day events** containing the word **"Away"** on your **primary calendar** within a specific date range.  
It ensures only events you created or organized are deleted, and no email notifications are sent to other participants.

---

## Features
- Scans your **primary calendar** day by day for a given window.
- Matches only events that:
  - Are **all-day** events
  - Contain the word **"away"** (case-insensitive) in the title or description
  - Were created or organized by **you**
- Deletes them **without sending update emails** to guests.
- Logs detailed statistics (events checked, skipped, deleted, failed).

---

## Requirements
- A Google account with Calendar access.
- Google Apps Script enabled for your account.
- The **Calendar Advanced Service** must be turned on:
  1. In the Apps Script editor, go to **Services** → **+**.
  2. Enable **Calendar API**.

---

## Usage
1. Open [Google Apps Script](https://script.google.com/).
2. Create a new project and paste in the code from `Code.gs`.
3. Edit the window variables:
   ```javascript
   var START_YMD = '2025-08-01';        // inclusive
   var END_YMD_EXCLUSIVE = '2025-09-01'; // exclusive
For example, the above will delete all "Away" all-day events overlapping August 2025.
4. Save the script.
5. Run the function:

javascript
Copy code
deleteMyAwayAllDay_onPrimary_byDay();
The first time, you’ll be prompted to authorize the script.

Example Log Output
json
Copy code
{
  "window": { "startInclusive": "2025-08-01", "endExclusive": "2025-09-01" },
  "daysScanned": 31,
  "eventsChecked": 45,
  "matchedAwayAllDay": 6,
  "deleted": 6,
  "skippedNotAllDay": 10,
  "skippedNotMine": 2,
  "failed": 0
}
Notes
The script checks all events that overlap the window, even if they start before it.

Multi-day all-day events are deduplicated, so they are only processed once.

Non-all-day events, events without "away" in title/description, and events not organized by you are skipped.

Failed deletions (rare, e.g. permissions issues) are logged but do not stop the run.

Disclaimer
This script permanently deletes events. Test with a short window first to confirm it behaves as expected. Use at your own risk.

pgsql
Copy code

Do you want me to also make a **GitHub-friendly version** with setup badges (like “Google Apps Script” or “Calendar API enabled”) and an **example screenshot** of the log output?
