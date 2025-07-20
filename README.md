# dotenv-nelua

Implements the ability to use `.env` files while also being a drop in replacement for `os.getenv`

## How to install

Copy the `dotenv.nelua` file into your project and require it

```lua
local dotenv = require("path.to.dotenv")
```

Or add it to your [nlpm](https://github.com/kmafeni04/nlpm) package dependencies

```lua
{
  name = "dotenv-nelua",
  repo = "https://github.com/kmafeni04/dotenv-nelua",
  version = "COMMIT-HASH-OR-TAG",
},
```

## Quick start

```lua
local dotenv = require("path.to.dotenv")
local env, err = dotenv:load()
-- Handle the err as you see fit, it's an empty string if there's none
local var = env:get("YOUR_VAR")
```

## Reference

### Dotenv

Record containing all your env variables

```lua
local Dotenv = @record{
  vars: hashmap(string, string)
}
```

### Dotenv.load

Loads the specified file or a `.env` file\
Returns the env map and an error string\
If no error occurs, the string is empty

```lua
function Dotenv.load(filename: facultative(string)): (Dotenv, string)
```

### Dotenv:get

Trys to get the environment variable from os.getenv then tries the `.env` file\
Returns the value of that variable or an empty string

```lua
function Dotenv:get(env: string, default: string): string
```

