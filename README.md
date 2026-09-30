# Half Marathon Accountability — 14 February 2027

A small two-person daily accountability website for a half-marathon challenge.

## What it does

- Countdown to 14 February 2027
- Two people: You + Sister
- Daily one-tap punch-in
- Exercise/training log
- Healthy food log
- Unhealthy food log
- Optional daily note
- Today's shared status
- Recent 14-day history
- Simple streak count
- Mobile-first design, suitable for a WhatsApp link

## Why Firebase?

A static website alone does not give both phones a shared database. Firebase provides the database and hosting. Firebase currently has a no-cost Spark plan and no payment information is needed for the no-cost plan.

## Setup (one time)

1. Create a Firebase project at https://console.firebase.google.com/
2. Create a Web App inside the project.
3. Enable Authentication -> Sign-in method -> Anonymous.
4. Create Firestore Database.
5. Add these Firestore rules:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /challenges/feb14-half-marathon-2027/entries/{entryId} {
      allow read, write: if request.auth != null;
    }
  }
}

6. The Firebase Web App config is already filled in inside `index.html` for the Run Pigeon Run project.
7. Install Firebase CLI if you want command-line deployment:
   npm install -g firebase-tools
8. Log in:
   firebase login
9. In this folder:
   firebase init hosting
   - choose your Firebase project
   - public directory: `.`
   - single-page app: No
   - overwrite index.html: No
10. Deploy:
   firebase deploy

Firebase will give you a URL. Send that URL to your sister on WhatsApp.

## Important

This is intentionally a private family tool, not a production-grade public app. Anyone who gets the private URL can potentially access the challenge data. Do not put sensitive personal information into it.

## Countdown

From 30 September 2026 to 14 February 2027 there are 137 days remaining when counting elapsed calendar days from tomorrow. If you count both today and race day inclusively, it is 138 calendar days.
