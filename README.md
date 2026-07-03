# 💤 수면 트래커 — 나만의 최적 수면 시간 찾기

김경일 교수(아주대 심리학과) 세바시 강연 제1134회 실천 도구

## 기능

- 매일 수면 시간 · 애플워치 수면점수 · 기분 점수(1–10) 기록
- 월별 평균 통계 대시보드
- 최적 수면 시간 자동 분석 (수면시간 × 기분점수 상관관계)
- **한 기기에서 입력 → 모든 기기에서 실시간 동기화** (Firebase 필요)
- 오프라인 로컬 모드 지원

## GitHub Pages 배포

1. 이 레포지토리를 GitHub에 Fork 또는 Clone
2. `index.html` 파일만 있으면 됩니다
3. Settings → Pages → Source: `Deploy from branch` → `main`
4. `https://username.github.io/sleep-tracker` 으로 접속

## Firebase 실시간 동기화 설정

1. [console.firebase.google.com](https://console.firebase.google.com) 접속
2. 새 프로젝트 생성
3. Firestore Database 활성화 (테스트 모드)
4. 프로젝트 설정 → 앱 추가 → 웹앱 → Config 복사
5. 앱 내 **⚙️ 설정** 탭에 Firebase Config JSON 붙여넣기
6. **사용자 키** 설정 (모든 기기에서 동일한 키 사용)

## 데이터 구조 (Firestore)

```
users/{userId}/entries/{entryId}
  date: string       # YYYY-MM-DD
  sleepHours: number # 3.0 ~ 12.0
  watchScore: number # Apple Watch 수면점수 (0-100, optional)
  moodScore: number  # 기분 점수 (1-10)
  memo: string       # 메모 (optional)
  ts: number         # timestamp
```

## 멀티디바이스 사용법

1. 모든 기기에서 같은 URL 접속
2. ⚙️ 설정 탭에서 동일한 **사용자 키** 입력 (예: `jaejin`)
3. Firebase Config 입력 후 연결
4. 어느 기기에서 입력해도 모든 기기에 즉시 반영

---

Based on Sebasi Talk #1134 by Prof. Kim Kyung-il (Ajou University, Psychology)
