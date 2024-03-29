콜백 함수와 Promise는 자바스크립트에서 비동기 코드를 처리하는 두 가지 주요 패턴입니다. 콜백 함수는 비동기 작업의 완료 시에 콜백 함수를 호출하는 방식으로 사용되며, Promise는 비동기 작업의 성공 또는 실패에 대한 결과를 처리하는 객체입니다.

콜백 함수는 간단한 비동기 작업에 적합하며, 코드를 간편하게 작성할 수 있는 장점이 있습니다. 그러나 중첩된 콜백 함수의 사용은 가독성을 떨어뜨리고, 에러 핸들링이 복잡해질 수 있는 콜백 헬 현상을 야기할 수 있습니다.

Promise는 콜백 헬을 방지하고 가독성 있게 비동기 코드를 작성할 수 있는 장점이 있습니다. .catch()를 통한 에러 핸들링이 용이하며, 여러 비동기 작업을 체이닝하여 깔끔한 코드를 유지할 수 있습니다. 하지만 간단한 비동기 작업에는 콜백 함수에 비해 코드가 불필요하게 복잡할 수 있는 단점이 있습니다.

<!--
### Async/await란?
기존 비동기 처리 방식인 콜백 함수와 Promise의 한계와 복잡성에 대한 문제점들을 해결하기 위해 등장하게 되었습니다. Async/await의 사용은 코드를 동기적으로 작성할 수 있어 코드의 가독성과 유지보수성을 향상시킬 수 있습니다. -->
