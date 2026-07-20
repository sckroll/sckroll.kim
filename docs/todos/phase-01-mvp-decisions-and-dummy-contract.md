# Phase 01 — MVP 결정과 더미 콘텐츠 계약

## 상태

- 상태: 진행 중
- 진입일: 2026-07-20
- 목적: 디자인과 최종 명세를 차단하는 미결정 사항의 해소
- 대표 콘텐츠 의존성: 비차단

## 이미 완료된 항목

- [x] 라우트 구조 확정
- [x] 홈의 채용 담당자 우선 정보 구조 확정
- [x] `POSTS`와 `PROJECTS` 데이터 경계 확정
- [x] 접근성·성능·검색의 목표 방향 확정
- [x] Base UI 시맨틱 사용 원칙 확정
- [x] 대표 콘텐츠 선정의 병렬 트랙 전환
- [x] 더미 fixture 기반 개발 방향 확정

## 사용자 체크리스트 — 제품 기본값

- [x] canonical 기준 도메인의 `https://sckroll.kim` 확정
- [x] MVP의 한국어 중심 콘텐츠 확정
- [x] 홈 시계의 `Asia/Seoul` 기준 확정
- [x] 웹 이력서 우선과 같은 페이지의 PDF 다운로드 확정
- [x] 하단 저작권 기호와 현재 연도 처리 방식 확정
- [x] analytics 수집 범위와 개인정보 처리 방향 확정

## 사용자 체크리스트 — 인프라와 콘텐츠

- [x] 초기 호스팅의 Vercel 채택 확정
- [x] 일반 이미지 저장소의 Vercel Blob 확정
- [x] 장편 영상의 외부 영상 서비스 사용 범위 확정
- [x] Notion Markdown API 우선과 Block API 보완 방식 확정
- [x] 미지원 Notion 블록의 식별 가능한 fallback 정책 확정
- [x] Webhook의 최초 릴리스 제외 확정
- [x] 시간 기반 재검증 범위 확정

## 이번 검수에서 확정된 세부 사항

- 모바일의 저작권과 제작자 문구 두 줄 배치
- 그 외 화면의 두 문구 한 줄 배치
- `Asia/Seoul` 기준 현재 연도의 동적 반영
- 일반 게시용 이미지의 Vercel Blob 저장
- 장편 영상의 Vercel Blob 저장 범위 제외
- 장편 영상의 YouTube 공개·일부 공개 업로드
- 썸네일 facade 이후 `youtube-nocookie.com` 플레이어 로드
- 일부 공개 영상의 링크 보유자 접근 가능성 인지
- 저장량·전송량 증가 시 Cloudflare R2 재검토
- 일반 본문의 Notion Markdown API 우선 조회
- 구조·메타데이터 보존이 필요한 블록의 Block API 선택 조회
- Block API의 pagination과 `has_children` 기반 재귀 조회
- Notion 파일 URL 만료에 대응하는 재조회 또는 안정 URL 변환
- 전체 Notion 콘텐츠의 `cacheLife('hours')` 기반 1시간 서버 재검증
- Webhook 없는 단일 재검증 정책과 콘텐츠별 캐시 격리
- Google Tag Manager 없는 GA4 직접 연동
- 한국 대상 MVP의 사전 동의 화면 없는 최소 수집 GA4 즉시 로드
- Google Signals·광고 개인화·광고 계정 연결·User-ID·사용자 제공 데이터 제외
- 기본 페이지 조회와 이력서 PDF 다운로드 중심의 최소 이벤트 수집
- 개인정보 처리방침과 지속 가능한 분석 거부 수단 제공
- 해외 이용자 대상 확장과 광고 기능 추가 전 동의 요구 재검토
- 미지원 Notion 블록의 안전한 텍스트와 하위 콘텐츠 유지
- fallback 요소의 `notion-block--unsupported` 클래스와 원본 타입 속성
- 추후 전용 렌더러 교체를 위한 블록 타입별 매핑 경계

## 공식 문서 조사 기반 권장안


## 공식 조사 근거

