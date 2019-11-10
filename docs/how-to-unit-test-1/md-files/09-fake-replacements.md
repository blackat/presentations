# Fake replacements

<img src="images/intruder.png" alt="Help the cat" width="40%"/>


## Test doubles

- <span class="text-highlight">**Simulate**</span> part of the system at run-time with <span class="text-highlight-red">*pre-determinated interactions*</span>.
- <span class="text-highlight">**Simulations**</span> are called:
    - mocks
    - stubs
    - dummies
    - fake spy


## Type of test doubles

- <span class="text-highlight">**Mock**</span> uses <span class="text-highlight-red">*behaviour verification*</span> (has a method been called?).
- <span class="text-highlight">**Fake object**</span> has <span class="text-highlight-red">*working implementation*</span> by shorcut so not useful for production (in memory db).
- <span class="text-highlight">**Stub**</span> uses <span class="text-highlight-red">*state verification*</span> (is the variable equal to 2?).
- <span class="text-highlight">**Spy**</span> is a <span class="text-highlight-red">*stub*</span> able to <span class="text-highlight-red">*record information*</span> on how it was called (how many times?).