## Prerequisites

### Enable Automatic Time Sync settings on phone

Before installing an authenticator, please enable the automatic time sync on your mobile phone or other device.

Here is how you can do it on your Iphone:
Go to Settings > General > Date & Time > Set Automatically

<img src="https://github.com/liquidinvestigations/docs-img/blob/main/Iphonedatetime.png" width=300 align=center>
<BR CLEAR=”right” />

<BR CLEAR=”right” />
Here is how you do it on your MAC OS: 
Open the Date & Time Preferences and check the the 'set time zone automatically using current location' box

<BR CLEAR=”right” />

<BR CLEAR=”right” />
<img src="https://github.com/liquidinvestigations/docs-img/blob/main/MacOS_3.png" width=400 align=center>

<BR CLEAR=”right” />

<BR CLEAR=”right” />

Additionally please check your time settings by opening https://time.is/ on the device that has the authenticator and see the text "Your time is exact!" and error under 5 seconds

Look at potential time differences here: http://browserspy.dk/date.php and look at "Difference between server and PC time".

Have one of the following apps installed: Google Authenticator, Authy, Duo Mobile
Be ready to receive your on boarding code per pgp or per Signal.

## Add new user to the Liquid bundle:

---

### [admin]


In the Liquid Investigations home page, click the right top menu button and go to `[admin]`.

<img src="https://user-images.githubusercontent.com/7493327/209174206-9bbe729c-b4b8-4f3e-b9f9-ccb0c688e2cb.png" width=400 align=center>



---

*Reminder*: Make sure to manage the user creation and invitations process from the "Liquid Investigations" home page `[admin]` interface, and not from the Hoover admin interface. Both have the same theme, so there might be some confusion.

---

### Add User

* Click on the green +Add, on the left side of Users; OR
* Click on ADD USER + button on the right;

<img src="https://user-images.githubusercontent.com/7493327/209175404-0e10946e-3a1e-46e9-98a9-1fa70552700e.png" width=800 align=center>


---

### Set Username and Initial Password

* Add the username and password using the firstname.lastname convention;
* Make sure not to use use **“-”**;
* If the username is taken, you'll get an error (add surname or change order).

<img src="https://user-images.githubusercontent.com/7493327/209176305-05c4556f-f062-4ab6-9068-5caf43e0f1f3.png" width=800 align=center>

**Note**: When 2FA is enabled, the admin cannot use this initial password to enter into the account; Use some random text twice, and
create the invitation link afterwards. The user will not need this initial password to use the link.



---

### Edit User details

* On the 'First name' field please enter the entire name (both first and last name);

* On the 'Last name' field please enter the name of the media organization;

* On the 'Email address' field please enter the user's email;

All the other fields are to be left to default.

* Click 'Save', bottom right.

---

### Random Username

If the intention is to anonymize everyone, the admin can use a couple of random dictionary words for the usernames. For example, on Linux or macOS, you can use this terminal command to sample [the words file on your machine](https://en.wikipedia.org/wiki/Words_(Unix)):

```
$ cat /usr/share/dict/words | grep -E '^[A-Za-z]+$' | sort | uniq | sort -R | head -n2 | xargs -n2 printf '%s.%s\n'

refulgence.blended
```

---

## Onboard user (and 2FA Re-invite process)


* The user should have executed all the Prerequisites (without admin privilege);
* Go to Users in the Liquid Investigations home page `[admin]` interface (as shown in first screenshot above), type in the username and click Search;
* Click the checkbox to select the user that you intend to onboard;
* On Action dropdown menu, select 'Create invitations' and click Go.

<img src="https://user-images.githubusercontent.com/7493327/209174791-dc88fc73-1ffb-4d8c-9961-c9f60f8a9272.png" width=800 align=center>


* Send the generated Url to the user via encrypted email only.

<img src="https://user-images.githubusercontent.com/7493327/209174974-a18c3fd2-a126-4e3a-8306-22df2b85e494.png" width=800 align=center>

* Send these pages to the user along with the invite link:
- https://github.com/liquidinvestigations/docs/wiki/User-Guide%3A-Login
- https://github.com/liquidinvestigations/docs/wiki/User-Guide%3A-Manage-2FA-Devices

**Warning**: The link will be valid for 30 minutes and a single use, repeat this process if it expires. Do not open it yourself, else it will expire. 

* Caution if using Web Services like Whatsapp, Facebook Messenger, Signal, Slack, Gmail, Sheets or Excel: they will visit the link to give you a "preview", and it will expire. 

Instructions for disabling link previews in Signal are shown in the [User Guide: Login](https://github.com/liquidinvestigations/docs/wiki/User-Guide%3A-Login) page linked above.


---
Back to [User Guide](https://github.com/liquidinvestigations/docs/wiki/User-Guide)
