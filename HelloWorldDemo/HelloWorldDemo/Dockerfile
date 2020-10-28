#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

#FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
#WORKDIR /app
#EXPOSE 80
#EXPOSE 443

#FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
#WORKDIR /src
#COPY ["HelloWorldDemo/HelloWorldDemo.csproj", "HelloWorldDemo/"]
#RUN dotnet restore "HelloWorldDemo/HelloWorldDemo.csproj"
#COPY . .
#WORKDIR "/src/HelloWorldDemo"
#RUN dotnet build "HelloWorldDemo.csproj" -c Release -o /app/build

#FROM build AS publish
#RUN dotnet publish "HelloWorldDemo.csproj" -c Release -o /app/publish

#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "HelloWorldDemo.dll"]

#local build and publish
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY HelloWorldDemo.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c release -o /app

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "HelloWorldDemo.dll"]
