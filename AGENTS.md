# 저장소 작업 지침

## 문서 목적

- 모든 에이전트와 개발 도구가 공유하는 작업 기준
- 새 디바이스와 새 세션에서 동일한 맥락을 복원하기 위한 진입점
- 최종 명세 확정 전 검토용 컨텍스트의 보존

## 필수 진입 절차

1. `AGENTS.md` 전체 확인
2. [`docs/README.md`](docs/README.md)의 문서 지도 확인
3. [`docs/project-context.md`](docs/project-context.md)의 목표와 범위 확인
4. [`docs/technical-decisions.md`](docs/technical-decisions.md)의 기술 결정 확인
5. [`docs/notion-context.md`](docs/notion-context.md)의 데이터 소스와 스키마 상태 확인
6. [`docs/quality-decisions.md`](docs/quality-decisions.md)의 접근성·성능·검색·테스트 결정 확인
7. [`docs/review-backlog.md`](docs/review-backlog.md)의 미결정 사항과 다음 단계 확인
8. [`docs/todos/README.md`](docs/todos/README.md)의 현재 Phase와 체크리스트 확인
9. `git status`와 최근 커밋을 통한 사용자 변경 사항 확인
10. 현재 단계에 필요한 스킬과 공식 문서의 최신 내용 확인

## 현재 프로젝트 상태

- 개인 웹사이트 리뉴얼의 기획 및 기술 설계 단계
- 국내 채용 담당자와 면접관 중심의 초기 사용자 설정
- 프론트엔드 전문성을 기반으로 Product Engineer로 확장하는 포지셔닝
- 최종 명세와 구현 계획의 미확정 상태
- 시각 디자인과 디자인 시스템 작업의 후속 단계 배치
- 애플리케이션 스캐폴딩과 기능 구현의 미착수 상태
- Sckroll 워크스페이스의 Notion 스키마 변경 미착수 상태
- Phase 01 MVP 결정과 더미 콘텐츠 계약 검수 단계

## 유지할 핵심 결정

- 공개 포스트 데이터 소스로 `POSTS` 데이터베이스 사용
- 프로젝트 데이터 소스로 `PROJECTS` 데이터베이스 사용
- 미션·비전·핵심 가치의 근거로 `RESOURCES`의 `내 삶의 미션, 비전과 목표` 페이지 사용
- React와 Next.js App Router 중심의 정적 우선 아키텍처
- Server Component 기본과 작은 Client Island 구성
- Base UI의 기능별 시맨틱 요소 유지
- 이동 기능의 링크 요소와 실행 기능의 버튼 요소 사용
- 모바일 우선과 WCAG 2.2 AA 수준의 접근성 목표
- `@playwright/test` 기반 E2E와 `playwright-cli` 기반 탐색·생성·디버깅
- Notion 런타임 연동의 서버 전용 SDK 사용
- `ntn`의 개발·조회·관리 용도 한정
- 디자인 확정 전 Storybook과 시각 회귀 테스트의 보류
- 대표 콘텐츠 선정과 개발 작업의 병렬 진행
- 실제 콘텐츠 준비 전 도메인 계약 기반 더미 fixture 사용

## 작업 제한

- 사용자 재검수 전 최종 명세 파일 작성 금지
- 최종 명세 승인 전 구현 계획 전환 금지
- 별도 승인 전 Notion 데이터베이스와 페이지의 쓰기 작업 금지
- 사용자 토큰과 비밀 값의 문서·소스·커밋 포함 금지
- 사용자 기존 변경 사항의 임의 수정·삭제 금지
- 확정 사항과 제안 사항의 상태 혼합 금지
- 복잡성의 근거가 없는 라이브러리와 추상화 추가 금지

## 문서 규칙

- 한국어 본문 작성
- 문장과 목록 항목의 명사형 종결
- A/B 대조형 문구의 남발 금지
- 파일당 200줄 이하 유지
- 최종 명세와 검토용 컨텍스트 문서의 분리
- 결정 변경 시 관련 컨텍스트 문서의 동시 갱신
- 날짜가 필요한 결정의 `YYYY-MM-DD` 형식 기록

## 개발 원칙

- 접근성 요구의 기능 요구사항 취급
- 링크·버튼·랜드마크·제목 구조의 네이티브 시맨틱 우선
- CSS Grid 시각 순서와 DOM·탭 순서의 일치
- 외부 데이터 경계의 런타임 검증과 사이트 모델 변환
- Notion 장애와 호출 제한을 고려한 캐시 및 오류 격리
- 실제 사용자 관점의 테스트 시나리오 작성
- role과 accessible name 중심의 Playwright locator 사용
- 고정 sleep과 `networkidle` 기반 대기의 금지
- 공식 문서 기반의 최신 버전과 API 확인

## 도구 사용 원칙

- Notion 조회와 추후 관리 작업의 `ntn` 사용
- 브라우저 탐색과 locator 생성의 `playwright-cli` 사용
- 지속 가능한 회귀 테스트의 `@playwright/test` 사용
- 시각 디자인 단계의 Figma와 관련 MCP 사용 예정
- 파일 검색의 `rg`와 `rg --files` 우선 사용
- 파일 수정의 `apply_patch` 우선 사용

## 커밋 규칙

- Conventional Commits 형식 준수
- scope 생략
- 한국어 제목 작성
- 제목과 본문의 명사형 종결
- 필요한 본문의 간결한 목록 구성
- 예시 형식: `docs: 프로젝트 컨텍스트 기록`

## 세션 종료 절차

1. 변경된 결정과 미결정 사항의 문서 반영
2. 파일별 200줄 제한 확인
3. 명사형 종결과 금지 표현 확인
4. 링크와 식별자 정확성 확인
5. `git diff --check`와 `git status` 확인
6. 검증 결과와 다음 작업의 사용자 공유
