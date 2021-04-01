
Credits: Modified from https://github.com/rescript-lang/bsb-bench

## Get started

Run `ocaml unix.cma gen.ml -n 10 test` to generate a performance test for dune

## Description

The test involves the generation of DR * DC directories, the
"directory matrix", and each directory contains MR * MC modules,
the "module matrix". The module in row r and column c of the module
matrix depends on all modules in the previous row of the same
directory. The first row of modules in a directory depends on 
all modules in the preceding row of directories.


The test setup also permits a lot of parallelism for actually executing
the rules: the modules in the same row can be compiled in parallel,
as well as the directories in the same row.

Every module includes a big comment, so that the size of the files
is not super-small. 

To test it 

```sh
ocaml unix.cma gen.ml -n 10 test
cd test && esy && time esy x dune build @all
```
