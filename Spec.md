# Running Crew — Product Specification
Version: MVP v1.0

## 1. Product Overview
Running Crew는 사람들이 함께 러닝 약속을 만들고,
함께 달리고, 기록을 남길 수 있도록 돕는
Group Running Platform이다.

## 2. Product Goal
사용자가 별도의 설명 없이 다음 플로우를 완료할 수 있어야 한다.
1. 크루 생성
2. 러닝 이벤트 생성
3. 참가자 초대
4. 오프라인 러닝
5. 러닝 기록 확인

## 3. Target User
- 러닝 크루 운영자
- 정기적으로 함께 달리는 러너
- 친구들과 러닝 약속을 만드는 사용자

## 4. Core User Flow
Login
↓
Crew 생성 또는 선택
↓
Running Event 생성
↓
Invitation 링크 공유
↓
참가자 확정
↓
오프라인 러닝
↓
완주 기록 수동 입력
↓
결과 확인

## 5. MVP Features

### Authentication
- 이메일 로그인
- Google 로그인
- 사용자 프로필 생성

### Crew
Crew 정보: 이름, 설명, 대표 이미지, 공개 여부
사용자는 크루 생성, 수정, 참여, 탈퇴를 수행할 수 있다.

### Running Event
이벤트 정보: 제목, 날짜, 시작 시간, 집합 장소,
최대 인원, 목표 Pace, 설명
사용자는 이벤트 생성, 수정, 삭제, 참여, 취소를 수행할 수 있다.

### Invitation
이벤트는 공유 가능한 링크를 생성한다.
초대받은 사용자는 링크 접속 후 참가 여부를 선택할 수 있다.
MVP에서는 링크 기반 초대만 지원한다.

### Running Record
러닝 완료 후 참가자는 완주 기록을 수동으로 입력한다.
입력 항목: 거리(km), 소요 시간(분)

### Result
결과 화면 포함 정보: 총 거리, 총 시간, 평균 Pace,
참가자 목록 및 각자의 기록

## 6. Screens
Splash, Login, Home, Crew List, Crew Detail,
Create Crew, Event List, Event Detail, Create Event,
Running Record Input, Running Result, Profile

## 7. Functional Requirements

### Authentication
- FR-01. 사용자는 이메일/비밀번호로 회원가입하고
  로그인할 수 있어야 한다
- FR-02. 사용자는 Google 계정으로 로그인할 수 있어야 한다
- FR-03. 로그인한 사용자는 프로필을 생성하고
  수정할 수 있어야 한다

### Crew
- FR-04. 사용자는 크루를 생성할 수 있어야 한다
- FR-05. 크루 생성자는 크루 정보를 수정할 수 있어야 한다
- FR-06. 사용자는 공개 크루에 참여할 수 있어야 한다
- FR-07. 사용자는 가입한 크루에서 탈퇴할 수 있어야 한다

### Running Event
- FR-08. 크루 멤버는 이벤트를 생성할 수 있어야 한다
- FR-09. 이벤트 생성자는 이벤트를 수정하고
  삭제할 수 있어야 한다
- FR-10. 사용자는 이벤트에 참여 신청하고
  취소할 수 있어야 한다
- FR-11. 시스템은 최대 인원이 초과된 이벤트에
  참여 신청을 허용하지 않아야 한다

### Invitation
- FR-12. 이벤트 생성자는 초대 링크를 생성할 수 있어야 한다
- FR-13. 초대 링크에 접속한 사용자는 로그인 후
  참가 여부를 선택할 수 있어야 한다

### Running Record
- FR-14. 이벤트 참가자는 거리(km)와 소요 시간(분)을
  수동으로 입력할 수 있어야 한다
- FR-15. 입력된 기록은 이벤트 결과 화면에서
  참가자 전체 기록과 함께 표시되어야 한다

### Result
- FR-16. 사용자는 결과 화면에서 총 거리, 총 시간,
  평균 Pace, 참가자 목록과 각자의 기록을
  확인할 수 있다

## 8. Acceptance Criteria
- AC-01. 필수 입력값이 비어있으면 이벤트가 저장되지
  않고 해당 필드에 오류 메시지가 표시된다
- AC-02. 최대 인원이 가득 찬 이벤트의 참여 신청 버튼은
  비활성화되고 "마감" 텍스트가 표시된다
- AC-03. 참여 신청 완료 시 참석자 수가 즉시 업데이트되고
  확인 메시지가 표시된다
- AC-04. 완주 기록 저장 완료 시 성공 메시지가 표시되고
  이벤트 결과 화면에서 기록을 확인할 수 있다
- AC-05. 초대 링크 접속한 비로그인 사용자는 로그인 후
  해당 이벤트 상세 화면으로 돌아온다
- AC-06. 크루 탈퇴 시 확인 다이얼로그가 표시되고
  확인을 누른 경우에만 탈퇴가 처리된다

## 9. Out of Scope
- GPS 실시간 기록, 결과 외부 공유
- 채팅, 랭킹, 배지, AI 코치
- 실시간 위치 공유, 친구 추천
- 푸시 마케팅, 러닝 분석, 웨어러블 연동

## 10. Success Criteria
사용자는 아래를 별도의 설명 없이 완료할 수 있어야 한다.
- 크루를 만든다, 이벤트를 만든다, 사람을 초대한다
- 함께 달린다, 기록을 입력한다, 결과를 확인한다

## 11. Future Scope
MVP 이후 사용자 검증을 거친 후에만 추가를 검토한다.
Chat, Push Notification, Apple Watch, Garmin,
Strava Sync, Crew Feed, Running Statistics,
Achievement, AI Coach, Route Recommendation,
GPS 자동 기록, 결과 외부 공유
