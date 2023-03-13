# Checking Current Line

You can use **debug.getinfo()** to get the current line of code, which can then be checked to determine whether or not it has been beautified.

```lua
local function getCurrentLine()return debug.getinfo(1).currentline end --> line 1

print( getCurrentLine() )
--> return 1
```

```lua
local function getCurrentLine()
    return debug.getinfo(1).currentline --> line 2
end

print(getCurrentLine())
--> return 2
```

**debug.getinfo()** returns a table containing information about the calling function, such as source which is a string representing the source file name or chunk name.
This information can be used to retrieve the current line number or maximum line length.

I mentioned that checking the current line is helpful in determining if the code is beautified, but it's important to note that utilizing the maximum line information can also achieve the same goal.