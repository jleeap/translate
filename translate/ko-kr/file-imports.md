# 외부 파일 삽입

![doc-imports](https://cloud.githubusercontent.com/assets/1908863/22716507/f352a4b6-ed5b-11e6-9bac-88837f111de0.gif)

## 사용법

단지

`@import "your_file"`

로 쉽게 이용할 수 있다. :)

`<!-- @import "your_file" -->` 또한 가능하다.

## 새로고침 버튼

새로고침 버튼은 미리보기의 오른쪽 모서리에 표기된다.
클릭해서 파일 캐시를 지우고 미리보기를 새로고침 할 수 있다.
이미지 캐시를 지우려는 경우 유용할 수 있다. [#144](https://github.com/shd101wyy/markdown-preview-enhanced/issues/144) [#249](https://github.com/shd101wyy/markdown-preview-enhanced/issues/249)

![screen shot 2017-02-07 at 5 48 52 pm](https://cloud.githubusercontent.com/assets/1908863/22716917/c7088ae0-ed5d-11e6-8db9-e1ab035a3a2b.png)

## 지원 파일 형식

- `.jpeg(.jpg), .gif, .png, .apng, .svg, .bmp` 파일은 마크다운 이미지로 처리된다.
- `.csv` 파일은 마크다운 표로 변환된다. 
- `.mermaid` 파일은 mermaid로 렌더링된다.
- `.dot` 파일은 viz.js (graphviz)로 렌더링된다.
- `.plantuml(.puml)` 파일은 PlantUML로 렌더링된다.
- `.html` 파일은 즉시 내장된다.
- `.js` 파일은 `<script src="your_js"></script>`를 통해 삽입할 수 있다.
- `.less` 와 `.css` 파일은 스타일로 삽입된다. 현재는 오직 로컬 `less` 파일만 지원된다. `.css` 파일은 `<link rel="stylesheet" href="your_css">`로 삽입된다.
- `.pdf` 파일은 `pdf2svg`에 의해 `svg` 파일로 변환되어 삽입된다.
- `markdown` 파일은 즉시 번역되어 삽입된다.
- 다른 모든 파일은 코드 블록으로 렌더링된다.

## 이미지 삽입

```markdown
@import "test.png" {width="300px" height="200px" title="my title" alt="my alt"}
```

## 온라인 파일 삽입

예시:

```markdown
@import "https://raw.githubusercontent.com/shd101wyy/markdown-preview-enhanced/master/LICENSE.md"
```

## PDF 파일 삽입

PDF 파일을 삽입할 때, [pdf2svg](extra.md)가 설치되어 있어야한다.
Markdown Preview Enhanced 는 로컬과 온라인 PDF 파일 삽입을 지원한다.
그러나 용량이 너무 큰 PDF파일을 삽입하는 것은 추천하지 않는다.

예시:

```markdown
@import "test.pdf"
```

### PDF 배치

- **page_no**
  PDF의 `n번째` 페이지를 표시. 한 페이지만 표시한다. 예를 들어 `{page_no=1}` 는 1 페이지를 의미한다.
- **page_begin**, **page_end**
  이용. 예를 들어 `{page_begin=2 page_end=4}` 은 2, 3, 4 페이지를 의미한다.

## 코드블록으로 강제 렌더링

```markdown
@import "test.puml" {code_block=true class="line-numbers"}
@import "test.py" {class="line-numbers"}
```

## 코드블록으로 삽입

```markdown
@import "test.json" {as="vega-lite"}
```

## 특정 줄 삽입

```markdown
@import "test.md" {line_begin=2}
@import "test.md" {line_begin=2 line_end=10}
@import "test.md" {line_end=-4}
```

## 코드 청크로 파일 삽입

```markdown
@import "test.py" {cmd="python3"}
```

[➔ 코드 청크](code-chunk.md)