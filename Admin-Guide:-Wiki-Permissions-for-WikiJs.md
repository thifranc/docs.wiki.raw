WikiJs is EIC network's collaborative knowledge base.  A detailed guide to Wiki.js is available here: https://docs.requarks.io/.


## Home Page permissions
Add permissions in the liquid investigations home page admin to allow groups and users to use the Wiki.js app.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs1.png" width=800 align=center>
<BR CLEAR=”right” />
<BR CLEAR=”right” />


<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs2.png" width=800 align=center>
<BR CLEAR=”right” />
<BR CLEAR=”right” />


Log into the Wikijs app and assign group permissions. 

## Group Permissions and Page Rules

### Create Groups
Go to the Admin page by clicking on the settings icon

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs3.png" width=200 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Go to Groups and create new group. 

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs4.png" width=800 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Click on the group of your choice to assign users.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs5.png" width=800 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Create a new User (if needed) and assign to the respective group.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs6.png" width=600 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Assign **Permissions** to a group; these allow or deny users specific actions on the wiki page.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs.7.png" width=800 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

Assign **Page Rules** to a group; A page rule specifies exactly where permissions are applicable.

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/adminwikijs8.png" width=800 align=center>

<BR CLEAR=”right” />
<BR CLEAR=”right” />

The 'Permissions' and 'Page Rules' system is a bit confusing: each permission should be enabled in the 'Permissions' tab as well as in the 'Page Rules' tab, to make sure all these permissions will be applied. 

Only adding permissions on the 'Permissions' tab does not give default / implicit permissions - it merely allows the 'Page Rules' permissions to actually work.

Caveat: The UI doesn't alert you on this:

* it lets the user to enable some permissions in 'Page Rules' even if the user forgets to enable them in'Permissions'
* it doesn't warn the user after permissions were added under'Permissions' without ever using them under 'Page Rules'

The Permission administration should only happen on 1 browser tab. If you have 2 browser tabs open and toggle between 'Permissions' and 'Page Rules', the permissions or rules don't stick.

For more details around 'Permissions' and 'Page Rules', please check out https://docs.requarks.io/groups

### Asset permissions
An admin can control assets permissions (image uploads) with  `read:asset` and `write:asset` permissions.

If users upload assets to the default path / then everyone can see that folder, so the screenshots are not secret anymore
<BR CLEAR=”right” />
<BR CLEAR=”right” />
Recommendation: Remove `asset:write` and `page:write` permissions from / folder, making users use their own namespaces


