FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build

WORKDIR /worker/app

COPY ./src/Worker/Worker.csproj ./

RUN dotnet restore

COPY ./src/Worker/ .

RUN dotnet publish -c Release -o /app


FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime

WORKDIR /worker/app

COPY --from=build /app .

ENTRYPOINT ["dotnet", "Worker.dll"]