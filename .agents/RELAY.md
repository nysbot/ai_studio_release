# RELAY — 자동 이어받기 지시서

> 이 파일이 있고 `status: ACTIVE` 이면, 누가 한도로 끊겨도 **살아 있는 에이전트가 자동으로**
> 이 지시를 이어서 수행한다(_central-management/protocols/auto-relay-protocol.md).
> 끄려면 status 를 PAUSED 로 바꾼다. 전체 중단은 `touch _central-management/state/relay.stop`.
> 실행 근거는 `_central-management/qa/relay-ledger.md`.

status: PAUSED

## 지시

1. `.agents/TASKS.md` 의 `## Now` 에서 미해결 **P0 → P1** 순으로 **한 건만** 골라 처리한다.
2. 고친 것은 **실행으로 확인한다** — 테스트·빌드·실제 구동·로그(solo-mode §2.1: 의견보다 실행).
   확인 수단이 없으면 그 수단을 먼저 만든다.
3. `## Now` 가 비어 있으면 **새 기능을 만들지 않는다.** 아래에서 한 건만 한다:
   ① `qa/solo-debt.md` 미해소 부채 소진 ② 실패 테스트·경고 정리
   ③ `.agents/CURRENT.md` 를 실제 코드 상태와 일치시키기
4. 끝나면 `.agents/CURRENT.md` 와 `TASKS.md` 를 **현재 상태로** 갱신하고 로컬 커밋한다.
   다음 에이전트는 이 두 파일만 보고 이어받는다.