- [GA4 웹사이트 설정](https://support.google.com/analytics/answer/14183469): 계정·속성·웹 데이터 스트림 구성
- [GA4 기본 수집 정보](https://support.google.com/analytics/answer/11593727): 클라이언트 식별자·세션·기기 정보 등의 기본 수집 범위
- [개인정보 보호법 제15조](https://law.go.kr/lsLinkCommonInfo.do?lsJoLnkSeq=1020398485): 개인정보 수집·이용의 적법 근거
- [개인정보 처리방침 작성지침](https://m.pipc.go.kr/np/cop/bbs/selectBoardArticle.do?bbsId=BS074&mCode=C020010000&nttId=11133): 쿠키와 맞춤형 광고의 거부권 안내
- [개인정보 국외 이전 안내](https://www.pipc.go.kr/np/default/page.do?mCode=D060040010): 국외 처리의 근거와 공개 의무
- [Notion Markdown 본문](https://developers.notion.com/guides/data-apis/working-with-markdown-content): 전체 본문과 `unknown_block_ids` 조회
- [Notion Block 객체](https://developers.notion.com/reference/block): 블록 타입·하위 블록·미지원 타입 구조
- [Notion 페이지 본문 조회](https://developers.notion.com/guides/data-apis/working-with-page-content): pagination과 하위 블록 재귀 조회
- [Next.js 시간 기반 재검증](https://nextjs.org/docs/app/getting-started/revalidating): `cacheLife` 기반 캐시 갱신
- [Vercel Blob 가격](https://vercel.com/docs/vercel-blob/usage-and-pricing): 저장·작업·전송량 기준
- [Cloudflare R2 가격](https://developers.cloudflare.com/r2/pricing/): 저장·작업과 무료 egress 기준
- [YouTube 임베드](https://support.google.com/youtube/answer/171780): 개인정보 보호 강화 모드
- [Vimeo 영상 공개 범위](https://help.vimeo.com/hc/en-us/articles/12426199699985): 일부 공개와 embed-only 범위
- [Cloudflare Stream 가격](https://developers.cloudflare.com/stream/pricing/): 저장·재생 시간 기준
- [Mux 가격](https://www.mux.com/pricing): 영상 수와 재생 시간 기반 무료·종량제 범위

## 사용자 체크리스트 — 개발 도구

- [x] npm 패키지 매니저 결정
- [x] Node.js 24 LTS 기준 확정
- [x] TypeScript 6 최신 안정 버전과 호환성 기준 확정
- [ ] ESLint와 Prettier 채택 확정
- [ ] 외부 데이터 검증의 Zod 채택 확정
- [ ] 변환 계약 테스트의 Vitest 채택 확정
- [ ] Motion의 Phase 04 또는 후속 도입 시점 확정
- [ ] Zustand와 TanStack Query의 MVP 제외 재확인

## 이번 검수에서 확정된 개발 도구

- npm 패키지 매니저 사용
- `package-lock.json` 생성과 커밋
- `packageManager` 필드의 실제 npm 버전 고정
- Node.js 24 LTS 메이저 버전 사용
- `.nvmrc` 또는 `.node-version`의 `24` 기록
- `engines.node`의 `>=24 <25` 범위 지정
- 24 계열 최신 보안 패치의 지속 적용
- TypeScript 6 최신 안정 버전과 `strict: true` 사용
- TypeScript·Next.js·ESLint·타입 패키지의 설치 시점 호환성 검증
- 필요한 전역 타입의 `types` 명시

## 더미 콘텐츠 계약

### 프로젝트 fixture

- [ ] 프로젝트 4개 구성
- [ ] 대표 프로젝트 2개 구성
- [ ] 비공개 프로젝트 1개 구성
- [ ] 긴 제목과 긴 요약을 가진 프로젝트 1개 구성
- [ ] 미디어가 없는 프로젝트 1개 구성
- [ ] 문제·역할·의사결정·성과·기술 스택 필드 포함

### 포스트 fixture

- [ ] 포스트 6개 구성
- [ ] 대표 포스트 2개 구성
- [ ] 초안 포스트 1개 구성
- [ ] 긴 제목과 다중 태그 포스트 1개 구성
- [ ] 대표 이미지 없는 포스트 1개 구성
- [ ] 기술·제품·AI 개발·취미 분류 포함

### 공통 fixture

- [ ] 프로필·소개·미션·핵심 가치 데이터 구성
- [ ] 이력서 타임라인 샘플 구성
- [ ] TMI 문자열 8개 이상 구성
- [ ] 고정 날짜와 안정적인 slug 사용
- [ ] 샘플 프로젝트·포스트의 명시적 표기
- [ ] 실제 회사명·제품명·수치·개인정보 미사용
- [ ] 공개 빌드에서 더미 데이터 제거 여부를 확인하는 안전장치 설계

## 에이전트 지원 체크리스트

- [ ] 미결정 항목별 추천안과 근거 정리
- [ ] `Project`, `Post`, `SiteProfile` 도메인 계약 초안 작성
- [ ] Notion 속성과 도메인 필드의 매핑표 작성
- [ ] 더미 fixture의 정상·경계·비공개 사례 정의
- [ ] 실제 콘텐츠 교체 절차 정의
- [ ] 사용자 결정의 컨텍스트 문서 반영

## 완료 조건

- [ ] 제품 기본값 전부 확정
- [ ] 인프라·콘텐츠 기본안 전부 확정
- [ ] 개발 도구의 도입·보류 상태 확정
- [ ] 더미 콘텐츠 수량과 데이터 계약 승인
- [ ] Notion 후속 스키마의 속성명·타입·필수 여부 승인
- [ ] Phase 02 디자인 시스템 착수 승인
