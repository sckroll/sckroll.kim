# 프로젝트 문서 지도

## 문서 성격

- 새 디바이스와 새 세션을 위한 프로젝트 컨텍스트 모음
- 최종 명세 작성 전 사용자 재검수를 위한 중간 기록
- 구현 계약과 승인 완료 명세의 지위 미부여

## 문서 목록

- [`project-context.md`](project-context.md): 프로젝트 배경, 사용자, 포지셔닝, 콘텐츠, 페이지 구조
- [`technical-decisions.md`](technical-decisions.md): 기술 스택, 컴포넌트 경계, Notion 연동, 렌더링
- [`notion-context.md`](notion-context.md): Notion 식별자, 현재 스키마, 운영 제약, 변경 후보
- [`content-contract.md`](content-contract.md): 도메인 모델, fixture, Notion 속성 매핑, 교체 절차
- [`quality-decisions.md`](quality-decisions.md): 접근성, 성능, 미디어, GEO·AEO·SEO, 테스트
- [`review-backlog.md`](review-backlog.md): 결정 상태, 미결정 사항, 후속 검토 순서
- [`todos/README.md`](todos/README.md): 현재 Phase, 전체 로드맵, 단계별 체크리스트
- [`../AGENTS.md`](../AGENTS.md): 에이전트 작업 규칙과 세션 재개 절차

## 문서 우선순위

1. 사용자의 최신 직접 지시
2. 사용자 검수를 마친 향후 최종 명세
3. `AGENTS.md`의 저장소 작업 지침
4. 코드와 외부 도구에서 확인한 현재 상태
5. `docs`의 검토용 컨텍스트

## 갱신 원칙

- 결정 변경 시 관련 문서와 결정 상태의 동시 갱신
- 잠정 제안의 확정 표현 금지
- 폐기된 결정의 삭제보다 변경 사유 기록 우선
- 최종 명세 작성 시 본 문서들의 근거 자료 활용
- 최종 명세 확정 후에도 세션 연속성 기록의 유지

## 기준 시점

- 최초 기록일: 2026-07-18
- 최종 명세 상태: 미작성
- 구현 계획 상태: 미작성
- 애플리케이션 상태: 미구축
