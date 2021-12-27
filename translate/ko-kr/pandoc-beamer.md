# Beamer Document

## 개요

Beamer 프레젠테이션을 **Markdown Preview Enhanced**에서 생성할 때, 문서의 font-matter 에 `beamer_presentation` 을 `output`으로 지정한다.   
 `#` 와 `##` 헤더 태그를 이용해 구분된 슬라이드 쇼를 만들 수 있다.(헤더 없이 수평줄(`----`)을 이용해 새 슬라이드를 만들 수도 있다.)  
아래는 간단한 슬라이드 쇼에 대한 예시이다.

```markdown
---
title: "Habits"
author: John Doe
date: March 22, 2005
output: beamer_presentation
---

# In the morning

## Getting up

- Turn off alarm
- Get out of bed

## Breakfast

- Eat eggs
- Drink coffee

# In the evening

## Dinner

- Eat spaghetti
- Drink wine

---

![picture of spaghetti](images/spaghetti.jpg)

## Going to sleep

- Get in bed
- Count sheep
```

## 내보내기 경로

`path` 옵션을 이용해 내보내기 경로를 지정할 수 있다. 예시:

```yaml
---
title: "Habits"
output:
  beamer_presentation:
    path: /Exports/Habits.pdf
---

```

`path` 가 지정되어 있지 않다면 문서는 자동적으로 같은 리렉토리 안에 내보내기한 파일을 저장한다.

## Incremental Bullets

You can render bullets incrementally by adding the `incremental` 옵션을 더해 글머리 기호를 :

```yaml
---
output:
  beamer_presentation:
    incremental: true
---

```

If you want to render bullets incrementally for some slides but not others you can use this syntax:

```markdown
> - Eat eggs
> - Drink coffee
```

## 테마

`theme`, `colortheme`, 그리고 `fonttheme` 옵션들을 이용하여 특정 Beamer 테마를 적용할 수 있다.

```yaml
---
output:
  beamer_presentation:
    theme: "AnnArbor"
    colortheme: "dolphin"
    fonttheme: "structurebold"
---

```

## 목차

`toc` 옵션은 프레젠테이션의 시작부분에 목차를 추가시킬 수 있다.(목차에는 1 레벨 목차로만 구성된다.) 예시:

```yaml
---
output:
  beamer_presentation:
    toc: true
---

```

## Slide Level

`slide_level` 옵션은 각각의 슬라이드의 제목 레벨을 정의한다. 기본값으로 제일 높은 헤더 단계이며, 문서의 다른 헤더가 아닌 내용이 바로 뒤에 나온다. 이 기본 값은 `slide_level`로 지정하여 변경할 수 있습니다. :

```yaml
---
output:
  beamer_presentation:
    slide_level: 2
---

```

## 구문 하이라이트

`highlight` 옵션은 구문 하이라이트 스타일을 지정한다. 지원되는 스타일로는 “default”, “tango”, “pygments”, “kate”, “monochrome”, “espresso”, “zenburn”, 그리고 “haddock” 이 있다.(구문 하이라이트를 사용하고 싶지 않다면 null 로 지정한다.):

For example:

```yaml
---
title: "Habits"
output:
  beamer_presentation:
    highlight: tango
---

```

## Pandoc Arguments

위에서 설명한 pandoc 기능 중 YAML 옵션에서 해당 기능이 없다면 사용자 지정 `pandoc_args`을 통해 이용할 수 있다. 예시:

```yaml
---
title: "Habits"
output:
  beamer_presentation:
    pandoc_args: ["--no-tex-ligatures"]
---

```

## 공유 옵션

여러 개의 문서들의 공유 옵션을 통일해서 정해주고 싶다면 디렉토리에  `_output.yaml` 이름을 포함하면 된다. YAML 구분기호나 출력개체는 이 파일에 적용되지 않는다. 예시:

**\_output.yaml**

```yaml
beamer_presentation:
  toc: true
```

`_output.yaml` 과 같은 디렉토리에 있는 모든 문서는 해당 옵션을 공유한다. 문서에 명시적으로 정의된 옵션은 해당 사항에 영향을 받지 않는다.