This Docker image can be customized to have MS Build Tools with any one
workload. Multiple images can be built with different workloads as needed.

# Arguments

The `WORKLOAD` argument is mandatory. Leave the rest blank for VS2019 on Win10.
Any workload from [this list][workloads] should work. Only provide the last
part of the qualified name of the workflow (after the last dot).

|variable|description|default|
|--------|-----------|-------|
|`WIN_VERSION`|Version of Windows to base from|"1809"|
|`VS_VERSION`|Version of Visual Studio to install|"16"|
|`VS_PATH`|Install path for Visual Studio|"C:\VisualStudio"|
|`WORKLOAD`|Visual Studio workload to install|`none`|

[workloads]: https://docs.microsoft.com/en-us/visualstudio/install/workload-component-id-vs-community?view=vs-2022&preserve-view=true

# Example

```batch
docker build ^
--build-arg WIN_VERSION=1809 ^
--build-arg VS_VERSION=16 ^
--build-arg WORKLOAD=VCTools ^
-m 2GB ^
-t pgsocks/buildtools:16-VCTools ^
docker
```
