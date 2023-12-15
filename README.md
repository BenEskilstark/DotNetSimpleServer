

## On Your Computer
### Initial setup:
- install .NET 8.0 sdk
- use VSCode
- clientside static files go in wwwroot/
### Making and deploying changes:
- build and run with
  - `dotnet run`
  - go to localhost:8000 to see it running
- prepare for release with
  - `dotnet publish -c Release`
- transfer to droplet with
  - `scp -r bin/Release/net8.0/publish/* user@123.456.78.90:~/myapp`

## On The Droplet
### First time:
- install MS signing key:
  - `wget https://dot.net/v1/dotnet-install.sh`
  - `sudo bash dotnet-install.sh -c Current`
- install .NET 8 runtime:
  - `sudo apt-get update`
  - `sudo apt-get install -y apt-transport-https`
  - `sudo apt-get update`
  - `sudo apt-get install -y aspnetcore-runtime-6.0`
- test installation with:
  - `dotnet --list-runtimes`
- Also need nginx. See [my nginx server](https://github.com/BenEskilstark/nginx_server)
### Running the server:
- MUST cd into the directory where the [myservername].dll is
- Basic running with:
  - `dotnet [myservername].dll`
- Or run in the background with:
  - `touch server.log`
  - `nohup dotnet [myservername].dll > server.log 2>&1 &`

