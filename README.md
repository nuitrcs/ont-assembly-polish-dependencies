# ont-assembly-polish-dependencies Singularity Image

This repository contains a Singularity recipe file to build an image containing
the dependencies of the
[https://github.com/nanoporetech/ont-assembly-polish](https://github.com/nanoporetech/ont-assembly-polish)
pipeline.

To use, build or pull this image, then check out the above repository from
Github to somewhere you can edit it, e.g.:
```
$ cd $HOME && singularity pull shub://nuitrcs/ont-assembly-polish-dependencies
$ git checkout git@github.com:nanoporetech/ont-assembly-polish.git $HOME/ont-assembly-polish
```
Then edit `$HOME/ont-assembly-polish/config.mk` as necessary for your analysis.

To run the pipeline:
```
$ cd $HOME/ont-assembly-polish
$ singularity exec -B /path/to/my/data:/data $HOME/ont-assembly-polish-dependencies_latest.sif make all
```
