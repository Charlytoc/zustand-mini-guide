# Introduction and Concepts
Zustand is a library that provides a minimalistic way to create stores in React. It gives you access to context throughout your entire application, whenever you need it. This tutorial consists of 3 simple steps: creating the store, consuming a state, and changing a state inside a function.

## Creating the Store

To start, you could create a store file with Zustand. This could simply be a file called `store.js`, or `store.tsx` if you are using TypeScript. Here's a basic set up:

```javascript
import { create } from 'zustand';

const useStore = create((set, get) => ({
  numberOfStudents: 3
}));

export default useStore;
```

With this simple code snippet, you can now access the `numberOfStudents` throughout your entire application!

## Consuming a State

To consume a state from the store, here's a simple way to get it done:

```javascript
// Import the hook
import useStore from 'path/to/store';

const SomeComponent = () => {
  // Instantiate the hook
  const store = useStore();

  // Get the state you want
  const { numberOfStudents } = store;

  // Use the state
  return <div>The number of students is: {numberOfStudents}</div>
};
```

## Changing a State

To change a state, add a method to the store object that updates something inside the store. For example:

```javascript
import { create } from 'zustand';

const useStore = create((set, get) => ({
  numberOfStudents: 3,
  
  addAnStudent: () => {
    // The get function lets you get the current store inside a method of the store
    const {numberOfStudents} = get();
    
    // The set function lets you change the store. It can change a single key or the entire store.
    set({numberOfStudents: numberOfStudents+1});
  },
}));

export default useStore;
```

With this setup, the `addAnStudent` function allows you to add a student to the store, thereby adjusting `numberOfStudents` accordingly.