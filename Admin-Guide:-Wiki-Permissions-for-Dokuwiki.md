DokuWiki allows for access control for each page and namespace of the wiki. Permissions can be given to individual users or to entire groups.
Admin permissions will be assigned in both the Liquid Core Admin page as well as in the DokuWiki Admin pages.

## Liquid Core Admin interface

1.  Go to Liquid Admin

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/1.png" width=800 align=center>
<BR CLEAR=”right” />


2. Under 'Groups' click the green plus sign to create the group of your choice.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/2.png" width=800 align=center>
<BR CLEAR=”right” />


3. Name your group and assign the desired permissions by selecting the checkmarks next to the apps

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/3.png" width=800 align=center>
<BR CLEAR=”right” />


4. A list of the groups that you created will be displayed under 'Groups', each having access to the different available apps

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/4.png" width=800 align=center>
<BR CLEAR=”right” />


5. Go to Liquid Admin under Users and create a User and assign it to a Group

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/5.png" width=1000 align=center>
<BR CLEAR=”right” />


6. When creating a user, you can assign the user to a specific group

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/6.png" width=1000 align=center>
<BR CLEAR=”right” />



In this example, the user test.1 is part of the toto_cutugno and celentano groups


7. A list of the created users and their respective group membership will be displayed in the Users view

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/7.png" width=800 align=center>
<BR CLEAR=”right” />




**Notes**: 
* Only users marked as "Staff" and "Superuser" in the Liquid Home Page Admin will see this interface.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/13.png" width=800 align=center>
<BR CLEAR=”right” />




*  Any user marked as "Staff" and "Superuser" in the Liquid Home Page Admin will have potential access to the entire wiki, both secret and public: they can give themselves access to any page.



<br clear="both"/>


## DokuWiki Admin interface
The Wiki Groups themselves are independent of the rest of the system. If you create a group in the 'Liquid Core Admin' page, it will not be synced here, so the user needs to be given access to users and groups separately from the home page or Hoover.

1. Navigate to the DokuWiki App, to the Admin interface

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/8.png" width=800 align=center>
<BR CLEAR=”right” />


### 'Virtual Groups': Create and manage wiki groups

2. Select 'Virtual Groups' 

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/9.png" width=800 align=center>
<BR CLEAR=”right” />


3. Use these simple forms, to add new groups to the system, and link existing users to groups.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/10.png" width=800 align=center>
<BR CLEAR=”right” />


**Caveat**: This page does not check if the usernames are actually valid in the system, so please double-check if the correct username is set. To avoid any errors, please copy/paste the username from the Liquid Core Admin page instead of manually writing it.

<br clear="both"/>


### 'Access Control Lists'

To see this mage, you must have `Superuser` permission.

This page controls what users and groups have the following permissions:  `Read  Edit  Create  Upload  Delete`. It allows you to configure access for each page/namespace, either for a specific user or for an entire group.
You can also set the default permission set (the `*` namespace).

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/11.png" width=800 align=center>
<BR CLEAR=”right” />

When managing group access permissions, you can assign different levels of permissions, with 'None' being the most limiting access level and  'Delete' being the most permissive level, depending on each use case. 

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/WikiPermissions/12.png" width=800 align=center>
<BR CLEAR=”right” />

More information on the 'Access Control Lists' system, including examples, can be found here: [Dokuwiki Access Restrictions](https://www.dokuwiki.org/acl#access_restrictions), [Access Control Examples](https://www.dokuwiki.org/acl#acls_by_example).

## Pre-defined Groups: ALL, admin

You can make use of the following groups created automatically:
- `ALL` and `user` - both contain all users of the wiki.
- `admin` - contains people with Admin access (marked as Staff in Liquid Home Page). However, they cannot access the Virtual Group or ACL pages.
- `superuser` - contains all people with Superuser access (marked as Superuser in Liquid Home Page)


### The Superuser permission model

Accounts marked as `Superuser` in the Liquid Home page (and automatically added to the `superuser` group in DokuWiki) are the only accounts that can access the Virtual Group Manager and the ACL Manager. They are not restricted by the ACLs they create. This means they can view, edit, move, delete any page, in any namespace.

Because of their elevated access, these accounts should only be used by people with direct access to the servers, for maintenance and fixing permissions.

See [Dokuwiki Access Restrictions Documentation](https://www.dokuwiki.org/acl#access_restrictions) for more details.

## Warnings 
* The Virtual Manager and ACL forms do not check if the groups and usernames are actually valid in the system, so please double-check the correct group is set. When possible, use copy/paste from the Liquid Home Page / Virtual Group manager instead of manually writing the user/group name, to avoid errors.
* When setting up permissions for deep namespaces, do NOT set higher permissions for the deeper namespaces than the ones above. Doing so will break the Sitemap page for the users where this happens. See [sneaky_index](https://www.dokuwiki.org/config:sneaky_index) for more details.