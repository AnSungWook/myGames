# MyGames Monorepo

모든 게임을 한 저장소에서 관리하기 위한 기본 디렉터리 구조입니다.

## 루트 구조

```
myGames/
├── backend/
│   ├── core/                 # 공통 백엔드 라이브러리
│   └── games/
│       ├── number-baseball/  # 숫자 야구 게임 백엔드 코드 (submodule)
│       └── up-down/          # 업다운 게임 자리 (플레이스홀더)
├── frontend/
│   └── core/                 # 공통 프론트엔드(게임별 컴포넌트 포함)
└── mobile/
    └── app/                  # 모바일 앱 쉘
```

### Backend
- `backend/core`: 여러 게임에서 공유하는 DTO, 유틸, 인증 로직 등을 배치.
- `backend/games/<game>`: 게임별 API/서비스 코드. `number-baseball`은 서브모듈로 연결되어 있으며, `up-down`은 빈 디렉터리(.gitkeep)로 자리를 만들어 두었습니다.

### Frontend
- `frontend/core`: 공통 셸과 라우팅을 담당하는 React 앱. 각 게임은 컴포넌트 형태로 추가합니다.

### Mobile
- `mobile/app`: 여러 게임을 묶는 모바일 앱 프로젝트(예: Flutter 웹뷰 쉘) 위치입니다.

필요한 게임이나 컴포넌트를 추가할 때는 위 패턴에 맞춰 디렉터리를 복제하면 됩니다.
