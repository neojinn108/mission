# CSS 정리

## 1. CSS란?

CSS는 **Cascading Style Sheets**의 약자로, HTML로 만든 웹페이지의 디자인과 배치를 꾸미는 데 사용하는 언어입니다.

HTML이 웹페이지의 구조를 담당한다면 CSS는 글자의 크기, 색상, 여백, 테두리, 정렬, 배치 등을 담당합니다.

## 2. CSS 적용 방식

### Inline CSS

HTML 태그 안에 `style` 속성을 직접 작성하는 방식입니다.

```html
<p style="color: blue;">파란색 글자</p>
```

### Internal CSS

HTML 파일의 `<head>` 안에 `<style>` 태그를 작성하는 방식입니다.

```html
<head>
    <style>
        p {
            color: blue;
        }
    </style>
</head>
```

### External CSS

CSS 내용을 별도의 `.css` 파일로 작성하고 HTML 파일에서 연결하는 방식입니다.

```html
<link rel="stylesheet" href="resume_style.css">
```

HTML과 CSS를 분리할 수 있어 유지보수가 편리합니다.

## 3. CSS Selector(선택자)

### 태그 선택자

```css
p {
    font-size: 16px;
}
```

### 클래스 선택자

```css
.intro {
    font-weight: bold;
}
```

### 아이디 선택자

```css
#name {
    font-size: 20px;
}
```

## 4. text 관련 속성

### font-size

글자 크기를 설정합니다.

```css
p {
    font-size: 18px;
}
```

### font-weight

글자 굵기를 설정합니다.

```css
h1 {
    font-weight: 700;
}
```

### text-align

글자의 정렬 방향을 설정합니다.

```css
p {
    text-align: center;
}
```

## 5. Box Model

HTML 요소는 박스 형태로 구성됩니다.

- Content: 실제 내용 영역
- Padding: 콘텐츠와 테두리 사이의 내부 여백
- Border: 요소의 테두리
- Margin: 요소 바깥쪽 여백

```css
div {
    width: 300px;
    height: 200px;
    padding: 20px;
    border: 1px solid black;
    margin: 20px;
}
```

## 6. box-sizing

```css
* {
    box-sizing: border-box;
}
```

`border-box`를 사용하면 width와 height 안에 padding과 border가 포함되어 크기 계산이 편리합니다.

## 7. 아이템 정렬

Flexbox를 사용하면 여러 요소를 쉽게 정렬할 수 있습니다.

```css
.container {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}
```

## 8. 반응형 디자인

화면 크기에 따라 레이아웃을 변경할 때 `@media`를 사용할 수 있습니다.

```css
@media (max-width: 600px) {
    .container {
        flex-direction: column;
    }
}
```

## 정리

HTML은 웹페이지의 구조를 만들고 CSS는 디자인과 배치를 담당합니다.

External CSS, 선택자, Box Model, Flexbox, 반응형 디자인을 활용하면 웹페이지를 더 보기 좋고 관리하기 쉽게 만들 수 있습니다.
