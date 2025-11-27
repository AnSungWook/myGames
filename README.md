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
│   └── number-baseball/
└── mobile/
    └── app/
```

### Backend
- `backend/core`: shared libraries, domain models, or infrastructure code that can be imported by all games.
- `backend/games/<game-name>`: service-specific code. Each game can hold its own infrastructure-as-code, API, and CI/CD workflow files.

### Frontend
- `frontend/<game-name>`: client apps per game. Keeps build pipelines focused on the game being released.

### Mobile
- `mobile/app`: umbrella mobile client consuming multiple games.

## CI/CD by game
Run CI/CD per game by triggering workflows located under each game's directory. Example GitHub Actions path:
```
backend/games/number-baseball/.github/workflows/backend.yml
frontend/number-baseball/.github/workflows/frontend.yml
```
By scoping workflows to each game folder, you can:
1. Detect changes limited to a game and skip others.
2. Deploy backend and frontend independently.
3. Keep shared `backend/core` changes reusable without forcing unrelated deployments.

Add more games by replicating the folder pattern.
