# Notion 연속성 컨텍스트

## 문서 상태

- 2026-07-18 KST 기준의 `ntn` 읽기 전용 재검증 결과
- Sckroll 워크스페이스의 현재 상태 기록
- 실제 데이터·스키마 변경 없는 조사 결과
- 최종 사이트 스키마의 미확정 상태

## 디바이스별 연결 원칙

- 현재 디바이스의 로컬 `ntn` 로그인 자격을 통한 Public API 조회 성공
- 현재 셸의 `NOTION_API_TOKEN` 미설정 상태
- 새 디바이스별 독립적인 `ntn` 인증 필요
- 인증 정보와 토큰의 문서·Git·브라우저 번들 포함 금지
- 현재 설치 확인 버전: `ntn 0.15.0`
- 실제 작업 시작 전 `ntn` 최신 안정 버전 재확인 필요
- Notion Worker 권한과 도입 계획의 현재 범위 제외

## 런타임 조회 원칙

- 목록 조회 기준으로 data source ID 사용
- 런타임 확정 방향: 공식 `@notionhq/client`
- 서버 전용 모듈과 환경 변수 기반 토큰 보관
- `import 'server-only'` 경계와 지연 초기화 getter 구성 후보
- 2026-07-18 조사 기준 API 버전 후보: `2026-03-11`
- 설치 시점의 SDK와 API 버전 호환성 재검증 필요

## POSTS 현재 상태

- 역할: 사이트 공개 포스트의 유일한 조회 대상
- 상위 데이터베이스 ID: `3a1addb5-da7c-804a-8ac2-fdbee73650cf`
- 데이터 소스 ID: `3a1addb5-da7c-8052-8c9e-000b1c19d7e2`
- 2026-07-18 기준 행 수: 0개

| 속성 | Property ID | 타입 |
|---|---|---|
| 이름 | `title` | `title` |

## PROJECTS 현재 상태

- 역할: 사이트 공개 프로젝트의 유일한 조회 대상
- 상위 데이터베이스 ID: `387f5ff1-ffea-4026-aa83-c3d1754d8775`
- 데이터 소스 ID: `3e8020fe-6969-4c1d-bad6-30ec461fa0ea`
- 2026-07-18 기준 행 수: 40개
- 이전 인라인 `Projects` 데이터 소스 `3b22e628-28b6-420b-8b65-19b1ce57e6c4` 제외

| 속성 | Property ID | 타입 |
|---|---|---|
| 이름 | `title` | `title` |
| 설명 | `prcT` | `rich_text` |
| 프로젝트 기간 | `h%7CWm` | `date` |
| 분류 | `Vgqw` | `select` |
| 상태 | `kLn%7C` | `status` |
| 포트폴리오 작성 여부 | `oG%7CK` | `status` |
| 기술 스택 | `kkxy` | `multi_select` |
| 중단 사유 | `%7BBF%3F` | `rich_text` |

### 현재 선택지

- 분류: `개인 프로젝트`, `재능교육`, `SSAFY`, `외주`
- 상태: `중단`, `보류`, `대기`, `진행 중`, `완료`
- 포트폴리오 작성 여부: `작성 전`, `작성 중`, `업데이트 필요`, `완료`
- 기술 스택: 44개 선택지
- 기술 스택 전체 선택지 기록의 API 재조회 우선

## RESOURCES 참조

- 역할: 미션·비전·핵심 가치의 근거
- 참조 페이지 제목: `내 삶의 미션, 비전과 목표`
- 참조 페이지 ID: `38eaddb5-da7c-804a-a8ca-ee5120f69232`
- 공개 포스트 조회 대상으로의 사용 금지

## 승인된 후속 스키마

- 세부 계약: [`content-contract.md`](content-contract.md)
- POSTS의 slug·공개·게시·분류·태그·미디어·대표·참고 자료 속성 추가
- PROJECTS의 slug·공개·대표 순서·역할·성과·미디어·URL·공개 맥락 속성 추가
- 기존 프로젝트 상태와 별도 공개 상태의 필요
- 기존 40개 행의 기본 비공개 유지
- 별도 사용자 승인 전 실제 스키마 변경 금지

## API와 콘텐츠 제약

- 연결당 평균 3 requests/sec와 워크스페이스 공유 한도
- 429·529 응답과 정수 초 `Retry-After` 처리 필요
- data source query의 page size 최대 100개
- `has_more`와 `next_cursor` 기반 pagination 필요
- Markdown API 기반의 일반 본문 조회와 변환 우선
- 구조·메타데이터 보존이 필요한 블록의 Block API 선택 조회
- Block API 사용 시 pagination과 하위 블록의 재귀 조회 적용
- Notion 파일 URL의 만료를 고려한 재조회 또는 안정 URL 변환
- 전체 공개 콘텐츠의 1시간 시간 기반 재검증
- Webhook 없는 단일 재검증 정책과 콘텐츠별 캐시 격리
- 미지원 Notion 블록의 식별 가능한 fallback 정책 확정
- 최초 릴리스의 Notion Webhook 제외
- Notion-hosted `file` URL의 1시간 유효기간
- external file URL과 Notion-hosted file URL의 별도 처리 필요
- 정적 HTML과 장기 캐시에 signed file URL 저장 금지

## 스키마 변경 안전 절차

1. 최종 속성 계약의 사용자 승인
2. 현재 스키마와 행 수의 재조회
3. 기존 데이터의 복구 가능 상태 확보
4. `ntn`을 통한 최소 변경 적용
5. property ID와 옵션의 재조회
6. TypeScript 사이트 모델과 fixture의 동시 갱신
7. 공개 필터와 변환 계약 테스트

## 공식 근거

- [Notion 인증](https://developers.notion.com/guides/get-started/authorization): 토큰과 연결 공유 방식
- [데이터 소스 조회](https://developers.notion.com/reference/retrieve-a-data-source): 스키마와 식별자 조회
- [데이터 소스 쿼리](https://developers.notion.com/reference/query-a-data-source): 목록·필터·페이지네이션
- [요청 한도](https://developers.notion.com/reference/request-limits): 요청 제한과 재시도
- [페이지 Markdown 조회](https://developers.notion.com/reference/retrieve-page-markdown): Markdown 본문 후보
- [파일 객체](https://developers.notion.com/reference/file-object): 파일 URL 유효기간
- [Webhook](https://developers.notion.com/reference/webhooks): 후속 실시간 갱신 검토 자료
