# Dokuwiki Access Control, Permissions, and Group Management


<img align="right" width="40%" src="https://user-images.githubusercontent.com/7493327/208932117-74188222-c933-4ac5-a4ef-a663a9265172.png">


The wiki supports controlling the access for each page and namespace of the wiki. Permissions can be given to individual users or to entire groups.

**Notes**: 
1. Only users marked as "Staff" and "Superuser" in the Liquid Home Page Admin will see this interface.
2. Conversely, any user marked as "Staff" and "Superuser" in the Liquid Home Page Admin will have potential access to the whole wiki, both secret and public: they can give themselves access to any page.
3. The Wiki Groups themselves are independent of the rest of the system. If you create a group in the "Liquid Home Page" app, it will not be synced here, so the user needs to be given access to users and groups separately from the home page or Hoover.



<br clear="both"/>


## The Admin Pages

<img align="right" width="40%" 
src="https://user-images.githubusercontent.com/7493327/208906880-4d05bf55-a55a-4ce0-b8cd-0fe13d70abf6.png"></img>

On the right is a screenshot of the admin page, with interesting links highlighted.


There are two interesting interfaces here: "Virtual Groups" and "Access Control Lists". Virtual Groups is used for creating and handling groups, while the ACL page controls what users and groups have the following permissions:  `Read  Edit  Create  Upload  Delete`

<br clear="both"/>

---

### Virtual Groups: Manage Wiki Groups

<img align="right" width="40%"
src="https://user-images.githubusercontent.com/7493327/208912439-3a54ab17-b884-4f90-85a4-41cc52316da7.png"></img>



You will find a couple of simple forms, as shown on the right. Using either one, you can add new groups to the system, and link existing users to groups.

**Warning**: This page does not check if the usernames are actually valid in the system - please double-check the correct username is set. When possible, use copy/paste from Liquid Home Page instead of manually writing the username, to avoid errors.

<br clear="both"/>

---

### Access Control Lists: Manage Wiki Permissions

<img align="right" width="40%" src="https://user-images.githubusercontent.com/7493327/208913060-5e766721-230d-478f-9cbf-33d5abb50047.png"></img>


This page allows you to configure access for each page/namespace, either for a specific user or for an entire group.
You can also set the default permission set (the `*` namespace).

More information on the ACL system, including examples, can be found in the [Dokuwiki Documentation on Access Control](https://www.dokuwiki.org/acl#acls_by_example).

**Warning**: This page form does not check if the groups are actually valid in the system - please double-check the correct group is set. When possible, use copy/paste from the Virtual Group manager instead of manually writing the group name, to avoid errors.
