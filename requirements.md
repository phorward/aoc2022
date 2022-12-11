# Requirements

- `for...in` is definitely missing!
- Rename `loop` back into `while` as it is more awk/c/python/rust-like.
- In a simple grammar like



- Constant list or dict `x : (1, 2, 3)` cannot be defined (becomes a parselet)
- `list`
  - I want to define a list named `list`
  - Slices would be useful in many ways
    - `sum((elfs[0],elfs[1],elfs[2]))` => `sum(elfs[..2])`
  - `range()` or other way to define a counted list
    - `x == pix - 1 || x == pix || x == pix + 1`
      - could be `x in range(pix - 1, pix + 1)`
      - or even `x in (pix - 1..pix + 1)`
  - `copy()`
  - `sort()`
  - `min()`
  - `max()`
  - `sum()`
- `dict`
  - I want to define a dict named `dict`
  - Should have their own syntax `d = []`
- `str`
  - `count()`
  - `contains()` or `"substr" in s`
- `int`/`float`
  - Missing `abs()` function
  - Missing `%` modulus operator
  -
