FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["FullSnack/FullSnack.csproj", "FullSnack/"]
RUN dotnet restore "FullSnack/FullSnack.csproj"
COPY . .
WORKDIR "/src/FullSnack"
RUN dotnet build "FullSnack.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "FullSnack.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "FullSnack.dll"]
