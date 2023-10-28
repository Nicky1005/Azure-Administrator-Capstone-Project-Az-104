
# Azure Administrator Capstone Project Az-104

## Project Overview
As an Azure Administrator, the project's goal is to implement a website architecture comprising three web pages deployed across Azure VMs, managed via an Application Gateway and VNet-VNet Peering in the Central US and West US regions.

## Architecture
### Web Pages Deployment
1. **Home Page** - Default page (VM2)
2. **Upload Page** - Allows file uploads to Azure Blob Storage (VM1)
3. **Error Page** - Handles 403 and 502 errors

### Application Gateway Configuration
- **Example.com**:
  - Home: Pointed to the home page
  - /upload: Directed to the upload page
  - Error pages pointed to error.html hosted in Azure Containers

### Traffic Distribution
- The Traffic Manager's domain 'Example' distributes traffic optimally between the Central US and West US regions.

### Storage Account Configuration
1. Host error.html as a static website in the Storage Account for handling 403 and 502 errors.
2. Create a container named 'upload' for file uploads.

### Technical Specifications
1. VM deployments in both regions within VNets.
2. Clone GitHub repo [azproject](https://github.com/azcloudberg/azproject) to all VMs.
3. Run `vm1.sh` on VM1 for the upload page and `vm2.sh` on VM2 for the home page.
4. Edit `config.py` on VM1 with storage account details and run `sudo python3 app.py`.
5. Connect both regions using VNet-VNet Peering.
6. Traffic Manager points to the application gateway in both regions.

## Deployment Instructions
1. Clone the project repository: `git clone https://github.com/azcloudberg/azproject`
2. Execute `./vm1.sh` on VM1 and `./vm2.sh` on VM2 from the project directory's terminal.
3. Update `config.py` on VM1 with storage account details.
4. Run `sudo python3 app.py` after the configurations.
5. Verify VNet-VNet peering and Traffic Manager settings.

