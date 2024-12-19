# Silent Failure of Async/Await in useEffect Hook

This repository demonstrates a common, yet difficult-to-debug issue in React Native applications: the silent failure of asynchronous operations within `useEffect` hooks.  The application fetches data from an API, but due to an unhandled promise rejection, it doesn't display any error messages, leaving the user with a perpetually loading screen.

The `DataFetch.js` file contains the buggy code. The `DataFetchSolution.js` offers a corrected version.

## Problem

The original code uses `async/await` inside `useEffect` to fetch data.  If the fetch fails (e.g., network issue, API unavailable), the promise rejects silently. Because there's no error handling within the `async` function and no `.catch` block around the `fetchData` call, the error is not caught and logged to the console. The `loading` state remains `true`, resulting in an endlessly loading screen.