# Perform the Microsoft.DesktopVirtualization resource provider registration

1. Login to the Azure Portal with the user we created in Lab01
2. In the portal go to your Subscription

<img src = "https://github.com/v8techit/WVD/blob/master/Media/subscription1.png" />

3. In your subscription search for **Resource Providers**

<img src ="https://github.com/v8techit/WVD/blob/master/Media/subscription2.png"/>

5. In the **Resource Providers** Search for **Desktop Virtualization**

<img src ="https://github.com/v8techit/WVD/blob/master/Media/subscription3.png" />

6. Make sure that Microsoft.DesktopVirtualization is Registered. If this provider is not Registered. Select Microsoft.DesktopVirtualization and click **Register** on top of the page.

**Note:** Registering can take a couple of minutes.

*After the provider is registered we can continue to deploy Windows Virtual Desktop*

# Create your host pool

Host pools are a collection fo one or more identical VMs within the WVD enviroments. Each host pool can contain an app group that users can interact with as they would on a physical desktop. 
In the following steps we will create an host pool via de Azure Portal. 

When you create a Windows Virtual Desktop host pool, you can create a VM from the Azure gallery, a managed image, or an unmanaged Image. 
In this lab we will use a Azure gallery image. In later labs we will use a custom image in a host pool.

1. Sign in to the Azure portal with the user we create in Lab01
2. Enter **Windows Virtual Desktop** into the search bar and select **Windows Virtual Desktop**

<img src ="https://github.com/v8techit/WVD/blob/master/Media/wvd1.png"/>

3. In the **Windows Virtual Desktop** overview page, select **Create a host pool**

<img src ="https://github.com/v8techit/WVD/blob/master/Media/wvd2.PNG"/>

4. On the **Basics** tab make sure the correct subscription is select
5. Select an existing Resource Group, or Create a new one
6. **Host Pool Name**: Make sure you enter a uniek name for your Host Pool
7. **Location:** This is the location where you metadata will be stored. C
8. **Host Pool Type** Choose **Pooled**
9. **Max Session Limit** 4
10. **Load Balancing algrorithm** Breadt-first

<img src = "https://github.com/v8techit/WVD/blob/master/Media/wvd3.PNG" />

11. Click **Next: Virtual Machines**

12. **Add virtual machines** select yes
13. **Resource group** Select an existing resource group
14. **Virtual Machine Location** Select the location where you VMs should be deployed (i.e. West Europe)

**Note: Make sure you choose the same location as you Azure AD DS. If you choose another location will not be able to connect to the Virtual Network of Azure AD DS**

15. **Virtual Machine Size** Leave to default
16. **Numbers of VMs** 1 *When you are using an Azure Sponsorship you vCPU limit is 10*
17. **Name Prefix** Enter an unique name for the host
18. **Image Type** Gallery
19. **Image**  Windows 10 Enterprise multi-session, Version 1909 + Microsoft 365 Apps for enterprise 
20.  **OS disk type** Standard SSD
21. **Virtual Network** Choose the network we created earlier when we deployed Azure AD DS
22. **Subnet** Leave to default
22. **Public IP** No
23. **Network Security Group** Basic
24. **Public Inbound Ports** No
25. **Specify domain or unit** No
26. **AD domain join UPN** Use the user we created in Lab01
27. **Password** Fill in the password
28. **Confirm Password** Confirm the password

<img src = "https://github.com/v8techit/WVD/blob/master/Media/wvd4.png"/>

29. Click **Next: Workspace**

The Host pool setup process creates a desktop application group by default. For the host pool to work correctly, we need to publish this app group to users or user groups, and you must register the app group to a workspace. 
We have the ability to select no at this moment, so we can register the app group later. Microsofts recommmendation is to register the app group as soons as possible. 

30. On the Workspace tab next to **Register desktop app group** click **yes**
31. **To this workspace** Select create new. Fill in a unique name and click ok.

<image src = "https://github.com/v8techit/WVD/blob/master/Media/wvd5.PNG"/>

32. Click **Next:Tags**
33. Click **Review + create**
34. After validation passed click **Create**

You Host Pool wil now be created. This can take a couple of minutes. 
**Note:** Do not continue until you host pool is created

# Add a user to your Application Group

The default app group created for a New Windows Virtual Desktop host pool also publishes the full desktop. In order to give users access to this desktop you need to add them to the app group.

1. In the Windows Virtual Desktop Overview page Select **Application groups**
2. Select your created application group
3. Under **Manage** Select **Assignments**
4. In the **Assignments** tab click **Add** on the top of the page
5. Search for your user (you can use the user we created in Lab01)
6. Click **Select**

<image src ="https://github.com/v8techit/WVD/blob/master/Media/wvd6.PNG"/>

7. To test user access go to: https://rdweb.wvd.microsoft.com/arm/webclient/
8. Login with the correct user

**Note** It can take a couple of minutes before the user is able to connect. If connection fails refresh the page an try it again.


            











