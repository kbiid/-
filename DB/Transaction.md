## 분산 트랜잭션
- 하나 이상의 서버가 연관되어 트랜잭션이 수행되는 트랜잭션으로 데이터베이스의 데이터 무결성 및 일관성을 보장

## 2PC(Phase Commit)의 정의
- 분산 데이터베이스 환경에서 원자성을 보장하기 위해 분산 트랜잭션에 포함되어 있는 모든 노드가 Commit되거나 Rollback하는 메커니즘
- 분산 데이터베이스 환경에서는 단일 Site별로 Commit 또는 Rollback이 수행된다면 트랜잭션의 기본 특징인 원자성을 만족할 수 없음
- 대용량화에 따른 데이터베이스를 분산화시키고, 지역적 분리의 한계를 극복할 수 있는 방안

## 분산 트랜잭션의 구성요소
- 서버 : 원격 노드에서 요구하는 데이터를 갖고 있는 노드
- 조정자(coordinator) : 분산 트랜잭션 참여자 목록을 관리하고 Global commit 등을 전파 및 제어하는 노드
- 참여자(participant) : 분산 트랜잭션에서 지역 트랜잭션을 수행하는 노드. 조정자를 인지하고 조정자의 요구에 따라 명령에 따름
- 클라이언트 : 분산 트랜잭션을 발생시키는 응용 프로그램이 위치한 노드

## 2PC의 동작절차
- 2PC는 Prepare 단계와 Commit 단계로 나뉘어 실행
  <ol>
  <li>Prepare 단계 : 전역 조정자가 분산 트랜잭션에 참여한 노드들에 Prepare요청. 그에 대한 결과 응답을 수집</li>
  <li>Commit 단계 : 분산 트랜잭션의 참여 노드들로부터 prepare에 대한 응답이 모두 yes이면 Commit 요구. 하나라도 no이면 Rollback 요구</li>
  </ol>
- 단계별 주체의 수행과정
  <ul>
  <li>1단계(prepare)
    <ul>
      <li>조정자(coordinator) : Prepare 메시지를 각 참여자에 대한 송신. 모든 참여자의 응답(y/n) 수집. 응답 없으면 타임아웃. no으로 간주</li>
      <li>참여자(participant) : Prepare 메시지를 waiting. 트랜잭션 준비되면 yes 전달. 준비되지 못하는 상태이면 no 전달.</li>
    </ul>
  </li>
  <li>2단계(commit)
    <ul>
      <li>조정자 : 모든 참여자가 준비상태 yes면 commit 송신. 하나라도 no면 rollback 송신</li>
      <li>참여자 : 조정자의 commit/rollback을 waiting. 조정자가 보내온 결과대로 올바르게 수행. 수행완료 메시지 송신.</li>
    </ul>
  </li>
  </ul>
