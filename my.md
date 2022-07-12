# Contents
 - [Difference between let and var?](#Difference-between-let-and-var?) 
 - [What is the difference between state and props in React?](#What-is-the-difference-between-state-and-props-in-React?)
 - [Differences between Functional Components and Class Components in React]
 (#Differences-between-Functional-Components-and-Class-Components-in-React) 
 - [Defines](#defines)

 
## Difference between let and var?
The main difference is scoping rules. Variables declared by ```var``` keyword are scoped to the immediate function body (hence the function scope) while ```let``` variables are scoped to the immediate enclosing block denoted by ```{ }``` (hence the block scope).
```function run() {
  var foo = "Foo";
  let bar = "Bar";

  console.log(foo, bar); // Foo Bar

  {
    var moo = "Mooo"
    let baz = "Bazz";
    console.log(moo, baz); // Mooo Bazz
  }

  console.log(moo); // Mooo
  console.log(baz); // ReferenceError
}

run();
```
---
.

.

.

.
.

.

.

.

.

.

.

.

.

.

.

## What is the difference between state and props in React?
For parent-child communication, simply pass props.
Use state to store the data your current page needs in your controller-view.
Use props to pass data & event handlers down to your child components.


|   | props  | state  |
|---|---|---|
| Can get initial value from parent Component?   | Yes  | No  |
| Can be changed by parent Component? | Yes  | No  |
| Can set default values inside Component?*   | Yes  | Yes  |
| Can change inside Component?     | No  | Yes  |
| Can set initial value for child Components? | Yes  | Yes  |
| Can change in child Components?  | Yes  | No  |

*Note that both props and state initial values received from parents override default values defined inside a Component.

---
### Defines
.

.

.

.

.

.

.

.

.

.

.
## Differences between Functional Components and Class Components in React