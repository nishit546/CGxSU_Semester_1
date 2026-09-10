# JavaScript Operators 

## What is an Operator?

An **operator** is a symbol that tells JavaScript to perform a specific mathematical, logical, or type-related operation on one or more values (called **operands**).

- **Operand**: The value or variable the operator works on.  
  Example: in `a + b`, `a` and `b` are operands, `+` is the operator.

***

## Types of Operators (Overview Table)

| Operator Type         | Symbols                                      |
|----------------------|----------------------------------------------|
| Arithmetic           | `+`, `-`, `*`, `/`, `%`, `**`                |
| Assignment           | `=`, `+=`, `-=`, `*=`, `/=`, `%=`            |
| Comparison           | `===`, `!==`, `>`, `<`, `>=`, `<=`           |
| Logical              | `&&`, `||`, `!`                               |
| Increment/Decrement  | `++`, `--`                                   |
| Type                 | `typeof`                                     |

***

## 1. Arithmetic Operators

Used for mathematical calculations.

| # | Operator Name      | Symbol |
|---|--------------------|--------|
| 1 | Addition           | `+`    |
| 2 | Subtraction        | `-`    |
| 3 | Multiplication     | `*`    |
| 4 | Division           | `/`    |
| 5 | Modulus (Remainder)| `%`    |
| 6 | Exponentiation     | `**`   |

### 1.1 Addition `+`

**Simple example:**
```js
let a = 10;
let b = 20;
let sum = a + b;
console.log('The sum of a & b:', sum); // 30
```

**Real-life example:**
```js
let productPrice = 1000;
let gstAndTaxes = 100;
let totalPrice = productPrice + gstAndTaxes; // 1100
```

***

### 1.2 Subtraction `-`

**Simple example:**
```js
let a = 50;
let b = 20;
let diff = a - b;
console.log('The difference of a & b:', diff); // 30
```

**Real-life example:**
```js
let walletBalance = 500;
let billAmount = 120;
let remainingBalance = walletBalance - billAmount; // 380
```

***

### 1.3 Multiplication `*`

**Simple example:**
```js
let price = 50;
let quantity = 4;
let total = price * quantity;
console.log('Total price:', total); // 200
```

**Real-life example:**
```js
let itemPrice = 250;
let numberOfItems = 3;
let cartTotal = itemPrice * numberOfItems; // 750
```

***

### 1.4 Division `/`

**Simple example:**
```js
let total = 100;
let people = 4;
let share = total / people;
console.log('Each person gets:', share); // 25
```

**Real-life example:**
```js
let totalBill = 800;
let friends = 4;
let perPersonBill = totalBill / friends; // 200
```

***

### 1.5 Modulus `%`

**Simple example:**
```js
let num = 17;
let remainder = num % 5;
console.log('Remainder when 17 is divided by 5:', remainder); // 2
```

**Real-life example:**
```js
let items = 17;
let boxCapacity = 5;
let leftoverItems = items % boxCapacity; // 2 items don't fit in full boxes
```

***

### 1.6 Exponentiation `**`

**Simple example:**
```js
let base = 2;
let power = 3;
let result = base ** power;
console.log('2 raised to power 3:', result); // 8
```

**Real-life example:**
```js
let side = 5;
let areaOfSquare = side ** 2; // 25
```

***

## 2. Assignment Operators

| # | Operator Name         | Symbol |
|---|-----------------------|--------|
| 1 | Assignment            | `=`    |
| 2 | Add and Assign        | `+=`   |
| 3 | Subtract and Assign   | `-=`   |
| 4 | Multiply and Assign   | `*=`   |
| 5 | Divide and Assign     | `/=`   |
| 6 | Modulus and Assign    | `%=`   |

### 2.1 Assignment `=`

**Simple example:**
```js
let x = 10;
console.log('Value of x:', x); // 10
```

**Real-life example:**
```js
let initialScore = 0; // starting score in a game
```

***

### 2.2 Add and Assign `+=`

**Simple example:**
```js
let score = 10;
score += 5;
console.log('New score:', score); // 15
```

**Real-life example:**
```js
let wallet = 500;
let cashback = 50;
wallet += cashback; // 550
```

***

### 2.3 Subtract and Assign `-=`

**Simple example:**
```js
let health = 100;
health -= 20;
console.log('Remaining health:', health); // 80
```

**Real-life example:**
```js
let lives = 3;
lives -= 1; // 2
```

***

### 2.4 Multiply and Assign `*=`

**Simple example:**
```js
let amount = 100;
amount *= 1.1;
console.log('Amount after 10% increase:', amount); // 110
```

**Real-life example:**
```js
let price = 500;
let taxRate = 1.18;
price *= taxRate;
```

***

### 2.5 Divide and Assign `/=`

**Simple example:**
```js
let total = 200;
total /= 4;
console.log('Result:', total); // 50
```

**Real-life example:**
```js
let workHours = 40;
let days = 5;
workHours /= days; // 8
```

***

### 2.6 Modulus and Assign `%=`

