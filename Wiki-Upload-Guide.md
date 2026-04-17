# Wiki Upload Guide

## 폴더 구조

```text
Home.md
HOG.md
Image-Redo-Prompts.md
_Sidebar.md
Hog_Image/
  1776400174.png
  1776400198.png
  1776400209.png
  1776400231.png
  1776400241.png
  1776400263.png
```

## 핵심 규칙

1. `Home.md`는 위키 첫 화면이다.
2. `HOG.md`는 본문 문서다.
3. 이미지는 `Hog_Image/` 폴더에 넣는다.
4. 본문에서는 상대경로로 이미지를 부른다.

예시:

```md
![HOG 전체 파이프라인](./Hog_Image/1776400174.png)
```

## 웹에서 수동으로 올릴 때

1. 위키 메인에서 `Home` 편집 화면을 연다.
2. `Home.md` 내용을 붙여넣는다.
3. `New Page`로 `HOG` 페이지를 만들고 `HOG.md` 내용을 붙여넣는다.
4. `New Page`로 `Image-Redo-Prompts` 페이지를 만들고 내용을 붙여넣는다.
5. 편집 중인 페이지 본문 하단에 이미지 파일을 드래그 앤 드롭해 업로드한다.
6. 업로드 후 생성된 경로 대신, 가능하면 위키 git 저장소 안에 `Hog_Image/` 폴더를 유지하는 방식으로 관리한다.

## 가장 쉬운 운영 방식

가능하면 위키 저장소를 로컬에 clone해서 아래처럼 관리한다.

```text
repo.wiki/
  Home.md
  HOG.md
  Image-Redo-Prompts.md
  _Sidebar.md
  Hog_Image/
```

그 다음 commit / push 하면 위키 구조가 안정적으로 유지된다.
