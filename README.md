# Nutri Tracker (No-Auth MVP)

React + Vite + Firebase Firestore + Barcode-Scanner (BrowserBarcodeDetector + ZXing Fallback).

✅ Kein Login: Daten werden pro Gerät/Browser über eine lokale Session-ID gespeichert: `sessions/{sessionId}/diary/...`

## Setup

1) Dependencies installieren
```bash
npm i
```

2) Firebase Web Config setzen
- Kopiere `.env.example` → `.env` und trage deine Werte ein.

3) Dev starten
```bash
npm run dev
```

## Firebase (Hosting + Rules)

> ⚠️ Dieses Projekt verwendet **offene Firestore Rules** (read/write für alle), weil du keinen Login willst.
> Jeder, der deine Project-ID kennt, kann Daten lesen/schreiben. Für ein privates MVP ok – für öffentlich im Netz: nicht ok.

### Regeln deployen
```bash
firebase login
firebase use tracker-d3a50
firebase deploy --only firestore:rules
```

### Hosting deployen
```bash
npm run build
firebase deploy --only hosting
```

## GitHub Actions Deploy

Workflow liegt unter `.github/workflows/deploy.yml`.

Du brauchst ein GitHub Secret:
- `FIREBASE_SERVICE_ACCOUNT_TRACKER_D3A50` (Service Account JSON)

Firebase Console → Project Settings → Service accounts → Generate new private key → JSON als Secret einfügen.
