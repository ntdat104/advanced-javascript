# Advanced - Javascript

---

## 1. Một số hàm built-in

1. Alert
2. Console
3. Confirm
4. Prompt
5. Set timeout
6. Set interval

## 2. Polyfill?

```js
if (!String.prototype.includes) {
  String.prototype.includes = function (search, start) {
    "use strict";

    if (search instanceof RegExp) {
      throw TypeError("First argument must not be a RegExp");
    }
    if (start === undefined) {
      start = 0;
    }
    return this.indexOf(search, start) !== -1;
  };
}

"javascript".includes();
```

## 3. IIFE - Immediately Invoked Function Expression

- Dùng dấu ; trước IIFE
- IIFE là hàm "private"

```js
// IIFE
(function () {
  console.log("IIFE");
});

// OOP
const app = (function() {
    // Private
    const cars = [];

    return {
        add(car) {
            cars.push(car);
        },
        edit(index, car) {
            cars[index] = car;
        }
        delete(index) {
            cars.splice(index, 1);
        }
    }
});
```

## 4. Scope - Phạm vi

- Các loại phạm vi:
  - Global - Toàn cầu
  - Code block - Khối mã: let, const
  - Local scope - Hàm: var, function
- Khi gọi một hàm luôn có một phạm vi mới được tạo
- Các hàm có thể truy cập các biến được khai báo trong phạm vi của nó và bên ngoài nó
- Cách thức một biến được truy cập

## 5. Closure

- Là một hàm có thể ghi nhớ nơi nó được tạo
- Truy cập được biến ở bên ngoài phạm vi của nó
- Viết code ngắn gọi hơn
- Biểu diễn, ứng dụng tính private trong OOP

```js
function run() {
  let counter = 0;

  function increase() {
    // closure
    return counter++;
  }

  return increase;
}

console.log(run()); // 1;
console.log(run()); // 2;
console.log(run()); // 3;
```

## 6. Hoisting

- Hoisting với "var", "function declaration"

```js
console.log(age); // undefined
console.log(fullname); // fullname is not defined
var age = 20;

console.log(sum(6, 9)); // 15;
function sum(a, b) {
  return a + b;
}
```

- Hoisting với "let" và "const"

```js
console.log(age); // cannot access 'age' before initialization
let age = 20;
```

# Hết.
