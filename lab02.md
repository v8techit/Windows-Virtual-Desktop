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


