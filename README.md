# CineFund

CineFund는 영화 탐색, 비교, 랭킹과 모의 펀딩을 제공하는 모노레포 프로젝트입니다.

## 구조

```text
backend-main/    Express API, Prisma, PostgreSQL
cine-fund-main/  React + Vite 프런트엔드
```

## 시작하기

필요 환경: Node.js `^22.12.0 || >=24.0.0`, pnpm `11.26.0`, Docker.

```bash
pnpm install
cp backend-main/.env.example backend-main/.env
pnpm db:up
pnpm db:migrate
pnpm db:generate
pnpm db:seed
```

`.env`가 이미 있으면 복사하지 말고 기존 값을 사용하세요. 프런트엔드 개발 서버는 `http://localhost:5173`, 백엔드 API는 `http://localhost:3000`에서 실행합니다. Vite 개발 프록시가 `/api` 요청을 백엔드로 전달합니다.

프런트엔드와 백엔드를 함께 실행하려면:

```bash
pnpm dev
```

각 서버를 따로 실행할 수도 있습니다.

```bash
pnpm dev:backend
pnpm dev:frontend
```

## 자주 쓰는 명령

| 명령 | 설명 |
| --- | --- |
| `pnpm dev:backend` | Express 개발 서버 |
| `pnpm dev:frontend` | Vite 개발 서버 |
| `pnpm build` | 프런트엔드 프로덕션 빌드 |
| `pnpm lint` | 프런트엔드 ESLint |
| `pnpm test` | 백엔드 단위 테스트 |
| `pnpm test:db` | 로컬 DB 연결 및 seed 데이터 검증 |
| `pnpm db:up` / `pnpm db:down` | 로컬 PostgreSQL 시작 / 중지 |
| `pnpm db:migrate` | 기존 Prisma migration 적용 |
| `pnpm db:generate` | Prisma Client 생성 |
| `pnpm db:seed` | 고정 영화 JSON을 DB에 반영 |

개별 패키지 명령은 `pnpm --filter cinefund-db <명령>` 또는 `pnpm --filter cine-fund <명령>`으로 실행할 수 있습니다. 상세한 데이터·API·작업 규칙은 각 패키지의 `README.md`, `AGENTS.md`, `docs/`를 참고하세요.

## 검증 상태

백엔드 단위 테스트, DB 연결 테스트, 프런트엔드 빌드는 각각 별도 명령입니다. API 코드가 구현되어 있어도 DB 적재, 브라우저 연동, 배포 환경 검증을 의미하지는 않습니다.
