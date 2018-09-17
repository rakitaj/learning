# Simplicity

## Core learnings
```
"software simplicity is a prerequisite to reliability."
```

Saying no keeps us free of distractions and keeps us focused.

## Notes
Short chapter. Eliminating the correct type of complexity helps us spend time and effort on what is called our core engineering efforts.

## Codebase
1. Remove commented lines (not comments!)
2. Remove unreachable code
3. Remvoe code that is behind unused feature flags - this one is especially dangerous
4. Think of every line of code written as a potential liability

## APIs
1. A smaller API is easier to maintain

## Modularity
1. Keep APIs separated and targeted
2. Keep binaries separated and modular - benefits of being able to do modular (aka small) deployments
  1. Find problems easier when only a small component of the system changes
  2. Easier and faster deployments


