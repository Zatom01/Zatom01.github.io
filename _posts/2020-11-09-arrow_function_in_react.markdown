---
layout: post
title:      "Arrow Function in React ?"
date:       2020-11-09 18:20:48 -0500
permalink:  arrow_function_in_react
---


What actually is Arrow function? When defining arrow function, we can get rid of the function keyword with shorter syntax compared to the traditional function with longer syntax. Arrow function automatically binds "this" to the surrounding code's context, meaning it will always be called with the context in which it was defined. 

First, let me show you an example of how we generally write functions in React. 
```
export class Counter extends Component {
    constructor(props) {
        super(props)

        this.state = {
            count: 0
        }

        this.handleClick = this.handleClick.bind(this)
    }

    handleClick() {
        this.setState({ count: this.state.count + 1 })

    }
```

In order for the handleClick function to work, we have to use 'bind' in the constructor. The bind() method allows an object to borrow a method from another object without making a copy of that method. Now imagine, when your component becomes complicated with lot of call back functions, the contructor would look ugly fast and unreadable.

Now lets write the same function, but with an arrow function like the following:
```
export class Counter extends Component {
    constructor(props) {
        super(props)

        this.state = {
            count: 0
        }
    }

    handleClick = () => {
        this.setState({ count: this.state.count + 1 })

    }
```
Here, in this arrow function, we don't have to use bind at all. 'this' will be automatically bound to the current class instance.  Also, because of the less code, it is easier to read and write no matter how many call back functions are defined.

Arrow functions can be anonymous. The same code can also be written like following and get the same output
```
export class Counter extends Component {
    constructor(props) {
        super(props)

        this.state = {
            count: 0
        }
    }

    render() {
        return (
            <div>
                <button onClick={() => this.setState({ count: this.state.count + 1 })}>Click Me : {this.state.count}</button>
            </div>
        )
    }
}

export default Counter

```

As you can see arrow functions have many benefits from not requiring to bind an object/function in constructor to much cleaner readable codes with less syntax.


