# concat
#### 연산자(operator) 정의: `concat(observables: ...*): Observable`

## Subscribe to observables in order as previous completes, emit values.

---
:bulb:  concat을 ATM기기 앞에 서있는 줄처럼 생각하시면 됩니다. 다음 구독 실행은 이전 Observable이 완료되기 전까지 실행이 불가능합니다!

:bulb:  이 연산자(operator)는 정적 또는 인스턴스 메서드로도 사용할 수 있습니다!

:bulb:  실행 순서가 상관이 없다면 [merge](merge.md) 연산자를 확인해보세요.

---

![](http://reactivex.io/rxjs/img/concat.png)

### Examples

( [예시 테스트코드](https://github.com/btroncone/learn-rxjs/blob/master/operators/specs/combination/concat-spec.ts) )

##### Example 1: 기본적인 2개의 Observable 결합

( [jsBin](http://jsbin.com/gegubutele/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/rxwnr3hh/) )

```js
//1,2,3 값 발생
const sourceOne = Rx.Observable.of(1,2,3);
//4,5,6 값 발생
const sourceTwo = Rx.Observable.of(4,5,6);
//emit values from sourceOne, when complete, subscribe to sourceTwo
const example = sourceOne.concat(sourceTwo);
//output: 1,2,3,4,5,6
const subscribe = example.subscribe(val => console.log('Example: Basic concat:', val));
```

##### Example 2: concat as static method

( [jsBin](http://jsbin.com/xihagewune/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/5qdtvhu8/) )

```js
//emits 1,2,3
const sourceOne = Rx.Observable.of(1,2,3);
//emits 4,5,6
const sourceTwo = Rx.Observable.of(4,5,6);

//used as static
const example = Rx.Observable.concat(
	sourceOne,
  sourceTwo
);
//output: 1,2,3,4,5,6
const subscribe = example.subscribe(val => console.log('Example: static', val));
```

##### Example 3: concat with delayed source

( [jsBin](http://jsbin.com/nezonosubi/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/L2s49msx/) )

```js
//emits 1,2,3
const sourceOne = Rx.Observable.of(1,2,3);
//emits 4,5,6
const sourceTwo = Rx.Observable.of(4,5,6);

//delay 3 seconds then emit
const sourceThree = sourceOne.delay(3000);
//sourceTwo waits on sourceOne to complete before subscribing
const example = sourceThree.concat(sourceTwo);
//output: 1,2,3,4,5,6
const subscribe = example.subscribe(val => console.log('Example: Delayed source one:', val));
```

##### Example 4: concat with source that does not complete

( [jsBin](http://jsbin.com/vixajoxaze/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/4bhtb81u/) )

```js
//when source never completes, the subsequent observables never runs
const source = Rx.Observable
  .concat(
  	Rx.Observable.interval(1000),
  	Rx.Observable.of('This','Never','Runs')  
  )
//outputs: 1,2,3,4....
const subscribe = source.subscribe(val => console.log('Example: Source never completes, second observable never runs:', val));
```


### Additional Resources
* [concat](http://reactivex.io/rxjs/class/es6/Observable.js~Observable.html#instance-method-concat) :newspaper: - Official docs
* [Combination operator: concat, startWith](https://egghead.io/lessons/rxjs-combination-operators-concat-startwith?course=rxjs-beyond-the-basics-operators-in-depth) :video_camera: :dollar: - André Staltz

---
> :file_folder: Source Code:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/concat.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/concat.ts)
