React Context
React Context is a way to manage state globally.

It can be used together with the useState Hook to share state between deeply nested components more easily than with useState alone.

The Problem
State should be held by the highest parent component in the stack that requires access to the state.

To illustrate, we have many nested components. The component at the top and bottom of the stack need access to the state.

To do this without Context, we will need to pass the state as "props" through each nested component. This is called "prop drilling".

The useContext hook is a built-in hook in React that allows you to access the value of a context directly within a functional component.


#DOCUMENTATION


Accepts a context object (the value returned from React.createContext) and returns the current context value for that context. The current context value is determined by the value prop of the nearest <MyContext.Provider> above the calling component in the tree.

When the nearest <MyContext.Provider> above the component updates, this Hook will trigger a rerender with the latest context value passed to that MyContext provider. Even if an ancestor uses React.memo or shouldComponentUpdate, a rerender will still happen starting at the component itself using useContext.

Don’t forget that the argument to useContext must be the context object itself:

Correct: useContext(MyContext)
Incorrect: useContext(MyContext.Consumer)
Incorrect: useContext(MyContext.Provider)
A component calling useContext will always re-render when the context value changes. If re-rendering the component is expensive, you can optimize it by using memoization.

Tip

If you’re familiar with the context API before Hooks, useContext(MyContext) is equivalent to static contextType = MyContext in a class, or to <MyContext.Consumer>.

useContext(MyContext) only lets you read the context and subscribe to its changes. You still need a <MyContext.Provider> above in the tree to provide the value for this context.
