# 변수선언 방식

### var - 중복선언 가능, 재할당 가능

```js
var animal = "pig";
console.log(animal); //pig

var animal = "dog";
console.log(animal); //dog

animal = "cat";
console.log(animal); //cat
```

원조 변수 선언 방식으로, 동일한 이름으로 중복선언가능
변수를 유연하게 사용할 수 있지만, 기존에 선언해둔 변수를 실수로 재선언 하는 문제 발생
코드가 길어지고 복잡해질 수록 실수로 재선언 되어 어떤 부분에서 값이 변경되고 어디서 문제가 일어나는지 알기 힘듬

### let - 중복선언 불가, 재할당 가능

```js
let animal = "pig";
console.log(animal); //pig

let animal = "dog";
console.log(animal); //dog
//Uncaught SyntaxError: Identifier 'title' has already been declared

animal = "cat";
console.log(animal); //cat
```

해당변수 중복선언시 이미 선언되었다는 에러메시지를 보여줌
중복선언이 불가하지만 변수에 값을 재할당하는 것은 가능

### **const** - 중복선언 불가, 재할당 불가

```js
let animal = "pig";
console.log(animal); //pig

let animal = "dog";
console.log(animal); //dog
//Uncaught SyntaxError: Identifier 'title' has already been declared

animal = "cat";
console.log(animal); //cat
```

재할당 가능한 `let`과 다르게 `const`는 재할당 또한 불가

# 스코프(Scope)

### var - 함수레벨 스코프

```js
function function_level() {
    if (true) {
        var a = 123;
        console.log(a); //123
    }
    console.log(a);
}

function_level(); //123
console.log(a); //ReferenceError: a is not defined
```

### let,const - 블록레벨 스코프

```js
function block_level() {
    if (true) {
        let a = 123;
        console.log(a); //123
    }

    console.log(a); // ReferenceError: a is not defined.
}
console.log(a); // ReferenceError: a is not defined.
```

> React 컴포넌트는 함수로 작성되는 경우가 많으며, 그 안에서는 주로 `let`과 `const`를 사용하여 변수를 선언합니다. 이는 블록 레벨 스코프를 가지기 때문에 함수 내부에서만 해당 변수를 사용할 수 있어, 변수가 예기치 않게 변경되거나 충돌하는 문제를 방지할 수 있습니다.
> 반면에, `var`는 함수 레벨 스코프를 가지므로, 같은 함수 내에서 여러 번 재선언할 수 있습니다. 이는 코드의 복잡성을 증가시키고, 예기치 않은 문제를 일으킬 수 있습니다. 따라서, `var`보다는 `let`과 `const`의 사용을 권장합니다.
> 또한, `const`는 한 번 선언하고 값이 변경되지 않는 상수를 정의할 때 사용하므로, 코드를 읽는 사람이 해당 변수의 값이 변경되지 않을 것임을 쉽게 이해할 수 있습니다.
