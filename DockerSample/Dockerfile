#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

## command to build the image
## docker build -f DockerSample/Dockerfile -t dotnet/sample .

## command to create a container
## docker run -p 8087:80 -d dotnet/sample

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY . .
WORKDIR "/src/DockerSample"
RUN dotnet publish "DockerSample.csproj" -c Release -o /app/publish 

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "DockerSample.dll"]
EXPOSE 80