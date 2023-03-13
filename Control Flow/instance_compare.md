# Instance Compare

Comparing two different instances that have the same data.

```lua
if {"hi"} == {"hi"} then --> different memory
    return true
else
    return false
end
--> return false
```