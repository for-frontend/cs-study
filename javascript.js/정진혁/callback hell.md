# 콜백지옥

### 콜백 함수란 무엇인가?

콜백 함수는 다른 함수의 인수로 전달되어 실행되는 함수입니다. 콜백 함수는 비동기 코드에서 자주 사용됩니다. 즉, 콜백 함수는 어떤 작업이 완료된 후에 실행되는 함수입니다.

### 콜백지옥이란?

비동기 작업이 완료된 후에 특정 코드를 실행하려면, 콜백 함수를 사용합니다. 그러나 이렇게 콜백 함수를 사용하면, 비동기 작업이 중첩되거나 여러 개가 연속으로 이루어질 경우 코드의 가독성이 떨어지고 복잡해지는 문제가 발생합니다. 이를 '콜백 지옥'(Callback Hell)이라고 부릅니다.

최신 자바스크립트를 배워서 콜백에 대한 직접적인 경험은 없지만, 그 현상과 이를 해결하기 위해 도입된 promise와 async/await에 대해 이해해야함

### 해결방법

1. **promise**

```javascript
new Promise(function (resolve, reject) {
    // 비동기 작업 수행
})
    .then(function (result) {
        // 성공 시 처리
    })
    .catch(function (error) {
        // 실패 시 처리
    });
```

Promise는 비동기 작업의 최종 완료 또는 실패를 나타내는 객체입니다. Promise는 비동기 작업이 완료될 때까지 기다린 후, 성공하면 결과를 반환하고, 실패하면 오류를 반환합니다. 이를 통해 콜백 함수를 연결하는 대신, 체이닝 방식을 사용해 가독성을 향상시킬 수 있습니다.

2. **Async/Await**

```javascript
async function myFunc() {
    try {
        const result = await someAsyncFunction();
        // 성공 시 처리
    } catch (error) {
        // 실패 시 처리
    }
}
```

async/await는 Promise를 더욱 쉽게 사용할 수 있게 해주는 문법입니다. async 함수 내부에서 await 키워드를 사용하면 Promise의 완료를 기다릴 수 있습니다. 이를 통해 비동기 작업을 마치 동기 작업처럼 코딩할 수 있습니다.

---

이는 자바스크립트의 비동기 처리 방식이 발전하면서 콜백에서 Promise, 그리고 async/await로 진화한 결과입니다.
