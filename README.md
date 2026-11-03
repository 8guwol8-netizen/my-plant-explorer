# 🌱 학교 식물 탐사대 — 연수용 시작 버전

사진으로 식물을 알아보고, 국립수목원 공식 정보·교과서와 잇는 웹앱의 **연수용 시작 버전**이에요.
앱은 다 돌아가요. 연수에서는 **클로드 웹(무료)** 에게 프롬프트를 보내 이 앱을 우리 학교·우리 반에 맞게 바꿔요.
내 컴퓨터에 설치할 것은 없어요.

- 연수 진행표·프롬프트(노션): https://app.notion.com/p/40ddc287784c80b7bfb1cfbed4cf9c17
- 완성본 앱 둘러보기: https://plant-explorer-delta.vercel.app

## 1. 내 앱 만들기 — 버튼 한 번

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2F7guwol7-max%2Fplant-explorer-starter&project-name=my-plant-explorer&repository-name=my-plant-explorer)

1. 위 **Deploy** 버튼 → 'Git Providers' 에 GitHub·GitLab·Bitbucket 버튼이 보이고 **Create 가 회색**이면 **GitHub** 를 눌러 로그인 → Vercel 권한 허용(Authorize) → (나오면) Install → 이 화면으로 돌아오기
2. 저장소 이름(`my-plant-explorer`)은 그대로 두고 **Create** → **Deploy**
   - **Create 가 안 보이거나 눌리지 않으면**: 이름 칸 아래에 '이미 있다(already exists)'는 빨간 글씨가 있는지 보고 이름을 바꿔요(예: `my-plant-explorer-2`). 'Git Providers' 버튼만 보이면 **GitHub** 를 눌러 연결해요(GitHub 창이 안 뜨면 팝업 차단 풀기)
3. 1~2분 뒤 축하 화면이 나오면 **Continue to Dashboard** → **Domains** 의 주소(`https://my-plant-explorer-○○○.vercel.app` 처럼)가 **내 앱**이에요

이제 **내 GitHub 저장소**에서 파일을 고쳐 저장(Commit)하면 1~2분 뒤 내 앱이 자동으로 바뀌어요.
서버 지역(서울)과 Node 버전은 `vercel.json`·`package.json` 에 들어 있어서 따로 바꿀 것이 없어요.

## 2. 우리 학교에 맞게 바꾸는 자리

클로드 웹 채팅에서 **+ → Add from GitHub** 로 아래 파일만 골라 첨부한 뒤 프롬프트를 보내요.

| 바꾸고 싶은 것 | 첨부할 파일 |
| --- | --- |
| 앱 이름, 맨 아래 메뉴(이름·순서·추가), '어디에서 찾았나요?' 장소 | `lib/site.ts` |
| 새 메뉴 화면 | `lib/site.ts` (새 화면 파일은 클로드가 만들어 줘요: `app/주소/page.tsx`) |
| 교과서 연결에 성취기준 더하기, 우리 반 활동으로 바꾸기 | `data/curriculum-extra.json` (+ 클로드에 '성취기준' 커넥터) |
| 잎 모양·잎맥·줄기 그림 도움말 설명 | `lib/termText.ts` 🚧 지금 비어 있어요 |

- `data/curriculum-extra.json` 은 지금 `[]`(빈 목록)이에요. 여기에 넣은 성취기준은 기본 자료와 합쳐지고, 같은 코드를 넣으면 적은 칸(활동·학생 문장·연결 조건)만 바뀌어요.
- 예시·정답: [lib/termText.ts](https://github.com/7guwol7-max/plant-explorer/blob/claude/affectionate-johnson-msxhyk/lib/termText.ts) · [data/curriculum-extra.json](https://github.com/7guwol7-max/plant-explorer/blob/claude/affectionate-johnson-msxhyk/data/curriculum-extra.json)

## 3. 받은 코드 붙여 넣기

- 있는 파일 고치기: 내 저장소에서 키보드 `t` → 파일 이름 → 파일 열기 → 오른쪽 위 **연필** → `Ctrl+A` → `Ctrl+V` → **Commit changes**
- 새 파일 만들기: 저장소 첫 화면 **Add file → Create new file** → 이름 칸에 경로 그대로(예: `app/school/page.tsx`) → 붙여 넣기 → **Commit changes**
- 1~2분 뒤 내 앱 새로고침. Vercel → Deployments 맨 위가 **Ready**(초록)면 반영된 거예요
  - 빨간 **Error** 면: 그 배포 → Build Logs 의 빨간 줄을 복사해 클로드에게 '이 오류가 났어. 고친 파일 전체를 다시 줘' (그동안 앱은 직전 버전으로 계속 열려요)

## 4. 키

키는 코드에도, 클로드 채팅에도 붙여 넣지 않아요. 내 앱 → ⚙️ 설정 화면에 넣으면 그 기기 브라우저에만 저장돼요.

- 공공데이터포털 '산림청 국립수목원_식물자원 조회 서비스' 일반 인증키 — https://www.data.go.kr
- 제미나이 API 키(무료로 시작 가능) — https://aistudio.google.com/apikey
- 키 없이 둘러보기: Vercel → Settings → Environment Variables 에 `MOCK` = `1` → Redeploy (연습 자료로 동작)

## 만든 것

Next.js 15 · React · TypeScript. 데이터베이스·로그인 없음. 학생 기록은 그 기기 브라우저에만 저장돼요.
완성본 저장소: https://github.com/7guwol7-max/plant-explorer
