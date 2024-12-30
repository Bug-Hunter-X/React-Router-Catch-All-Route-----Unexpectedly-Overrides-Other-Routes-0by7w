# React Router Catch-All Route Bug

This repository demonstrates a common, yet subtle, bug in React Router v6 where the catch-all route (`*`) unexpectedly overrides other routes, even when more specific routes appear to be a better match.

The issue stems from the order of routes defined within the `<Routes>` component.  The catch-all route, intended to handle 404 errors, should only be used as a last resort, otherwise it will catch all the requests before it reaches the rest of the routing configurations.

## Reproduction

1. Clone the repository.
2. Run `npm install`.
3. Run `npm start`.

Observe that navigating to `/about` will still lead to the NotFound component, due to the catch-all route taking precedence. 

## Solution

The solution involves reordering routes in the `<Routes>` component.  The catch-all route must be placed last to correctly catch only unmatched paths.

See `AppSolution.js` for the corrected code.