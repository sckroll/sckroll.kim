# Phase 02 — 디자인 시스템과 핵심 화면

## 상태

- 상태: 대기
- 진입 조건: Phase 01 완료
- 목적: 구현 전에 필요한 최소 디자인 언어와 화면 계약 확정
- 디자인 도구: Figma와 관련 MCP
- 콘텐츠 입력: 승인된 더미 fixture

## 사용자 체크리스트 — 시각 방향

- [ ] 사이트를 표현할 브랜드 키워드 3개 선정
- [ ] 참고 사이트와 선호 요소 3개 이내 정리
- [ ] 피하고 싶은 시각 표현 정리
- [ ] 라이트 테마 단독 또는 다크 테마 포함 범위 결정
- [ ] 한글·영문 폰트 후보 승인
- [ ] 컬러 분위기와 강조색 승인
- [ ] Bento의 밀도와 여백 방향 승인
- [ ] 재미·위트 타일의 표현 강도 승인
- [ ] 로고 인트로의 분위기와 최대 지속 시간 승인

## 사용자 체크리스트 — 디자인 시스템 Foundation

- [ ] semantic color 역할 승인
- [ ] 텍스트·배경·경계·상태 컬러의 대비 확인
- [ ] typography scale과 line-height 승인
- [ ] spacing scale 승인
- [ ] radius·border·shadow 규칙 승인
- [ ] 모바일·태블릿·데스크톱 breakpoint 승인
- [ ] 모바일 우선 grid와 최대 콘텐츠 폭 승인
- [ ] 아이콘 크기와 stroke 규칙 승인
- [ ] focus ring 규칙 승인
- [ ] duration·easing·reduced-motion 규칙 승인

## 사용자 체크리스트 — 핵심 컴포넌트

- [ ] `Button` 디자인과 상태 승인
- [ ] `Link`와 본문 링크 디자인 승인
- [ ] `IconButton` 디자인과 accessible name 규칙 승인
- [ ] 전역 Navigation과 모바일 메뉴 승인
- [ ] Bento Tile과 Card variant 승인
- [ ] 프로젝트·포스트 Thumbnail 승인
- [ ] Badge·Tag 디자인 승인
- [ ] Collapsible·더보기 디자인 승인
- [ ] 본문 typography와 코드 블록 스타일 승인
- [ ] 빈 상태·오류 상태·로딩 상태 승인

## 사용자 체크리스트 — 핵심 화면

- [ ] 홈 모바일 화면 승인
- [ ] 포트폴리오 상세 모바일 화면 승인
- [ ] 홈 데스크톱 Bento 화면 승인
- [ ] `/about`의 정보 구조 확인
- [ ] `/resume`의 정보 구조 확인
- [ ] `/posts`·`/portfolio` 목록 재사용 가능성 확인
- [ ] 320 CSS px reflow 확인
- [ ] 긴 제목·요약·태그의 레이아웃 확인
- [ ] 이미지 없는 카드의 레이아웃 확인

## 에이전트 지원 체크리스트

- [ ] Figma 파일과 페이지 구조 제안
- [ ] Figma Variables 기반 Foundation 구성
- [ ] Base UI 구조와 대응하는 핵심 컴포넌트 구성
- [ ] 상태·variant·반응형 속성 정의
- [ ] 더미 fixture를 반영한 실제 길이 화면 구성
- [ ] 색상 대비와 조작 영역 검증
- [ ] 모션 원칙과 reduced-motion 대안 정의
- [ ] 디자인 결정의 컨텍스트 문서 반영

## Figma MCP 사용 시점

- [ ] Figma 파일 생성 전 관련 Figma 스킬 확인
- [ ] 변수와 컴포넌트 명명 규칙 합의 이후 MCP 작업
- [ ] 핵심 컴포넌트 구조 안정 이후 코드 연결 검토
- [ ] 코드 API 안정 이후 Code Connect 검토
- [ ] 사용자 승인 없는 Figma 외부 변경 금지

## 완료 조건

- [ ] Foundation 승인
- [ ] 핵심 컴포넌트 승인
- [ ] 핵심 3개 화면 승인
- [ ] 접근성 제약의 디자인 반영 확인
- [ ] 더미 콘텐츠의 정상·경계 사례 반영 확인
- [ ] 구현 가능한 토큰과 컴포넌트 명세 확보
- [ ] Phase 03 최종 명세 작성 승인
