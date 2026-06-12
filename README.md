# ⚽ FunToTo - 축구 점수 맞추기 토토

통신 AI 사업본부 구성원들과 축구 경기 점수를 예상하고 베팅하는 사내 토토 게임입니다.

---

## 바로 접속

**https://funtoto.vercel.app**

별도 설치 없이 브라우저에서 바로 사용 가능합니다 (모바일 지원).

---

## 관리자 / 관전자 모드

| 모드 | 설명 |
|------|------|
| 👁 관전자 (기본) | 점수 현황, 배당률 조회만 가능 |
| 🔑 관리자 | 참여자 등록, 수금 체크, 결과 입력, 새 게임 등 전체 기능 |

우측 상단 **🔑 관리자** 버튼 클릭 후 비밀번호 입력으로 관리자 전환.

---

## 주요 기능

- 실시간 동기화 — 관리자가 입력하면 모든 접속자 화면에 즉시 반영
- 점수별 배당률 실시간 계산 (파리뮤추얼 방식)
- 수금 여부 체크
- 경기 결과 입력 시 당첨자 및 수령액 표시
- 게임 기록 저장 및 불러오기
- 모바일 최적화

---

## 개발자 가이드

### 기술 스택

- **Frontend**: 단일 HTML 파일 (빌드 불필요)
- **Database**: Firebase Realtime Database (실시간 동기화)
- **Hosting**: Vercel

### 로컬 실행

```bash
# index.html 을 브라우저로 직접 열거나
open index.html

# 또는 간단한 로컬 서버 실행
npx serve .
```

### Vercel 배포

```bash
# Vercel CLI 설치 (최초 1회)
npm i -g vercel

# 배포 (GitHub 연동 없이 직접 배포)
vercel --prod
```

> **주의:** Vercel Hobby 플랜에서 private 저장소를 GitHub 연동으로 배포하면  
> "commit author did not have contributing access" 오류가 발생할 수 있습니다.  
> 이 경우 `vercel --prod` CLI 직접 배포 또는 저장소를 Public으로 변경하세요.

### Firebase 설정 변경 시

`index.html` 상단 `firebaseConfig` 부분을 교체하세요:

```js
const firebaseConfig = {
  apiKey:            "AIza...",
  authDomain:        "funtoto-xxxxx.firebaseapp.com",
  databaseURL:       "https://funtoto-xxxxx-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId:         "funtoto-xxxxx",
  storageBucket:     "funtoto-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId:             "1:123456789:web:abcdef"
};
```

Firebase Realtime Database 보안 규칙 (사내 전용):
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

### 파일 구조

```
funToTo/
├── index.html   # 앱 본체 (Firebase 설정 포함)
├── server.js    # 로컬 전용 서버 (선택적, 미사용)
└── README.md
```
