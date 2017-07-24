---
layout: post
title: "[무작정 따라하기 - 09] Arrow Navigation Styles"
description: "Codrops 사이트 예제 따라하기"
date: 2017-07-20
tags: [연습, css, hover effect]
comments: false
share: true
---

# Arrow Navigation Styles  

Codrops 사이트에 있는 [Arrow Navigation Styles](https://tympanus.net/codrops/2014/05/28/arrow-navigation-styles/) 샘플을 따라 만들었다.  
여러 가지의 화살표 네비게이션 효과를 적용한 샘플이다. 화살표들은 svg 아이콘을 사용하고 `transition`과 `animation`을 사용하였다.  

> [github 작업 링크](https://github.com/taekbari/SideProject/tree/master/09_Arrow_Navigation_Styles)  
> [데모 링크](https://taekbari.github.io/SideProject/09_Arrow_Navigation_Styles/)  

## 작성하면서 공부한 내용  

### `SVG`  

Scalable Vector Graphics(확장 가능한 벡터 그래픽). XML 기반으로 2차원의 벡터 그래픽을 표현하기 위해 사용된다.  
벡터 기반이기 때문에 기존의 비트맵 기반의 포맷과 달리 사이즈가 늘어나도 사진이 깨지지 않고 매끄럽게 표현되며 Web 환경에서는 CSS를 이용하여 스타일링이 가능하고 Javascript를 이용해서 이벤트 핸들링도 가능하다는 장점이 있다. 반면에 간단한 경우에는 JPG나 PNG보다 더 적은 용량일 수 있지만 Path가 많아지고 점점 더 무거워지면 기본 이미지 포맷보다 더 커질 수 있다.  

#### `<svg>`  

svg의 Root 태그이며 다음과 같이 사용된다.  

```html  
<svg width="300" height="300" xmlns="http://w3.org/2000/svg" version="1.1" viewbox="0 0 300 300">
</svg>
```

> `xmlns` : svg는 XHTML 스펙을 따르고 있기 때문에 NameSpace를 지정해줘야 한다.  
> `version` : 사용할 svg 스펙 버전을 말하는데 일반적으로 1.1을 사용하면 된다.  
> `width` & `height` : svg 요소의 크기를 지정해주며 무조건 지정해줘야 한다.  
> `viewbox` : 실제 svg영역 중에 보여줄 기준점을 정하는 속성이다. `viewbox="x y width height"`로 이우어져 있는데 `width`나 `height` 값이 0 이하이면 SVG가 렌더링 되지 않는다.  

#### `<path>`  

가장 강력한 기본 도형으로 선과 곡선, 호 등 다양한 형태를 그릴 수 있다.  
Paths는 여러개의 직선과 곡선을 합쳐서 복잡한 도형을 그릴 수 있게 해준다.  
Path의 모양은 `d`로 정의된다. `d` 속성은 여러 개의 명령어와 그 파라미터들로 이루어지며 좌표는 절대로 단위를 가질 수 없다.  

> 모든 명령은 2가지 변형이 존재하는데,  
> 알파벳이 대문자일 경우 : 뒤 따르는 좌표는 페이지의 절대좌표를 참조  
> 알파벳이 소문자일 경우 : 마지막 위치에 대한 상대적 좌표로 참조  

#### `<use>`  

`<g>`, `<svg>` 그리고 `<symbol>` 요소는 물론 다른 `<use>` 요소를 포함한 그래픽 SVG 요소를 복사하고 다시 사용할 수 있도록 하는 요소이다.  

#### `stroke` 속성  

SVG에서 제공하는 선긋기 속성으로 SVG 코드 또는 CSS 파일 내에서 설정이 가능하다.  

> `stroke` : 선의 색상을 결정하는 속성  
> `stroke-width` : 선의 두께를 결정하는 속성  
> `stroke-linecap` : 선의 끝모양을 결정하는 속성으로 `butt`, `round`, `squre` 속성값을 갖는다.  
> `stroke-dasharray` : 점선을 표현할 때 사용하는 속성  

### `perspective-origin`  

뷰어가 보여지는 위치를 결정하는 속성. `perspective` 속성에 의해 소실점으로 사용된다. 즉, `perspective-origin` 속성만 사용할 경우, 아무 효과가 나타나지 않는다.  

> 소실점 (vanishing point) : 우리가 사는 물리세계에서는 서로 평행한 두 직선은 영원히 만나지 않는다. 하지만 카메라 영상에서는 평행한 직선도 만날 수 있으며 교점의 좌표도 구할 수 있다. 이 교점을 소실점이라고 한다.  

---  

### 참고 사이트  

* [SVG 시작하기#1](https://brunch.co.kr/@kkak10/3)  
* [Paths](https://developer.mozilla.org/ko/docs/Web/SVG/Tutorial/Paths)  
* [SVG Stroke Properties](https://www.w3schools.com/graphics/svg_stroking.asp)  
* [perspective-origin on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/perspective-origin)  
