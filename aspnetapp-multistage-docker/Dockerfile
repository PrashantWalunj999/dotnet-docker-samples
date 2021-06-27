#Stage 1
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build

WORKDIR /source 
COPY . . 

RUN dotnet restore 
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app 


#Stage 2
FROM mcr.microsoft.com/dotnet/aspnet:3.1 as run 

EXPOSE 80 
WORKDIR /app
COPY --from=build /app/ .
ENV ASPNETCORE_URLS http://*:80
CMD dotnet aspnetapp.dll


