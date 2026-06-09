# ⚽ FunToTo - 축구 점수 맞추기 토토

통신 AI 사업본부 구성원들과 축구 경기 점수를 예상하고 베팅하는 사내 토토 게임입니다.

---

## Firebase 설정 (최초 1회)

### 1. Firebase 프로젝트 생성

1. [Firebase 콘솔](https://console.firebase.google.com) 접속
2. **프로젝트 추가** → 프로젝트 이름 입력 (예: `funtoto`)
3. Google 애널리틱스는 선택 사항

### 2. Realtime Database 활성화

1. 좌측 메뉴 **빌드 > Realtime Database** 클릭
2. **데이터베이스 만들기** → 위치 선택 (asia-southeast1 권장)
3. 보안 규칙 → **테스트 모드**로 시작 (30일 공개 쓰기 허용)
4. 이후 **규칙** 탭에서 아래로 변경 (사내 전용이므로 공개 허용):
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```

### 3. 앱 등록 및 Config 복사

1. 프로젝트 설정(⚙️) > **앱 추가 > 웹(`</>`)** 클릭
2. 앱 닉네임 입력 후 등록
3. 표시되는 `firebaseConfig` 값 복사

### 4. `index.html` 에 붙여넣기

파일 상단 `firebaseConfig` 부분을 교체하세요:

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

### 5. Vercel 배포

```bash
# Vercel CLI 설치 (최초 1회)
npm i -g vercel

# 배포
vercel
```

또는 GitHub 저장소를 Vercel에 연결하면 push 시 자동 배포됩니다.

---

## 로컬 실행 (서버 없이)

Firebase 설정만 완료되면 `index.html`을 브라우저로 직접 열어도 됩니다.

---

## 관리자 / 관전자 모드

| 모드 | 설명 |
|------|------|
| 👁 관전자 (기본) | 점수 현황, 배당률 조회만 가능 |
| 🔑 관리자 | 참여자 등록, 수금 체크, 결과 입력 등 전체 기능 |

입력 필드 외부에서 **`QkrQkrdl`** 를 키보드로 입력하면 관리자 모드로 전환됩니다.

---

## 주요 기능

- 실시간 동기화 — 관리자가 입력하면 모든 관전자 화면에 즉시 반영
- 점수별 배당률 실시간 계산
- 수금 여부 체크
- 경기 결과 입력 시 당첨자 및 수령액 표시
- 모바일 지원

## 파일 구조

```
funToTo/
├── index.html   # 앱 본체 (Firebase 설정 포함)
├── server.js    # 로컬 전용 서버 (선택적 사용)
└── README.md
```
