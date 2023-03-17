# Using String.Dump

This method is designed to prevent tampering of built-in functions.
can be used in the following situation:
```lua
function loadstring(s)
   print(s)
   return s
end
```

### How It Works

In Lua, **string.dump** is a function that allows you to serialize a Lua function into a binary format. This binary format can be later loaded and executed by another Lua program.

```lua
local function  foo()
    return true
end

print(string.dump(foo))
```

If you try to call **string.dump** with a built-in function as its parameter, you will get an error message, as it's not possible to serialize a built-in function in Lua.

```lua
print(string.dump(print)) --> error: unable to dump given function
```

### Detect Tampering

Now, let's write code that detects tampering.

Use **pcall** to handle information about is function success or not.
You can use **pcall** to handle information about whether a function call was successful or not.

Here is an example:
```lua
local func = load
local isSuccess = pcall(
    function()
    string.dump(func)
    end
) --> return false

if isSuccess then --> In normal circumstances, it has to be false.
   --> If the function is not a built-in function, it indicates that tampering has occurred and execution will reach this point
else
   --> Original Code
end
```