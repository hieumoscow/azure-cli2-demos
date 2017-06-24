# azure-cli2-demos - D.Evans
Azure CLI 2 Commands which can be used in either demos or for provisioning Azure resources


# Docs on WebApp CLI2 here
# https://docs.microsoft.com/en-us/cli/azure/webapp

# Install az (Azure CLI 2.0) on Mac OS X
curl -L https://aka.ms/InstallAzureCli | bash

az group create --name pokedemorg --location "Southeast Asia" --output jsonc

# Create App Service plan
az appservice plan create --sku S1 --name sng_asp2 --is-linux --location "Southeast Asia" --resource-group "pokedemorg" --output jsonc

# Create WebApp on Linux Worker running a Docker Container
# http://pokewww.azurewebsites.net/
az webapp create --resource-group pokedemorg --name pokewww --deployment-container-image-name hasjo/pokemon-showdown --plan sng_asp2 --output jsonc

# View logs to troubleshoot
az webapp log download --name pokewww --resource-group pokedemorg

# Takes 30 seconds to connect to the streaming service
az webapp log tail --name pokewww --resource-group pokedemorg
2017-06-24T04:28:17  Welcome, you are now connected to log-streaming service.

# Deletes App Service Plan and AppService
az webapp delete --name pokewww --resource-group pokedemorg
