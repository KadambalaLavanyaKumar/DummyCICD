# Use the official .NET SDK image as the base image
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env

# Set the working directory in the container
WORKDIR /app

# Copy the project files to the container
COPY . ./

# Restore dependencies and build the application
RUN dotnet restore
RUN dotnet publish -c Release -o out

# Create a runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build-env /app/out .

# Expose the port that the application will run on
EXPOSE 80

# Command to run the application
ENTRYPOINT ["dotnet", "DummyCICD.dll"]
