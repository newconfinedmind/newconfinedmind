# Portfolio

## Technical Preferences

### Principles

| Prefer | Avoid |
|---|---|
| Open source | Vendor lock-in |
| Self-hostable tools | Platform-dependent architecture |
| Explicit SQL | Hidden ORM behavior |
| Web standards | Framework-specific magic |
| Docker Compose | Overcomplicated infrastructure |
| Understanding internals | Blind abstraction usage |

오픈소스와 교체 가능한 도구를 선호한다. 특정 플랫폼 안에서만 자연스럽게 동작하는 구조보다는, 필요하면 다른 환경으로 옮길 수 있고 내부 동작을 직접 확인할 수 있는 구성을 선호한다. 편리한 매니지드 서비스도 사용할 수 있지만, 프로젝트의 핵심 부분이 특정 서비스의 정책, 가격, SDK, 배포 방식에 강하게 묶이는 구조는 기본 선택지로 두지 않는다.

기술을 사용할 때는 가능한 한 원리부터 이해하려고 한다. OAuth와 PKCE, Git의 내부 구조, HTTP, 네트워크, 데이터베이스의 동작 방식처럼 겉으로는 도구가 감춰주는 부분도 시간만 충분하면 직접 파고드는 편이다. 추상화 자체를 싫어하는 것은 아니지만, 이해하지 못한 채로 사용하는 추상화는 선호하지 않는다.

### Frontend & Backend

프론트엔드는 React Router, Vite, TypeScript, Tailwind CSS, shadcn/ui, pnpm 조합을 선호한다. Next.js는 기본 선택지로 두지 않는다. React 자체보다 특정 플랫폼과 배포 모델에 강하게 묶이는 방식이 마음에 들지 않고, 프레임워크가 너무 많은 결정을 대신하는 구조도 선호하지 않는다.

React Router는 단순히 라우팅 라이브러리로만 보지 않고, 현재는 풀스택 React 애플리케이션을 구성하는 중심 도구로 사용한다. 서버 사이드 로직이나 백엔드에 가까운 기능도 React Router의 기능을 활용하는 쪽을 선호한다. 별도의 백엔드 프레임워크를 항상 분리하기보다는, 프로젝트의 규모와 성격에 따라 React Router 안에서 처리할 수 있는 부분은 그 안에서 처리하는 방식을 선호한다.

상태 관리와 데이터 fetching에서는 낙관적 UI, TanStack Query, Zustand를 선호한다. React Context로 전역 상태를 크게 관리하는 방식보다는 Zustand를 사용하는 쪽이 더 잘 맞는다. prop drilling은 선호하지 않는다. 함수 이름, 변수 이름, 컬럼 이름처럼 코드 안의 이름을 정하는 일에도 시간을 쓰는 편이고, 좋은 예제와 기존의 우수한 구현을 참고하는 편이다.

Vite는 개발 서버와 빌드 도구로 선호한다. 전체 애플리케이션 구조를 강하게 규정하는 메타프레임워크보다, 필요한 구성을 직접 조합할 수 있는 도구가 더 잘 맞는다. TypeScript는 기본 언어로 사용하고, 타입을 느슨하게 두기보다는 가능한 한 명시적으로 유지하는 편을 선호한다.

스타일링은 Tailwind CSS v4를 선호한다. 컴포넌트 단위로 UI를 나누고, 스타일도 컴포넌트 근처에서 바로 파악할 수 있는 방식이 좋다. shadcn/ui는 컴포넌트를 패키지처럼 숨겨서 쓰는 방식이 아니라, 코드로 가져와 직접 소유하고 수정할 수 있다는 점에서 선호한다. Zod도 자주 사용하는 도구다. 입력값, API 경계, 폼 데이터처럼 런타임 검증이 필요한 부분에서 타입과 실제 데이터의 간극을 줄이는 데 유용하다.

### Runtime

런타임은 웹 표준에 가까운 환경을 선호한다. `Request`, `Response`, `fetch`, `URL`, `Headers` 같은 Web API를 그대로 사용할 수 있는 구조가 좋다. 이 점에서 Cloudflare Workers는 선호하는 런타임이다. 배포가 단순하고, 비용이 낮고, 런타임 모델이 비교적 명확하다.

FastAPI, Express, Hono도 사용할 수 있지만 기본 선택지는 아니다. 별도의 API 서버가 필요한 경우에는 프로젝트 성격에 따라 선택할 수 있고, 홈서버에서 FastAPI나 Express API 서버를 직접 돌리며 여러 실험을 해본 경험도 있다. 다만 현재의 풀스택 React 프로젝트에서는 React Router의 서버 기능을 먼저 고려한다. 백엔드를 항상 독립된 서버 애플리케이션으로 분리해야 한다고 보지는 않는다.

