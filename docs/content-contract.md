# 콘텐츠 계약

## 문서 상태

- 2026-07-20 기준의 사용자 승인과 PROJECTS 재검수 상태를 반영한 검토용 계약
- 최종 명세 확정 전의 도메인·fixture·Notion 매핑 기준
- 실제 애플리케이션 구현과 Notion 스키마 변경의 미착수 상태
- POSTS 후속 스키마의 승인 상태
- PROJECTS 후속 스키마의 재검수 상태

## 공통 보조 타입

### `Reference`

- `label`: 화면에 표시할 링크 이름
- `url`: 검증을 통과한 외부 URL
- 포스트 최하단의 참고 자료 목록 용도
- 빈 배열을 허용하는 다중 항목 구조

### `ProfileSection`

- `id`: 섹션 식별자
- `title`: 섹션 제목
- `body`: Markdown 기반 섹션 본문
- `order`: 화면 표시 순서
- 취미·작업 원칙·현재 관심사 등의 확장 용도

### `Media`

- `src`: 안정적인 공개 미디어 URL
- `alt`: 문맥형 대체 텍스트
- `width`, `height`: 레이아웃 예약용 원본 비율 정보

## `Post` 도메인 모델

- `id`, `slug`, `title`, `summary`
- `status`: `draft` 또는 `published`
- `publishedAt`, `updatedAt`
- `category`, `tags`, `featured`
- `coverImage`: 선택형 `Media`
- `references`: `Reference[]`
- `body`: Markdown 본문과 보완 블록 정보
- 기존 `externalUrl` 후보의 제거

## `Project` 도메인 모델

- `id`, `slug`, `title`, `summary`
- `publicationStatus`: `private` 또는 `public`
- `projectStatus`, `portfolioStatus`
- `featuredOrder`, `period`, `category`
- `role`, `context`, `decisions`, `outcomes`
- `techStack`, `coverImage`
- `serviceUrl`, `repositoryUrl`
- `body`: Markdown 본문과 보완 블록 정보

## `SiteProfile` 도메인 모델

- `name`, `role`, `headline`, `bio`
- `mission`, `vision`, `coreValues`
- `contacts`, `resumeTimeline`, `resumePdfUrl`
- `tmiItems`
- `sections`: `ProfileSection[]`

## `POSTS` 후속 스키마

| Notion 속성 | 타입 | 사이트 필드 | 공개 조건 |
|---|---|---|---|
| 이름 | title | `title` | 필수 |
| Slug | rich_text | `slug` | 필수·고유 |
| 공개 상태 | select | `status` | `공개` |
| 게시 일시 | date | `publishedAt` | 필수 |
| 요약 | rich_text | `summary` | 필수 |
| 분류 | select | `category` | 필수 |
| 태그 | multi_select | `tags` | 선택 |
| 대표 이미지 | files | `coverImage` | 선택 |
| 대표 노출 | checkbox | `featured` | 기본 해제 |
| 참고 자료 | rich_text | `references` | 선택 |

- `공개 상태` 선택지의 `초안`, `공개` 구성
- `공개 상태` 기본값의 `초안` 구성
- `참고 자료`의 링크 이름과 hyperlink를 가진 복수 rich text 조각 구성
- hyperlink가 없는 구분 문자와 빈 조각의 변환 제외
- 공개 시 필수 조건의 Zod 변환 경계 검증

## `PROJECTS` 후속 스키마 제안

| Notion 속성 | 타입 | 사이트 필드 | 공개 조건 |
|---|---|---|---|
| 이름 | title | `title` | 필수 |
| 설명 | rich_text | `summary` | 필수 |
| Slug | rich_text | `slug` | 필수·고유 |
| 공개 상태 | select | `publicationStatus` | `공개` |
| 대표 순서 | number | `featuredOrder` | 선택 |
| 프로젝트 기간 | date | `period` | 필수 |
| 분류 | select | `category` | 필수 |
| 상태 | status | `projectStatus` | 필수 |
| 포트폴리오 작성 여부 | status | `portfolioStatus` | 운영용 |
| 역할 | rich_text | `role` | 필수 |
| 성과·지표 | rich_text | `outcomes` | 선택 |
| 기술 스택 | multi_select | `techStack` | 선택 |
| 대표 이미지 | files | `coverImage` | 선택 |
| 서비스 URL | url | `serviceUrl` | 선택 |
| 저장소 URL | url | `repositoryUrl` | 선택 |
| 공개용 맥락 | rich_text | `context` | 필수 |

- `공개 상태` 선택지의 `비공개`, `공개` 구성
- `공개 상태` 기본값의 `비공개` 구성
- 기존 프로젝트 진행 상태와 사이트 공개 상태의 분리
- 공개 시 필수 조건의 Zod 변환 경계 검증
- 기존 속성 사용 현황을 반영한 사용자 재승인 필요

## 더미 fixture 계약

- Phase 02의 화면 검증용 문구·길이·이미지 조건 작성
- Phase 04의 TypeScript fixture 파일 생성

### 프로젝트

- 전체 4개와 대표 프로젝트 2개 구성
- 비공개 사례 1개 구성
- 긴 제목·요약 사례 1개 구성
- 미디어 없는 사례 1개 구성
- 문제·역할·의사결정·성과·기술 스택 필드 포함

### 포스트

- 전체 6개와 대표 포스트 2개 구성
- 초안 사례 1개 구성
- 긴 제목·다중 태그 사례 1개 구성
- 대표 이미지 없는 사례 1개 구성
- 기술·제품·AI 개발·취미 분류 포함
- 참고 자료가 없거나 여러 개인 사례 포함

### 공통

- 프로필·소개·미션·핵심 가치와 확장 섹션 구성
- 이력서 타임라인 샘플과 TMI 8개 이상 구성
- 고정 날짜와 안정적인 slug 사용
- 샘플 상태의 화면 표시
- 실제 회사명·제품명·수치·개인정보 사용 금지
- production의 fixture adapter 사용을 막는 빌드 안전장치

## 실제 콘텐츠 교체 절차

1. 승인된 Notion 스키마의 별도 쓰기 승인
2. `ntn` 기반 현재 스키마 재조회와 복구 기준 기록
3. 최소 속성 추가와 property ID 재조회
4. 실제 콘텐츠 입력과 공개 조건 검증
5. Notion adapter의 도메인 계약 테스트
6. production 환경의 fixture adapter 차단 확인
7. 샘플 표기 미검출과 실제 콘텐츠 사용자 검수
