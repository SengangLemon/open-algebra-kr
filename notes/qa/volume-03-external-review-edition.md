# Volume 3 외부 검토용 판본 검수 — Draft 0.10

검수 대상: `volume3/` 전권, 외부 검토 안내, 검토 지침·상태표와 이슈 양식

검수일: 2026-08-08

PDF 감사 기준 커밋: `21a293ba05a404574feec2e1045cb9ae1c3613bc`

GitHub Actions: Run `31253294662`, Volume 1·Volume 2·Volume 3 매트릭스 빌드 모두 성공

Volume 3 artifact: `9020673073`, ZIP digest `sha256:84fa845a6bd0beb20785285384933f3b742c012e02749098ed010ebe3b85ef85`

## 결과 요약

- 판형: A4
- Volume 3 PDF: **303쪽**
- XeLaTeX/xdvipdfmx 빌드: 성공
- PDF 제목: `Open Algebra KR, Volume 3, Draft 0.10`
- PDF 개요: **258개**
- 내부·외부 링크: **346개**
- 모든 페이지: `595.28 × 841.89 pt`, 회전 `0`
- 물리적으로 빈 페이지: 없음
- 페이지 경계 밖 텍스트 블록: 없음
- 유효하지 않은 링크·목차 목적지: 없음
- 폼·JavaScript·첨부파일·암호화: 없음
- 모든 사용 글꼴: PDF에 임베드됨
- Ghostscript 전체 페이지 해석 검사: 성공
- PDF SHA-256: `e2d5452973d01e71f7905536681d583d6cd848df8c0e13c45c793afca0a3eab1`

GitHub Actions의 Node.js 폐기 예정 경고는 외부 액션에 관한 것이며 LaTeX 원고나 생성된 PDF의 오류가 아니다.

## 1. 판본의 성격

Draft 0.10은 외부 검토가 끝난 판본이 아니라, **독립 외부 검토를 요청하기 위한 판본**이다. 저자와 AI 도구가 수행한 장별·전권 내부 QA를 외부 검토 완료로 표시하지 않는다.

PDF와 저장소에 다음 내용을 명시했다.

- 외부 검토용 공개 초고이며 정식 출판본이 아님
- 내부 검수와 집필에 참여하지 않은 독립 검토를 구분함
- 수학적 정확성, 학습 흐름, 한국어 교열, 판면·접근성을 별도로 검토함
- 발견 사항을 GitHub Issues와 수정 커밋으로 추적함
- blocker와 major가 해결된 뒤에만 릴리스 후보로 승격함

## 2. 외부 검토 기반시설

### 2.1 PDF 안내

`volume3/frontmatter/review-notice.tex`을 추가하여 다음을 PDF 안에서 바로 확인할 수 있게 했다.

- 판본과 검토 목적
- 검토 요청 분야
- 물리 페이지·정리·문제 번호를 포함한 오류 보고 형식
- GitHub Issues 주소
- 검토 지침의 저장소 경로

### 2.2 검토 지침과 상태표

다음 문서를 추가했다.

- `notes/reviews/volume-03-external-review-guide.md`
- `notes/reviews/volume-03-review-status.md`

검토 지침은 장별로 높은 위험을 가진 정리·공식·가정을 나열하고, `blocker`, `major`, `minor`, `copyedit`, `layout`, `suggestion`의 심각도를 정의한다. 상태표는 각 장의 수학 검토, 한국어 교열과 판면 검토의 실제 담당·범위를 추적한다.

### 2.3 이슈 양식과 공개 추적 이슈

다음 이슈 양식을 추가했다.

- `.github/ISSUE_TEMPLATE/volume3-mathematical-review.md`
- `.github/ISSUE_TEMPLATE/volume3-copyedit-layout.md`

공개 검토 라운드의 상위 추적 이슈를 열었다.

- 수학 검토: Issue #23
- 한국어 교열·판면 검토: Issue #24

두 이슈 모두 검토자의 전문 범위, 실제 확인 범위, 방법과 집필 참여 여부를 기록하도록 요청한다.

## 3. 수학적 수정

Chapter 1의 대칭 유리함수 고정체 정리에서 기본대칭식의 대수적 독립성 증명을 초월차수 논증으로 강화했다.