### Database

데이터베이스는 PostgreSQL을 기본 선택지로 둔다. Supabase, Firebase, MongoDB, SQLite 계열도 사용해봤지만, 장기적으로는 PostgreSQL을 직접 운영하는 방식을 선호한다. 특히 Supabase는 PostgreSQL 기반이라는 점은 좋지만, Auth, Storage, Realtime, Edge Functions, SDK, 운영 방식까지 함께 사용하다 보면 플랫폼에 묶이는 부분이 많아져 기본 선택지로 두지 않는다.

ORM은 Prisma나 Drizzle보다 postgres.js를 이용해 SQL을 직접 작성하는 방식을 선호한다. 쿼리와 데이터 모델이 코드 안에서 직접 보이는 편이 좋다. 데이터베이스는 애플리케이션의 핵심 구조에 가깝기 때문에, 쿼리가 추상화 뒤에 숨거나 ORM의 모델 정의와 마이그레이션 방식에 강하게 끌려가는 구조는 선호하지 않는다.

간단한 프로젝트에서는 Cloudflare D1 같은 SQLite 계열도 사용할 수 있다. 다만 D1은 작은 프로젝트나 Cloudflare Workers와 강하게 결합된 단순한 서비스에 적합한 선택지로 보고, 장기적으로 관리할 데이터가 있는 프로젝트에서는 PostgreSQL을 우선 고려한다. MySQL은 기본적으로 선호하지 않는다.

### Infrastructure

프로젝트 인프라는 Docker Compose로 관리하는 방식을 선호한다. Kubernetes나 복잡한 오케스트레이션이 필요한 규모가 아니라면, 서비스 구성을 명시적으로 볼 수 있고 로컬과 홈서버 환경에서 그대로 다루기 쉬운 Docker Compose가 더 잘 맞는다. 데이터베이스, 크롤러, 백엔드, 작업 큐, 관리 도구 같은 구성 요소를 한 프로젝트 안에서 직접 확인하고 제어할 수 있는 방식이 좋다.

도메인은 보통 Hosting.kr에서 구매하고, DNS는 Cloudflare를 사용한다. Cloudflare는 DNS 외에도 Email Routing, Workers, Tunnel, Zero Trust, Hyperdrive, R2처럼 함께 사용할 수 있는 기능이 많아서 기본 인프라 계층으로 두기 좋다. 홈서버를 외부에 노출할 때는 포트를 직접 열기보다 Cloudflare Tunnel을 이용해 아웃바운드 연결로 노출하고, Zero Trust로 접근을 제한하는 구성을 선호한다.

PostgreSQL은 보통 직접 운영하는 쪽을 선호한다. Cloudflare Workers에서 PostgreSQL에 접근해야 하는 경우에는 Hyperdrive를 통해 커넥션 풀링을 처리하는 구성을 고려한다. 매니지드 서비스가 편하다는 점은 인정하지만, 장기적으로 비용과 통제권을 생각하면 직접 운영 가능한 구조가 더 잘 맞는다.

### Auth

인증은 Auth0 같은 매니지드 인증 서비스보다 jose, arctic을 이용해 직접 구현하는 방식을 선호한다. OAuth provider 연동, PKCE, redirect flow, token exchange, session handling 같은 흐름을 애플리케이션 안에서 직접 이해하고 다루는 쪽이 좋다.

인증은 편리한 서비스 하나로 해결할 수도 있지만, 애플리케이션의 경계와 권한 모델에 직접 연결되는 부분이라 지나치게 외부 플랫폼에 맡기는 것을 선호하지 않는다. JWT, 세션, 쿠키, CSRF, PKCE 같은 요소가 어떻게 맞물리는지 이해한 상태에서 필요한 만큼 직접 구성하는 방식을 선호한다.

### Web Analytics & Marketing

웹 서비스 운영에서는 쿠키, 세션, 리다이렉트, 트래킹 파라미터, 광고 픽셀, 전환 측정처럼 브라우저와 네트워크 계층에서 실제로 무슨 일이 일어나는지 이해하려고 한다. 단순히 SDK를 붙이는 수준이 아니라, 요청과 응답, 쿠키 저장 범위, 도메인, 리퍼러, UTM, 광고 플랫폼의 attribution이 어떻게 이어지는지 확인하며 다루는 편이다.

퍼포먼스 마케팅도 직접 집행해본 경험이 있다. freemove.kr을 홍보할 때 네이버, 당근, Google 등에서 광고를 돌려봤고, 제품을 만든 뒤 실제 유입을 만들고 측정하는 과정까지 경험했다.

