<img alt="Renzzle" src="https://raw.githubusercontent.com/Renzzle/.github/main/profile/banner.png" width="100%"/>

<p align="center">
  <a href="https://apps.apple.com/app/id6793042991"><img alt="App Store" src="https://img.shields.io/badge/App_Store-26241F?style=for-the-badge&logo=appstore&logoColor=white"/></a>
  <a href="https://play.google.com/store/apps/details?id=com.renzzle_fe"><img alt="Google Play" src="https://img.shields.io/badge/Google_Play-26241F?style=for-the-badge&logo=googleplay&logoColor=white"/></a>
</p>

## Service

Renzzle은 오목 퍼즐 앱입니다. 주어진 국면에서 AI의 방어를 뚫고 이기는 수순을 찾습니다. 초보자부터 고수까지 자기 수준에 맞는 문제로 수읽기를 연습할 수 있습니다.

- **트레이닝** · 난이도별로 정리된 문제집을 차례로 풀며 실력을 다집니다.
- **커뮤니티** · 직접 문제를 만들어 공유하고, 다른 사용자의 문제를 풀고 평가합니다. AI 검증을 통과한 문제에는 인증 표시가 붙습니다.
- **랭킹전** · 트레이닝 문제와 인증된 커뮤니티 문제 중 내 레이팅에 맞는 문제가 이어서 나오고, 결과에 따라 레이팅이 오르내립니다.

## Projects

### Backend

`Renzzle_BE` · API 서버와 공유 링크 웹 페이지

![Backend](https://go-skill-icons.vercel.app/api/icons?i=java,spring,mysql,redis,aws,cloudflare,docker,githubactions,prometheus,grafana&perline=10)

- Google Play · App Store 인앱 결제 서버 검증, 스토어 환불 반영
- 랭킹전 결과가 중복 전송돼도 한 번만 반영
- 공유 링크 페이지 서버 렌더링, iOS · Android 딥링크
- PR 댓글로 테스트 · 운영 서버 배포

### Frontend

`Renzzle_FE` · iOS · Android 앱

![Frontend](https://go-skill-icons.vercel.app/api/icons?i=reactnative,typescript&perline=2)

- C++ AI 엔진을 네이티브 모듈로 탑재해 기기 안에서 수읽기
- 인앱 결제, 광고, 7개 언어
- 운영 화면 앱 내장 (문제 검수, 공지, 결제 내역)

### AI

`Renzzle_AI` · C++ 렌주 AI 엔진

![AI](https://go-skill-icons.vercel.app/api/icons?i=cpp,wasm&perline=2)

- Alpha-Beta 탐색, PVS, Iterative Deepening
- Transposition Table, Zobrist Hashing
- VCF 전용 탐색, 렌주 금수 판정
- 앱에는 네이티브로, 웹에는 WebAssembly로 같은 엔진 사용

## Architecture

```mermaid
flowchart LR
    AI["Renzzle_AI<br/>C++ 엔진"] -. 네이티브 모듈 .-> App["앱<br/>React Native"]
    AI -. WebAssembly .-> Web["브라우저<br/>공유 링크"]
    App --> CF[Cloudflare]
    Web --> CF
    CF --> Caddy --> API[Spring Boot]
    API --> MySQL
    API --> Redis
    API --> Store[Google Play / App Store]
```
