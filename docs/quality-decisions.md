# 품질 결정 기록

## 문서 상태

- 2026-07-18 기준의 검토용 품질 결정
- 접근성·성능·검색 방향과 테스트 제안의 재검수 대상
- 최종 명세와 완료 기준의 미확정 상태

## 접근성 확정 방향

- 목표 기준: WCAG 2.2 AA
- 상세 수용 기준의 최종 명세 단계 재검수
- `lang="ko"`, skip link, landmark, 논리적 heading 구조
- 프로젝트 작성 규칙으로 페이지별 하나의 대표 `h1`
- 키보드 전 구간 조작과 명확한 `focus-visible`
- 포커스 표시와 포커스 대상의 가림 방지
- DOM·시각·탭 순서의 일치
- 일반 텍스트 4.5:1과 큰 텍스트 3:1 이상의 명도 대비
- 비텍스트 UI·포커스 표시 3:1 이상의 대비와 색상 단독 정보 전달 금지
- 최소 24×24 CSS px와 프로젝트 목표 44×44 CSS px의 조작 영역
- 아이콘 단독 컨트롤의 accessible name 제공
- 더보기 상태의 `aria-expanded` 제공
- 추가 타일 표시 후 사용자 포커스의 안정적 유지
- `prefers-reduced-motion` 환경의 인트로·이동 효과 축소
- 다른 콘텐츠와 병행되는 5초 초과 자동 모션의 일시정지·중지·숨김 수단 제공
- 정보 이미지의 문맥형 대체 텍스트와 장식 이미지의 빈 대체 텍스트
- 음성 포함 사전 녹화 영상의 동기화 자막 제공
- 중요한 시각 정보의 오디오 설명과 필요한 대본 제공
- 320 CSS px reflow, 200% 텍스트 확대, 400% 페이지 확대 검증
- 영어 문구와 콘텐츠 조각의 `lang="en"` 지정

## 성능 확정 방향

- 모바일·데스크톱을 분리한 실제 사용자 p75 측정
- 각 측정군의 LCP 2.5초 이하 목표
- INP 200ms 이하와 CLS 0.1 이하 목표
- 첫 화면 LCP 이미지의 초기 HTML 발견 가능성 확보
- 단일 LCP 후보의 선택적 높은 fetch priority 적용
- LCP 후보 이미지의 lazy loading 제외
- 이미지 크기·비율 예약과 정확한 `sizes` 제공
- 비핵심 이미지의 지연 로드
- 일반 게시용 이미지의 Vercel Blob 배치와 버전형 불변 URL 사용
- `next/font` 기반 자체 호스팅과 사용 subset·weight 최소화
- 사용자 재생 영상의 poster와 `preload="none"` 기본
- 사용자 재생 영상의 네이티브 컨트롤과 하단 source 연결 지연
- 외부 iframe 플레이어의 제목 제공과 오디오 자동 재생 제한
- 외부 영상 플레이어의 썸네일 facade 적용
- Blender 원본보다 웹용 파생 이미지·영상 우선
- 런타임 3D 뷰어의 사용자 동작 이후 로드
- 무거운 라이브러리의 필요한 화면 단위 동적 로드
- Server Component 기본과 Client Island 격리
- Notion 콘텐츠의 정적 우선 렌더링과 태그 기반 캐시 무효화
- `transform`과 `opacity` 중심의 모션 구성
- 이미지·영상·초기 JavaScript 용량 예산의 후속 확정

## GEO·AEO·SEO 확정 방향

- 크롤 가능한 서버 렌더링 HTML 제공
- 페이지별 title, description, canonical, Open Graph 이미지 제공
- `sitemap.ts`, `robots.ts`, 올바른 404와 redirect 구성
- 핵심 경력·프로젝트 정보의 HTML 텍스트 제공
- 홈의 `WebSite` 구조화 데이터
- 소개의 `ProfilePage`와 `Person` 구조화 데이터
- 포스트의 `BlogPosting` 구조화 데이터
- 의미 있는 2단계 이상 상세 경로의 `BreadcrumbList` 구조화 데이터
- 영상 중심 전용 페이지의 `VideoObject` 후속 적용
- 보이는 내용과 JSON-LD의 일치
- 고유한 실제 경험과 명확한 근거 중심의 콘텐츠
- Google Search 기준의 기존 SEO 체계 내 GEO·AEO 처리
- 구조화 데이터의 순위와 검색 기능 노출 비보장
- 특별한 AI 전용 schema의 미사용
- AI 전용 마크업과 `llms.txt`의 MVP 제외
- JSON-LD의 `<` 문자 escape와 화면 데이터 일치 검증
- Google 지원 유형의 Rich Results Test와 전체 Schema.org 구조의 Schema Markup Validator 검증
- 출시 후 URL Inspection 기반 색인 확인
- Search Console 기반의 색인·검색 성과·구조화 데이터 관측
- 지원 시 Search Console 생성형 AI 성과의 별도 관측
- RUM 또는 Speed Insights 기반의 실제 사용자 성능 관측
- Lighthouse와 PageSpeed Insights의 진단·회귀 탐지 용도

