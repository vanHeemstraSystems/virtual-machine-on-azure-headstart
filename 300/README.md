# 300 - Create a Windows Virtual Machine in the Azure Portal

You will deploy a Windows 2019 Datacenter virtual machine in the Azure portal.

Often used as a bridge for modernizing on-premises workloads to Microsoft Azure, virtual machines are an important piece of any organization's cloud strategy. This lab will walk you through deploying a Windows Server 2019 virtual machine in Microsoft Azure. This VM will act as a web server for your organization. You'll deploy Azure Bastion for secure browser-based access to your virtual machine. Then you'll implement common network configuration steps, and resize your virtual machine for performance improvement. You will finish with implementing Azure Disk Encryption using Azure Key Vault to secure your virtual machine's disks. When completed, you will have deployed and configured a secure web server.

In this challenge, you will deploy a Windows Server 2019 Datacenter edition virtual machine that will become a web server in Microsoft Azure.

1. Click **[Open Azure portal](https://login.microsoftonline.com/organizations/oauth2/v2.0/authorize?redirect_uri=https%3A%2F%2Fportal.azure.com%2Fsignin%2Findex%2F&response_type=code%20id_token&scope=https%3A%2F%2Fmanagement.core.windows.net%2F%2Fuser_impersonation%20openid%20email%20profile&state=OpenIdConnect.AuthenticationProperties%3DMb-Zkifm8iOh8SurtYWzqJdj2X9VVmjb2Nibl1_4Msfh1ckihngnQ3PLAhch4KN-w_NFx7intHUnGTTkyXF1k9qfXmwTcGIa5vKV-V-0xx-Iu-Hr8liJhz7v1hhzU-Nk-jgiOWfH3Hl6mbpr1ZJFR2g0gwr7ytUYyfHEUPwYAgj7PjmjNbQL8VUXSUd4EMMtmNol9rB_euoBSRJKpnSE69bKskb_11qM1HL59SKtLUPwTLwZun_dTqb9l4wSM9kemzVwVG_HJZxoxpbdtazKQIn9fHhYpasEiaB9WR5iT9W22oo7q3wskMFAGO3ZMRZcLn6f7W9WgY9JiUqtam-Ba1q1_X4ykF1Ni0qcNkunNRr8UHL9EAPaL92RtNXh1Fr-_j_yFcJPqLCTOM2ySp5rtA&response_mode=form_post&nonce=637841379636724262.NzZlZDdiZDItN2EwYi00ZDlkLWEzMTAtNzc4NDEyZTY0Y2IwZTg1YjA0YWUtNTk0Yy00MzllLWJkM2EtOTQxNmEzOTA1YjMw&client_id=c44b4083-3bb0-49c1-b47d-974e53cbdf3c&site_id=501430&client-request-id=a859f2f4-c659-4382-83b9-70b3dc12fef6&x-client-SKU=ID_NET472&x-client-ver=6.12.2.0&sso_reload=true)** (recommended to open in new Incognito window) to access the lab environment, then use the provided credentials to log in.

![Screenshot 2022-03-29 101135](https://user-images.githubusercontent.com/12828104/160565259-5de2ef9c-82a8-4770-9291-98519c69f40f.png)

2. Use the search bar at the top of the page to navigate to the **Virtual machines** service.

![Screenshot 2022-03-29 101556](https://user-images.githubusercontent.com/12828104/160566299-f7a683a0-d5fc-4071-ac72-53454fc0c223.png)

3. At the **Virtual machines** page, click the **+Create** button, then choose **+ Virtual machine**.

![Screenshot 2022-03-29 102309](https://user-images.githubusercontent.com/12828104/160567258-70fba4f4-a9f1-4ab5-97bb-1958fc4c42f3.png)

4. In the **Create a virtual machine** window, enter the following information under the Basics tab:

- **Resource Group**: Click **Create new**, enter ```pluralsight-resource-group```, then click **OK**.

![Screenshot 2022-03-29 103839](https://user-images.githubusercontent.com/12828104/160570305-4a52470d-2576-4171-9fc5-9c6fee6df70b.png)

- **Virtual machine name**:  ```vm-lab-win001```

- **Region**: Choose **(US) East US** from the dropdown menu. **Note**: In our case we are restricted to (Europe) West Europe.

- **Image**: Choose **Windows Server 2019 Datacenter - Gen2** from the dropdown menu

- **Size**: Select **Standard_DS1_v2 - 1 vcpu, 3.5 GiB memory**.

- **Username**:  ```azurelabadmin```

- **Password**: ```L234FOmdwer#2```

- **Confirm password**:  ```L234FOmdwer#2```

- **Public inbound ports**: Choose **None**.

![Screenshot 2022-03-29 105038](https://user-images.githubusercontent.com/12828104/160573027-913b1a7d-0c76-4aa0-97bf-26b5cea7854e.png)

5. Click **Next: Disks**, then **Next: Networking**.

![Screenshot 2022-03-29 105622](https://user-images.githubusercontent.com/12828104/160574114-fa2e63a6-ecd2-4cf7-879a-d256779a1597.png)

6. On the **Networking** tab under the **Virtual network** dropdown menu, click the **Create new** link.

7. In **Create virtual network**, change the **Name** to ```vnet-lab-001```.

8. In the **Address Space** section, make sure the listed **Address range** is set to ```10.0.0.0/16```.

9. Under **Subnets**, delete the given **default** subnet, then add the following:

- **Subnet name**:  ```snet-lab-001``` 

- **Address range**:  ```10.0.0.0/24``` 

![Screenshot 2022-03-29 110123](https://user-images.githubusercontent.com/12828104/160575585-a39e599e-13ce-45b1-a804-63912307e354.png)

10. Click **Ok**. 

11. Back at the **Networking** tab, under **Public IP**, click **Create new**.

12. In **Create public IP address**, enter the following and then click **OK**.

- **Name**: ```vm-lab-win001-ip``` (This should be entered already for you.) ***Note***: As our policy does not allow exposure to the Public Internet, we choose **None** instead.

- **SKU**: **Standard**

13. For **Public inbound ports**, choose **None**.

![Screenshot 2022-03-29 131040](https://user-images.githubusercontent.com/12828104/160598918-6869886e-16a9-45d6-905d-c8347cce66e8.png)

Networking

![Screenshot 2022-03-29 125704](https://user-images.githubusercontent.com/12828104/160597007-a39e1849-d61b-49cc-a844-fcb4852ac5cc.png)

Management

![Screenshot 2022-03-29 130057](https://user-images.githubusercontent.com/12828104/160597430-4ced05d3-a281-4f46-b055-b2f0c9317a3a.png)

Advanced

![Screenshot 2022-03-29 130423](https://user-images.githubusercontent.com/12828104/160597976-d727f955-e01b-410d-a68b-b9b3d22d7784.png)

Tags

14. Leave the rest of the defaults, and click **Review + create**.

15. In the **Review + create** tab, wait for the **Validation passed** message, then click **Create** to begin the build out of the virtual machine. 

- ***Note***: This process may take a few minutes. As you are waiting for the VM to be built out, you will see all of the other resources being deployed with it including a network security group, public IP, and other resources used by the VM.

![Screenshot 2022-03-29 131604](https://user-images.githubusercontent.com/12828104/160599663-9d334c63-ffe5-4abf-97d1-3fb3cdfd0bb6.png)

Review and Create

16. When your deployment is complete, click on **Go to resource**. This will take you to the ```vm-lab-win001 Overview```.

Review the **Properties** tab and verify the information–such as a **Computer name** of **vm-lab-win001**, and a **Size** of **Standard DS1 v2**–matches the values in the tasks above. You may need to click **Refresh** to get up-to-date information on the Properties tab.

Congratulations! You have deployed your first virtual machine running Windows Server 2019 Datacenter. Creating VMs through the Azure Portal is a quick process as long as you have all of the information you need for size, type, and networking.
