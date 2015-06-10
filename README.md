# envman

## Who and for what?

- connect tools with each other : one tool saves an ENV, the other uses it (input & output)
- manage your environment-sets : use different ENVs for different projects


## How? - Use cases

- multi PATH handling: you have `packer` in your `$HOME` dir, in a bin subdir and terraform in another
  - create an envman `.envset` to include these in your `$PATH`


## TODO

- `init`: create an empty .envstore file into the current directory
- move CLI commands to separate files, one for each command
  - like in [https://github.com/docker/swarm](https://github.com/docker/swarm)
- multi ENV file handling
  - with an arg: `-envstore=path/to/envstore/file.yml` : use this file
  - if there's a .envstore file in the current dir use that one
  - if neither is present: use `$HOME/.envman/.envstore`
- check Go standard package errors (ex: `os.Setenv`)
- expand environment variables **on read** (not at store)
- better progress feedback:
  - present the file path the env is saved into for `add` command
- better command error handling
- ~~store ENVs as Map, not as Slice/array~~
- better help texts
- **print**: should work for empty as well
- clear : empty the store
- `env [bash/fish]` : exports ENVs in a bash/fish compatible format
  - for bash it prints `export KEY=value` statements
  - which can be run like this: `$(envman env bash)` to import the ENVs into the current ENV session
