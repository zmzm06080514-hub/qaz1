# Quest 프로젝트 정리 메모

현재 작업 폴더에 `Quest-main`, `Quest`, `Quest/Quest-main`가 함께 존재해 실행 대상이 혼동될 수 있습니다.

## 권장 실행 기준

- 메인 작업 폴더: `Quest-main`
- 테스트/배포 전 확인 파일:
  - `Quest-main/index.html`
  - `Quest-main/src/EventManager.js`
  - `Quest-main/src/SubmitHandler.js`

## Firebase 저장 실패 시 점검 순서

1. `index.html`에 Firebase CDN 스크립트 2개가 포함되어 있는지 확인
2. `window.appFirebase.firestore`가 초기화되는지 확인
3. 폼 제출 버튼 타입이 `submit`인지 확인
4. 이벤트가 버튼 클릭이 아니라 폼 `submit` 이벤트에 연결되어 있는지 확인
5. Firestore 보안 규칙에서 `submissions` 컬렉션 쓰기 허용 여부 확인

## 현재 반영된 수정

- 폼 제출 이벤트를 `click` 중심에서 `submit` 중심으로 변경
- 제출 버튼 `type="submit"`으로 통일
- 잘못 삽입된 HTML 문자(`~`) 제거
- 누락된 Firebase 초기화 스크립트(복사본 폴더) 추가
