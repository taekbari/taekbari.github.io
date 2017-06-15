---
layout: post
title: "Modernizr란??"
description: "Modernizr 알아보기"
date: 2017-06-01
tags: [study, modernizr, library]
comments: false
share: true
---

# Modernizr  

오픈소스 자바스크립트 라이브러리로, HTML5와 CSS3의 명세에 정의된 요소와 속성들에 대한 지원여부를 점검하는 방식으로 기존의 방식보다 더 정확한 분류가 가능하다.  

* 웹문서에 Modernizr 스크립트를 포함하면, 현재 브라우저가 CSS3 뿐만 아니라 HTML5의 기능에 대해서도 지원하는 정도를 점검할 수 있다.  
* Modernizr라는 자바스크립트 객체를 생성하여 boolean 속성으로 지원여부를 판단하게 된다.  
* `<html>` 요소에 어떤 요소와 속성들이 지원되고 지원되지 않는지 클래스 값을 이용해 표현해 준다.  
* 제공하는 script loader를 사용하여 구형 브라우저에 polyfill를 제공할 수 있다. 자바스크립트를 이용하여 지원 안되는 부분에 대한 기능을 추가할지 아니면 단순히 웹페이지의 기능을 축소할지에 대한 결정도 할 수 있게 된다.  

## Modernizr 사용법  

[Modernizr](https://modernizr.com/) 홈페이지에 접속하여 지원여부를 확인하고 싶은 요소 또는 속성을 선택하여 다운로드하여 사용한다.  

### Modernizr 삽입  

`<head>` 요소에 다운로드한 스크립트를 삽입힌다.  
```html  
<head>
  <link rel="stylesheet" href="css/main.css">
  <script src="js/vendor/modernizr-2.6.2.min.js"></script>
</head>
```  
성능적인 측면에서 스타일시트 다음에 위치하는 것이 추천된다.  

* html5 shiv는 `<body>` 요소 이전에 실행되어야 하기 때문이다.  
* Modernizr를 이용해 CSS 클래스들을 추가한다면 FOUC를 예방하기 위해 필요하다.  

> FOUC(Flash Of Unstyled Content) 란?  
> 외부의 CSS가 불러오기 전에 잠시 스타일이 적용되지 않은 웹 페이지가 나타나는 현상이다. 이 현상은 스타일이 적용되지 않은 웹 페이지가 스타일이 적용된 웹 페이지로 변화하는 것이다.  

### `no-js` 추가  

`<html>` 요소에 `class="no-js"`를 추가한다.  
Modernizr가 실행되면서 자바스크립트가 사용가능하다면 `no-js`부분은 `js`로 변경되고 Modernizr builder에서 체크한 속성들을 검사하여 지원하지 않는 속성에 대해서는 해당 클래스명 앞에 `no-`를 삽입해주게 된다.  

## Modernizr.load() 사용법  

Modernizr.load는 polyfill을 이용한다면 대역폭과 성능을 향상시키는데 도움이 된다.  
```javascript  
Modernizr.load({
  test: Modernizr.geolocation,
  yep: 'geo.js',
  nope: 'geo-polyfill.js'
});
```  
브라우저에서 geolocation 지원 여부에 따라 서로 다른 스크립트를 로드할 수 있다. 이와 같은 방법으로 불필요한 코드를 다운로드 하는 것을 막을 수 있어 대역폭을 감소시키고 페이지 성능을 향상시킨다.  

## Modernizr를 이용한 감지  

Modernizr의 속성은 모두 소문자로 이루어져 있으며 기본적으로 아래와 같은 포맷을 사용한다.  
```javascript  
if (Modernizr.canvas) {
  // canvas supported
}
else {
  // canvas not supported
}
```  

---  

### 참고 사이트  

* [Modernizr - 브라우저 기능검사](http://webdir.tistory.com/82)  
