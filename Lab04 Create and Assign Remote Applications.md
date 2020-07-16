# Create a RemoteApp group

1. Return to the Azure Portal an login when needed.
2. Search for and select **Windows Virtual Desktop**
3. In The Windows Virtual Desktop page select **Application Groups** in the left menu

<img src ="https://github.com/v8techit/WVD/blob/master/Media/wvd7.png"/>

You should already have one Application Security Group. This is defeault group, which was created when we deployed the host pool.

4. Click **Add** on top of the page.
5. On the **Basics** tab make sure you subscription is selected
6. Choose an existing Resourcegroup or Create a new one.
7. You hostpool should already be selected. This is the host pool we created earlier.
8. **location** is the location where you metadata is stored.
9. **Application group type** Select **RemoteApp**

**Note:** As you can see the Desktop option is grayed out. We already have a Desktop group is this host pool. Only one Desktop group per host pool is allowed.

10. **Application group name** Enter a unique name for your application group.

<img scr = "https://github.com/v8techit/WVD/blob/master/Media/wvd8.PNG" />

11. Click **Next:Assignments**

12. On the **Assignments** tab you can add users or AD groups. Those users (or groups) will have access to the Remote Apps.

13. Click **Add Azure AD users or user Groups** and add yourself to this Application Group.
14. Click **Next: Applications**
15. On the **Applications** tab click **Add applications**

We have the option to add applications from the Windows Startmenu, or we can provide our own filepath where the application is located.

<img src ="https://github.com/v8techit/WVD/blob/master/Media/wvd9.PNG"/>

16. In the **Add application** Select **Start menu**
17. **Application**: Outlook
18. **Display name:** Leave default
19. **Description** Outlook for endusers
20. **Require command line** No
21. Click **Save**

**Note:** If you want to add more apps, repeat step 16 - 21 

<img src = "https://github.com/v8techit/WVD/blob/master/Media/wvd10.PNG" />

22. Click **Next:Workspace**
23. Next to **Register application group** click **yes**
24. Click **Next:tags**
25. Click **Review and Create**

After the validation is passed click **Create**

Creation of the Application Group can take a couple of minutes.

26. After the Application group is deployed you can test if the user can access the application
27. Go to: https://rdweb.wvd.microsoft.com/arm/webclient/ 
28. Logon with the user account that is assigned to the application group.

<img src = "https://github.com/v8techit/WVD/blob/master/Media/wvd11.PNG" />


















