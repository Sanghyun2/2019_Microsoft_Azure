# AZ-203 Training (2019.06.27)

서울창업허브 세미나실3, 백범로 31길 21, 서울창업허브, 마포구, 서울특별시

한국무역협회와 MS Korea 주최

주제 : **AZ-203(Developing Solutions for Microsoft Azure) Exam Objectivees**

> 강의자료 : [AZ-203-DevelopingSolutionsforMicrosoftAzure](https://github.com/MicrosoftLearning/AZ-203-DevelopingSolutionsforMicrosoftAzure)

## 내용정리

**Implement Azure Function** : 환경을 잡아주지 않고 코드만 올려서 기능을 사용할 수 있음.

Storage Durability and Availability
1. LRS - 3 replicas, 1 region
2. ZRS - 3 replicas, across 3 Zones
3. GRS - 6 replicas, 2 regions

Azure Storage
1. Blob Storage
2. Table Storage
3. Queue Storage
4. File Storage

## 오전수업
1. Short brief of AZ-203 
1. [PowerShell Install](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)
1. [Azure CLI Install](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos?view=azure-cli-latest)
1. [Azure Resource Manager Tools Install](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.azurerm-vscode-tools)
1. Microsoft Azure Storage Explorer Install
1. Visual Studio 2019 Install
    1. Azure Developer Tools
    1. .Net Developer Tools

## 오후수업

#### AZ-203_01_lab.md
Lab Scenario #1 : Deploying compute workloads by using images and containers

#### AZ-203_02_lab.md
Lab Scenario #2 : Building a web application on Azure Platform-as-a-Service offerings

#### AZ-203_05_lab.md
Lab Scenario #5 : Monitoring services deployed to Azure

#### AZ-203_06_lab.md
Lab Scenario #6 : Creating a multi-tier solution by using services in Azure

#### 실습
- 실습 사이트 : [C#을 사용하여 Azure Virtual Machine 만들기 및 관리](https://docs.microsoft.com/ko-kr/azure/virtual-machines/windows/csharp)
- 실습 내용 : Visual Studio 이용해서 Resource Group 생성하고 VM 실행하기
- 순서 : C# Console Application 생성
- Program.cs
```C#
using System;
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;

namespace az_203_1906
{
    class Program
    {
        static void Main(string[] args)
        {
            var credentials = SdkContext.AzureCredentialsFactory
                .FromFile("/Users/sanghyeon2/Projects/az-203-1906/azureauth.properties.txt");

            var azure = Azure
                .Configure()
                .WithLogLevel(HttpLoggingDelegatingHandler.Level.Basic)
                .Authenticate(credentials)
                .WithDefaultSubscription();

            var groupName = "20190629-az203";
            var vmName = "az203";
            var location = Region.KoreaCentral;

            Console.WriteLine("Creating resource group...");
            var resourceGroup = azure.ResourceGroups.Define(groupName)
                .WithRegion(location)
                .Create();

            Console.WriteLine("Creating availability set...");
            var availabilitySet = azure.AvailabilitySets.Define("myAVSet")
                .WithRegion(location)
                .WithExistingResourceGroup(groupName)
                .WithSku(AvailabilitySetSkuTypes.Managed)
                .Create();

            Console.WriteLine("Creating public IP address...");
            var publicIPAddress = azure.PublicIPAddresses.Define("myPublicIP")
                .WithRegion(location)
                .WithExistingResourceGroup(groupName)
                .WithDynamicIP()
                .Create();

            Console.WriteLine("Creating virtual network...");
            var network = azure.Networks.Define("myVNet")
                .WithRegion(location)
                .WithExistingResourceGroup(groupName)
                .WithAddressSpace("10.0.0.0/16")
                .WithSubnet("mySubnet", "10.0.0.0/24")
                .Create();

            Console.WriteLine("Creating network interface...");
            var networkInterface = azure.NetworkInterfaces.Define("myNIC")
                .WithRegion(location)
                .WithExistingResourceGroup(groupName)
                .WithExistingPrimaryNetwork(network)
                .WithSubnet("mySubnet")
                .WithPrimaryPrivateIPAddressDynamic()
                .WithExistingPrimaryPublicIPAddress(publicIPAddress)
                .Create();

            Console.WriteLine("Creating virtual machine...");
            azure.VirtualMachines.Define(vmName)
                .WithRegion(location)
                .WithExistingResourceGroup(groupName)
                .WithExistingPrimaryNetworkInterface(networkInterface)
                .WithLatestWindowsImage("MicrosoftWindowsServer", "WindowsServer", "2012-R2-Datacenter")
                .WithAdminUsername("azureuser")
                .WithAdminPassword("Azure12345678")
                .WithComputerName(vmName)
                .WithExistingAvailabilitySet(availabilitySet)
                .WithSize(VirtualMachineSizeTypes.StandardD2V3)
                .Create();

            var vm = azure.VirtualMachines.GetByResourceGroup(groupName, vmName);

            Console.WriteLine("Getting information about the virtual machine...");
            Console.WriteLine("hardwareProfile");
            Console.WriteLine("   vmSize: " + vm.Size);
            Console.WriteLine("storageProfile");
            Console.WriteLine("  imageReference");
            Console.WriteLine("    publisher: " + vm.StorageProfile.ImageReference.Publisher);
            Console.WriteLine("    offer: " + vm.StorageProfile.ImageReference.Offer);
            Console.WriteLine("    sku: " + vm.StorageProfile.ImageReference.Sku);
            Console.WriteLine("    version: " + vm.StorageProfile.ImageReference.Version);
            Console.WriteLine("  osDisk");
            Console.WriteLine("    osType: " + vm.StorageProfile.OsDisk.OsType);
            Console.WriteLine("    name: " + vm.StorageProfile.OsDisk.Name);
            Console.WriteLine("    createOption: " + vm.StorageProfile.OsDisk.CreateOption);
            Console.WriteLine("    caching: " + vm.StorageProfile.OsDisk.Caching);
            Console.WriteLine("osProfile");
            Console.WriteLine("  computerName: " + vm.OSProfile.ComputerName);
            Console.WriteLine("  adminUsername: " + vm.OSProfile.AdminUsername);
            Console.WriteLine("  provisionVMAgent: " + vm.OSProfile.WindowsConfiguration.ProvisionVMAgent.Value);
            Console.WriteLine("  enableAutomaticUpdates: " + vm.OSProfile.WindowsConfiguration.EnableAutomaticUpdates.Value);
            Console.WriteLine("networkProfile");
            foreach (string nicId in vm.NetworkInterfaceIds)
            {
                Console.WriteLine("  networkInterface id: " + nicId);
            }
            Console.WriteLine("vmAgent");
            Console.WriteLine("  vmAgentVersion" + vm.InstanceView.VmAgent.VmAgentVersion);
            Console.WriteLine("    statuses");
            foreach (InstanceViewStatus stat in vm.InstanceView.VmAgent.Statuses)
            {
                Console.WriteLine("    code: " + stat.Code);
                Console.WriteLine("    level: " + stat.Level);
                Console.WriteLine("    displayStatus: " + stat.DisplayStatus);
                Console.WriteLine("    message: " + stat.Message);
                Console.WriteLine("    time: " + stat.Time);
            }
            Console.WriteLine("disks");
            foreach (DiskInstanceView disk in vm.InstanceView.Disks)
            {
                Console.WriteLine("  name: " + disk.Name);
                Console.WriteLine("  statuses");
                foreach (InstanceViewStatus stat in disk.Statuses)
                {
                    Console.WriteLine("    code: " + stat.Code);
                    Console.WriteLine("    level: " + stat.Level);
                    Console.WriteLine("    displayStatus: " + stat.DisplayStatus);
                    Console.WriteLine("    time: " + stat.Time);
                }
            }
            Console.WriteLine("VM general status");
            Console.WriteLine("  provisioningStatus: " + vm.ProvisioningState);
            Console.WriteLine("  id: " + vm.Id);
            Console.WriteLine("  name: " + vm.Name);
            Console.WriteLine("  type: " + vm.Type);
            Console.WriteLine("  location: " + vm.Region);
            Console.WriteLine("VM instance status");
            foreach (InstanceViewStatus stat in vm.InstanceView.Statuses)
            {
                Console.WriteLine("  code: " + stat.Code);
                Console.WriteLine("  level: " + stat.Level);
                Console.WriteLine("  displayStatus: " + stat.DisplayStatus);
            }
            Console.WriteLine("Press enter to continue...");
            Console.ReadLine();

            Console.WriteLine("Stopping vm...");
            vm.PowerOff();
            Console.WriteLine("Press enter to continue...");
            Console.ReadLine();

            vm.Deallocate();

        }
    }
}
```
- azureauth.properties.txt
```subscription=6789b5cd-7235-4298-93b7-3a8eed70aa66
client=a7855cbc-576f-4cc3-b378-72a88c2671ce
key=1q2w3et
tenant=9dc04b19-a3d5-4f3b-831a-ab44edee5daf
managementURI=https://management.core.windows.net/
baseURL=https://management.azure.com/
authURL=https://login.windows.net/
graphURL=https://graph.windows.net/
```
#### The Container Advantage
- Version In 해줌

#### DevOps
- 운영과 개발을 동시에 진행
- 왜 Cloud Infra 에서 DevOps 가 나오는지?
- Blue Green Deploy : Blue ASG ? Green ASG ? (AWS)
- 애자일 방법론

- - -
##### 더 알아보기
1. Cloud 사용하는 이유? Cloud 를 효율적으로 사용하는 방법?
    - Reason 1 : **Automatically create virtual machines (VMs) to run tasks and immediately terminate.**
2. RDB vs DBA ?
3. AWS 비용 산정 및 그리기 : [Cloudcraft - Draw AWS](https://cloudcraft.io)
4. IP : "10.0.0.0/16" 에서 16이 의미는?
5. Kubernetes Service ?
6. Apache, Tomcat ?
