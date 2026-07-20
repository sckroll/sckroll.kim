# Phase 06 — 품질 검증과 Release Candidate

## 상태

- 상태: 대기
- 진입 조건: Phase 05 완료
- 목적: 접근성·기능·성능·검색·디자인 수용 기준 충족
- 실제 콘텐츠 의존성: 기술 검증 비차단

## 자동 품질 게이트

- [ ] format check 성공
- [ ] ESLint 성공
- [ ] TypeScript typecheck 성공
- [ ] Vitest 계약 테스트 성공
- [ ] production build 성공
- [ ] Chromium E2E 성공
- [ ] Mobile WebKit E2E 성공
- [ ] Firefox 핵심 여정 성공
- [ ] 실패 시 trace·console·request 기록 확인
- [ ] 임의 sleep과 `networkidle` 미사용 확인

## Playwright 사용자 여정

- [ ] 홈에서 정체성·대표 프로젝트·이력서 CTA 확인
- [ ] 프로젝트 목록과 상세 이동 확인
- [ ] 포스트 목록과 상세 이동 확인
- [ ] Bento 더보기 상태와 포커스 유지 확인
- [ ] 인트로 중 핵심 콘텐츠 접근 가능성 확인
- [ ] reduced-motion의 모션 축소 확인
- [ ] 메일·GitHub 링크 시맨틱 확인
- [ ] 빈 상태·404·오류 상태 확인
- [ ] back·forward 탐색과 URL 상태 확인

## 수동 접근성 검증

- [ ] skip link와 landmark 탐색 확인
- [ ] 키보드 전 구간 탐색 확인
- [ ] 포커스 순서와 시각 순서 일치 확인
- [ ] 포커스 표시와 가림 방지 확인
- [ ] VoiceOver 기본 흐름 확인
- [ ] 320 CSS px reflow 확인
- [ ] 200% 텍스트 확대 확인
- [ ] 400% 페이지 확대 확인
- [ ] 텍스트·비텍스트 대비 확인
- [ ] 조작 영역 크기 확인
- [ ] 이미지 대체 텍스트 확인
- [ ] 영상 자막·대본·오디오 설명 확인

## 성능 검증

- [ ] 모바일·데스크톱 Lighthouse 기준선 측정
- [ ] LCP 이미지의 초기 HTML 발견 가능성 확인
- [ ] LCP 이미지 lazy loading 제외 확인
- [ ] 이미지 크기·비율·`sizes` 확인
- [ ] 비핵심 미디어 지연 로드 확인
- [ ] 초기 JavaScript와 미디어 용량 확인
- [ ] CLS 발생 요소 확인
- [ ] 긴 task와 INP 위험 확인
- [ ] Motion·3D·영상 라이브러리의 동적 로드 확인
- [ ] 실제 사용자 성능 수집 방식 확정

## GEO·AEO·SEO 검증

- [ ] 페이지별 title·description·canonical 확인
- [ ] Open Graph 이미지 확인
- [ ] `sitemap.ts`와 `robots.ts` 확인
- [ ] 404·redirect·내부 링크 확인
- [ ] 홈 `WebSite` JSON-LD 확인
- [ ] 소개 `ProfilePage`·`Person` JSON-LD 확인
- [ ] 포스트 `BlogPosting` JSON-LD 확인
- [ ] 의미 있는 경로의 `BreadcrumbList` 확인
- [ ] JSON-LD와 화면 콘텐츠의 일치 확인
- [ ] Rich Results Test와 Schema Markup Validator 확인

## 디자인 QA

- [ ] Figma와 핵심 화면 비교
- [ ] 모바일·태블릿·데스크톱 breakpoint 확인
- [ ] 긴 콘텐츠와 미디어 없는 상태 확인
- [ ] hover·focus·disabled·loading 상태 확인
- [ ] 타이포그래피와 grid 일관성 확인
- [ ] 모션 duration·easing·reduced-motion 확인
- [ ] 디자인 시스템 변경의 Figma·코드 동시 반영
- [ ] 시각 회귀 테스트 도입 필요성 재검토

## 사용자 Release Candidate 검수

- [ ] 채용 담당자 30~60초 이해 가능성 검수
- [ ] 대표 프로젝트와 이력서 도달성 검수
- [ ] 모바일 완성도 검수
- [ ] 콘텐츠 교체 편의성 검수
- [ ] 공개 전 남은 차단 항목 확인
- [ ] Phase 07 착수 승인

## 완료 조건

- [ ] 자동 품질 게이트 전부 성공
- [ ] 접근성 수동 점검 완료
- [ ] 성능 목표의 기준선 확보
- [ ] 검색·구조화 데이터 검증 완료
- [ ] 디자인 QA 완료
- [ ] Release Candidate 사용자 승인
