# Create and configure an Azure Active Directory Domain Services managed domain
Azure Active Directory Domain Services (Azure AD DS) provides managed domain services such as domain join, group policy, LDAP, Kerberos/NTLM authentication that is fully compatible with Windows Server Active Directory. You consume these domain services without deploying, managing, and patching domain controllers yourself. Azure AD DS integrates with your existing Azure AD tenant. This integration lets users sign in using their corporate credentials, and you can use existing groups and user accounts to secure access to resources.

You can create a managed domain using default configuration options for networking and synchronization, or manually define these settings. This tutorial shows you how to use default options to create and configure an Azure AD DS managed domain using the Azure portal.

1. Login to you Azure Portal.

**Note** Make sure you login with the user we created in Lab 01

2. On the Azure Portal menu, select **Create a resource**
3. Enter *Domain Services* into the search bar, then choose *Azure AD Domain Services* from the search suggestions.
4. Click **Create**

<img src = "https://github.com/v8techit/WVD/blob/master/Media/ADDS.png"/>

5. Make sure the correct subscription is selected
6. Select the Resource group to which the managed domain should belong or choose to create a new resource group.
7. Fill in the **Project details** 
    
    a. **DNS Domain Name:** leave this to the default. It should be your domainname. (i.e. demo.onmicrosoft.com)
    
    b. **Region:** Make sure you deploy ADDS in the same Region where you want to deploy Windows Virtual desktop. (i.e. West Europe)
    
    c. **SKU:** For this lab choose the **Standard tier**
    
    d. **Forest type:** Leave it to default (user)
    
    <img src = "https://github.com/v8techit/WVD/blob/master/Media/ADDS_projectdetails.PNG"/>

8. Click **Next**

9. On the Networking tab leave it to default and click **Next**

10. On the **Administation Page** click *Manage group membership*

11. In the Manage group membership page click **Add Members**

12. Select the user you are currently logged in with (This should be the user created in Lab01)

13. Click **Select**

<img src ="https://github.com/v8techit/WVD/blob/master/Media/add_member.PNG"/>

14. Once the user is added on top of the page click **Create Azure AD Domain Services** to return to the wizard

<img src = "https://github.com/v8techit/WVD/blob/master/Media/back_wizzard.png"/>

15. On the **Administration** page click next

16. On the Syncronization page make sure the **Synchronization type** is set to **All**

17. Click **Next**

18. After the validation is completed click **Create**

19. On the **You should know...** Click **OK**

**Note:** Creation of the managed domain can take **up to an hour**

*When the managed domain is fully provisioned, the **Overview** tab shows the domain status as **Running***

<img src = "https://github.com/v8techit/WVD/blob/master/Media/add-ds_deployed.PNG"/>


# Update DNS settings for the Azure Virtual Network

With Azure AD DS successfully deployed we can now configure some necessary settings. One of those settings is to configure the Virtual Network to allow other connected VMs and applications to use the managed domain. To get this connectivity, we need to update the DNS server settings for the Virtual Network to point to the two IP Addresses where the managed domain is deployed.

1. In the **overview** tab you will see some **Required Configuration steps**. The first step is to update DNS server settings for the Virtual Network. 

*Note: Once this step is completed, it will no longer show on the overview page*

2. To update the DNS server settings, select the **Configure** button

<img src = "https://github.com/v8techit/WVD/blob/master/Media/dns_configure.PNG" />

# Enable user accounts for Azure AD DS

In order to authenticate users on the managed domain, AD DS needs password hashes in a format that can work with NTLM and Kerberos authentication. 
We are working with Cloud-only users accounts. Those accounts are saved in Azure AD. Azure AD doesn't generate or store password hashes that can be used with NTLM or Kerberos. 
The steps to generate and store these password hashes is a user interaction. 

User must change their password before they can use Azure AD DS. This password change process causes the password hasshes for Kerberos and NTLM authentication to be generated and stored in Azure AD. 
The User account isn't synchronized from Azure AD to Azure AD DS until the password is changed. 
So we have **two options:**

- Either expire the password for all cloud users, which will force a password change
- or instruct user to manually change their passwords. 

We will manually change the password for our lab user (the user we created in Lab01)

1. go to the Azure AD Access Panel page at https://myapps.microsoft.com
2. In the top-right corner, select your name, then choose **Profile** from the drop-down menu

<img src = "https://github.com/v8techit/WVD/blob/master/Media/password_change.png" />

3. on the **Profile** page select **Change Password**
4. on the **Change password** page, enter your existing password, then enter and confirm a new password
5. Select **Submit**

<img src = "https://github.com/v8techit/WVD/blob/master/Media/changepassword3.png" />

**Note:** it takes a few minutes before the password is usable in Azure AD DS. 

We are now done with setting up Azure AD DS. This managed domain will be used when we deploy Windows Virtual Desktop. 






