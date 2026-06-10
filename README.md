# newconfinedmind

AI 기능을 실제 서비스로 빠르게 만들고, 웹 애플리케이션, 인프라, 데이터베이스, 결제, 광고 유입까지 직접 다룹니다. 최근에는 공장 기계 프리셋을 음성/채팅으로 만들고 선택하는 SaaS인 boxfold에 집중하고 있습니다.

## Focus

- AI tool calling, STT/TTS, LLM 기반 업무 도구
- React Router, Vite, TypeScript, Tailwind CSS 기반 풀스택 웹 애플리케이션
- Cloudflare Workers, Tunnel, Zero Trust, Hyperdrive 중심 인프라
- PostgreSQL, postgres.js, 명시적 SQL, 직접 운영 가능한 데이터 구조
- 쿠키, 세션, 리다이렉트, UTM, 광고 픽셀, 전환 측정 등 웹 분석과 퍼포먼스 마케팅

## Selected Work

### boxfold

현재 주력 프로젝트입니다. 공장에서 쓰는 기계 프리셋을 음성/채팅으로 만들고 선택하는 SaaS를 만들고 있습니다. React Router, Cloudflare Workers, PostgreSQL, TanStack Query, Zustand, AI SDK를 중심으로 구성하고 있습니다.

### Dreamerola

직접 녹음한 내용을 바탕으로 Gemini API를 호출해 꿈일기를 기록하고 분석하는 iOS 앱입니다. 유료 Apple Developer Program을 사용해 실제 App Store 심사를 통과했습니다.

### Jedger

AI를 이용해 복식부기를 다루는 서비스입니다. PG 승인을 기다리고 있으며, PortOne SDK를 사용해 실제 결제 가능한 상용 서비스로 가는 과정을 다루고 있습니다.

### Cunvus

Remotion 라이브러리와 홈서버 Node 프록시를 이용해 카드뉴스와 동영상을 만들 수 있는 프로젝트입니다. 콘텐츠를 이미지와 영상 형태로 자동 생성하는 흐름을 다뤘습니다.

### teamMED Management Science Project

서울시 따릉이 데이터를 이용해 대여소와 시간대별 순유입/순유출을 예측하고, 자전거 재배치 전략을 설계한 경영과학 팀프로젝트입니다. TensorFlow, Pandas/SQLite, Folium 시각화, Google OR-Tools 기반 최소 비용 흐름 문제 모델링을 다뤘습니다.

### freemove.kr

스쿠터 대여 사이트로 만들었던 프로젝트이며, 이후 주식회사 네솔에게 이전했습니다. 사이트 제작뿐 아니라 네이버, 당근, Google 광고를 직접 집행하며 유입과 광고 성과를 확인했습니다.

### braindev.jangyunje.com

PDF를 읽고 퀴즈를 만드는 서비스를 약 5시간 만에 만든 프로젝트입니다. 빠르게 요구사항을 서비스 형태로 바꾸고 AI 기능을 실제 사용 가능한 도구로 연결한 사례입니다.

### theindex.today / dlvr.life

CRM과 AI 기반 데이터 조작을 실험한 프로젝트들입니다. Supabase, 홈서버, PostgreSQL로 이어지는 데이터 운영 실험과 AI tool calling을 통한 DB 업데이트 흐름을 다뤘습니다.

## Technical Preferences

- Open source and self-hostable tools over vendor lock-in
- Explicit SQL over hidden ORM behavior
- Web standards such as Request, Response, fetch, URL, Headers
- Zustand over large React Context state trees
- TanStack Query and optimistic UI for server state
- Zod for runtime validation at API and form boundaries
- Cloudflare DNS, Workers, Tunnel, Zero Trust, Email Routing, Hyperdrive
- PostgreSQL as the default database for long-lived services
