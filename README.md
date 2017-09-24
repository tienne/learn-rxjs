# Learn RxJS

RxJs에 대한 명확한 예제, 설명 그리고 정보가 기재되어있습니다.
해당 페이지는 [learnrxjs](https://www.learnrxjs.io/)의 내용을 번역한 페이지입니다.
그외에 추가적인 자료도 계속 추가할 예정입니다.

## RxJS 소개

[RxJS](https://github.com/ReactiveX/rxjs)는 최근 가장 뜨거운 라이브러리 중 하나입니다. 이벤트를 처리하기 위한 강력한 기능을 제공함으로써, 많은 프레임워크, 라이브러리 그리고 유틸리티로 활용되어 제공되고 있습니다. 
Rx는 [거의 모든 언어](http://reactivex.io/languages.html)로 활용할 수 있어, 반응성 프로그래밍에 대한 탄탄한 이해력을 가지고 있다면, 조금 더 쉽게 습득이 가능합니다.

**하지만...**

RxJS와 리액티브 프로그래밍을 배우는것은 [어렵습니다](https://twitter.com/hoss/status/742643506536153088). 많은 개념, 다양한 API 및 사고 방식의 근본적인 변화가 필요합니다.[(명령형과 선언적 스타일 비교)](http://codenugget.co/2015/03/05/declarative-vs-imperative-programming-web.html) 
이 사이트는 이러한 개념을 접근하기 쉽고, 명확하고 쉽게 찾을 수있는 예제를 작성하는 데 중점을두고 있으며, 웹에서 가장 우수한 RxJS 관련 자료의 참조를 제공합니다. 최종 목표는 [공식문서](http://reactivex.io/rxjs/)와 기존 학습 자료를 보완하여 학습곡선을 낮추어 새롭고 신선한 관점으로 제공하는 것입니다.
Rx를 배우는 것은 어렵지만 배울 가치는 충분히 있습니다!

## 이 페이지에서 다루는 내용들

#### Operators(연산자)

Operator(연산자)는 observable의 복잡한 비동기 작업을 우아하고 선언적인 해결책을 제공하는 강력한 힘을 가지고 있습니다.
이 섹션에서는 [JSBin](https://jsbin.com)과 [JSFiddle](https://jsfiddle.net) 양쪽에 모든 ([RxJS 5 연산자](/operators/README.md))들에 명확하고 실행 가능한 예제와 함께 포함되어있습니다. 해당하는 각 operator(연산자)에 대한 추가 정보 및 사용법에 대한 링크도 제공됩니다.

##### 연산자 분류
* [Combination](/operators/combination/README.md)
* [Conditional](/operators/conditional/README.md)
* [Creation](/operators/creation/README.md)
* [Error Handling](/operators/error_handling/README.md)
* [Multicasting](/operators/multicasting/README.md)
* [Filtering](/operators/filtering/README.md)
* [Transformation](/operators/transformation/README.md)
* [Utility](/operators/utility/README.md)

**혹은...**

[Operator 전체목록(알파벳순)](/operators/complete.md)

#### Concepts
Observable의 동작원리 같은 기초지식이 없다면, RxJS가 엄청난 '마법'처럼 느껴지기 쉽습니다.
이 섹션에서는 반응성 프로그래밍과 observable의 주요 개념들을 편안하게 느낄 수 있도록 다루고 있습니다.  

*Coming Soon!*

#### Recipes
RxJS에 대한 일반적인 사용 사례 및 흥미로운 솔루션등의 예시를 제공합니다.

[예시 목록](/recipes/README.md)

## 입문용 자료들
RxJS와 리액티브 프로그래밍이 처음이십니까? 이 사이트에 있는 내용 말고 다른 훌륭한 글과 동영상들이 도움 될 것 입니다. 여러분들의 학습경험을 시작하세요!


#### 읽을자료 목록
* [RxJS Introduction](http://reactivex.io/rxjs/manual/overview.html#introduction) - RxJS 공식 문서
* [The Introduction to Reactive Programming You've Been Missing](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754) - André Staltz

#### 동영상자료 목록
* [Asynchronous Programming: The End of The Loop](https://egghead.io/courses/mastering-asynchronous-programming-the-end-of-the-loop) - Jafar Husain
* [What is RxJS?](https://egghead.io/lessons/rxjs-what-is-rxjs) - Ben Lesh
* [Creating Observable from Scratch](https://egghead.io/lessons/rxjs-creating-observable-from-scratch) - Ben Lesh
* [Introduction to RxJS Marble Testing](https://egghead.io/lessons/rxjs-introduction-to-rxjs-marble-testing) - Brian Troncone
* [Introduction to Reactive Programming](https://egghead.io/courses/introduction-to-reactive-programming) :dollar: - André Staltz
* [Reactive Programming using Observables](https://www.youtube.com/watch?v=HT7JiiqnYYc&feature=youtu.be) - Jeremy Lund

#### 실습자료 목록
* [Functional Programming in JavaScript](http://reactivex.io/learnrx/) - Jafar Husain

#### 학습도구 목록
* [Rx Marbles - Interactive diagrams of Rx Observables](http://rxmarbles.com/) - André Staltz
* [Rx Visualizer - Animated playground for Rx Observables](https://rxviz.com) - Misha Moroshko

*RxJs 버전 4에 관심이 있으시면 여길 참고하세요. [Denis Stoyanov's](https://github.com/xgrommx) excellent [eBook](https://xgrommx.github.io/rx-book/)!*

## 번역목록
* [简体中文](https://rxjs-cn.github.io/learn-rxjs-operators)
* [한국어](https://github.com/tienne/lean-rxjs)

### 참조
이 GitBook에 포함 된 모든 참고 자료는 RxJs와 관련된 무료 및 유료 자료들입니다.
포함해야한다고 생각되는 내용이나 동영상을 발견 한 경우 상단의 * 페이지 수정 * 링크 메뉴를 클릭하고 Pull를 제출해주세요. 피드백은 항상 환영입니다.