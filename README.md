# pdmwrapper

## TL;DR
Build/test Python projects with decent dependency management and without tool installation hassle.
* `git clone https://github.com/houbie/pdmwrapper.git`
* `./pdmw install`
* `./pdmw run pytest`

## What?
Experiment to mimic the [gradle wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html)
features for [PDM](https://pdm.fming.dev/)

The wrapper is a small script that is stored in the source repo of a project.
The wrapper forwards all invocations to the actual build tool, but on the first invocation 
it will install the correct version of the build tool inside the project. 

## Why?
The benefits are threefold:
* build results are consistent because all developers and the CI/CD server use the same version
  of the build tool
* frictionless development setup: just clone and build the project,
  having the platform (Python in this case) installed is enough to get started
* breaking changes in the build tool don't break your project

The developers that will once inherit your projects will be very grateful that they don't have to
spend a couple of days setting up a dev environment in order to change one line of code.

## How?
* The script installs PDM in _.pdm/$PDM_VERSION_  with something like 
`pip install pdm==$PDM_VERSION --target .pdm/$PDM_VERSION`
* It adds _.pdm/$PDM_VERSION_ to the _PYTHONPATH_
* Calls `pdm` while passing all arguments

## TODO
* Cleanup the _pdmw_ wrapper script
* Create a Windows script
* Is `pip install` the best strategy? Or is it better to maintain a 
  downloadable self contained  archive, or ...?

I'm not a shell specialist and python noob, so definitely need help here.
