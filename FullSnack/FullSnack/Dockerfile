FROM microsoft/dotnet:2.2-sdk as build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore 

COPY . ./
RUN dotnet publish -c Release -o out

FROM microsoft/dotnet:2.2-sdk 
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "FullSnack.dll"] 