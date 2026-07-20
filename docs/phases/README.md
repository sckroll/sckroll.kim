# 프로젝트 Phase 로드맵

## 문서 상태

- 기준일: 2026-07-20
- 목적: 새 세션과 새 디바이스의 작업 재개 기준
- 범위: 검토·디자인·명세·개발·검증·배포의 단계별 체크리스트
- 최종 명세와 상세 구현 계획의 지위 미부여

## 상태 표기

- `완료`: 진입 조건과 완료 조건 충족 상태
- `진행 중`: 현재 사용자 검토와 결정이 필요한 상태
- `대기`: 선행 Phase 완료 전 착수 금지 상태
- `병렬`: 다른 Phase와 함께 진행 가능한 상태
- `[x]`: 확인 완료 항목
- `[ ]`: 확인 또는 작업 필요 항목

## 현재 위치

- 현재 Phase: `Phase 01 — MVP 결정과 더미 콘텐츠 계약`
- 완료 Phase: `Phase 00 — 컨텍스트 기준선`
- 병렬 트랙: `대표 콘텐츠 준비`
- 애플리케이션 구현 상태: 미착수
- Notion 스키마 변경 상태: 미착수
- 시각 디자인 상태: 미착수
- 최종 명세 상태: 미작성

## 전체 순서

| Phase | 상태 | 핵심 결과물 |
|---|---|---|
| [Phase 00](phase-00-context-baseline.md) | 완료 | 프로젝트 컨텍스트와 기술 방향 |
| [Phase 01](phase-01-mvp-decisions-and-dummy-contract.md) | 진행 중 | 미결정 사항과 더미 콘텐츠 계약 |
| [Phase 02](phase-02-design-system-and-key-screens.md) | 대기 | 최소 디자인 시스템과 핵심 화면 |
| [Phase 03](phase-03-final-spec-and-plan.md) | 대기 | 최종 명세와 승인된 구현 계획 |
| [Phase 04](phase-04-foundation-and-vertical-slice.md) | 대기 | 개발 기반과 채용 담당자 세로 단면 |
| [Phase 05](phase-05-notion-and-content-pages.md) | 대기 | Notion 연동과 콘텐츠 페이지 |
| [Phase 06](phase-06-quality-and-release-candidate.md) | 대기 | 접근성·테스트·성능·검색 검증 |
| [Phase 07](phase-07-launch-and-real-content.md) | 대기 | 실제 콘텐츠와 공개 배포 |
| [콘텐츠 트랙](content-track.md) | 병렬 | 공개 가능한 실제 콘텐츠 |

## Phase 전환 규칙

- 각 Phase의 진입 조건 확인 이후 작업 시작
- 각 Phase의 사용자 체크리스트 우선 검수
- 각 Phase의 완료 조건 충족 이후 다음 Phase 전환
- 미확정 결정을 기본값으로 고정할 경우 문서 상태 갱신 필요
- 결정 변경 시 관련 컨텍스트와 Phase 문서의 동시 갱신
- Phase 03 최종 명세 승인 전 코드·설정·의존성 변경 금지
- Phase 05 스키마 승인 전 Notion 쓰기 작업 금지
- Phase 07 공개 전 모든 더미 콘텐츠 제거 또는 실제 콘텐츠 교체

## 현재 사용자의 다음 작업

1. [Phase 01](phase-01-mvp-decisions-and-dummy-contract.md)의 사용자 결정 항목 검수
2. 더미 프로젝트·포스트의 수량과 범위 승인
3. 호스팅·미디어·본문 렌더링 기본안 승인
4. 테스트·도구 기본안 승인
5. Phase 02 디자인 시스템 작업 전환 승인

## 에이전트 작업 원칙

- 현재 Phase 밖의 작업 착수 금지
- 사용자 결정을 요구하는 항목의 임의 확정 금지
- 더미 콘텐츠의 명시적인 샘플 표기
- 실제 회사명·제품명·지표·민감 정보의 더미 데이터 포함 금지
- 실제 데이터 계약과 더미 fixture 계약의 일치
- Phase 완료 시 로드맵과 관련 컨텍스트의 상태 갱신

## 10영업일 MVP 일정의 기준점

- Phase 03 완료 이후 시작하는 구현 일정
- Phase 04부터 Phase 07까지의 개발·검증 기간
- 대표 콘텐츠 준비 상황과 공개 일정에 따른 Phase 07 조정 가능성
- 디자인 검수 지연에 따른 Phase 02·03 일정 분리 가능성
