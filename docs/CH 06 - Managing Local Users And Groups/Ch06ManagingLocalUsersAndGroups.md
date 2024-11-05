---
title: Chapter 6 Managing Local Users and Groups
author: Marko Shaffer
date: 2023-06-11 11:00:00 +0800
categories: [Red Hat System Administration I, Linux Fundamentals - ITEC 200]
tags: [Linux, Red Hat, System Administration, ITEC200]     # TAG names should always be lowercase
---
[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)

# Chapter 6: Managing Local Users and Groups
> Red Hat System Administration I 8.2
>
> Information Technology, Franklin University
>
> ITEC 200: Linux Fundamentals
>
> Professor Kagan Ulucay
>
> 6/11/2023

## Outcomes:
> In this lab you will set a default local password policy, create a supplementary group for three users, allow that group to use sudo to run commands as root, and modify the password policy for one use
> 
> - Set a default password aging policy of the local user's password.
> 
> - Create a group and use the group as a supplementary group for new users.
> 
> - Create three new users with the new group as their supplementary group.
> 
> - Configure the group members of the supplementary group to run any command as any user using **sudo**.
> 
> - Set a user-specific password aging policy.

## Workstation Login:
Log in to workstation as student using student as the password.

|          | Franklin VM: | Standard User Account: | The Student's Root Account: |
|----------|--------------|------------------------|-----------------------------|
| Username | kiosk        | student                | root                        |
| Password | redhat       | student                | redhat                      |

```bash
[kiosk@foundation0 ~]$ rht-vmctl start all
[kiosk@foundation0 ~]$ rht-vmview view workstation
```

On workstation, run the **lab edit-review start** command.

```bash
[student@workstation ~]$ lab users-review start
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image1.png)

## How TO:
1.  From workstation, open an SSH session to serverb as student.

```bash
[student@workstation ~]$ ssh student@serverb
...output omitted...
[student@serverb ~]$
```
![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image2.png)


2.  On serverb, ensure that newly created users have passwords that must
    be changed every 30 days.

    1.  Set PASS_MAX_DAYS to 30 in /etc/login.defs. Use administrative
        rights while opening the file with the text editor. You can use
        the **sudo vim /etc/login.defs** command to perform this step.
        Use student as the password when **sudo** prompts you to enter
        the student user's password.

```bash
...output omitted...

# Password aging controls:
#
# PASS_MAX_DAYS Maximum number of days a password may be used.
# PASS_MIN_DAYS Minimum number of days allowed between password changes.
# PASS_MIN_LEN Minimum acceptable password length.
# PASS_WARN_AGE Number of days warning given before a password expires.
#
PASS_MAX_DAYS 30
PASS_MIN_DAYS 0
PASS_MIN_LEN 5
PASS_WARN_AGE 7

...output omitted...
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image3.png)


![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image4.png)


![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image5.png)


3.  Create the new group called consultants with a GID of 35000.

```bash
[student@serverb ~]$ sudo groupadd -g 35000 consultants
```
![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image6.png)

4.  Configure administrative rights for all members of consultants to be
    able to execute any command as any user.

    1.  Create the new file /etc/sudoers.d/consultants and add the
        following content to it. You can use the **sudo vim
        /etc/sudoers.d/consultants** command to perform this step.

```bash
%consultants ALL=(ALL) ALL
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image7.png)


![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image8.png)


5.  Create the consultant1, consultant2, and consultant3 users
    with consultants as their supplementary group.

```bash
[student@serverb ~]$ sudo useradd -G consultants consultant1
[student@serverb ~]$ sudo useradd -G consultants consultant2
[student@serverb ~]$ sudo useradd -G consultants consultant3
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image9.png)

6.  Set the consultant1, consultant2, and consultant3 accounts to expire
    in 90 days from the current day.

    1.  Determine the date 90 days in the future. You may get a
        different value as compared to the following output based on the
        current date and time of your system.

```bash
[student@serverb ~]$ date -d "+90 days" +%F
2019-04-28
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image10.png)

2.  Set the account expiry date of the consultant1, consultant2,
    and consultant3 accounts to the same value as determined in the
    preceding step.

```bash
[student@serverb ~]$ sudo chage -E *2019-04-28* consultant1
[student@serverb ~]$ sudo chage -E *2019-04-28* consultant2
[student@serverb ~]$ sudo chage -E *2019-04-28* consultant3
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image11.png)

7.  Change the password policy for the consultant2 account to require a
    new password every 15 days.

```bash
[student@serverb ~]$ sudo chage -M 15 consultant2
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image12.png)

8.  Additionally, force the consultant1, consultant2,
    and consultant3 users to change their passwords on the first login.

    1.  Set the last day of the password change to 0 so that the users
        are forced to change the password whenever they log in to the
        system for the first time.

```bash
[student@serverb ~]$ sudo chage -d 0 consultant1
[student@serverb ~]$ sudo chage -d 0 consultant2
[student@serverb ~]$ sudo chage -d 0 consultant3
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image13.png)

2.  Log off from serverb.

```bash
[student@serverb ~]$ exit
logout
Connection to serverb closed.
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image14.png)

## Evaluation:

> On workstation, run the **lab users-review grade** command to confirm
> success of this exercise.

```bash
[student@workstation ~]$ lab users-review grade
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image15.png)

## Finish

> On workstation, run **lab users-review finish** to complete this lab.
> This script deletes the user accounts and files created throughout the
> lab to ensure that the environment is clean.

```bash
[student@workstation ~]$ lab users-review finish
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingLocalUsersAndGroups/image16.png)

> This concludes the lab.

[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)
