This is just a quick reference for Lua syntax when you're not sure.

This reference presumes basic programming knowledge in Lua and in general.

[Lua](https://www.lua.org/about.html) is a powerful, efficient, lightweight, embeddable scripting language. It supports procedural programming, object-oriented programming, functional programming, data-driven programming, and data description.

* [Comments](#comments)
* [Operators](#operators)
* [Variables](#variables)
* [Strings](#strings)
* [If](#if)
* [For](#for)
* [While](#while)
* [Repeat](#repeat)
* [Functions](#functions)
* [Tables](#tables)
* [Modules](#modules)
* [Errors](#errors)

### Comments

```lua
-- Single line coment
```

```lua
--[[
    Multiline
    Block coment
--]]
```

### Operators

```lua
+  -  *  /  %  ^        -- Arithmetic operators
==  ~=  >=  <=  >  <    -- Relational operators
and  or  not            -- Logical operators
```

```lua
..                      -- Concatenate two strings
#                       -- String or Table length
```

### Variables

```lua
x = 1           -- Global variable
```

```lua
local x = 2     -- Local/scoped variable
```

```lua
x, y = 3, 4     -- Init many at once
```

### Strings

```lua
print('Hello ' .. 'World')      -- String concatenation
```

```lua
str = "hello"
print(#str)                     -- String size
```

```lua
str = [[
    Hello
    World
]]
print(str, #str)
```

### If

```lua
if a == b then
    -- code
end
```

```lua
if a ~= b then
    -- code
else
    -- code
end
```

```lua
if a > b then
    -- code
elseif a < b then
    -- code
end
```

### For

```lua
for i = 1, 10 do       -- init, max value
    print(i)
end
```

```lua
for i = 1, 5, 2 do     -- init, max value, increment
    print(i)
end
```

```lua
for i = 10, 1, -1 do   -- Reverse loop
    print(i)
end
```

```lua
arr = {'Hello', 'World'}

for i, v in ipairs(arr) do          -- Iterate an array
    print(i, v)
end
```

```lua
fruit = {name='apple', color='red'}

for k, v in pairs(fruit) do         -- Iterate table key=value
    print(k, v)
end
```

### While

```lua
while a < b do
    -- code
end
```
 
### Repeat

```lua
repeat
    -- code
until a > b
```
 
### Functions

```lua
function example()
    -- code
end
```
 
```lua
function add(a, b)
    return a + b
end
```

```lua
function point()
    return 2, 3
end
```

```lua
fn = function()                 -- Anonymous function
    -- code
end
```
 
```lua
fn = function()
    return function()           -- Closure function
        -- code
    end
end
```
 
```lua
fn = function(...)              -- Variable arguments
    for i, v in ipairs(arg) do  -- 'arg' variable magically appears
        print(i, v)
    end
end
fn(5, 6, 7)                     -- Calling with variable arguments
```

### Tables

```lua
fruit = {}
fruit = {name='apple'}
fruit = {['name']='apple'}      -- Same as above

fruit.color = 'red'
fruit['color'] = 'red'          -- Same as above

name = fruit.name
name = fruit['name']            -- Same as above

arr = {1, 2, 3}
arr[4] = 4
```

```lua
dog = {}
    
function dog:speak(o)
    print('woof')
end

dog:speak()
```

```lua
Animal = {}

function Animal:new(o)       -- Inheritance mechanism
    o = o or {}
    setmetatable(o, self)
    self.__index = self
    return o
end

function Animal:speak()
    print('no sound')
end

Dog = Animal:new()

function Dog:speak()
    print('woof')
end

dog = Dog:new{}
dog:speak()
```

```lua
dot_vs_colon = {}

function dot_vs_colon:colon()           -- 'self' is available
    print('self:', self == nil)
end

function dot_vs_colon.dot()             -- 'self' is not available
    print('self:', self == nil)
end

dot_vs_colon:colon()
dot_vs_colon.dot()
```

### Modules

```lua
require 'something'
```

```lua
local example = require 'example'
```

### Errors

```lua
function foo()
    error({ msg='oops' })
end

status, err = pcall(foo)

if err then
    print(status, err.msg)
end
```
