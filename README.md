# dag_scheduler_workspace_go
This will act as the root level directory for the backend and frontend </br>
components that communicate with the C++ code via service calls. </br>
See https://go.dev/doc/tutorial/workspaces for more information. </br>

## Developer Notes

### How to clone the repository and all the go modules as git submodules
```
> git clone \
  --recurse-submodules git@github.com:mehoggan/dag_scheduler_workspace_go.git
```

### How to add a module in this workspace
```sh
> git clone <git url>
> go work use <path to module>
> git submodule add <path to module>
```

### Keep things up-to-date
```sh
> git submodule update --inite --recursive
```

### How to run a module in this workspace
```sh
> go run <module name in go.mod>
```

### How to test a module in this workspace
```sh
> go test <module name in go.mod>
```

### How to realease a module in this workspace

```sh
> cd <module>
# Do work run tests.
> git checkout -b <branch_name>
> git add --all :/
> git commit -m "<your commit message>"
> git push origin HEAD:main
> GIT_SHA=$(git log --pretty=oneline | head -n 1 | awk '{print $1}')
> CURR_GIT_TAG=$(git tag -l | tail -n 1)
> git tag -a <Incremented CURR_GIT_TAG>  <GIT_SHA>
> git push --tags
> cd ../
```