**Simple example:**
```js
let num = 17;
num %= 5;
console.log('Result:', num); // 2
```

**Real-life example:**
```js
let counter = 7;
let maxIndex = 5;
counter %= maxIndex;
```

***

## 3. Comparison Operators

| # | Operator Name         | Symbol |
|---|-----------------------|--------|
| 1 | Strict Equality       | `===`  |
| 2 | Strict Inequality     | `!==`  |
| 3 | Greater Than          | `>`    |
| 4 | Less Than             | `<`    |
| 5 | Greater Than or Equal | `>=`   |
| 6 | Less Than or Equal    | `<=`   |

### 3.1 Strict Equality `===`

**Simple example:**
```js
let a = 5;
let b = "5";
let result = a === b;
console.log('a === b:', result); // false
```

**Real-life example:**
```js
let storedPassword = 1234;
let enteredPassword = 1234;
let isCorrect = storedPassword === enteredPassword; // true
```

***

### 3.2 Strict Inequality `!==`

**Simple example:**
```js
let x = 10;
let y = "10";
let result = x !== y;
console.log('x !== y:', result); // true
```

**Real-life example:**
```js
let userRole = "guest";
let requiredRole = "admin";
let isNotAdmin = userRole !== requiredRole; // true
```

***

### 3.3 Greater Than `>`

**Simple example:**
```js
let age = 20;
let result = age > 18;
console.log('Is age > 18?', result); // true
```

**Real-life example:**
```js
let salary = 60000;
let threshold = 50000;
let isHighEarner = salary > threshold; // true
```

***

### 3.4 Less Than `<`

**Simple example:**
```js
let price = 50;
let budget = 100;
let result = price < budget;
console.log('Is price < budget?', result); // true
```

**Real-life example:**
```js
let marks = 65;
let passingMarks = 75;
let isFail = marks < passingMarks; // true
```

***

### 3.5 Greater Than or Equal `>=`

**Simple example:**
```js
let marks = 75;
let result = marks >= 75;
console.log('Is marks >= 75?', result); // true
```

**Real-life example:**
```js
let age = 18;
let canVote = age >= 18; // true
```

***

### 3.6 Less Than or Equal `<=`

**Simple example:**
```js
let items = 5;
let limit = 10;
let result = items <= limit;
console.log('Are items <= limit?', result); // true
```

**Real-life example:**
```js
let cartItems = 8;
let maxAllowed = 10;
let isWithinLimit = cartItems <= maxAllowed; // true
```

***

## 4. Logical Operators

Used to combine or invert boolean conditions.

| # | Operator Name | Symbol |
|---|---------------|--------|
| 1 | Logical AND   | `&&`   |
| 2 | Logical OR    | `||`   |
| 3 | Logical NOT   | `!`    |

### 4.1 Logical AND `&&`

**Definition:** Returns `true` only if **both** operands are truthy.

**Simple example:**
```js
let isLogged = true;
let hasPermission = true;
let canAccess = isLogged && hasPermission;
console.log('Can access?', canAccess); // true
```

**Real-life example:**
```js
let isPaidUser = true;
let hasSubscription = true;
let canWatchPremium = isPaidUser && hasSubscription; // true only if both
```

***

### 4.2 Logical OR `||`

**Definition:** Returns `true` if **at least one** operand is truthy.

**Simple example:**
```js
let isMember = false;
let hasCoupon = true;
let canGetDiscount = isMember || hasCoupon;
console.log('Can get discount?', canGetDiscount); // true
```

**Real-life example:**
```js
let isLoggedIn = false;
let isGuest = true;
let canBrowse = isLoggedIn || isGuest; // true
```

***

### 4.3 Logical NOT `!`

**Definition:** Inverts the boolean value: `true` → `false`, `false` → `true`.

**Simple example:**
```js
let isActive = true;
let isInactive = !isActive;
console.log('Is inactive?', isInactive); // false
```

**Real-life example:**
```js
let isBanned = false;
let canLogin = !isBanned; // true
```

***

## 5. Increment / Decrement Operators

| # | Operator Name | Symbol |
|---|---------------|--------|
| 1 | Increment     | `++`   |
| 2 | Decrement     | `--`   |

### 5.1 Increment `++`

**Simple example:**
```js
let count = 5;
count++;
console.log('New count:', count); // 6
```

**Real-life example:**
```js
let attempts = 0;
attempts++; // one attempt done
```

***

### 5.2 Decrement `--`

**Simple example:**
```js
let lives = 3;
lives--;
console.log('Remaining lives:', lives); // 2
```

**Real-life example:**
```js
let stock = 10;
stock--; // one item sold
```

***

## 6. Type Operator: `typeof`

**Simple example:**
```js
let name = "Alice";
let age = 25;
let isActive = true;

console.log(typeof name);    // "string"
console.log(typeof age);     // "number"
console.log(typeof isActive); // "boolean"
```

**Real-life example:**
```js
function add(a, b) {
  if (typeof a !== "number" || typeof b !== "number") {
    console.log("Please provide numbers only");
    return;
  }
  return a + b;
}
```

***

