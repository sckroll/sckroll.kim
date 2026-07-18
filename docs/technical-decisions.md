# 기술 결정 기록

## 문서 상태

- 2026-07-18 기준의 검토용 기술 결정
- 확정 결정과 잠정 제안의 명시적 구분
- 최종 명세 작성 전의 재검수 대상

## 기본 기술 스택

### 확정 방향

- React 최신 안정 버전
- Next.js 최신 안정 버전과 App Router
- TypeScript
- Tailwind CSS
- Base UI
- Notion API와 공식 JavaScript SDK
- Playwright와 `playwright-cli`
- 설치 시점의 최신 안정 버전 재확인과 잠금 파일 고정

### 추가 권장 도구

- 외부 데이터 런타임 검증용 Zod
- Notion 변환 계약 테스트용 Vitest
- 코드 품질용 ESLint와 Prettier
- 일반 웹 미디어용 안정적 Blob 또는 CDN 저장소

### 잠정 인프라 후보

- Next.js 배포용 Vercel
- 안정적 미디어 저장용 Vercel Blob 또는 동등한 저장소

### MVP 보류 도구

- Zustand
- TanStack Query
- Storybook
- GSAP
- 런타임 3D 렌더링 라이브러리

### 사용 제외 도구

- shadcn/ui

## 상태 관리 원칙

- Server Component와 URL 상태의 우선 활용
- 단일 컴포넌트 상호작용의 지역 상태 활용
- 실제 전역 클라이언트 상태 요구 발생 시 Zustand 재검토
- 클라이언트 데이터 캐시 요구 발생 시 TanStack Query 재검토

## Base UI와 시맨틱 원칙

- Base UI의 headless interaction primitive 용도
- 실행과 상태 변경의 `Button` 또는 적절한 Trigger 사용
- 내부 이동의 Next.js `Link` 사용
- 외부 이동과 메일의 `<a>` 사용
- 링크와 버튼 외형의 공통 스타일 함수 공유
- 링크를 Base UI `Button`으로 변환하는 구성 금지
- `render` 합성 시 전달 props와 ref의 실제 DOM 연결
- 프로젝트 카드 전체 이동 기능의 링크 요소 구성
- Bento 더보기 기능의 버튼 또는 `Collapsible.Trigger` 구성

## 컴포넌트 경계

- 공통 레이아웃과 콘텐츠 렌더링의 Server Component 기본
- 시계, 더보기, 인트로, 필요한 애니메이션의 작은 Client Island 구성
- 페이지 전체의 Client Component 전환 금지
- 도메인 모델과 Notion 응답 타입의 분리
- 콘텐츠 조회, 변환, 렌더링, 상호작용의 책임 분리

## Notion 워크스페이스

- 대상 워크스페이스: `Sckroll`
- 개발·관리 CLI: `ntn`
- 런타임 접근: `server-only` 모듈의 공식 Notion SDK
- 2026-07-18 조사 기준 Notion API 버전 후보: `2026-03-11`
- 인증 토큰의 환경 변수와 배포 시크릿 보관
- Client Component와 브라우저 번들의 토큰 포함 금지

## Notion 데이터 소스

### POSTS

- 용도: 사이트 공개 포스트
- 상위 데이터베이스 ID: `3a1addb5-da7c-804a-8ac2-fdbee73650cf`
- 데이터 소스 ID: `3a1addb5-da7c-8052-8c9e-000b1c19d7e2`
- 현재 확인 속성: 제목 속성 `이름`
- 2026-07-18 기준 행 수: 0개
- 후속 스키마 후보: slug, 공개 상태, 게시 일시, 요약, 태그, 대표 이미지 또는 안정적 커버 URL, 대표 노출 여부, 외부 URL

### PROJECTS

