# syntax=docker/dockerfile:1

FROM mcr.microsoft.com/dotnet/sdk:6.0 as build-env
workdir /App
COPY . ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0 as runtime
WORKDIR /App
COPY --from=build-env /App/out .
ENV ASPNETCORE_URLS=https://+:8080
EXPOSE 8080
ENTRYPOINT ["dotnet", "esoSampleProject.dll"]