## Playwright 확정 방향

- Playwright seed fixture와 시나리오 명세 기반 E2E
- 홈 포지셔닝, 주요 CTA, 목록·상세 이동, 더보기, 404의 핵심 여정
- role과 accessible name 중심 locator
- 필요한 영역의 ARIA snapshot
- reduced-motion과 Mobile WebKit 검증
- 키보드, VoiceOver, 확대, reflow의 수동 점검
- 배포 전 Chromium·Firefox·WebKit 핵심 여정 검증
- 시각 디자인 확정 전 시각 회귀 테스트 보류

## 추가 테스트와 CI 제안

- Notion 변환과 공개 필터의 Vitest 계약 테스트
- 실 Notion 호출을 제거한 익명화 fixture 기반 CI
- CI 후보: format, lint, typecheck, unit, build, Chromium·Mobile WebKit smoke

## Playwright 운영 방식

```text
E2E 시나리오 명세
        ↓
seed fixture 기반 실행
        ↓
playwright-cli 탐색·locator 생성
        ↓
@playwright/test 회귀 테스트
        ↓
--debug=cli 연결과 실패 진단
```

- 시나리오별 독립적인 seed 상태
- 사용자 수준의 단계와 관찰 가능한 기대 결과 기록
- 임의 sleep과 `networkidle` 사용 금지
- 실패 시 locator·앱 오류·요청·명세 불일치의 순차 진단
- 사용자 의도 확인이 필요한 명세·동작 충돌의 자동 수정 금지

## 애니메이션 도구 제안

- 기본 후보: Motion
- 적용 대상: 로고 인트로, 타일 등장, 간단한 레이아웃 전환
- GSAP 재검토 조건: 복잡한 타임라인과 스크롤 연출의 디자인 확정
- Motion과 GSAP의 동시 도입 금지
- 인트로 완료 전 핵심 콘텐츠와 탐색의 접근 가능성 유지

## 분석과 개인정보 확정 방향

- 유입 분석 도구의 Google Analytics 4 사용
- Google Tag Manager 없는 직접 GA4 연동
- 한국 대상 MVP의 사전 동의 화면 없는 GA4 즉시 로드
- 2026-07-20 조사 기준의 분석 쿠키에 대한 일률적 사전 동의 의무 미확인
- Google Signals·광고 개인화·광고 계정 연결·User-ID·사용자 제공 데이터의 MVP 제외
- URL·페이지 제목·이벤트 매개변수의 개인 식별 정보 포함 금지
- 기본 페이지 조회와 이력서 PDF 다운로드 중심의 최소 이벤트 수집
- 개인정보 처리방침의 수집 항목·목적·보유 기간·거부 방법 공개
- Google의 처리와 국외 처리 관련 사항의 실제 설정 기준 공개
- 쿠키 삭제 또는 분석 비활성화를 위한 지속 가능한 거부 수단 제공
- 해외 이용자 대상 확장과 광고 기능 추가 전 지역별 동의 요구 재검토
- 식별 가능성 또는 국외 이전의 적법 근거가 불명확한 구성의 사전 동의 방식 전환

## 후속 운영 검토

- 출시 전 GA4 실제 설정과 국외 처리 고지 문구의 법률 검토
- 자체 RUM 데이터의 저장소·보존 기간·개인정보 처리
- CI 성능 회귀 임계값과 실패 정책
- 지원 브라우저·저사양 기기·네트워크 테스트 범위
- 출시 후 실제 검색·Core Web Vitals 데이터 기반 재조정 시점
