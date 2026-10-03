# 100일 프로젝트 — 폰 홈 화면 앱

푸시업 · 스쿼트 · 10km 100일 챌린지(2026-06-26 → 2026-10-03)를 돌아보는 화면. 100일 기록이 코드에 고정으로 들어가 있고, 입력 기능은 없습니다.

## 보는 법

| 주소 | 화면 |
|---|---|
| `index.html` | 세로 회고 화면. 칸·구간을 누르면 그날 기록과 메모 |
| `index.html?play` | 하루씩 채워지는 재생(약 25초). 이야기가 있는 날에서 멈추고, 끝에 인바디 공개 |
| `index.html?play&land` | 1920×1080 가로 화면으로 재생(영상 녹화용) |
| `&speed=2` | 재생 속도 배수 |

재생 중 스페이스바 = 일시정지, R = 처음부터.

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

## 고칠 만한 곳 (index.html)

- 기록: `const LOG` — 한 줄이 10일, `p`=푸시업 `s`=스쿼트 `r`=10km, `-`=안 함
- 메모: `const MEMO` (1~46일은 노션 체크리스트, 47일부터는 구글포토로 추정)
- 구간: `const CHAPTERS`
- 인바디: `const INBODY`
- 재생에서 멈추는 날과 시간: `const HOLD`
- 시작일: `const START=Date.UTC(2026,5,26)` (월은 0부터)
