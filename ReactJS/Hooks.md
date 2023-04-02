## React Hooks
- New Feature edition in 16.8
- Allows React core features without writing a class
- Works only in functional component

## Why Hooks?
- Problem of understanding ***this*** keyword
- Remember to bind event handlers
- Minified version of code is not good and make hot reloading very unreliable
- HOC and render props pattern to reuse stateful logic, make code harder
- For complex scenarios like data fetching and event subscriptions
	- related code gets placed at multiple places like componentDidMount and componentDidUpdate
	- subscribe to events code goes to go to componentDidMount and unsubsciption code goes to componentWillUnmount
- Cannot break into smaller components

## Types of hooks
- useState - state
- useEffect - side effects
- useContext - context API
- useReducer - reduce
- useCallback - cache a function
- useMemo - cache a value
- useRef - reference a dom node or a value
- useImperitiveHandle
- useLayoutEffect
- useDebugValue
- customHooks

### useState Hook
- add state to functional components
- in class state is always a object, in FC, we can create state as number, string, object etc.
- return an array `[currentValue of element, function to set the value]
- if state on previous value, pass a second function in setState to work with it.
- if using arrays or objects, always spread the previous state and then update the keys

### useEffect Hook
- perform side effects in functional components
- close replacement for `componentDidMount, componentDidUpdate, componentWillUnmount`

### useContext Hook
- context provides the data to the nested components (component tree) without passing the data to props manually at every level.

### useReducer Hook
- hook for state management
- alternative to useState
- useState is build using useReducer
- have two params - useReducer(reducerFn, initialState)
- reducerFn(currentState, action)
- return `[newState, dispatch]
- When to use what?
	- useState - local state,  number, bool, string data types, no biz logic 
	- useReducer - global state, object and array data types, complex biz logic

### useCallback Hook 
- to improve performance
- to return a memoized version of a callback function that only changes if one of the dependencies has changed
- useful when passing these callbacks to optimize child re-renders that rely on referene equality

### useMemo Hook
- performance optimization
- to return a memoized value and recompute only if one of the dependencies changes
- cache a fn - useCallback, cache a value - useMemo

### useRef Hook
- to access DOM nodes by passing ref={ref} on dom element
- can be used any mutable value
- persist value through re-renders
- don't cause any renders when it's value changes


### custom Hooks
- a JS function whose name starts with "use"
- it can call other hooks if required
- to share logic between two or more components (HOC, Render Props)