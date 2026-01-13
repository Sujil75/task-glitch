# Task Management App – Bug Fix Summary

## Overview

This is a **React + TypeScript Task Management Dashboard** that allows users to create, edit, delete, and track tasks along with analytics like ROI, Revenue per Hour, and Performance Grade.

During development, several issues were identified that impacted stability, correctness, and user experience. All have been addressed and fixed.

---

## Bugs Fixed

1. **Double Fetch on Load**

   * Data was being fetched twice when the app loaded.
   * The root cause was improper `useEffect` handling and React StrictMode causing multiple renders.
   * The fix ensures the fetch runs only once on initial load.

2. **Undo Snackbar Logic**

   * Deleted tasks sometimes remained in memory after the Undo Snackbar closed, leading to inconsistent state.
   * The fix clears the last deleted task and resets the state when the Snackbar closes, whether the user clicks Undo or not.

3. **Unstable Task Sorting**

   * Sorting tasks by ROI caused flickering when multiple tasks had the same ROI value.
   * The fix adds a secondary sort criterion (like task title) to maintain stable order.

4. **Event Bubbling on Row Buttons**

   * Clicking Edit or Delete buttons inside a row also triggered the row’s click event, opening the task view dialog unintentionally.
   * The fix stops event propagation on these buttons to prevent unintended behavior.

5. **Unsafe ROI Calculations**

   * Calculations like Revenue ÷ Time could produce `Infinity` or `NaN` when time was zero or revenue was invalid.
   * The fix validates inputs and returns a safe value if calculation is not possible, preventing UI errors.

---

## Impact of Fixes

* Improved **data consistency** and **UI stability**.
* Enhanced **user experience**, ensuring buttons behave correctly.
* Correct and safe **ROI and performance calculations**.
* Overall, the app now runs reliably without flickering or unexpected behavior.