### AI

AI 서비스 구현에는 Vercel AI SDK를 선호한다. 특정 모델 공급자 하나에 강하게 묶이지 않고, 여러 공급자를 바꾸거나 조합하기 쉽고, fallback 구성을 만들기 좋기 때문이다. 모델 호출, 스트리밍, provider 교체 같은 부분을 애플리케이션 코드 안에서 비교적 일관된 방식으로 다룰 수 있는 점이 좋다.

폐쇄형 모델도 사용하지만 오픈웨이트 모델을 더 선호한다. 모델 자체를 직접 이해하고, 필요하면 다른 런타임이나 배포 방식으로 옮길 수 있는 가능성이 있는 쪽이 좋다. gpt-oss-120b 같은 오픈웨이트 모델에 관심이 있다.

AI 코딩 도구는 단순한 질의응답 도구보다는 코드베이스 안에서 함께 수정하고 검토하는 개발 도구로 사용한다. 로컬 개발 환경에 맞게 세팅하고, 실제 프로젝트의 구현, 리팩터링, 검토 과정에 넣어 사용하는 방식을 선호한다.

### Automation & Data Work

크롤링과 자동화는 주로 Python과 Playwright를 사용한다. Selenium보다 Playwright를 선호한다. 브라우저 자동화가 필요한 경우에도 API, DOM, 네트워크 요청을 비교적 명확하게 다룰 수 있는 도구가 더 잘 맞는다.

임시로 JupyterLab에서 돌리는 방식보다는 생 Python 스크립트나 FastAPI 안에 넣어 운영 가능한 형태로 만드는 방식을 선호한다. 크롤링 결과도 JSON 파일로 쌓아두기보다는 데이터베이스에 저장하는 편이 좋다. 데이터가 쌓이기 시작하면 결국 조회, 갱신, 중복 처리, 스케줄링, 실패 복구 같은 문제가 생기기 때문에 처음부터 DB에 넣는 구성이 더 자연스럽다.

경영과학 수업에서는 따릉이 대여소별 순유입/순유출을 예측하고, 그 결과를 바탕으로 재배치 전략을 시뮬레이션하는 프로젝트를 진행했다. 대여소 임베딩, 시간/날짜 순환 인코딩, TensorFlow 모델, SQLite/Pandas 기반 집계, Folium 지도 시각화, 최소 비용 흐름 문제로의 모델링까지 다뤘다. 딥러닝은 TensorFlow를 사용해 기본적인 수준으로 다룰 수 있고, 로컬 노트북에서 CUDA나 Anaconda 환경을 구성해본 경험도 있다.

### Hardware

소프트웨어 밖의 간단한 하드웨어 작업도 다룰 수 있다. Arduino 기반의 간단한 장치를 만들 수 있고, EasyEDA로 PCB를 설계해 JLCPCB에 제작을 맡겨본 경험이 있다. 기본적인 배선, 전기 개념, 납땜을 다룰 수 있다.

하드웨어를 전문 영역으로 내세우기보다는, 필요한 경우 물리적인 장치까지 직접 만들어볼 수 있는 정도의 역량으로 보는 편이 맞다. 소프트웨어로만 끝나지 않는 작은 자동화나 장치 제작이 필요할 때 직접 시도할 수 있다.

## What I’ve Built

### boxfold.newconfinedmind.workers.dev

boxfold.newconfinedmind.workers.dev는 현재 주력하고 있는 프로젝트다. 공장에서 올라가는 작업 흐름과 연결된 서비스를 만들고 있다. 현재 집중하고 있는 프로젝트이므로, 상세 설명은 `Current Focus` 섹션에서 더 다루는 편이 좋다.

### Dreamerola

Dreamerola는 직접 녹음한 내용을 바탕으로 Gemini API를 호출해 꿈일기를 기록하고 분석하는 iOS 앱이다. 유료 Apple Developer Program 비용을 내고 실제 App Store 심사를 통과했다는 점에 의미가 있다. 기능 자체도 중요하지만, iOS 앱을 실제 배포 대상으로 만들고 심사 절차를 통과한 경험이 핵심이다.

### Jedger

Jedger는 AI를 이용해 복식부기를 다루는 서비스다. 현재 PG 승인을 기다리고 있으며, 실제로 돈을 받을 수 있는 서비스로 가기 위한 단계에 있다. iOS 앱에서 App Store 심사 통과가 의미 있었던 것처럼, Jedger에서는 결제와 정산을 포함한 상용 서비스 운영의 관문을 통과하는 것이 중요하다.