```text
각 T_i는 k(s_1,...,s_n) 위에서 대수적
⇒ L=k(T_1,...,T_n)은 k(s_1,...,s_n) 위에서 대수적
⇒ trdeg_k k(s_1,...,s_n)=trdeg_k L=n
⇒ n개의 생성원 s_1,...,s_n은 k 위에서 대수적으로 독립
```

이 논증은 새로운 독립변수와 그 근을 다시 도입하는 이전 서술보다 짧고, 고정체 계산과 대수적 독립성 사이의 의존관계를 직접 보여 준다.

## 4. 텍스트와 용어 검사

`pdftotext -layout`과 PyMuPDF 추출 결과에서 다음을 확인했다.

```text
Draft 0.10: 존재
Draft 0.9: 0회
Draft 0.1: 0회
외부 검토 안내 제목: 존재
GitHub Issues URL: 존재
“외부 검토가 완료되었다는 뜻이 아니다”: 존재
분해삼차식: 0회
정상확장: 0회
미해결 참조 ?? : 0회
U+FFFD 대체문자: 0회
검은 사각형 대체문자: 0회
```

## 5. PDF 구조 검사

PyMuPDF와 PDF 검사 스크립트로 다음을 확인했다.

```text
pages: 303
page size: 595.28 × 841.89 pt on all pages
rotation: 0 on all pages
outline items: 258
links: 346
bad outline destinations: 0
bad link destinations: 0
blank physical pages: 0
text blocks outside page boundary: 0
form fields: 0
attachments: 0
encrypted: false
```

`pdffonts`에서 모든 글꼴의 embedded 값이 `yes`이고, Ghostscript nullpage로 303쪽 전체를 오류 없이 해석했다.

## 6. 렌더링과 시각 검수

### 6.1 변경 페이지

Draft 0.9와 정규화된 텍스트를 비교했을 때 Draft 0.10에서 고유하게 달라진 물리 페이지는 다음과 같다.

```text
1–14, 30
```

이는 표지·판권면·외부 검토 안내·목차·머리말·독자 안내와 Chapter 1의 보강된 증명 페이지이다. 이 페이지들을 포함하도록 물리 페이지 `1–18, 29–31, 303`을 PDFium 150dpi로 렌더링하여 육안 검수했다. 표지, 검토 안내, URL, 목차, 머리말, 학습 경로 도식, 수식과 색상 상자에 잘림·겹침·깨진 한글이 없음을 확인했다.

표지·판권면·검토 안내와 보강된 증명 페이지는 Poppler 150dpi로 다시 렌더링하여 두 렌더러에서 동일한 판면을 확인했다.

### 6.2 Draft 0.9와의 회귀 비교

Draft 0.9와 Draft 0.10에서 정규화된 텍스트가 유일하게 일치하는 페이지를 대응시켰다.

```text
Draft 0.9 pages: 301
Draft 0.10 pages: 303
unique text-matched pages: 288
pixel-identical at 72dpi: 288
changed matched pages: 0
```

따라서 외부 검토 안내와 의도한 증명 수정 이외의 기존 본문은 불필요하게 재조판되지 않았다.

### 6.3 감사 PDF의 재현성

PDF 감사 전에 검토한 Draft 0.10 빌드와 GitHub Actions Run `31253294662`의 감사 artifact를 72dpi로 전 페이지 비교했다.

```text
raster-equal pages: 303
raster-changed pages: 0
```

두 파일은 생성시각 메타데이터로 바이너리 해시는 다를 수 있지만, 303쪽의 시각적 결과는 동일하다.

## 7. 현재 판정

**Draft 0.10 외부 검토용 판본 제작과 내부 출고 검수 완료.**

다음 사항은 아직 완료되지 않았다.

- 집필에 참여하지 않은 수학자의 독립 검토
- 전문 한국어 교열자의 전권 교열
- 인쇄·접근성을 포함한 전문 판면 디자인 검수

이 세 항목의 실제 범위와 결과는 `notes/reviews/volume-03-review-status.md`와 공개 이슈에서 별도로 추적한다. 외부 검토가 접수되기 전에는 “외부 검토 완료”로 표시하지 않는다.
