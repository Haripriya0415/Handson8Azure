
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443 

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["Handson8Azure/Handson8Azure.csproj", "Handson8Azure/"]
RUN dotnet restore "Handson8Azure/Handson8Azure.csproj"
COPY . .
WORKDIR "/src/Handson8Azure"
RUN dotnet build "Handson8Azure.csproj" -c Release -o /app/build 
FROM build AS publish
RUN dotnet publish "Handson8Azure.csproj" -c Release -o /app/publish 
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Handson8Azure.dll"]
 