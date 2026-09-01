# old-photos — 데이터·이미지 호스팅

「옛날 사진 AI갤러리」(`old-photos`) 앱이 받는 **정적 파일만** 두는 저장소다.
앱 코드는 [`shoo99/toss-old-photos`](https://github.com/shoo99/toss-old-photos) 에 있다.

```
data/photos.json   앱이 받는 유일한 목록 파일 (스키마 = 앱 저장소 SCHEMA.md)
img/{id}-o.jpg     원본(흑백) · 긴 변 1600px · JPEG 80
img/{id}-t.jpg     썸네일     · 긴 변  400px · JPEG 70
logo-600.png       앱 로고 (granite.config.ts 의 brand.icon 이 가리킨다)
```

## 만드는 법 — 손으로 고치지 마라

허브(dell-126)의 `_tools/oldphotos-build.mjs` 가 만든다.

```
Wikimedia Commons → 라이선스 필터 → 1600px 리사이즈 → 여기로 push
```

🔴 **`items` 의 순서가 곧 공개 순서다.** 다시 낼 때 정렬을 바꾸면
**어제 열려 있던 사진이 오늘 잠긴다.** 새 사진은 배열 뒤에 붙인다.

🔴 **라이선스 판정은 앱의 `src/lib/license.js` 를 그대로 import 해서 쓴다.**
허브가 규칙을 베껴 쓰면 앱과 어긋나는 순간 이중 잠금이 뜻을 잃는다.

## 실린 것의 출처

전부 Wikimedia Commons. Public domain · CC0 · CC BY · No restrictions · KOGL Type 1 만 싣는다.
CC BY-SA · ND · NC · 불명은 **버린다** — AI 복원이 2차적저작물 생성이라서다.
사진마다 `license` · `author` · `credit` · `sourceUrl` 을 담고, 앱이 화면에 표시한다.
