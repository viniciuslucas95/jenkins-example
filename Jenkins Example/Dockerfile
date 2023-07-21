FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

WORKDIR /app

RUN apt-get update && apt-get install -y git

RUN git clone https://github.com/viniciuslucas95/jenkins-example.git .

RUN dotnet restore "Jenkins Example/Jenkins Example.csproj"
RUN dotnet publish "Jenkins Example/Jenkins Example.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS final

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "Jenkins Example.dll"]