- 용도: 사이트 공개 프로젝트
- 상위 데이터베이스 ID: `387f5ff1-ffea-4026-aa83-c3d1754d8775`
- 데이터 소스 ID: `3e8020fe-6969-4c1d-bad6-30ec461fa0ea`
- 현재 확인 속성: `기술 스택`, `분류`, `상태`, `설명`, `이름`, `중단 사유`, `포트폴리오 작성 여부`, `프로젝트 기간`
- 2026-07-18 기준 행 수: 40개
- 후속 스키마 후보: slug, 사이트 공개 상태, 대표 노출 여부 또는 정렬값, 역할, 성과·지표, 대표 이미지 또는 안정적 커버 URL, 서비스 URL, 저장소 URL, 공개용 맥락
- 프로젝트 진행 상태와 사이트 공개 상태의 별도 관리 방향
- 공개 상태 속성명·타입·옵션의 후속 확정 필요
- 이전 인라인 `Projects` 데이터 소스 `3b22e628-28b6-420b-8b65-19b1ce57e6c4`의 조회 대상 제외

### RESOURCES

- 용도: 미션·비전·핵심 가치의 근거 조회
- 참조 페이지: `내 삶의 미션, 비전과 목표`
- 참조 페이지 ID: `38eaddb5-da7c-804a-a8ca-ee5120f69232`
- 사이트 공개 포스트 조회 소스로 사용 금지

## Notion 스키마 작업 상태

- 실제 스키마 변경의 후속 작업 배치
- 사용자 검토와 명시적 승인 이후의 `ntn` 쓰기 작업
- 스키마 변경 전 fixture와 사이트 도메인 모델의 우선 작성 제안
- 변경 전 데이터 백업 또는 현재 스키마 기록 필요
- 상세 스키마와 조회 제약의 [`notion-context.md`](notion-context.md) 기록

## 콘텐츠 데이터 흐름

```text
POSTS / PROJECTS
        ↓
server-only Notion client
        ↓
런타임 검증과 사이트 모델 변환
        ↓
캐시와 태그
        ↓
Server Component
```

- Notion 응답 구조의 UI 직접 노출 금지
- 목록과 상세의 독립적인 조회·변환 함수 구성
- 공개 상태와 slug 검증 실패 항목의 공개 목록 제외
- 없는 상세 콘텐츠의 `notFound()` 처리
- warm cache 존재 시 Notion 장애 중 캐시된 공개 콘텐츠의 제공 방향

## 렌더링과 캐시

### 사용자 확인 방향

- 공개 페이지의 정적 우선 렌더링
- 목록·상세의 태그 기반 캐시 무효화
- Webhook과 시간 기반 재검증의 병행 방향
- 공개 콘텐츠와 후속 초안 미리보기의 렌더링 분리

### 잠정 구현안

- `cacheComponents: true`와 Node.js 런타임 조합
- Next.js Cache Components와 `'use cache'` 활용 방향
- `cacheLife`와 `cacheTag` 기반 SDK 함수 캐시
- 목록 태그 예시: `notion:posts`, `notion:projects`
- 상세 태그 예시: `notion:page:{pageId}`
- Notion Webhook의 변경 신호 활용
- Webhook raw body 서명 검증과 이벤트 중복·순서 역전 처리
- 이벤트 수신 후 최신 Notion 상태 재조회
- Route Handler의 `revalidateTag(tag, { expire: 0 })` 후보
- 웹훅 누락 대비 6~24시간 시간 기반 재검증 제안
- 태그 재검증 사용 시 정적 export 제외
- `ntn`의 웹사이트 런타임 의존성 제외

## Notion 오류와 미디어

- 429·529 응답의 `Retry-After` 준수와 제한된 재시도
- 목록·상세·홈 섹션의 오류 격리
- 사용자 화면의 토큰·내부 ID·원본 오류 메시지 노출 금지
- 1시간 유효기간의 Notion-hosted `file` URL 장기 저장 금지
- 게시용 이미지와 영상의 안정적 Blob 또는 CDN URL 사용 방향
- 미디어 자동 복제 파이프라인의 후속 검토

## 품질 결정 연결

- 접근성·성능·검색·테스트 세부 사항의 [`quality-decisions.md`](quality-decisions.md) 기록
