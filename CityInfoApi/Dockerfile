FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY CityInfoApi.csproj .
RUN dotnet restore 
COPY . .
# WORKDIR /src/CityInfoApi
RUN dotnet build --output /app

FROM build AS publish
RUN dotnet publish --output /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "CityInfoApi.dll"]