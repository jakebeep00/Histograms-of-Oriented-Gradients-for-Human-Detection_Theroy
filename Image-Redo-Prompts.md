# HOG 이미지 재제작 프롬프트

아래 프롬프트는 기존 그림 중 교체가 필요한 5장을 다시 만들기 위한 기준이다.  
공통 스타일은 다음으로 통일한다.

- 배경: 흰색 또는 아주 밝은 회색
- 스타일: 논문/강의용 기술 다이어그램
- 비율: `16:9`
- 색상: 파랑, 주황, 회색 계열 위주
- 텍스트: 영어 또는 한국어 중 하나로 일관
- 목표: 장식보다 정보 전달 우선, 축/범례/수식/라벨 명확

---

## 1. Motivation 비교 그림 (`1776400164.png` 교체용)

```text
Create a clean academic comparison diagram for HOG motivation on a white background, 16:9 ratio.

Left side title: "Existing Methods"
- Show three small panels labeled "Wavelet", "PCA-SIFT", and "Shape Context"
- Represent them as sparse local descriptors or weakly structured local features
- Show that they capture only partial local information around a human in a cluttered background
- Add short labels such as "sensitive to illumination", "limited shape representation", "sparse/local response"

Right side title: "HOG"
- Show a human silhouette covered by a dense regular grid
- Inside each grid cell, show small orientation histogram icons
- Emphasize dense local gradient distribution over the full body shape
- Add short labels such as "dense grid descriptor", "shape-focused", "robust to illumination changes"

Center caption:
"Why HOG? Robust human shape representation under cluttered background and illumination change"

Design notes:
- Make the comparison visually symmetric
- Do not place Shape Context under HOG
- Make the message explicitly: local/sparse descriptors vs dense gradient histogram encoding
```

---

## 2. Raw Data 시각화 (`1776400186.png` 교체용)

```text
Create a technical diagram explaining raw image data for HOG, white background, 16:9 ratio.

Left:
- Show a 120x120 grayscale human image patch
- Add a highlighted 8x8 square region

Middle:
- Zoom into the 8x8 patch
- Show enlarged grayscale blocks corresponding to the selected region

Right:
- Show the same 8x8 patch as a numeric pixel matrix
- IMPORTANT: every value must be an integer between 0 and 255
- Use realistic grayscale values such as 35, 48, 52, 180, 210, etc.

Bottom caption:
"Raw image patch is represented as a grid of pixel intensities before gradient computation"

Design notes:
- Include a subtle arrow from image patch to zoomed patch to numeric matrix
- Make sure there are no values above 255
- Keep the matrix readable and neat
```

---

## 3. Block Normalization / L2-Hys (`1776400221.png` 교체용)

```text
Create an educational diagram explaining HOG block normalization with L2-Hys, white background, 16:9 ratio.

Left panel:
- Show two similar local edge patterns
- One under bright sunlight, one under shadow
- Their raw histogram magnitudes should be visibly different
- Label: "Before normalization"

Center panel:
- Show a 2x2 cell block
- Concatenate four 9-bin histograms into one 36-D block vector
- Display the formula flow:
  "v -> v / sqrt(||v||^2 + eps^2) -> clip at 0.2 -> renormalize"
- Label this explicitly as "L2-Hys"

Right panel:
- Show the normalized histograms becoming similar in relative pattern
- Label: "After normalization"
- Add note: "contrast differences reduced, shape pattern preserved"

Design notes:
- Must include clipping and renormalization, not just plain L2 normalization
- Keep the math readable and visually connected to the block vector
- Use bar-chart histograms, not abstract symbols
```

---

## 4. Ablation Study 요약 그림 (`1776400253.png` 교체용)

```text
Create a clean multi-panel ablation-study summary figure for HOG (Dalal and Triggs 2005), white background, 16:9 ratio.

Panel A: Orientation bins
- x-axis: number of orientation bins
- y-axis: miss rate
- Show a U-shaped trend with best region around 9 bins
- Highlight "9 bins" as a practical optimum

Panel B: Smoothing scale
- x-axis: sigma
- y-axis: miss rate
- Show performance degrading as smoothing increases
- Highlight "sigma = 0" as best

Panel C: Cell / Block size summary
- Use a small heatmap or annotated matrix
- Distinguish:
  "Paper best miss-rate point: 6x6 cells, 3x3 blocks"
  "Common default configuration: 8x8 cells, 2x2 blocks"

Bottom caption:
"Ablation study shows that fine gradients, 9 bins, local contrast normalization, and overlapping blocks are critical"

Design notes:
- Do not claim 8x8 + 2x2 is the paper-wide best in every setting
- Clearly separate experimental best point from commonly used default setting
- Make axes and legends readable
```

---

## 5. DET Curve 해석 그림 (`1776400275.png` 교체용)

```text
Create a DET curve explanation figure for HOG vs older methods, white background, 16:9 ratio.

Main plot:
- x-axis: False Positives Per Window (FPPW), log scale
- y-axis: Miss Rate, log scale
- Lower-left region must be visually labeled as "better"

Curves:
- HOG
- Wavelet
- PCA-SIFT
- Shape Context

Important:
- HOG curve must be clearly lower and more left than the others across the important range
- Visually show that HOG achieves much lower false positives at similar miss rates

Add annotations:
- "Lower-left is better"
- "At similar miss rate, HOG reduces false positives by around an order of magnitude"

Design notes:
- Do not place HOG above worse methods
- Keep the legend simple and clean
- Make the overall message immediately readable even without reading the paper
```
