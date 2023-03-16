# Using Table Key

In Lua, table keys can be of any data type, not just limited to strings or numbers.
```lua
local t = {}
t[true] = 1
t[{}] = 2
t[function()end] = 3
t[coroutine.create(function()end)] = 4
t[nil] = 5 --> error: key cant be nil
```
