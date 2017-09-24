# combineAll
#### 연산자(operator) 정의: `combineAll(project: function): Observable`

## Observable의 Observable들이 완료(complate)되면 [combineLatest](combinelatest.md)를 적용하여 Observable의 Observable들을 평평하게 만듭니다.

![Image](http://reactivex.io/rxjs/img/combineAll.png)

### Examples

( [예시 테스트코드](https://github.com/tienne/learn-rxjs/blob/master/operators/specs/combination/combineall-spec.ts) )

##### 예시 1: 각각 일정한 간격의 Observable 맵핑 처리

( [jsBin](http://jsbin.com/cokinogime/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/pvj1nbLa/) )

```js
//1초 간격으로 2회 스트림 발생
const source = Rx.Observable.interval(1000).take(2);
//source에서 발생되는 값을 일정간격으로 5회 반복되는 스트림으로 맵핑
const example = source.map(val => Rx.Observable.interval(1000).map(i => `Result (${val}): ${i}`).take(5));
/*
  source에서 발생되는 2회 값들을 각각 내부적으로 1초 간격으로 5회 발생되는 observable로 맵핑되며 
  combineAll은 combineLatest 방식을 사용하여,
  observable의 값이 발생 할 때마다 각각의 마지막 값을 발생시킵니다.
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
