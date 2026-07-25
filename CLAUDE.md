# running-crew 프로젝트 규칙

## 언어 규칙
- 모든 응답, 주석, 커밋 메시지, 대화는 한국어로 진행한다
- 코드 내 식별자(변수/함수/컴포넌트명)는 영어를 사용한다

## 프로젝트 개요
- 러닝 크루(러닝 모임) 이벤트 관리 모바일 앱
- 핵심 기능
  - 회원가입 / 로그인
  - 모임 일정 등록 / 초대 / 조회
  - 러닝 기록 관리

## 기술 스택
- Frontend: React Native (Expo SDK 54, Expo Router)
- 언어: TypeScript
- Backend / Auth / DB: Supabase
- 상태 관리: React Query (서버 상태) + Zustand (클라이언트 전역 상태)
- 폼: React Hook Form
- 버전 관리: GitHub

## Expo SDK 버전 고정
- Expo SDK는 54 버전으로 고정한다
- App Store/Play Store에 배포된 Expo Go 앱이 SDK 54까지만 공식 지원하기 때문이다 (SDK 55 이상은 Apple 앱스토어 승인 대기 상태)
- SDK를 업그레이드하려면 먼저 Expo Go 앱스토어 배포 버전이 해당 SDK를 지원하는지 확인한 뒤 진행한다

## 코딩 컨벤션
- 모든 파일은 TypeScript(.ts/.tsx)로 작성하며 `any` 사용을 지양한다
- 컴포넌트: PascalCase (`RunCard.tsx`)
- 함수/변수: camelCase
- 상수: UPPER_SNAKE_CASE
- 커스텀 훅: `use` 접두사 (`useRunSchedule.ts`)
- 타입/인터페이스: PascalCase, `interface`를 기본으로 사용하고 유니온 등에는 `type` 사용
- 컴포넌트는 함수형 컴포넌트로 작성
- 스타일은 `StyleSheet.create`를 사용하고 인라인 스타일은 지양한다
- import 순서: 외부 라이브러리 → 절대경로 내부 모듈(`@/`) → 상대경로
- 절대경로 import(`@/`)를 사용하고 깊은 상대경로(`../../../`)는 지양한다
- 환경 변수(Supabase URL/Key 등)는 `.env`에 두고 `EXPO_PUBLIC_` 접두사로 노출하며 저장소에 커밋하지 않는다

## 폴더 구조 규칙
```
running-crew/
├── app/                    # Expo Router 라우트 (화면 단위)
│   ├── (auth)/             # 로그인/회원가입 등 인증 플로우
│   ├── (tabs)/             # 로그인 후 메인 탭 화면
│   └── _layout.tsx
├── src/
│   ├── components/         # 재사용 가능한 UI 컴포넌트
│   ├── features/           # 도메인 단위 기능 모듈 (auth, schedule, running-log 등)
│   ├── hooks/               # 공용 커스텀 훅
│   ├── lib/                 # Supabase 클라이언트 등 외부 서비스 연동
│   ├── store/                # Zustand 스토어
│   ├── types/                # 공용 타입 정의
│   └── constants/             # 색상, 사이즈 등 상수
├── assets/                 # 이미지, 폰트 등 정적 리소스
├── .env                    # 환경 변수 (미커밋)
└── CLAUDE.md
```
- 화면(라우팅) 관련 코드는 `app/`에만 두고, 실제 로직/컴포넌트는 `src/`에 작성한 뒤 `app/`에서 불러온다
- 도메인별 로직은 `src/features/{도메인명}/` 하위에 모아서 관리한다 (예: `src/features/auth/`, `src/features/schedule/`)

## 작업 원칙
- 화면 구현 전 항상 목적과 요구사항을 먼저 정의한다
- 불필요한 추상화, 조기 최적화를 지양한다
- Supabase 스키마 변경 시 마이그레이션 파일로 관리한다
