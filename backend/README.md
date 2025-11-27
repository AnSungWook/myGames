# Backend

Java 21 + Gradle 기반 백엔드 코드가 위치합니다. 공통 코드와 게임별 서비스가 분리되어 있어 재사용성과 CI/CD 구성을 쉽게 합니다.

## 디렉터리

```
backend/
├── core/               # 공통 DTO, 유틸, 인증 등 재사용 모듈
└── games/
    ├── number-baseball/ # 숫자 야구 게임의 Spring Boot 서비스 (submodule)
    └── up-down/         # 업다운 게임용 자리를 미리 확보 (.gitkeep)
```

### core
- Java 21 모듈 또는 Gradle 멀티프로젝트로 구성합니다.
- `gradle test`로 단위 테스트를 실행하고, 다른 서비스에서 composite build 혹은 배포된 아티팩트로 참조합니다.

### games/<game>
- 게임별 API 서버. `number-baseball` 디렉터리는 서브모듈로 연결되어 있고, `up-down`은 추후 프로젝트를 추가할 수 있도록 빈 디렉터리만 유지합니다.

필요한 게임이 늘어나면 `games/<새로운-게임>` 폴더를 추가하고 동일한 패턴을 따르면 됩니다.
