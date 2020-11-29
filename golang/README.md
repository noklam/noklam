# Notes
- go get golang.org/x/tour -> Result in C:/User/<user_name>/go/bin
- The first statement in a Go source file must be package name. Executable commands must always use package main.
- install directory is controlled by the GOPATH and GOBIN environment variables.
- Exported names - Captial Letter only - similar to internal method. i.e. math.pi cannot be used, but math.Pi


# Commands
```go
# Set go binary path for installed command
go env -w GOBIN=/somewhere/else/bin
```

# Setup
- Jupyter for Go: https://github.com/gopherdata/gophernotes#windows
```
docker run -it -p 8888:8888 gopherdata/gophernotes:latest-ds
```
## Mount to local storage notebooks
`docker run -it -p 8888:8888 -v notebooks:/path/to/notebooks/in/docker gopherdata/gophernotes`
## Window Local Install
```
env GO111MODULE=on go get github.com/gopherdata/gophernotes
mkdir -p ~/.local/share/jupyter/kernels/gophernotes
cd ~/.local/share/jupyter/kernels/gophernotes
cp "$(go env GOPATH)"/pkg/mod/github.com/gopherdata/gophernotes@v0.7.1/kernel/*  "."
chmod +w ./kernel.json # in case copied kernel.json has no write permission
sed "s|gophernotes|$(go env GOPATH)/bin/gophernotes|" < kernel.json.in > kernel.json

# Jupyter Config
mkdir %APPDATA%\jupyter\kernels\gophernotes
xcopy %GOPATH%\src\github.com\gopherdata\gophernotes\kernel %APPDATA%\jupyter\kernels\gophernotes /s
```