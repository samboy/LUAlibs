# rg32.c

`rg32.c` is a library with a better `math.random()` for Lua.  The shell
script `compile.rg32.sh` can compile it for Linux and Cygwin; Mac users
can look at the script to figure out how to compile things on a Mac.
The resulting `.so` (`.dll` on Windows) file can be loaded in Lua:

```lua
require("rg32")
rg32.randomseed("1234")
string.format("%04x",rg32.rand16())
print(rg32.random())
rg32.randomseed(101.1) -- Converted to "101.1"
print(rg32.random(1,5))
print(rg32.random())
```

The API is a superset of Lua’s `math.random`, with the call `rand16` 
(random number from 0 to 65535) added to the usual `randomseed` and 
`random` calls (both of which have an API compatible with Lua’s native 
`math.random`).

Actually, `rg32.randomseed` takes a *string* as its argument.  However,
if a number is given, Lua automatically performs “coercion” and
makes the number a string.

