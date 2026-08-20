# 넥서스엔(NexusN) 홈페이지

jlhuman.com 컨셉을 참고해 제작한 HR 서비스 기업 홈페이지입니다.
빌드 과정 없이 동작하는 정적 사이트로, `index.html`을 브라우저로 열면 바로 확인할 수 있습니다.

## 메인 페이지 시안 3종

### 고객사 선택용 신규 시안

- **시안 3** (`v3/index.html`) - 네이비와 민트 기반의 모던 휴먼 HR
- **시안 4** (`v4/index.html`) - 코랄 포인트와 곡선형 구성을 사용한 웜 코퍼레이트
- **시안 5** (`v5/index.html`) - 블랙과 라임, 비대칭 구성을 사용한 볼드 에디토리얼
- **시안 6** (`v6/index.html`) - 화이트와 블루 기반의 미니멀 테크 HR
- **시안 8-1** (`v8-1/index.html`) - 별도 제작자가 시안 8에 0818 수정요청을 반영한 기존 제작안
- **시안 8-2** (`v8-2/index.html`) - 원본 시안 8에서 직접 분기한 밝은 팀 이미지 중심 신규 제작안

각 시안은 동일한 회사 정보와 메뉴 구조를 사용하며, 레이아웃과 색상, 카드 표현 방식만 서로 다르게 구성했습니다.

- **시안 A** (`index.html`) — 화이트 + 블루의 클래식한 기업 사이트 스타일 (jlhuman.com 컨셉, 그래픽 배경)
- **시안 B** (`v2/index.html`) — 클래식 코퍼레이트 스타일 (명조체 제목, 딥 네이비 + 골드 포인트, 정갈한 박스형 구성)
- **시안 C** (`v3/index.html`) — 포토 코퍼레이트 스타일 (시안 A 기반 + 실제 사진으로 화면 구성)

세 시안은 동일한 메뉴/콘텐츠를 공유하며, 서브페이지는 현재 시안 A 스타일입니다.
시안 확정 후 선택된 디자인을 서브페이지 전체에 적용하고 나머지 시안을 정리하면 됩니다.

### 사진 (assets/img/)

시안 C에 사용된 사진은 모두 **무료 Unsplash License**(상업 이용 가능, 출처 표기 불필요)이며,
워터마크가 있는 Unsplash+ 유료 사진은 사용하지 않았습니다. 인물은 아시아계 모델 위주로 선정했습니다.
회사 실제 사진으로 바꾸려면 `assets/img/`의 파일을 같은 이름으로 교체하면 됩니다.
- 무료 사진: Unsplash(unsplash.com), Pexels(pexels.com), Pixabay(pixabay.com)
- 유료(한국인 모델 다수): 게티이미지뱅크, 크라우드픽, 셔터스톡

## 구조

```
index.html            메인 (슬라이드 배너 · WHY NEXUSN · 사업영역 · 프로세스 · 인재상 · Contact)
css/style.css         공통 스타일 (컬러는 최상단 :root 변수에서 일괄 변경)
js/main.js            공통 스크립트 (메뉴 구조 NAV, 헤더/푸터 렌더링, 슬라이더)
about/                회사소개: greeting(인사말) · overview(개요) · vision(비전) · why · history(연혁, 숨김)
services/             사업소개: outsourcing(도급) · dispatch(파견) · hr-solution
                      └ recruiting-agency(채용대행) · headhunting · consulting (depth 3)
recruit/              채용정보: talent(인재상) · process · jobs(진행 중인 채용) · apply(인재풀 등록)
board/                게시판: notice(공지) · insight(HR Insight) · certificate(증명서 발급 요청)
legal/                privacy(개인정보처리방침) · terms(이용약관)
assets/forms/         입사지원서 · 증명서 발급 신청서 양식 (xlsx)
```

## 운영/수정 가이드

- **메뉴 수정**: `js/main.js` 상단의 `NAV` 배열만 고치면 모든 페이지의 GNB/모바일 메뉴/서브페이지 탭에 반영됩니다.
- **회사 연혁 공개**: 페이지는 `about/history.html`에 만들어져 있고 메뉴에서는 숨김 상태입니다.
  공개하려면 `js/main.js`의 `NAV`에서 "회사 연혁" 항목의 `hidden: true`를 지우고, 연혁 내용(현재 예시)을 실제로 교체하세요.
- **메인 슬라이드 이미지**: 현재는 그라데이션 배경 3장이며 4.5초 간격으로 자동 전환됩니다.
  실제 사진을 쓰려면 `css/style.css`의 `.slide-1 ~ .slide-3`에 `background-image: url(...)`을 넣으면 됩니다.
  슬라이드를 4장으로 늘리려면 `index.html`의 `.slides` 안에 `<div class="slide slide-4"></div>`를 추가하고 CSS에 `.slide-4` 배경을 정의하세요.
- **지도**: 현재 구글 지도 embed(키 불필요)가 들어 있습니다. 카카오 지도를 쓰려면
  map.kakao.com에서 주소 검색 → 공유 → "지도 퍼가기" HTML을 복사해 `index.html`·`about/overview.html`의 iframe과 교체하세요.
  네이버/카카오 지도로 이동하는 버튼은 이미 포함되어 있습니다.
- **채용 공고**: `recruit/jobs.html`의 `job-card` 블록(현재 예시 3건)을 복사/수정해 관리합니다.
- **게시판 글**: `board/notice.html`, `board/insight.html`의 `board-list` 항목을 직접 수정합니다.
  글이 많아지면 블로그/노션 연동이나 CMS 도입을 권장합니다.
- **양식 파일**: `assets/forms/`의 xlsx 두 개는 전달받은 공식 입사지원서·증명서 발급 신청서입니다. 파일을 교체할 때는 현재 파일명을 유지하면 기존 다운로드 링크를 그대로 사용할 수 있습니다.

## 교체가 필요한 내용 (검토 필수)

- `about/overview.html` — 대표이사명(현재 "홍길동" 자리표시자)
- `about/history.html` — 연혁 내용 (예시)
- `recruit/jobs.html` — 채용 공고 (예시)
- `board/notice.html`, `board/insight.html` — 게시글 (예시)
- `legal/privacy.html`, `legal/terms.html` — 표준 양식 기반 초안이므로 시행 전 법률 검토 권장

## 배포

정적 파일이므로 Netlify, Vercel, GitHub Pages, Cloudflare Pages 또는 일반 웹호스팅에
폴더 전체를 업로드하면 됩니다. 별도의 서버나 빌드 설정이 필요 없습니다.
