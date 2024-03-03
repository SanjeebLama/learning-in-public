# React Tsx

### Defining Component Props and State:

```tsx
import React from "react";

interface ButtonProps {
  text: string;
  onClick: () => void;
}

const Button = ({ text, onClick }: ButtonProps) => {
  return <button onClick={onClick}>{text}</button>;
};

export default Button;
```

## useState with different data types

### State with Primitive Data Types:

```tsx
interface CounterProps {
  initialCount: number;
}

....

const [count, setCount] = useState<number>(initialCount);

const [text, setText] = useState<string>("");
```

### State with Object Data Type:

```tsx
interface User {
  name: string;
  age: number;
}

....
const [user, setUser] = useState<User>({ name: "", age: 0 }); // State with object type
```

### State with Array Data Type:

```tsx
const [todos, setTodos] = useState<string[]>([]); // State with array type
```

### Passing useState hook as an argument

```tsx
import React, { useState } from "react";
import ChildComponent from "./ChildComponent";

const ParentComponent: React.FC = () => {
  const [count, setCount] = useState<number>(0);

  return (
    <div>
      <ChildComponent state={[count, setCount]} />
    </div>
  );
};

export default ParentComponent;

//Child Component
import React from "react";

interface Props {
  state: [number, React.Dispatch<React.SetStateAction<number>>];
}

const ChildComponent: React.FC<Props> = ({ state }) => {
  const [count, setCount] = state;

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default ChildComponent;

// or if passed separately

interface StateInterface {
  count: number;
  setCount: React.Dispatch<React.SetStateAction<number>>;
}
```

# Basic Prop Types Example

```ts
type AppProps = {
  message: string;

  count: number;

  disabled: boolean;
  /** array of a type! */

  names: string[];
  /** string literals to specify exact string values, with a union type to join them together */

  status: "waiting" | "success";
  /** an object with known properties (but could have more at runtime) */

  obj: {
    id: string;
    title: string;
  };
  /** array of objects! (common) */

  objArr: {
    id: string;
    title: string;
  }[];
  /** any non-primitive value - can't access any properties (NOT COMMON but useful as placeholder) */

  obj2: object;
  /** an interface with no required properties - (NOT COMMON, except for things like `React.Component<{}, State>`) */

  obj3: {};
  /** a dict object with any number of properties of the same type */

  dict1: {
    [key: string]: MyTypeHere;
  };

  dict2: Record<string, MyTypeHere>; // equivalent to dict1
  /** function that doesn't take or return anything (VERY COMMON) */

  onClick: () => void;
  /** function with named prop (VERY COMMON) */

  onChange: (id: number) => void;
  /** function type syntax that takes an event (VERY COMMON) */

  onChange: (event: React.ChangeEvent<HTMLInputElement>) => void;
  /** alternative function type syntax that takes an event (VERY COMMON) */

  onClick(event: React.MouseEvent<HTMLButtonElement>): void;
  /** any function as long as you don't invoke it (not recommended) */

  onSomething: Function;
  /** an optional prop (VERY COMMON!) */

  optional?: OptionalType;
  /** when passing down the state setter function returned by `useState` to a child component. `number` is an example, swap out with whatever the type of your state */

  setState: React.Dispatch<React.SetStateAction<number>>;
};
```

# Useful React Prop Type Example

```ts
export declare interface AppProps {
  children?: React.ReactNode; // best, accepts everything React can render

  childrenElement: React.JSX.Element; // A single React element

  style?: React.CSSProperties; // to pass through style props

  onChange?: React.FormEventHandler<HTMLInputElement>; // form events! the generic parameter is the type of event.target
  //  more info: https://react-typescript-cheatsheet.netlify.app/docs/advanced/patterns_by_usecase/#wrappingmirroring

  props: Props & React.ComponentPropsWithoutRef<"button">; // to impersonate all the props of a button element and explicitly not forwarding its ref

  props2: Props & React.ComponentPropsWithRef<MyButtonWithForwardRef>; // to impersonate all the props of MyButtonForwardedRef and explicitly forwarding its ref
}
```

# Function Components

```tsx
// Declaring type of props - see "Typing Component Props" for more examples
type AppProps = {
  message: string;
}; /* use `interface` if exporting so that consumers can extend */

// Easiest way to declare a Function Component; return type is inferred.
const App = ({ message }: AppProps) => <div>{message}</div>;

// you can choose annotate the return type so an error is raised if you accidentally return some other type
const App = ({ message }: AppProps): React.JSX.Element => <div>{message}</div>;

// you can also inline the type declaration; eliminates naming the prop types, but looks repetitive
const App = ({ message }: { message: string }) => <div>{message}</div>;

// Alternatively, you can use `React.FunctionComponent` (or `React.FC`), if you prefer.
// With latest React types and TypeScript 5.1. it's mostly a stylistic choice, otherwise discouraged.
const App: React.FunctionComponent<{ message: string }> = ({ message }) => (
  <div>{message}</div>
);
```

# Hooks

## useState

```tsx
const [state, setState] = useState(false);
// `state` is inferred to be a boolean
// `setState` only takes booleans

const [user, setUser] = useState<User | null>(null);

// later...
setUser(newUser);

// Type Assertions if a state is initilized soon after setup and always has a value after:
const [user, setUser] = useState<User>({} as User);

// later...
setUser(newUser);

// This temporarily "lies" to the TypeScript compiler that {} is of type User. You should follow up by setting the user state — if you don't, the rest of your code may rely on the fact that user is of type User and that may lead to runtime errors.
```

## useCallback

```tsx
const memoizedCallback = useCallback(
  (param1: string, param2: number) => {
    console.log(param1, param2)
    return { ok: true }
  },
  [...],
);
/**
 * VSCode will show the following type:
 * const memoizedCallback:
 *  (param1: string, param2: number) => { ok: boolean }
 */

function useCallback<T extends Function>(callback: T, deps: DependencyList): T;

// @ts-expect-error Parameter 'e' implicitly has 'any' type.
useCallback((e) => {}, []);
// Explicit 'any' type.
useCallback((e: any) => {}, []);
```

## use Reducer

```tsx
import { useReducer } from "react";

const initialState = { count: 0 };

type ACTIONTYPE =
  | { type: "increment"; payload: number }
  | { type: "decrement"; payload: string };

function reducer(state: typeof initialState, action: ACTIONTYPE) {
  switch (action.type) {
    case "increment":
      return { count: state.count + action.payload };
    case "decrement":
      return { count: state.count - Number(action.payload) };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: "decrement", payload: "5" })}>
        -
      </button>
      <button onClick={() => dispatch({ type: "increment", payload: 5 })}>
        +
      </button>
    </>
  );
}
```

## useEffect / useLayoutEffect

```tsx
function DelayedEffect(props: { timerMs: number }) {
  const { timerMs } = props;

  useEffect(
    () =>
      setTimeout(() => {
        /* do stuff */
      }, timerMs),
    [timerMs]
  );
  // bad example! setTimeout implicitly returns a number
  // because the arrow function body isn't wrapped in curly braces
  return null;
}

// solution
function DelayedEffect(props: { timerMs: number }) {
  const { timerMs } = props;

  useEffect(() => {
    setTimeout(() => {
      /* do stuff */
    }, timerMs);
  }, [timerMs]);
  // better; use the void keyword to make sure you return undefined
  return null;
}
```

## [useRef](https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/hooks#useref)
