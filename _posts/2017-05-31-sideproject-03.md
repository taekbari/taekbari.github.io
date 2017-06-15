---
layout: post
title: "[무작정 따라하기 - 03] Slide Push Menus"
description: "Codrops 사이트 예제 따라하기"
date: 2017-05-31
tags: [연습, 정규 표현식]
comments: false
share: true
---

# Slide Push Menus  

Codrops 사이트에 있는 [Slide and Push Menus](https://tympanus.net/codrops/2013/04/17/slide-and-push-menus/) 샘플을 따라 만들었다.  
메뉴 목록을 보여주는 6가지 스타일을 제공하는 샘플이다. 스타일 중 4가지는 메뉴 목록이 컨텐츠 영역 위에 나타나는 스타일이고 2가지는 좌우에서 메뉴 목록이 보여지면서 컨텐츠 영역이 좌우로 밀리는듯한 스타일이다.  
샘플에서 사용하는 스크립트 내용은 클래스의 추가, 삭제, 검색을 위한 헬퍼 함수들을 모아놓은 것이며, https://github.com/ded/bonzo 에서 제공하는 내용이다.  

> [github 작업 링크](https://github.com/taekbari/SideProject/tree/master/03_Slide_Push_Menus)  
> [데모 링크](https://taekbari.github.io/SideProject/03_Slide_Push_Menus/)  

## 작성하면서 공부한 내용  

### 정규 표현식  

샘플에서 사용한 정규 표현식은 다음과 같다.  
클래스 이름을 포함하고 있는지를 체크하기 위한 정규 표현식이다.  

```javascript  
function classReg (className) {
  return new RegExp("(^|\\s+)" + className + "(\\s+|$)")
}
```  
> 전달인자로 받은 className 앞에 공백 또는 문자열의 시작이 오고, 뒤에는 공백 또는 문자의 끝이 오는지를 검사하는 정규 표현식.  
> 즉, 전달인자로 받은 className이 존재하는지를 판단하기 위한 정규 표현식이다.  

* `^` : 입력 문자의 시작위치를 검색. `^A`는 검색하고자 하는 문장의 시작문자가 A인지를 검사  
* `|` : 부분합연산(OR)  
* `\s` : 공백, 탭, 폼피드 등의 공백을 검색  
* `+` : 1개 이상의 문자를 검색  
* `()` : 한번 match를 수행해서 나온 결과를 기억  
* `$` : 입력 문자열의 끝 위치를 검색. `A$`는 검색하고자 하는 문장의 마지막 문자가 A인지를 검사  

---

#### 참고 사이트  
* [자바스크립트 정규 표현식](http://noritersand.tistory.com/90)  
