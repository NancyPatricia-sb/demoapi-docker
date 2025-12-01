FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copiar el proyecto desde la subcarpeta DemoApi
COPY DemoApi/*.csproj ./
RUN dotnet restore

# Copiar todo el código de DemoApi
COPY DemoApi/. ./
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "DemoApi.dll"