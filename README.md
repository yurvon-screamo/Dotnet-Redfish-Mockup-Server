# Redfish.Mockup.Server

A simple dotnet aot 8.0 program that can be copied into a folder at the top of any Redfish mockup and can serve Redfish requests on the specified IP/port.

Idea from - [DMTF](https://github.com/DMTF/Redfish-Mockup-Server) (with more performance, but with less functionality).

## About

The Redfish Mockup Server serves Redfish requests against a Redfish mockup. The server runs at either a specified IP address and port or the default IP address and port, default `0.0.0.0:8080`.

Edit `appsettings.json` and set target listen address:port.

You can find DMTF-published sample mockups at [All Published Versions of DSP2043](https://www.dmtf.org/dsp/DSP2043 "https://www.dmtf.org/dsp/DSP2043").

To create a mockup from a service, use the [Redfish-Mockup-Creator](https://github.com/DMTF/Redfish-Mockup-Creator "https://github.com/DMTF/Redfish-Mockup-Creator").

## Requirements

To run the mockup server natively on your system:

* Install Dotnet sdk 8.0.

To run the mockup server as a Docker container:

* Install [Docker](https://www.docker.com/get-started "https://www.docker.com/get-started").

## Usage

Configure:

* edit [appsettings.json](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel/endpoints?view=aspnetcore-8.0#configure-endpoints-in-appsettingsjson) and set target listen address:port (default `0.0.0.0:8080`).
* set "ContentRelativePath" variable to set redfish-mockup data directory (default - `content`).

Run application in debug: `dotnet run`

Or build and run build:

* Build application: `dotnet publish "./dotnet-redfish.csproj" -c Release -o ../release /p:UseAppHost=true`
* Run application: `../release/dotnet-redfish`

Or build and run docker image:

* Build image: `docker build -t dotnet-redfish .`
* Run image: `docker run -p 8080:8080 -it dotnet-redfish`
