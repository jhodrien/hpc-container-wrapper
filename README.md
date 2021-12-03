## Frontends

- `cont-conda`
- `pycont`
- `wrapcont`
- `instcont`


## Special vars

These can be set before starting the tool

`CW_DEBUG_KEEP_FILES`
Don't delete build files when failing. 

`CW_LOG_LEVEL`
How verbosely to report program actions

- 0 only error
- 1 only warnings
- 2 general (default)
- >2 debug

## Notes
`SINGULARITY_BIND` handled after `-B`
ordering within both matter! -> nested bind mounts possible.
Not that while loop devices can be mounted on bind mounts,
any extra bind mounts will be applied after extra loop device (image mounts) 
so to mask dirs on disk with an image mount, the path can not be bind mounted.
(exception is the default $HOME mount, which is applied before loop device mounts)



## Convoluted path modifications in py scripts

The idea is that everything works even if a completely different python
environment is active, we also avoid having any extra envs set while parsing
the conf to allow for very "creative" usages of the tool

## instcont

Technically updating masked disk installations
is not an issue, but let's not do that until there is a specific
request. The tool now drops the full path leading to the target
from the bind list, if more binds are needed a yaml input needs to be constructed. 
