# nutrifit-site — 뉴트리핏 소개 웹사이트 v1

정적 HTML 한 장(`index.html`) + `assets/`. 빌드 도구 없음. 웹 기획서 v1(2026-09-24)의 구성 0~9번 섹션을 그대로 따릅니다.

## 채워 넣을 자리 (파일만 넣으면 자동 반영)

| 자리 | 파일 | 규격 |
|---|---|---|
| 히어로 폰 화면 3장 · 3단계 · 결과 예시 | `assets/screens/s03.png` `s04.png` `s05.png` `s07.png` (`s02.png`는 예비) | 앱 화면 캡처, 세로 9:19.5 (예: 390×845), PNG |
| 공감 한 줄 배경 사진 | `assets/photo-cubes.jpg` | 이유식 큐브 트레이/그릇을 위에서, WebP·JPG 200KB 이하. 스톡이면 `index.html`의 `.credit` 문구에 출처 |
| 수상 이미지 | `assets/award.jpg` | 상장 또는 행사 사진, 4:3 |
| 팀 사진 | `assets/team/cha.jpg` `kang.jpg` `jung.jpg` | 정사각형, 자연광 |
| 베타 신청 구글 폼 | `index.html` 맨 아래 `BETA_FORM_URL = ""` | 3문항(월령·이메일·주 몇 회) 폼을 만든 뒤 URL만 넣기. 비어 있으면 메일 링크 사용 |
| 방문 통계 | `index.html` 맨 아래 주석 | Cloudflare Web Analytics 토큰 |
| OG 이미지 | `assets/og.png` (생성됨) | 배포 후 `og:image`를 절대 URL로 |

파일이 없는 동안은 "캡처 자리" 표시가 보입니다. 파일을 넣으면 표시가 사라지고 이미지가 그대로 들어갑니다.

## 배포 (GitHub Pages) — 운영 중

**주소: https://chayoyo3-hash.github.io/nutrifit-site/** (저장소 `github.com/chayoyo3-hash/nutrifit-site`, 2026-09-29 배포)

이 폴더(`site/`)가 원본입니다. 고친 뒤 저장소 루트에서 한 줄:

```powershell
.\scripts\deploy_site.ps1 -Message "docs: 캡처 교체"
```

스크립트가 `nutrifit-site` 저장소를 `%TEMP%`에 받아 `site/`를 그대로 복사하고 `main`·`gh-pages`에 push합니다(Pages는 `gh-pages`를 서빙). 1~2분 뒤 반영됩니다.
`og:image`·`og:url`은 이미 배포 주소 기준 절대 URL입니다.

## 도메인 연결 (지원금 승인 후)

1. 이 폴더에 `CNAME` 파일을 만들고 도메인 한 줄만 적음 (예: `nutrifit.kr`) → push
2. DNS에 추가: `A` 레코드 4개 (호스트 `@`): `185.199.108.153` `185.199.109.153` `185.199.110.153` `185.199.111.153` · `CNAME` (호스트 `www`): `<계정>.github.io`
3. GitHub **Settings → Pages → Custom domain**에 도메인 입력, *Enforce HTTPS* 체크

## 배포 전 확인

- 결과 예시·면책 문구 임상·규제 검토 (기획서 7장)
- 모바일 400px에서 가로 스크롤 없음, 첫 화면 2초 이내 (이미지 200KB 이하)
- 연락처 메일은 `index.html`에서 `chayoyo3@gmail.com` 세 곳
