
## Testing

Testing principles. The goals are to write as few tests as possible for maximum coverage of real world usage (not code coverage).

  * Write tests to increase confidence our customers' experience will be good.
  * To exercise important flows like signing up, purchasing, core product experience.
  * Prefer e2e tests, the highest possible level, over unit tests (most of the time).
  * Tie test cases to unchanging real world business logic and inputs, not implementation. This prevents their need to be rewriten during refactors.
  * Keep your test scenarios and code as similar as possible to real usage. Your tests should run the backend server, load actual client pages (like selenium would), and flip a switch to trigger test mode in your front end template.
