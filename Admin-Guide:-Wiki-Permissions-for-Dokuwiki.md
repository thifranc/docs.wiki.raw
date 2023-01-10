The wiki allows for access control for each page and namespace of the wiki. Permissions can be given to individual users or to entire groups.

<img src="https://user-images.githubusercontent.com/7493327/208932117-74188222-c933-4ac5-a4ef-a663a9265172.png" width=800 align=center>
<BR CLEAR=”right” />


**Notes**: 
* Only users marked as "Staff" and "Superuser" in the Liquid Home Page Admin will see this interface.
*  Any user marked as "Staff" and "Superuser" in the Liquid Home Page Admin will have potential access to the entire wiki, both secret and public: they can give themselves access to any page.
* The Wiki Groups themselves are independent of the rest of the system. If you create a group in the "Liquid Home Page" app, it will not be synced here, so the user needs to be given access to users and groups separately from the home page or Hoover.



<br clear="both"/>


## The Admin Pages

Here is a screenshot of the admin page, highlighting potential links of interest.

<img src="https://user-images.githubusercontent.com/7493327/208906880-4d05bf55-a55a-4ce0-b8cd-0fe13d70abf6.png" width=800 align=center>
<BR CLEAR=”right” />

There are two interesting interfaces here: 'Virtual Groups' and 'Access Control Lists':
* 'Virtual Groups' is used for creating and handling groups; 
* The 'Access Control Lists' page controls what users and groups have the following permissions:  `Read  Edit  Create  Upload  Delete`.

<br clear="both"/>

---

### 'Virtual Groups': Manage Wiki Groups

Use either of these simple forms, to add new groups to the system, and link existing users to groups.

<img src="https://user-images.githubusercontent.com/7493327/208912439-3a54ab17-b884-4f90-85a4-41cc52316da7.png" width=800 align=center>
<BR CLEAR=”right” />


**Warning**: This page does not check if the usernames are actually valid in the system, so please double-check if the correct username is set. To avoid any errors, please copy/paste the username from the Liquid Home Page instead of manually writing it.

<br clear="both"/>

---

### 'Access Control Lists': Manage Wiki Permissions

This page allows you to configure access for each page/namespace, either for a specific user or for an entire group.
You can also set the default permission set (the `*` namespace).

<img src="https://user-images.githubusercontent.com/7493327/208913060-5e766721-230d-478f-9cbf-33d5abb50047.png" width=800 align=center>
<BR CLEAR=”right” />

More information on the 'Access Control Lists' system, including examples, can be found here: [Dokuwiki Access Restrictions](https://www.dokuwiki.org/acl#access_restrictions), [Access Control Examples](https://www.dokuwiki.org/acl#acls_by_example).

**Warning**: 
* This page form does not check if the groups are actually valid in the system, so please double-check the correct group is set. When possible, use copy/paste from the Virtual Group manager instead of manually writing the group name, to avoid errors.
* Do NOT use the default groups called `user`, `admin` or `user,admin` (this last one is a result of a bug). You can, however, use the `ALL` group as specified in the [Dokuwiki Access Restrictions Documentation](https://www.dokuwiki.org/acl#access_restrictions), or your own custom groups from the Virtual Group Manager.