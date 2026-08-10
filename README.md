# 100일 프로젝트 — 폰 홈 화면 앱

푸시업 · 스쿼트 · 10km 100일 기록(2026-06-26 → 2026-10-03). Day 1~46은 노션 체크리스트 내용이 기본값으로 들어가 있습니다.

## 파일

| 파일 | 역할 |
|---|---|
| `index.html` | 앱 본체 |
| `manifest.json` | 앱 이름·아이콘·전체화면 설정 |
| `sw.js` | 오프라인 캐시 (설치 조건) |
| `icon-192.png` / `icon-512.png` | 홈 화면 아이콘 |
| `icon-1024.png` | 여분 원본 |

## 올리는 법 (GitHub Pages)

1. GitHub에서 새 저장소를 만듭니다. 공개(public)로 해야 Pages가 무료입니다.
2. 이 폴더의 파일을 저장소 최상단에 올립니다. 웹에서 **Add file → Upload files**로 드래그해도 됩니다.
3. **Settings → Pages → Source: Deploy from a branch**, 브랜치 `main`, 폴더 `/ (root)`, 저장.
4. 1~2분 뒤 `https://<계정>.github.io/<저장소>/` 주소가 나옵니다.

노트북 Claude Code로 할 경우:

```bash
cd <이 폴더>
git init && git add . && git commit -m "100일 프로젝트"
gh repo create hundred-day --public --source=. --push
gh api -X POST repos/:owner/hundred-day/pages -f source[branch]=main -f source[path]=/
```

## 홈 화면에 추가

- **안드로이드(크롬)**: 주소를 열고 ⋮ → 앱 설치 / 홈 화면에 추가
- **아이폰(사파리)**: 공유 버튼 → 홈 화면에 추가

설치하면 주소창 없이 전체화면으로 뜨고, 비행기 모드에서도 열립니다.

## 기록 저장 방식

기록은 앱을 연 브라우저 안에 저장됩니다. 서버가 없어서 기기끼리 자동으로 맞춰지지 않습니다.

- 다른 기기로 옮길 때: 원래 기기에서 **기록 복사** → 새 기기에서 **기록 붙여넣기**
- 브라우저 데이터를 지우면 입력분이 사라지고 노션 46일치 기본값만 남습니다

## 고칠 만한 곳

- 시작일: `index.html`의 `const START=Date.UTC(2026,5,26)` (월은 0부터)
- 종목·색: `:root`의 `--push` `--squat` `--run`, 그리고 `.marks` 버튼 세 개
- 기본값 46일치: `const SEED` 블록
