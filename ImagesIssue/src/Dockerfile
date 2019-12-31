FROM FROM stulzq/dotnet:2.2.0-aspnetcore-runtime-with-image AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY . "ImagesIssue/"
RUN dotnet restore "ImagesIssue/ImagesIssue.csproj"
COPY . .
WORKDIR "/src/ImagesIssue"
RUN dotnet build "ImagesIssue.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "ImagesIssue.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "ImagesIssue.dll"]
