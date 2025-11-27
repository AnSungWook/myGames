# MyGames Monorepo

This repository is structured around independent game experiences so each game can have its own backend, frontend, and mobile surface while still sharing reusable backend core components.

## Top-level layout

```
myGames/
├── backend/
│   ├── core/
│   └── games/
│       └── number-baseball/
├── frontend/
│   ├── core/
│   └── games/
│       └── number-baseball/
└── mobile/
    └── app/
```

### Backend
- `backend/core`: shared libraries, domain models, or infrastructure code that can be imported by all games.
- `backend/games/<game-name>`: service-specific code. Each game can hold its own infrastructure-as-code, API, and CI/CD workflow files.

### Frontend
- `frontend/core`: shared shell/landing experience surfaced to players. Handles navigation, auth, feature discovery, and bootstrapping each game module.
- `frontend/games/<game-name>`: per-game UI modules that plug into the core shell. Each module can have its own build and release workflow while still being consumed by the shared core app.

### Mobile
- `mobile/app`: umbrella mobile client consuming multiple games.

## CI/CD by game
Run CI/CD per game by triggering workflows located under each game's directory. Example GitHub Actions path:
```
backend/games/number-baseball/.github/workflows/backend.yml
frontend/games/number-baseball/.github/workflows/frontend.yml
```
By scoping workflows to each game folder, you can:
1. Detect changes limited to a game and skip others.
2. Deploy backend and frontend independently.
3. Keep shared `backend/core` changes reusable without forcing unrelated deployments.

Add more games by replicating the folder pattern.
