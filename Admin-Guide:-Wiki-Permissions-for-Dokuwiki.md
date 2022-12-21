# Dokuwiki Access Control, Permissions, and Group Management


<img align="right" width="40%" 
src="https://user-images.githubusercontent.com/7493327/208906880-4d05bf55-a55a-4ce0-b8cd-0fe13d70abf6.png"></img>

The wiki supports controlling the access for each page and namespace of the wiki. Permissions can be given to individual users or to entire groups.

**Note**: The Wiki Groups here are independent from the rest of the system. If you create a group in the "Liquid Home Page" app, it will not be synced here, so the user needs to be onboarded separately.

## The Admin Pages


On the right is a screenshot of the admin page, with interesting links highlighted.


There are two interesting interfaces here: "Virtual Groups" and "Access Control Lists". Virtual Groups is used for creating and handling groups, while the ACL page controls what users and groups have the following permissions:  `Read  Edit  Create  Upload  Delete`

---

### Virtual Groups: Manage Wiki Groups


You will find a couple of simple forms, as shown on the right. One can connect users to groups, or create new groups for some users.

**Warning**: This page does not check if the usernames are actually valid in the system - please double-check the correct username is set. When possible, use copy/paste instead of manually writing the username, to avoid errors.

---

### Access Control Lists: Manage Wiki Permissions