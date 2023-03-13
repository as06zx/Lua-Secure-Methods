# Using Anonymous Function

When Lua code is beautified, semicolons are often removed to make the code more concise. For example:

```lua
local n = 1; --> before
local n = 1  --> after
```

To prevent beautified code from working, you can use anonymous functions. Here's an example:

```lua
local a = (function()
     return nil
end); --> a is local variable that stores a function
(function()end)() --> call anonymous function with no parameters

--> Perfectly working code!
```
However, if the code is beautified by removing the semicolon, it will no longer work as intended:

```lua
local a = (function()
    return nil
end) --> semicolon removed

(function()
end)() --> call nil

--> error: attempt to call a nil value!
```