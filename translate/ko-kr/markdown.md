# Save as Markdown

**Markdown Preview Enhanced** supports compilation into **GitHub Flavored Markdown** so that the exported markdown file will include all graphs (as png images), code chunks (hide and only include results), math typesettings (show as image) etc and can be published on GitHub.

## 사용법

미리보기에서 우클릭하여, `Save as Markdown`을 선택한다.

## 설정

이미지 디렉토리와 출력 경로를 front-matter 로 설정할 수 있다.

```yaml
---
markdown:
  image_dir: /assets
  path: output.md
  ignore_from_front_matter: true
  absolute_image_path: false
---

```

**image_dir** `optional`  
생성된 이미지를 저장한 위치를 지정한다. 예를 들어, `/assets` 은 모든 이미지가 프로젝트 디렉토리 하위의 `assets` 디렉토리에 저장된다. 만약 **image_dir** 이 정해지지 않았다면, 패키지 설정의 `Image folder path` 로 저장된다. 기본값은 `/assets`이다.

**path** `optional`  
마크다운 파일의 출력값을 저장할 위치를 지정한다. 만약 **path** 가 정해지지 않았다면, `filename_.md` 에 저장된다.

**ignore_from_front_matter** `optional`  
`false`로 설정하면, `markdown` 필드가 front-matter 에 포함된다.

**absolute_image_path** `optional`  
절대 이미지 경로를 사용할지 상대 이미지 경로를 사용할지 결정한다.

## 저장시 내보내기

아래와 같이 front-matter 에 추가한다:

```yaml
---
export_on_save:
  markdown: true
---

```

그러면 마크다운 파일이 마크다운 파일을 저장할 때마다 생성될 것이다.

## 알려진 문제점

- `WaveDrom` 은 아직 작동하지 않는다.
- 수식 출력이 부정확할 수 있다.
- `latex` 코드 청크는 아직 작동하지 않는다.