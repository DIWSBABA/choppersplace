# Chopper's Little World (GitHub Pages)

## What's included
- Responsive pet-care page with the three supplied Chopper drawings (backgrounds removed for overlay)
- Care actions, stat meters, local demo save, furniture purchases and draggable furniture
- Optional Firebase Realtime Database live shared save (one shared room/state between two devices)

## Publish to GitHub Pages
1. Create a public GitHub repository.
2. Upload **all contents of this folder**, including `assets/`, `index.html`, `style.css`, `app.js`, `firebase-config.js`.
3. Repository Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save.

## Enable cross-device shared realtime mode
1. Go to https://console.firebase.google.com and create a Firebase project.
2. Add a Web app, copy its config values into `firebase-config.js`.
3. Enable Realtime Database (create database in Europe region).
4. Replace Database Rules with these simple rules for a private demo **only** (public unauthenticated access allows anyone with the link to read/write your pet; not suitable for sensitive data):
```json
{
  "rules": {
    "chopper-world": {
      "shared-save": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```
5. Commit config file changes to GitHub. Open the Pages link on both devices. Both will now subscribe to the same shared database path and actions/state will appear on each device live.

## Notes / limitations
- Firebase rules above are open for demo simplicity; anyone who discovers the public database endpoint can alter the game. For a real private shared pet, add Firebase Authentication and access rules restricting the database to invited users.
- The supplied drawings are 2D poses; rotation is an interactive pose-switching illusion, not a real 3D model. A true 360° rotation requires a 3D Chopper model or a sprite sheet from multiple angles.
- The app is a starter game prototype. Day-by-day maintenance currently decreases stats periodically, but this is a lightweight simulated pet-care mechanic.
