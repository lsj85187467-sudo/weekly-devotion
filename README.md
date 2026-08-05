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

관리자 화면 최상단에 **자동 배포 상태 배너**가 항상 표시됩니다:
- 🟢 **자동 배포 활성** — 편집 저장하면 성도 앱에 즉시 반영됨. 다른 작업 필요 없음.
- 🔴 **자동 배포 미설정** — 편집 저장해도 성도 앱에 반영 **안 됨**. 저장 시 파일이 자동으로 다운로드되며 큰 안내 모달이 뜸.

### 자동 배포 활성 상태에서

1. **관리자 URL**로 접속 (`?admin=1`)
2. **예배 다시 보기 → [편집]** → 유튜브 URL·제목·본문·설교자 입력 → 저장
3. **말씀 묵상 → [편집]** → 대지·묵상 질문 채움 → 저장
4. 각 저장마다 `✓ 성도 앱에 자동 반영됨` 토스트가 뜨면 완료. 1–2분 후 성도 URL에 반영.

### 자동 배포 미설정/실패 상태에서 (권장: 토큰 한 번만 설정)

**A. 토큰 한 번 설정 (권장, 이후 완전 자동)**
1. 관리자 화면 최상단 빨간 배너의 **[🔑 토큰 설정]** 클릭
2. 안내 창의 링크(`https://github.com/settings/personal-access-tokens/new`)를 브라우저에서 열기
3. Token name: `weekly-devotion-auto` · Repository access: `Only select repositories → weekly-devotion` · Permissions → Repository permissions → **Contents = Read and write**
4. Generate token → 표시된 토큰(github_pat_로 시작)을 복사해 붙여넣기
5. 이후 저장은 완전 자동

**B. 매번 수동 업로드 (토큰 없이도 가능)**
- 편집 저장하면 앱이 자동으로 `content.json` + `content.js` 두 파일을 다운로드하고 큰 모달 표시
- 모달의 **[GitHub에 업로드]** 버튼 클릭 → 열린 페이지에 두 파일 드래그 → Commit
- 1–2분 후 성도 URL에 반영

**C. Claude에게 URL만 알리기 (가장 빠른 대안)**
- 새 유튜브 URL을 Claude에게 던지면 자동 매칭·수동 push로 즉시 반영. (예: 이번 세션 흐름)

> **왜 두 파일인가**: `content.json`은 정본이고, `content.js`는 `<head>`에서 인라인으로 즉시 로드되는 사본입니다. 안드로이드 카톡 인앱 브라우저는 fetch가 실패하는 경우가 있어 `content.json`이 안 읽힐 수 있는데, `content.js`가 있으면 fetch 여부와 무관하게 인라인 데이터로 앱이 정상 렌더됩니다.

## 개인 데이터

성도의 묵상 노트·기도 일지·나눔은 각자 브라우저 localStorage에 저장 (개인·기기별).
관리자의 sermon·worship 데이터는 `content.json` + `content.js`를 통해 모든 성도에게 공유.
