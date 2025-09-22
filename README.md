# 김개발 포트폴리오 (Static Web)

이 프로젝트는 `index.html`, `style.css`, `script.js`로 구성된 반응형 정적 포트폴리오 웹사이트입니다. 모바일/데스크톱 환경을 모두 고려했으며, 부드러운 스크롤, 섹션별 내비게이션 활성화, 스킬 바 애니메이션, 타이핑 효과, 카드/타임라인 등장 애니메이션, 간단한 폼 유효성 검사 등을 제공합니다.

## 미리보기
- **홈(히어로)**: 이름/직무 및 다국어 타이핑 효과, CTA 버튼
- **소개**: 경력 요약과 하이라이트 지표(년수/프로젝트/만족도)
- **기술**: 카테고리별 스킬 바(Intersection Observer로 애니메이션)
- **경력**: 타임라인 UI(좌우 교차 배치, 스크롤 등장)
- **프로젝트**: 카드 그리드(호버 상승, 태그/링크)
- **연락처**: 정보/소셜 링크 + 폼(간단 유효성 검사)

## 폴더/파일 구조
```
.
├─ index.html   # 페이지 마크업 (섹션: home/about/skills/experience/projects/contact)
├─ style.css    # 전체 스타일, 반응형(@media), 애니메이션 키프레임 포함
└─ script.js    # 내비 토글/스무스 스크롤/관찰자/타이핑/폼 검증/등장 애니메이션
```

## 주요 기능
- **반응형 내비게이션**: 햄버거 메뉴 토글(`.hamburger`, `.nav-menu.active`)
- **스무스 스크롤**: 고정 헤더 오프셋 고려, 섹션 이동
- **현재 섹션 활성화**: 스크롤 위치에 따라 `.nav-link.active` 업데이트
- **스킬 바 애니메이션**: `IntersectionObserver`로 `.skill-progress`의 `data-width` 적용 및 `animate` 클래스 부여
- **타이핑 효과**:
  - 단일 텍스트: `typeWriter(element, text)`
  - 멀티 텍스트: `multiTypeWriter(element, [texts])` (히어로 서브타이틀)
- **스크롤 등장 애니메이션**: `.timeline-item`, `.project-card`, `.skill-category`에 opacity/translateY 트랜지션
- **폼 유효성 검사**: 이름/이메일/제목/메시지 필수, 이메일 정규식 검사 후 알림
- **접근성 편의**: ESC 키로 모바일 메뉴 닫기, 외부 클릭/리사이즈 시 메뉴 상태 초기화

## 실행 방법
로컬 서버가 없어도 정적 파일만으로 동작합니다.

- 방법 A: 파일 더블클릭
  - `index.html`을 브라우저로 직접 열기
- 방법 B: 간단한 로컬 서버(권장)
  - Python
    - `python -m http.server 5500` 실행 후 `http://localhost:5500` 접속
  - Node (serve)
    - `npx serve -l 5500 .` 실행 후 `http://localhost:5500` 접속

## 커스터마이징 가이드
- **텍스트/콘텐츠**: `index.html`에서 섹션별 텍스트/프로젝트 카드/연락처 정보 수정
- **타이핑 문구 변경**: 히어로 영역의 `.typing-text`의 `data-texts` 배열 수정
- **스킬 수치 조정**: `.skill-progress`의 `data-width`(예: `90%`) 속성 변경
- **색상/테마**: `style.css`의 그라데이션/포인트 컬러(`[#3498db, #2ecc71]`) 조정
- **애니메이션 강도**: 등장 애니메이션 초기 스타일(불투명도/translateY/transition)을 `script.js` 219~225줄 근처에서 조정
- **헤더 높이 보정**: 고정 헤더 오프셋은 `section { scroll-margin-top: 80px; }`와 `script.js`의 스크롤 계산(`header.offsetHeight`)로 제어

## 기술적 참고
- Google Fonts: `Noto Sans KR`
- 인터랙션: `IntersectionObserver`, `requestTimeout` 기반 setTimeout 타이핑 루프
- 성능: 스크롤 이벤트 `throttle` 유틸로 최적화(약 60fps 목표)
- 모바일 대응: 768px/480px breakpoint에서 레이아웃 및 폰트 크기 조정

## 배포
정적 호스팅에 적합합니다.
- GitHub Pages: 리포지토리 `Settings > Pages`에서 루트 브랜치 선택
- Netlify/Vercel: 새 프로젝트로 연결 후 빌드 설정 없이 배포

## 라이선스
본 템플릿은 개인 포트폴리오 용도로 자유롭게 수정/배포할 수 있습니다. 외부 폰트/아이콘 사용 시 해당 라이선스를 따르세요.
