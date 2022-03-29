# 300 - Create a Windows Virtual Machine in the Azure Portal

You will deploy a Windows 2019 Datacenter virtual machine in the Azure portal.

Often used as a bridge for modernizing on-premises workloads to Microsoft Azure, virtual machines are an important piece of any organization's cloud strategy. This lab will walk you through deploying a Windows Server 2019 virtual machine in Microsoft Azure. This VM will act as a web server for your organization. You'll deploy Azure Bastion for secure browser-based access to your virtual machine. Then you'll implement common network configuration steps, and resize your virtual machine for performance improvement. You will finish with implementing Azure Disk Encryption using Azure Key Vault to secure your virtual machine's disks. When completed, you will have deployed and configured a secure web server.

In this challenge, you will deploy a Windows Server 2019 Datacenter edition virtual machine that will become a web server in Microsoft Azure.

1. Click **Open Azure portal** to access the lab environment, then use the provided credentials to log in.

2. Use the search bar at the top of the page to navigate to the **Virtual machines** service.

3. At the **Virtual machines** page, click the **+Create** button, then choose **+ Virtual machine**.

4. In the **Create a virtual machine** window, enter the following information under the Basics tab:

- **Resource Group**: Click **Create new**, enter ```pluralsight-resource-group```, then click **OK**.

- **Virtual machine name**:  ```vm-lab-win001```

- **Region**: Choose **(US) East US** from the dropdown menu 

- **Image**: Choose **Windows Server 2019 Datacenter - Gen2** from the dropdown menu

- **Size**: Select **Standard_DS1_v2 - 1 vcpu, 3.5 GiB memory**.

- **Username**:  ```azurelabadmin```

- **Password**: ```L234FOmdwer#2```

- **Confirm password**:  ```L234FOmdwer#2```

- **Public inbound ports**: Choose **None**.

5. Click **Next: Disks**, then **Next: Networking**.

6. On the **Networking** tab under the **Virtual network** dropdown menu, click the **Create new** link.

7. In **Create virtual network**, change the **Name** to ```vnet-lab-001```.

8. In the **Address Space** section, make sure the listed **Address range** is set to ```10.0.0.0/16```.

9. Under **Subnets**, delete the given **default** subnet, then add the following:

- **Subnet name**:  ```snet-lab-001``` 

- **Address range**:  ```10.0.0.0/24``` 

10. Click **Ok**. 

11. Back at the **Networking** tab, under **Public IP**, click **Create new**.

12. In **Create public IP address**, enter the following and then click **OK**.

- **Name*: ```vm-lab-win001-ip``` (This should be entered already for you.)

- **SKU**: **Standard**

13. For **Public inbound ports**, choose **None**.

14. Leave the rest of the defaults, and click **Review + create**.

15. In the **Review + create** tab, wait for the **Validation passed** message, then click **Create** to begin the build out of the virtual machine. 

- ***Note***: This process may take a few minutes. As you are waiting for the VM to be built out, you will see all of the other resources being deployed with it including a network security group, public IP, and other resources used by the VM.

16. When your deployment is complete, click on **Go to resource**. This will take you to the ```vm-lab-win001 Overview```.

Review the **Properties** tab and verify the information–such as a **Computer name** of **vm-lab-win001**, and a **Size** of **Standard DS1 v2**–matches the values in the tasks above. You may need to click **Refresh** to get up-to-date information on the Properties tab.

Congratulations! You have deployed your first virtual machine running Windows Server 2019 Datacenter. Creating VMs through the Azure Portal is a quick process as long as you have all of the information you need for size, type, and networking.
