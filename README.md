# Lectern

A browser-native presentation editor for academic talks. Decks are structured JSON plus assets, so Claude Code can edit them locally while the same React app runs as a Firebase-hosted web app on iPad.

## Use Locally

```bash
npm install
npm run lectern -- new decks/my-talk --title "My Talk"
npm run lectern -- open decks/my-talk
```

`lectern open` starts the full editor. `lectern present decks/my-talk` starts directly in presenter mode.

## Firebase Web App

1. Create a Firebase project with Anonymous Auth, Firestore, Storage, Hosting, and optional Functions.
2. Copy `.env.example` to `.env` and fill the `VITE_FIREBASE_*` values.
3. Run `npm run app:build`.
4. Deploy with `firebase deploy`.

Use `/?store=firebase&deck=my-talk` to edit a Firebase deck. The app stores deck metadata in Firestore and pasted images in Storage.

## AI

Local AI actions use `/api/ai` from `lectern open`. Set `ANTHROPIC_API_KEY` and `ANTHROPIC_MODEL` for model-backed edits; otherwise the editor returns deterministic safe fallbacks. Firebase hosting uses the callable `deckAiEdit` function in `functions/`.
