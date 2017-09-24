# combineLatest
#### 연산자(operator) 정의: `combineLatest(observables: ...Observable, project: function): Observable`

## 결합시키는 Observable들 중 아무 Observable의 값이 발생될때, 각각 마지막 값으로 넘겨줍니다.

---
:bulb:  이 연산자(operator)는 static 또는 Observable의 인스턴스 메서드로도 사용할 수 있습니다!

:bulb:  [combineAll](combineall.md) 연산자는 observable의 observable들이 완료되었을때 combineLatest를 이용하여 결합됩니다.

---

![](http://reactivex.io/rxjs/img/combineLatest.png)

### Examples

( [예시 테스트코드](https://github.com/btroncone/learn-rxjs/blob/master/operators/specs/combination/combinelatest-spec.ts) )

##### 예시 1: 일정 간격으로 발생되는 3개의 observable들을 결합
( [jsBin](http://jsbin.com/zupiqozaro/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/mygy9j86/) )

```js
//timerOne은 1초에 첫 번째 값을 내고 4초마다 한 번씩 값을 발생시킵니다.
const timerOne = Rx.Observable.timer(1000, 4000);
// timerTwo는 2초에 첫 번째 값을 내고 4초마다 한 번씩 값을 발생시킵니다.
const timerTwo = Rx.Observable.timer(2000, 4000);
//timerThree는 3초에 첫 번째 값을 내고 4초마다 한 번씩 값을 발생시킵니다.
const timerThree = Rx.Observable.timer(3000, 4000);

//하나의 타이머가 작동하면 각 타이머의 최신 값을 배열로 발생시킵니다.
const combined = Rx.Observable
.combineLatest(
    timerOne,
    timerTwo,
    timerThree
);

const subscribe = combined.subscribe(latestValues => {
  //타이머 one, two, three에 해당하는 값 변수 선언
  const [timerValOne, timerValTwo, timerValThree] = latestValues;
  /*
  	Example:
    timerOne first tick: 'Timer One Latest: 1, Timer Two Latest:0, Timer Three Latest: 0
    timerTwo first tick: 'Timer One Latest: 1, Timer Two Latest:1, Timer Three Latest: 0
    timerThree first tick: 'Timer One Latest: 1, Timer Two Latest:1, Timer Three Latest: 1
  */
  console.log(
    `Timer One Latest: ${timerValOne}, 
     Timer Two Latest: ${timerValTwo}, 
     Timer Three Latest: ${timerValThree}`
   );
});
```

##### 예시 2: projection function를 같이 넘긴 combineLatest 연산자(operator) 사용  

( [jsBin](http://jsbin.com/codotapula/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/uehasmb6/) )

```js
//timerOne은 1초에 첫 번째 값을 내고 4초마다 한 번씩 값을 발생시킵니다.
const timerOne = Rx.Observable.timer(1000, 4000);
// timerTwo는 2초에 첫 번째 값을 내고 4초마다 한 번씩 값을 발생시킵니다.
const timerTwo = Rx.Observable.timer(2000, 4000);
//timerThree는 3초에 첫 번째 값을 내고 4초마다 한 번씩 값을 발생시킵니다.
const timerThree = Rx.Observable.timer(3000, 4000);

//combineLatest 연산자(operator)는 projection 함수 넘겨줄 경우 스트림 발생시마다 projection 함수를 실행하여 값을 발생시킵니다.
const combinedProject = Rx.Observable
.combineLatest(
    timerOne,
    timerTwo,
    timerThree,
    (one, two, three) => {
      return `Timer One (Proj) Latest: ${one}, 
              Timer Two (Proj) Latest: ${two}, 
              Timer Three (Proj) Latest: ${three}`
    }
);
//발생된 값 구독하여 확인
const subscribe = combinedProject.subscribe(latestValuesProject => console.log(latestValuesProject));
```

##### 예시 3: 2개의 버튼 이벤트들을 결합

( [jsBin](http://jsbin.com/hiyetucite/edit?html,js,output) | [jsFiddle](https://jsfiddle.net/btroncone/9rsf6t9v/1/) )

```js
// html를 설정하는 함수
const setHtml = id => val => document.getElementById(id).innerHTML = val;

function(id) {
  return function(val) {
    document.getElementById(id).innerHTML = val;
  }
}
const addOneClick$ = id => Rx.Observable
    .fromEvent(document.getElementById(id), 'click')
    // 매 클릭을 1로 변경(맵핑)
    .mapTo(1)
    .startWith(0)
    // 클릭한것들을 계속 누적(reduce)
    .scan((acc, curr) => acc + curr)
    // 클릭횟수를 HTML에 적용시킵니다.
    .do(setHtml(`${id}Total`))
  
  
const combineTotal$ = Rx.Observable
  .combineLatest(
    addOneClick$('red'),
    addOneClick$('black')
  )
  .map(([val1, val2]) => val1 + val2)
  .subscribe(setHtml('total'));
```
###### HTML
```html
<div>
  <button id='red'>Red</button>
  <button id='black'>Black</button>
</div>
<div id="redTotal"></div>
<div id="blackTotal"></div>
<div id="total"></div>
```

### 추가 자료 목록
* [combineLatest](http://reactivex.io/rxjs/class/es6/Observable.js~Observable.html#instance-method-combineLatest) :newspaper: - Official docs
* [Combining streams with combineLatest](https://egghead.io/lessons/rxjs-combining-streams-with-combinelatest?course=step-by-step-async-javascript-with-rxjs) :video_camera: :dollar: - John Linquist
* [Combination operator: combineLatest](https://egghead.io/lessons/rxjs-combination-operator-combinelatest?course=rxjs-beyond-the-basics-operators-in-depth) :video_camera: :dollar: - André Staltz

---
> :file_folder: Source Code:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/combineLatest.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/combineLatest.ts)
