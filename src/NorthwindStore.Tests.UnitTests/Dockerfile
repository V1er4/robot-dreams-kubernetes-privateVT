main
FROM --platform=$BUILDPLATFORM mcr.microsoft.com/dotnet/sdk:6.0 AS build
ARG configuration=Release
=======
# See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

# This stage is used to build the service project
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
main
WORKDIR /src
COPY ["packages/", "packages/"]
COPY ["nuget.config", "."]
COPY ["NorthwindStore.Tests.UnitTests/NorthwindStore.Tests.UnitTests.csproj", "NorthwindStore.Tests.UnitTests/"]
main
COPY ["NorthwindStore.DAL/NorthwindStore.DAL.csproj", "NorthwindStore.DAL/"]
COPY ["NorthwindStore.BL/NorthwindStore.BL.csproj", "NorthwindStore.BL/"]
RUN dotnet restore "NorthwindStore.Tests.UnitTests/NorthwindStore.Tests.UnitTests.csproj"
COPY . .
WORKDIR "/src/NorthwindStore.Tests.UnitTests"
RUN dotnet build "NorthwindStore.Tests.UnitTests.csproj"

ENTRYPOINT ["dotnet", "test", "NorthwindStore.Tests.UnitTests.csproj"]
=======
COPY ["NorthwindStore.BL/NorthwindStore.BL.csproj", "NorthwindStore.BL/"]
COPY ["NorthwindStore.DAL/NorthwindStore.DAL.csproj", "NorthwindStore.DAL/"]
RUN dotnet restore "./NorthwindStore.Tests.UnitTests/NorthwindStore.Tests.UnitTests.csproj"
COPY . .
WORKDIR "/src/NorthwindStore.Tests.UnitTests"

RUN dotnet build "./NorthwindStore.Tests.UnitTests.csproj"

ENTRYPOINT ["dotnet", "test", "NorthwindStore.Tests.UnitTests.csproj"]
main