결제는 PortOne SDK를 사용한다. 서비스 규모가 아주 커지기 전까지, 구체적으로 MRR이 1,000만 원 이상이 되기 전까지는 PortOne SDK를 계속 사용할 계획이다. 결제 영역은 직접 구현보다 안정성과 심사, 운영 경험이 더 중요하게 작동하는 구간으로 보고 있다.

### Cunvus

Cunvus는 Remotion 라이브러리를 이용해 카드뉴스와 동영상을 만들 수 있는 프로젝트다. 렌더링이나 생성 작업은 홈서버의 Node 프록시를 경유하는 구조로 구성했다. 콘텐츠를 이미지나 영상 형태로 자동 생성하는 흐름을 다룬 프로젝트로 볼 수 있다.

### teamMED Management Science Project

경영과학 팀프로젝트에서는 서울시 따릉이 데이터를 이용해 대여소와 시간대별 순유입/순유출을 예측하고, 이를 바탕으로 자전거 재배치 전략을 설계했다. 단순한 통계 분석이 아니라, 예측 모델과 최적화 문제를 연결해 운영 효율과 이용자 편의를 동시에 다루는 프로젝트였다.

기술적으로는 대여소 ID를 그대로 쓰는 대신 임베딩 벡터로 표현하고, 시간과 날짜는 주기성을 반영하기 위해 사인/코사인 인코딩을 사용하는 구조를 검토했다. 이후 TensorFlow 모델, Pandas/SQLite 집계, Folium 지도 시각화, 재배치 전략 시뮬레이션을 다뤘고, 라우팅 문제는 Google OR-Tools의 최소 비용 흐름 문제로 풀 수 있다고 정리했다. AI 모델, 데이터 파이프라인, 시각화, 경영과학적 최적화를 한 문제 안에서 연결한 경험이다.

### freemove.kr

freemove.kr은 스쿠터 대여 사이트로 만들었던 프로젝트다. 이후 주식회사 네솔에게 이전했다. 실제 사용 목적이 있는 웹사이트를 만들고, 도메인과 서비스 운영까지 포함해 외부 주체에게 넘긴 경험으로 정리할 수 있다.

이 프로젝트를 홍보하는 과정에서 네이버, 당근, Google 광고를 직접 집행해봤다. 단순히 사이트를 만드는 데서 끝나지 않고, 실제 유입을 만들고 광고 성과를 확인하는 퍼포먼스 마케팅 경험까지 연결된 프로젝트다.

### braindev.jangyunje.com

braindev.jangyunje.com은 고모부의 부탁으로 만든 PDF 기반 퀴즈 생성 서비스다. PDF를 읽고 퀴즈를 만드는 서비스를 약 5시간 만에 만들었다. 빠르게 요구사항을 서비스 형태로 바꾸고, AI 기능을 실제 사용 가능한 도구로 연결하는 능력을 보여주는 사례다.

### theindex.today and dlvr.life

theindex.today와 dlvr.life는 오래전부터 만들고 싶었던 CRM 방향의 프로젝트와 연결되어 있다. Supabase를 사용하다가, 홈서버에서 Supabase를 직접 돌려보기도 했고, 이후 다시 PostgreSQL을 직접 쓰고 싶어지는 식의 기술 변천이 있었다. 그래서 현재는 관리가 잘 되고 있는 프로젝트라기보다는, CRM과 AI 기반 데이터 조작에 대한 실험이 쌓인 프로젝트들에 가깝다.

이 프로젝트들에서는 AI가 tool calling을 통해 데이터베이스를 업데이트하는 흐름을 다뤘다. 단순히 AI 응답을 화면에 보여주는 수준을 넘어서, AI가 실제 애플리케이션 상태와 DB를 변경하는 형태를 실험했다는 점에 의미가 있다.

## Current Focus

현재는 자주 쓰는 스택이 어느 정도 정립된 상태다. React Router, Vite, TypeScript, Tailwind CSS, shadcn/ui, TanStack Query, Zustand, PostgreSQL, Docker Compose, Cloudflare 인프라를 중심으로 프로젝트를 빠르게 만들고 운영하는 흐름이 잡혀 있다.

boxfold.newconfinedmind.workers.dev가 현재 가장 주력하는 프로젝트다. 공장이나 현장 업무에서 실제로 올라오는 흐름을 서비스로 만드는 작업에 집중하고 있다. 이 프로젝트는 지금 진행 중인 일이므로, 기능 범위, 사용자, 데이터 모델, 운영 방식이 더 구체화되면 별도의 대표 프로젝트로 분리해 설명하는 것이 좋다.
