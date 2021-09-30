#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["CICD Test/CICD Test.csproj", "CICD Test/"]
RUN dotnet restore "CICD Test/CICD Test.csproj"
COPY . .
WORKDIR "/src/CICD Test"
RUN dotnet build "CICD Test.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "CICD Test.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "CICD Test.dll"]