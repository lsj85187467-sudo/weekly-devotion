# 주중 묵상과 기도

행복한우리교회 성도가 주일 설교를 주중에 다시 시청·묵상·기도·나눔하는 정적 웹앱.

## URL

- **성도용**: https://lsj85187467-sudo.github.io/weekly-devotion/
- **관리자용 (편집 가능)**: https://lsj85187467-sudo.github.io/weekly-devotion/?admin=1

## 구조

단일 `index.html` (Vanilla HTML/JS + localStorage). 서버·로그인·비용 없음.

4탭:
1. 말씀 묵상 — 이번 주 주일 설교 + 나만의 묵상 노트 + 이번 말씀 나눔
2. 묵상 기도 — 감사/회개/간구/결단 4카테고리 개인 기도 일지
3. 공동체 기도제목 — 기도제목 관리·함께 기도합니다·응답 표시
4. 예배 다시 보기 — 5종 예배 유형별 유튜브 카탈로그·숏츠

## 매주 업데이트 절차 (관리자)

1. **관리자 URL**로 접속 (`?admin=1`)
2. **예배 다시 보기 → 주일 오전 [편집]** → 유튜브 URL·제목·본문·설교자 입력 → 저장
   - 자동으로 말씀 묵상 탭의 이번 주 설교로 연결됨
3. **말씀 묵상 → [편집]** → 대지·묵상 질문 채움 → 저장
4. 편집 화면 하단 **[📤 content.json 내보내기]** 클릭 → `content.json`과 `content.js` 두 파일이 다운로드됨
5. 두 파일을 이 리포지토리 최상단에 업로드 (**둘 다** 올려야 함)
   - GitHub 웹: 리포지토리 → Add file → Upload files → content.json + content.js 드래그 → Commit
6. 1–2분 후 성도가 접속하는 URL에 자동 반영

> **왜 두 파일인가**: `content.json`은 정본이고, `content.js`는 `<head>`에서 인라인으로 즉시 로드되는 사본입니다. 안드로이드 카톡 인앱 브라우저는 fetch가 실패하는 경우가 있어 `content.json`이 안 읽힐 수 있는데, `content.js`가 있으면 fetch 여부와 무관하게 최소한 인라인 데이터로 앱이 정상 렌더됩니다. GitHub 토큰(자동 배포)이 설정되어 있으면 두 파일 모두 자동으로 push됩니다.

## 개인 데이터

성도의 묵상 노트·기도 일지·나눔은 각자 브라우저 localStorage에 저장 (개인·기기별).
관리자의 sermon·worship 데이터는 `content.json` + `content.js`를 통해 모든 성도에게 공유.
