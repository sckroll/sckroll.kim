# Phase 05 — Notion 연동과 콘텐츠 페이지

## 상태

- 상태: 대기
- 진입 조건: Phase 04 완료
- 목적: 승인된 Notion 스키마와 실제 런타임 콘텐츠 계층 연결
- 외부 변경: 사용자 승인 이후의 Notion 쓰기 작업

## 사용자 승인 체크리스트

- [ ] `POSTS` 최종 속성명·타입·옵션 승인
- [ ] `PROJECTS` 최종 속성명·타입·옵션 승인
- [ ] 기존 40개 프로젝트의 마이그레이션 방식 승인
- [ ] Notion 스키마 쓰기 작업 승인
- [ ] 공개 상태와 대표 노출 규칙 승인
- [ ] 본문 렌더링 지원 블록 범위 승인
- [ ] 미디어 저장·복제 방식 승인
- [ ] Webhook 최초 릴리스 포함 여부 승인

## Notion 스키마 체크리스트

- [ ] 현재 database·data source ID 재확인
- [ ] 현재 속성과 행 수 기록
- [ ] 기존 데이터의 복구 가능 상태 확보
- [ ] `ntn` 최신 안정 버전 확인
- [ ] 최소 속성 변경 적용
- [ ] 변경 후 property ID·타입·옵션 재조회
- [ ] [`../notion-context.md`](../notion-context.md) 갱신
- [ ] fixture와 TypeScript 계약 갱신

## 런타임 연동 체크리스트

- [ ] 공식 Notion SDK의 server-only 모듈 구성
- [ ] 환경 변수 기반 토큰과 지연 초기화 구성
- [ ] API·SDK 호환 버전 고정
- [ ] data source query pagination 구성
- [ ] 공개 상태·slug·대표 노출 필터 구성
- [ ] 429·529와 `Retry-After` 처리
- [ ] Markdown API 기반 본문 변환 구성
- [ ] 지원 블록의 block API 보완 구성
- [ ] 미지원 블록의 대체·제외 처리
- [ ] Notion 응답과 사이트 도메인 모델 변환

## 캐시와 Webhook 체크리스트

- [ ] Cache Components와 Node.js 런타임 구성
- [ ] 목록·상세 `cacheTag` 구성
- [ ] `cacheLife` 시간 기반 안전망 구성
- [ ] warm cache 장애 동작 구성
- [ ] Webhook Route Handler 구성 여부 결정 반영
- [ ] Webhook raw body 서명 검증
- [ ] 이벤트 중복·순서 역전 처리
- [ ] 최신 Notion 상태 재조회
- [ ] 선택적 tag 무효화

## 미디어 체크리스트

- [ ] Notion-hosted file URL의 장기 저장 방지
- [ ] 안정적인 Blob·CDN URL 사용
- [ ] 이미지 크기·비율·`sizes` 구성
- [ ] 비핵심 이미지 지연 로드
- [ ] 영상 poster와 source 지연 연결
- [ ] 대체 텍스트·자막·대본 데이터 연결
- [ ] 미디어 없는 콘텐츠의 fallback 구성

## 페이지 체크리스트

- [ ] `/posts` 목록 연결
- [ ] `/posts/[slug]` 상세 연결
- [ ] `/portfolio` 목록 연결
- [ ] `/portfolio/[slug]` 상세 연결
- [ ] `/about`의 미션·비전·핵심 가치 연결
- [ ] `/resume`의 실제 데이터 교체 경로 구성
- [ ] 홈의 최신·대표 콘텐츠 연결
- [ ] 빈 목록·없는 slug·비공개 항목 처리
- [ ] fixture adapter와 Notion adapter의 계약 일치 확인

## 검증 체크리스트

- [ ] 익명화된 API fixture 계약 테스트
- [ ] 비공개·잘못된 slug 필터 테스트
- [ ] 빈 데이터와 API 오류 테스트
- [ ] 캐시 tag와 재검증 테스트
- [ ] 목록→상세 Playwright 테스트
- [ ] 비밀 값의 클라이언트 번들 제외 확인

## 완료 조건

- [ ] 승인된 스키마와 코드 계약의 일치
- [ ] 공개 콘텐츠 목록·상세의 안정적 렌더링
- [ ] Notion 장애의 오류 격리와 fallback 확인
- [ ] 실제 콘텐츠 교체 경로 확인
- [ ] Phase 06 착수 승인
