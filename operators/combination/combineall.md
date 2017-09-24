# combineAll
#### 연산자(operator) 정의: `combineAll(project: function): Observable`

## observable이 complete(완료)될 때 [combineLatest](combinelatest.md)를 이용하여 observable들을 합칩니다.

### Examples

( [예시 테스트코드](https://github.com/tienne/learn-rxjs/blob/master/operators/specs/combination/combineall-spec.ts) )

##### 예시 1: Mapping to inner interval observable

( [jsBin](http://jsbin.com/cokinogime/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/pvj1nbLa/) )

```js
//1초 간격으로 2회 스트림 발생
const source = Rx.Observable.interval(1000).take(2);
//map each emitted value from source to interval observable that takes 5 values
const example = source.map(val => Rx.Observable.interval(1000).map(i => `Result (${val}): ${i}`).take(5));
/*
  2 values from source will map to 2 (inner) interval observables that emit every 1s
  combineAll uses combineLatest strategy, emitting the last value from each
  whenever either observable emits a value
*/
const combined = example.combineAll();
/*
  output:
  ["Result (0): 0", "Result (1): 0"]
  ["Result (0): 1", "Result (1): 0"]
  ["Result (0): 1", "Result (1): 1"]
  ["Result (0): 2", "Result (1): 1"]
  ["Result (0): 2", "Result (1): 2"]
  ["Result (0): 3", "Result (1): 2"]
  ["Result (0): 3", "Result (1): 3"]
  ["Result (0): 4", "Result (1): 3"]
  ["Result (0): 4", "Result (1): 4"]
*/
const subscribe = combined.subscribe(val => console.log(val));
```


### 추가 자료 목록
* [combineAll](http://reactivex.io/rxjs/class/es6/Observable.js~Observable.html#instance-method-combineAll) :newspaper: - Official docs

---
> :file_folder: Source Code:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/combineAll.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/combineAll.ts)
