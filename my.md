# Questions
 - [Difference between let and var?](#difference-between-let-and-var?) 
 - [What is the difference between state and props in React?](#what-is-the-difference-between-state-and-props-in-react?)
 - [Differences between Functional Components and Class Components in React](#differences-between-functional-components-and-class-components-in-react)
 -  [Lifecycle of Components](#lifecycle-of-components)

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
## Differences between Functional Components and Class Components in React

| Functional Components | Class Components |
|---|---|
| A functional component is just a plain JavaScript pure function that accepts props as an argument and returns a React element(JSX).  | A class component requires you to extend from React. Component and create a render function which returns a React element.  |
| There is no render method used in functional components.  | It must have the render() method returning JSX (which is syntactically similar to HTML)  |
| Functional component run from top to bottom and once the function is returned it cant be kept alive.  | Class component is instantiated and different life cycle method is kept alive and being run and invoked depending on phase of class component.  |
| Also known as Stateless components as they simply accept data and display them in some form, that they are mainly responsible for rendering UI.  | Also known as Stateful components because they implement logic and state.  |
| React lifecycle methods (for example, componentDidMount) cannot be used in functional components.  | React lifecycle methods can be used inside class components (for example, componentDidMount).  |
|  Constructors are not used.	| Constructor are used as it needs to store state. 

Hooks can be easily used in functional components to make them Stateful.
example: 
```
const [name,SetName]= React.useState(‘ ‘)
```
It requires different syntax inside a class component to implement hooks.
example: 
```
constructor(props) {
   super(props);
   this.state = {name: ‘ ‘}
}
```

---
## Lifecycle of Components

hello
