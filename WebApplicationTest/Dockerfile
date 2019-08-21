FROM microsoft/dotnet:sdk AS build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o publishdir

FROM microsoft/dotnet:aspnetcore-runtime AS runtime
EXPOSE 5555
WORKDIR /app
COPY --from=build /app/publishdir .
ENTRYPOINT ["dotnet", "WebApplicationTest.dll"]