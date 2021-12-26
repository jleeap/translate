# 마크다운 입문

This article is a brief introduction to [GitHub Flavored Markdown writing](https://guides.github.com/features/mastering-markdown/).

## Markdown 이란?

`마크다운` 은 웹에서 텍스트를 스타일링하는 방법이다. 사용자가 문서의 표시를 제어한다. 마크다운으로 수행할 수 있는 방법 중에서는 글자를 굵게 또는 기울임꼴로 지정하거나 이미지를 추가하고 목록을 만드는 작업 등이 있다. 대부분의 마크다운은 '#' 또는 '*' 같은 특수 문자가 포함된 일반 텍스트로 작성된다.

## 문법

### 헤더

```markdown
# This is an <h1> tag

## This is an <h2> tag

### This is an <h3> tag

#### This is an <h4> tag

##### This is an <h5> tag

###### This is an <h6> tag
```

`id` 와 `class` 를 헤더가 추가하고 싶다면, `{#id .class1 .class2}`를 덧붙인다. 
예시:

```markdown
# This heading has 1 id {#my_id}

# This heading has 2 classes {.class1 .class2}
```

> This is a MPE extended feature.

### 강조

<!-- prettier-ignore -->
```markdown
*This text will be italic*
_This will also be italic_

**This text will be bold**
__This will also be bold__

_You **can** combine them_

~~This text will be strikethrough~~
```

### 리스트

#### 순서가 없는 리스트

```markdown
- Item 1
- Item 2
  - Item 2a
  - Item 2b
```

#### 순서가 있는 리스트

```markdown
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```

### 이미지

```markdown
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```

### 링크

```markdown
https://github.com - automatic!
[GitHub](https://github.com)
```

### Blockquote

```markdown
As Kanye West said:

> We're living the future so
> the present is our past.
```

### 수평선

```markdown
세 개 이상의...

---

하이폰(-)

---

별표(*)

---

밑줄(_)
```

### 인라인 코드

```markdown
I think you should use an
`<addr>` element here instead.
```

### 코드 블록

코드 블록 앞 뒤에 3개의 백틱 <code>\`\`\`</code> 을 배치하여 코드블록을 만들 수 있다.

#### 구문 하이라이트

선택적 언어 식별자를 추가하여 코드 블록에서 구문 하이라이트를 사용할 수 있다.

예를 들어, Ruby 코드에 구문 하이라이트를 적용하면:

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("Hello World!")
    puts markdown.to_html
    ```

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

#### 코드 블록 클래스 (MPE extended feature)

코드블록에 `class` 를 설정할 수 있다.

예를 들어, 코드블록에 `class1 class2` 를 추가하려면

    ```javascript {.class1 .class}
    function add(x, y) {
      return x + y
    }
    ```

##### 줄 번호(코드 라인)

코드 블록에 `line-numbers` 클래스를 추가하여 줄 번호(코드 라인)를 만들 수 있다.

예시:

````markdown
```javascript {.line-numbers}
function add(x, y) {
  return x + y;
}
```
````

![screen shot 2017-07-14 at 1 20 27 am](https://user-images.githubusercontent.com/1908863/28200587-a8582b0a-6832-11e7-83a7-6c3bb011322f.png)

##### 행 하이라이트

'highlight'특성을 추가해서 행을 하이라이트할 수 있다.

````markdown
```javascript {highlight=10}
```

```javascript {highlight=10-20}
```

```javascript {highlight=[1-10,15,20-22]}
```
````

### 일정표

```markdown
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```

### 표

분류를 하이폰 '-'(첫 번째 행에 대해)으로 나눈 다음 각 열을 파이프 '|'로 구분하여 표를 만들 수 있다.

<!-- prettier-ignore -->
```markdown
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
```

## 확장 구문

### 표

> 작동하려면 확장 설정에서 `enableExtendedTableSyntax` 를 활성화시켜야된다.

![screen shot 2017-07-15 at 8 16 45 pm](https://user-images.githubusercontent.com/1908863/28243710-945e3004-699a-11e7-9a5f-d74f6c944c3b.png)

### 이모지 & Font-Awesome

> `markdown-it parser`에서만 작동하고 `pandoc parser`에서는 작동하지 않는다.  
> 기본값으로 활성화 되어있고, 패키지 설정에서 비활성화 시킬 수 있다. 

```
:smile:
:fa-car:
```

### 위첨자

```markdown
30^th^
```

### 첨자

```markdown
H~2~O
```

### 각주

```markdown
Content [^1]

[^1]: Hi! This is a footnote
```

### 약어

```markdown
*[HTML]: Hyper Text Markup Language
*[W3C]: World Wide Web Consortium
The HTML specification
is maintained by the W3C.
```

### 표시

```markdown
==marked==
```

### CriticMarkup

CriticMarkup은 기본값으로 **사용불가능** 하도록 설정되어있다. 하지만 패키지 설정을 통해 활성화시킬 수 있다.  
[CriticMarkup User's Guide](https://criticmarkup.com/users-guide.php) 에서 CriticMarkup 에 대한 정보를 더 알 수 있다.

There are five types of Critic marks:

- Addition `{++ ++}`
- Deletion `{-- --}`
- Substitution `{~~ ~> ~~}`
- Comment `{>> <<}`
- Highlight `{== ==}{>> <<}`

> CriticMarkup only works with the markdown-it parser, but not the pandoc parser.

### 경고

```
!!! note This is the admonition title
    This is the admonition body
```

> Please see more information at https://squidfunk.github.io/mkdocs-material/reference/admonitions/

## 참조

- [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
- [Daring Fireball: Markdown Basics](https://daringfireball.net/projects/markdown/basics)

[➔ 수식 입력](math.md)