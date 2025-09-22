## 김개발 포트폴리오 웹사이트

정적 HTML/CSS/JavaScript로 구현된 개인 포트폴리오 템플릿입니다. 반응형 네비게이션, 히어로 영역 타이핑 효과, 스크롤 트리거 애니메이션, 스킬 바 애니메이션, 간단한 연락처 폼 등을 포함합니다.

### 주요 특징
- **반응형 네비게이션**: 햄버거 메뉴, 현재 섹션 하이라이팅, 스무스 스크롤(고정 헤더 보정).
- **타이핑 효과**: 단일/멀티 텍스트 타이핑(`typeWriter`, `multiTypeWriter`)과 커서 깜박임.
- **스킬 바 애니메이션**: `IntersectionObserver`로 가시 영역 진입 시 진행도 채우기.
- **스크롤 등장 효과**: 타임라인/프로젝트/스킬 섹션 요소 페이드업.
- **접근성/키보드 지원**: ESC로 모바일 메뉴 닫기, 외부 클릭 닫기, 리사이즈 처리.
- **퍼포먼스 유틸**: `utils.debounce`, `utils.throttle` 포함.

### 파일 구조
- `index.html`: 페이지 마크업. 섹션: `home`, `about`, `skills`, `experience`, `projects`, `contact`.
- `style.css`: 전체 스타일, 반응형, 애니메이션 키프레임.
- `script.js`: 네비게이션, 스크롤/타이핑/스킬바 애니메이션, 폼 유효성 검증 등 인터랙션 로직.

### 빠른 시작
1) 이 저장소를 다운로드/복제합니다.
2) 브라우저로 `index.html`을 엽니다.
   - 로컬 서버를 원하면 간단한 정적 서버(예: VS Code Live Server, `python -m http.server` 등)를 사용해도 됩니다.

### 커스터마이징 가이드
- **이름/텍스트**: `index.html`의 히어로 영역에서 `김개발`, 소개 문구 등을 수정합니다.
- **멀티 타이핑 문구**: 히어로의 `.typing-text`의 `data-texts` 속성 배열을 편집합니다.
  ```html
  <span class="typing-text" data-texts='["Full-Stack Software Engineer", "..."]'></span>
  ```
- **스킬 퍼센트**: 각 `.skill-progress`의 `data-width` 값을 조정합니다(예: `90%`).
- **프로젝트 카드**: `#projects` 섹션의 카드 제목/설명/기술 태그/링크를 수정합니다.
- **연락처 정보**: `#contact` 섹션의 이메일/전화/소셜 링크를 업데이트합니다.
- **컬러/테마**: `style.css`의 그라데이션, 브랜드 컬러(`#3498db` 등)를 변경합니다.

### 동작 상세 (script.js)
- 네비게이션
  - 햄버거 클릭으로 `.nav-menu.active` 토글.
  - 링크 클릭 시 고정 헤더 높이(`.header.offsetHeight`)만큼 보정하여 스무스 스크롤.
  - 스크롤 위치에 따라 현재 섹션의 `.nav-link.active` 업데이트.
  - 스크롤 100px 이상 시 헤더 배경/그림자 강화.
- 스킬 바
  - `IntersectionObserver`가 `.skill-progress` 가시 시 `style.width = data-width` 적용 및 `.animate` 추가.
- 타이핑 효과
  - `typeWriter(element, text, speed)` 단일 텍스트.
  - `multiTypeWriter(element, texts, typeSpeed, deleteSpeed, pauseTime)` 멀티 텍스트 루프.
- 스크롤 등장 애니메이션
  - `.timeline-item, .project-card, .skill-category`에 초기 opacity/translateY 부여 후 가시 시 0으로 전환.
- 기타
  - ESC/외부 클릭/리사이즈 시 모바일 메뉴 닫기.
  - `utils.debounce/throttle` 제공. `optimizedScrollHandler` 예시로 60fps(약 16ms) 스로틀 적용.

### 접근성 및 UX 메모
- 고정 헤더를 고려해 모든 `section`에 `scroll-margin-top: 80px` 적용.
- 키보드로 메뉴 닫기(ESC) 가능. 필요 시 포커스 트랩, ARIA 속성 추가를 권장.
- 컬러 대비는 대체로 양호하나, 배경 그라데이션 위 흰 텍스트 대비를 검토하세요.

### 성능 메모
- 스크롤 핸들러는 스로틀 적용. 추가 로직은 `optimizedScrollHandler`에 병합 권장.
- 타이핑/스크롤 애니메이션은 requestAnimationFrame이 아닌 `setTimeout`/CSS 전환 사용. 필요 시 최적화 가능.

### 폼 동작
- 현재 연락처 폼은 데모용입니다. 제출 시 간단한 유효성 검사 후 알림만 표시하고 리셋합니다.
- 실제 전송을 원하면 Fetch/Webhook/백엔드 연동 또는 Formspree 등 사용을 권장합니다.

### 알려진 제한/개선 아이디어
- 폼 백엔드 미연동(실제 메일 전송 없음).
- SEO 메타/OG 태그 최소화. 제목/설명/OG 이미지 추가 권장.
- 타임라인 중앙선/마커는 데스크톱 레이아웃 기준. 세부 반응형 미세 조정 가능.

### 배포
- 정적 호스팅에 적합(GitHub Pages, Netlify, Vercel 등). 빌드 과정 불필요.

### 라이선스
- 미지정(추후 필요 시 추가하세요).


