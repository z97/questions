# Questions
 - [Difference between let and var?](#difference-between-let-and-var?) 
 - [What is the difference between state and props in React?](#what-is-the-difference-between-state-and-props-in-react?)
 - [Differences between Functional Components and Class Components in React](#differences-between-functional-components-and-class-components-in-react)
 -  [Lifecycle of Components](#lifecycle-of-components)

# Difference between let and var?
The main difference is scoping rules. Variables declared by ```var``` keyword are scoped to the immediate function body (hence the function scope) while ```let``` variables are scoped to the immediate enclosing block denoted by ```{ }``` (hence the block scope).
```
function run() {
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
# What is the difference between state and props in React?
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
# Differences between Functional Components and Class Components in React

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
# React Component Lifecycle

Generally a React Component’s life cycle can be divided into three categories:

- Mounting
- Updating
- Unmounting

## Mounting:

During the initialization of the component when the instance of the component is being created and inserted into the DOM, following methods are called in the same order in which they are listed:

- ```constructor()```
- ```static getDerivedStateFromProps()```
- ```render()```
- ```componentDidMount()```

## Updating:

When component is re-rendered due to change in props or state etc, following methods are called:

- ```static getDerivedStateFromProps()```
- ```shouldComponentUpdate()```
- ```render()```
- ```getSnapshotBeforeUpdate()```
- ```componentDidUpdate()```
## Unmounting:
On unmounting or removal of component from the DOM, only a single React life cycle method is called:
- ```componentWillUnmount()```
---

## Lifecycle methods explained:
---

### ```render()```:

Most important life cycle method and the only method which is compulsory for the react component. It should be pure, meaning that it does not modify component state, it returns the same result each time it’s invoked, and it does not directly interact with the browser.

It returns a single element which represents the component during the rendering process and should either be a representation of a native DOM component (e.g. ```<p/>```) or another user-defined component. If nothing should be rendered, it can return null or undefined.

This function will be recalled after any change to the component's ```props``` or ```state```.

As mentioned earlier, it should not modify the component state meaning ```setState()``` cannot be defined in ```render()```. If you will try to ```setState()``` it will keep on calling render again and again which will result in an infinite loop resulting in breaking the application.

---
### ```componentDidMount()```:
Invoked immediately after a component is mounted meaning all the elements are rendered correctly. This method can be used for:

- Fetching data
- Adding event listeners
- Manipulating DOM elements
- Setting up subscriptions

---
### ```getDerivedStateFromProps()```:

This method is only for rare use cases where the ```state``` depends on changes in ```props```. It is called right before calling the ```render()``` method, both on the initial mount and on subsequent updates. It should return an object to update the ```state```, or ```null``` to update nothing.

---
### ```shouldComponentUpdate()```:

This method is also called before render life cycle method only when new ```props``` or ```state``` are received. It either returns ```true``` or ```false```. By default, return value is always ```true```.

It is only added as a life cycle method for performance optimization. This method is not called during the initial render or when the ```forceUpdate()``` is called.

### ```getSnapshotBeforeUpdate()```:

It is called right before the most recent changes to the DOM created by ```render()``` method takes effect. For example if we added multiple items to the list and before they are rendered, we want to get the scroll position of the last item of the previous list item, we can use this method to get that position.

This method is not commonly used. Any value retuned from this method will be passed to the ```componentDidUpdate()``` life cycle method as a parameter.

---
### ```componentDidUpdate()```:

This method is the update version of ```ComponentDidMount()```. It is called rite after the component update takes place, except the first time when the component is rendered.

```componentDidUpdate()``` takes two arguments as parameters, ```prevProps``` and ```prevState```. If the component has also implemented ```getSnapshotBeforeUpdate()```, a third parameter ‘snapshot’ is also passed as parameter to this method.

### ```componentWillUnmount()```:

This method is called right before when the component is going to be destroyed. In this lifecycle method we perform all the cleanup, like terminating network requests, unsubscribe to subscriptions, resetting timers etc.

```setState()``` should not be called in this method and we are going to destroy our component.

![React lifecycle](/lifecycle.jpg "Lifecycle")

## Functional Component : 
 
``` 
useEffect(() => {
  console.log("component has mounted");
  return(() => {
    console.log("component has unmounted")
  })
}, []) // changes in this array will update  component
```
