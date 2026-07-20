# Phase 04 — 개발 기반과 세로 단면

## 상태

- 상태: 대기
- 진입 조건: Phase 03 완료
- 목적: 더미 fixture 기반의 채용 담당자 핵심 사용자 흐름 구현
- Notion 스키마 의존성: 없음

## 착수 전 사용자 체크리스트

- [ ] 구현 계획 최종 승인 확인
- [ ] Figma Foundation과 핵심 화면 승인 확인
- [ ] 패키지 매니저와 런타임 기준 확인
- [ ] 배포 전 로컬·preview 범위 확인
- [ ] 더미 콘텐츠의 샘플 표기 확인

## 프로젝트 기반 체크리스트

- [ ] 최신 안정 버전 공식 문서 재확인
- [ ] Next.js App Router와 TypeScript 스캐폴딩
- [ ] Tailwind CSS 설정
- [ ] CSS 변수와 Figma 토큰 연결
- [ ] Base UI의 필요한 primitive 설치
- [ ] ESLint·Prettier·typecheck 설정
- [ ] Vitest·Playwright 설치와 기본 설정
- [ ] 환경 변수 예시와 비밀 값 제외 설정
- [ ] 경로 alias와 디렉터리 경계 설정
- [ ] GitHub Actions 기본 품질 게이트 설정

## 도메인과 fixture 체크리스트

- [ ] `Project`, `Post`, `SiteProfile` 타입 작성
- [ ] 런타임 schema 작성
- [ ] 콘텐츠 repository interface 작성
- [ ] 더미 fixture adapter 작성
- [ ] 정상·경계·비공개 fixture 작성
- [ ] 고정 날짜·slug·미디어 URL 적용
- [ ] 공개 빌드의 더미 데이터 안전장치 작성
- [ ] 변환과 필터 계약 테스트 작성

## 공통 UI 체크리스트

- [ ] `lang="ko"`와 metadata 기본값 구성
- [ ] skip link 구성
- [ ] header·nav·main·footer landmark 구성
- [ ] Navigation과 모바일 메뉴 구성
- [ ] Link·Button·IconButton 스타일 primitive 구성
- [ ] Bento Tile·Card·Thumbnail 구성
- [ ] Badge·Tag·Collapsible 구성
- [ ] focus-visible과 reduced-motion 기본값 구성
- [ ] 오류 경계와 404 기본 화면 구성

## 핵심 세로 단면 체크리스트

- [ ] 홈 인사말과 포지셔닝 구성
- [ ] 대표 프로젝트 Bento 타일 구성
- [ ] 대표 포스트와 TMI 타일 구성
- [ ] 시계·날짜 Client Island 구성
- [ ] 더보기 동작과 `aria-expanded` 구성
- [ ] 포트폴리오 목록 이동 구성
- [ ] 포트폴리오 상세 이동 구성
- [ ] 이력서·메일·GitHub CTA 구성
- [ ] 로고 인트로의 접근 가능한 기본 동작 구성

## Playwright 체크리스트

- [ ] seed fixture 작성
- [ ] 핵심 사용자 여정 명세 작성
- [ ] `playwright-cli` 기반 요소·흐름 탐색
- [ ] role·accessible name locator 생성
- [ ] 홈→프로젝트→이력서→연락처 E2E 작성
- [ ] 더보기와 reduced-motion E2E 작성
- [ ] Chromium·Mobile WebKit smoke 실행

## 사용자 검수 체크리스트

- [ ] 모바일 핵심 흐름 검수
- [ ] 데스크톱 Bento 흐름 검수
- [ ] 디자인 시스템 반영 정도 검수
- [ ] 더미 콘텐츠의 실제 콘텐츠 교체 가능성 검수
- [ ] 다음 Phase의 Notion 쓰기 승인 여부 결정

## 완료 조건

- [ ] production build 성공
- [ ] 핵심 계약 테스트 성공
- [ ] 핵심 Playwright 테스트 성공
- [ ] 키보드 기반 핵심 흐름 사용 가능
- [ ] 더미 fixture 기반 세로 단면 사용자 승인
- [ ] Phase 05 착수 승인
