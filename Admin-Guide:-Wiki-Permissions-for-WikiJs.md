WikiJs is EIC network's collaborative knowledge base.  A detailed guide to Wiki.js is available here: https://docs.requarks.io/.


## Home Page permissions
Add permissions in the liquid investigations home page admin to allow groups and users to use the Wiki.js app.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/11wikijs.png" width=200 align=center>
<BR CLEAR=”right” />
<BR CLEAR=”right” />

Log into the Wikijs app and assign group permissions. 

## Group Permissions and Page Rules

### Create Groups
Go to the Admin page by clicking on the settings icon

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/11wikijs.png" width=200 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Go to Groups and create new group. 

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/11wikijs.png" width=200 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Click on the group to assign users.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/11wikijs.png" width=200 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Create a new User and assign to the group.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/11wikijs.png" width=200 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Assign **Global Permissions** to a group; these allow or deny users specific actions on the wiki page. For more details, please check out https://docs.requarks.io/groups

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/11wikijs.png" width=200 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

The permission system is a bit confusing: for each permission, you need to set it both in the "Permissions" group, AND in "Page Rules" for where those permissions can be applied.

Only adding permissions on the 'Permissions' tab does not give default / implicit permissions - it merely allows the 'Page Rules' permissions to actually work.

Caveat: The UI doesn't alert you on this:

* it lets the user to enable some permissions in 'Page Rules' even if the user forgot to enable it under 'Permissions'
* it doesn't warn you after you added permissions under 'Permissions' without ever using them under 'Page Rules'

The Permission Administration should only happen on 1 browser tab. If you have 2 browser tabs open and toggle between 'Permissions' and 'Page Rules', the permissions or rules don't stick.

Admin can control assets permissions (image uploads) with read:asset and write:asset permissions
If users upload assets to the default path / then everyone can see that folder, so the screenshots are not secret anymore
Recommendation: Remove asset:write and page:write permissions from / folder, making users use their own namespaces
