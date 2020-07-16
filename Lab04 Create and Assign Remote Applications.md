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











