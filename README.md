[README.md](https://github.com/user-attachments/files/32922356/README.md)
# FoodShare BD — Complete Android Project

A full, self-contained Android Studio project — Gradle wrapper, build files, manifest, everything included. Just open it and run.

## Open and run
1. Extract this zip somewhere simple (Desktop or Documents both work fine).
2. In Android Studio: **File → Open** → select the extracted `FoodShareBD-Android` folder — specifically the one that directly contains `build.gradle.kts` and `settings.gradle.kts` at its top level (not a folder-inside-a-folder).
3. Let Gradle sync. First sync can take a few minutes — it needs to download the Gradle distribution and dependencies over the internet. Watch the progress bar at the bottom of the window.
4. If Android Studio pops up anything like "Trust this project?" or "A new version of Android Gradle Plugin is available" — that's normal on a first open. Trust it / dismiss the AGP prompt (you don't need to upgrade).
5. Once sync finishes with no red errors in the "Build" panel, connect your phone (USB debugging on) or start an emulator from Device Manager, and hit the green Run ▶ button.

## What's inside
The full app, combining every team member's screens into one flow:

- **Splash → Onboarding (3 cards) → Login** — Morsheda
- **Sign Up (with Donor/NGO role toggle), Forgot Password → Verification → Create New Password** — Farhana
- **Role Selection → Donor Dashboard → Add/Edit/My Donations → Donation Details** — Abdullah
- **NGO Dashboard → Available Donations (search + filters) → Donation Details (NGO view)** — Rifat
- **Confirm Claim bottom sheet** — Kazi Sadia Alam

**It's actually wired, not just navigation between static screens.** `DonationRepository.kt` is a shared in-memory store both sides read and write to:
- Posting a donation on the Donor side makes it appear on the NGO side's Available Donations list.
- Claiming a donation (via the Confirm Claim sheet) updates its status back on the Donor side — badge changes to "Claimed", the Matched NGO card appears on Donation Details, and "Confirm Pickup" becomes available.
- The dashboard stat numbers, filters, and "My Donations" list all reflect the real current data, not hardcoded text.

There's no backend — everything resets when the app process restarts, and login/signup don't check real credentials (there's nothing to check against). That's expected for a project at this stage.

**Stack:** Gradle 9.4.0 / Android Gradle Plugin 9.0.0 / Kotlin 2.3.0, compileSdk & targetSdk 35, minSdk 24. Dependencies: core-ktx, appcompat, material, viewpager2 — nothing exotic.

## If Gradle sync fails
Copy the exact error from the "Build" panel — if it's version-related, it's almost always a one-line fix in `build.gradle.kts` or `gradle/wrapper/gradle-wrapper.properties`.
