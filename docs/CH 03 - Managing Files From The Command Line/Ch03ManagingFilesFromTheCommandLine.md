---
title: Chapter 3 Managing Files from the Command Line Lab
author: Marko Shaffer
date: 2023-05-28 11:00:00 +0800
categories: [Red Hat System Administration I, Linux Fundamentals - ITEC 200]
tags: [Linux, Red Hat, System Administration, ITEC200]     # TAG names should always be lowercase
---
[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)

# Chapter 3: Managing Files from the Command Line Lab
> Red Hat System Administration I 8.2
>
> Information Technology, Franklin University
>
> ITEC 200: Linux Fundamentals
>
> Professor Kagan Ulucay
>
> 5/28/2023

## Outcomes:

> In this lab, you will efficiently create, move, and remove files and
directories by using the shell and a variety of file name matching
techniques.
>
> - Use wildcards to locate and manipulate files.

## Workstation Login:

> Log in to workstation as student using student as the password.

|          | Franklin VM: | Standard User Account: | The Student's Root Account: |
|----------|--------------|------------------------|-----------------------------|
| Username | kiosk        | student                | root                        |
| Password | redhat       | student                | redhat                      |

> On workstation, run the **lab files-review start** command. The command
runs a start script that determines if the serverb machine is reachable
on the network.

```bash
[student@workstation ~]$ lab cli-review start
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image1.png)

## How To:
1.  Use the **ssh** command to log in to serverb as the student user.
    The systems are configured to use SSH keys for authentication, and
    therefore a password is not required.

```bash
[student@workstation ~]$ ssh student@serverb
...output omitted...
[student@serverb ~]$
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image2.png)

2.  Before you create project files, use the **mkdir** command with
    brace expansion to create empty project planning documents in
    the /home/student/Documents/project_plans directory. (Hint:
    if ~/Documents does not exist, the -p option for
    the **mkdir** command will create it.)

> Create two empty files in the ~/Documents/project_plans directory: season1_project_plan.odf and season2_project_plan.odf.

```bash
[student@serverb ~]$ mkdir -p ~/Documents/project_plans]
[student@serverb ~]$ touch ~/Documents/project_plans/{season1,season2}\_project_plan.odf]
[student@serverb ~]$ ls -lR Documents/]
Documents/:
total 0
drwxrwxr-x. 2 student student 70 Jan 31 18:20 project_plans
Documents/project_plans:
total 0
-rw-rw-r--. 1 student student 0 Jan 31 18:20 season1_project_plan.odf
-rw-rw-r--. 1 student student 0 Jan 31 18:20 season2_project_plan.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image3.png)

3.  Create sets of empty practice files to use in this lab. If you do
    not immediately recognize the intended shell expansion shortcut, use
    the solution to learn and practice. Use shell tab completion to
    locate file path names easily.

> Create a total of 12 files with names tv_seasonX_episodeY.ogg.
> Replace *X* with the season number and *Y* with that season's episode,
> for two seasons of six episodes each.

```bash
[student@serverb ~]$ touch tv_season{1..2}\_episode{1..6}.ogg]
[student@serverb ~]$ ls tv\*
tv_season1_episode1.ogg tv_season1_episode5.ogg tv_season2_episode3.ogg
tv_season1_episode2.ogg tv_season1_episode6.ogg tv_season2_episode4.ogg
tv_season1_episode3.ogg tv_season2_episode1.ogg tv_season2_episode5.ogg
tv_season1_episode4.ogg tv_season2_episode2.ogg tv_season2_episode6.ogg
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image4.png)

4.  As the author of a successful series of mystery novels, your next
    bestseller's chapters are being edited for publishing. Create a
    total of eight files with names mystery_chapterX.odf.
    Replace *X* with the numbers 1 through 8.

```bash
[student@serverb ~]$ touch mystery_chapter{1..8}.odf
[student@serverb ~]$ ls mys\*
mystery_chapter1.odf mystery_chapter4.odf mystery_chapter7.odf
mystery_chapter2.odf mystery_chapter5.odf mystery_chapter8.odf
mystery_chapter3.odf mystery_chapter6.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image5.png)

5.  Use a single command to create two subdirectories
    named season1 and season2 under the Videos directory, to organize
    the TV episodes.

```bash
[student@serverb ~]$ mkdir -p Videos/season{1..2}
[student@serverb ~]$ ls Videos
season1 season2
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image6.png)

6.  Move the appropriate TV episodes into the season subdirectories. Use
    only two commands, specifying destinations using relative syntax.

```bash
[student@serverb ~]$ mv tv_season1* Videos/season1
[student@serverb ~]$ mv tv_season2* Videos/season2
[student@serverb ~]$ ls -R Videos/
Videos/:
season1 season2

Videos/season1:
tv_season1_episode1.ogg tv_season1_episode3.ogg
tv_season1_episode5.ogg
tv_season1_episode2.ogg tv_season1_episode4.ogg
tv_season1_episode6.ogg
  
Videos/season2:
tv_season2_episode1.ogg tv_season2_episode3.ogg
tv_season2_episode5.ogg
tv_season2_episode2.ogg tv_season2_episode4.ogg
tv_season2_episode6.ogg
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image7.png)

7.  Create a 2-level directory hierarchy with a single command to
    organize the mystery book chapters. Create my_bestseller under
    the Documents directory, and chapters under the
    new my_bestseller directory.

```bash
[student@serverb ~]$ mkdir -p Documents/my_bestseller/chapters
[student@serverb ~]$ ls -R Documents
Documents/:
my_bestseller project_plans

Documents/my_bestseller:
Chapters

Documents/my_bestseller/chapters:

Documents/project_plans:
season1_project_plan.odf season2_project_plan.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image8.png)

8.  Create three more subdirectories directly under
    the my_bestseller directory using a single command. Name these
    subdirectories editor, changes, and vacation. The -p option (create
    parents) is not needed because the my_bestseller parent directory
    already exists.

```bash
[student@serverb ~]$ mkdir Documents/my_bestseller/{editor,changes,vacation}
[student@serverb ~]$ ls -R Documents
Documents/:
my_bestseller project_plans

Documents/my_bestseller:
changes chapters editor vacation

Documents/my_bestseller/changes:

Documents/my_bestseller/chapters:

Documents/my_bestseller/editor:

Documents/my_bestseller/vacation:

Documents/project_plans:
season1_project_plan.odf season2_project_plan.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image9.png)

9.  Change to the chapters directory. Using the tilde (~) home directory
    shortcut to specify the source files, move all book chapters to
    the chapters directory, which is now your current directory. What is
    the simplest syntax to specify the destination directory?

```bash
[student@serverb ~]$ cd Documents/my_bestseller/chapters
[student@serverb chapters]$ mv ~/mystery_chapter* 
[student@serverb chapters]$ ls
mystery_chapter1.odf mystery_chapter4.odf mystery_chapter7.odf
mystery_chapter2.odf mystery_chapter5.odf mystery_chapter8.odf
mystery_chapter3.odf mystery_chapter6.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image10.png)

10. You sent the first two chapters to the editor for review. Move only
    those two chapters to the editor directory to avoid modifying them
    during the review. Starting from the chapters subdirectory, use
    brace expansion with a range to specify the chapter file names to
    move and a relative path for the destination directory.

```bash
[student@serverb chapters]$ mv mystery_chapter{1..2}.odf ../editor
[student@serverb chapters]$ ls
mystery_chapter3.odf mystery_chapter5.odf mystery_chapter7.odf
mystery_chapter4.odf mystery_chapter6.odf mystery_chapter8.odf
[student@serverb chapters]$ ls ../editor/
mystery_chapter1.odf mystery_chapter2.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image11.png)

11. While on vacation you intend to write chapters 7 and 8. Use a single
    command to move the files from the chapters directory to
    the vacation directory. Specify the chapter file names using brace
    expansion with a list of strings and without using wildcard
    characters.

```bash
[student@serverb chapters]$ mv mystery_chapter{7,8}.odf ../vacation
[student@serverb chapters]$ ls
mystery_chapter3.odf mystery_chapter5.odf
mystery_chapter4.odf mystery_chapter6.odf
[student@serverb chapters]$ ls ../vacation/
mystery_chapter7.odf mystery_chapter8.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image12.png)

12. Change your working directory to ~/Videos/season2, and then copy the
    first episode of the season to the vacation directory.

```bash
[student@serverb chapters]$ cd ~/Videos/season2
[student@serverb season2]$ cp \*episode1.ogg
~/Documents/my_bestseller/vacation
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image13.png)

13. Use a single **cd** command to change from your working directory to
    the ~/Documents/my_bestseller/vacation directory. List its files.
    Use the *previous working directory* argument to return to
    the season2 directory. (This will succeed if the last directory
    change with the **cd** command was accomplished with one command
    rather than several **cd** commands.) From the season2 directory,
    copy the episode 2 file into the vacation directory. Use the
    shortcut again to return to the vacation directory.

```bash
[student@serverb season2]$ cd ~/Documents/my_bestseller/vacation
[student@serverb vacation]$ ls
mystery_chapter7.odf mystery_chapter8.odf tv_season2_episode1.ogg

[student@serverb vacation]$ cd ~/home/ec2-user/Videos/season2
[student@serverb season2]$ cp \*episode2.ogg ~/Documents/my_bestseller/vacation
[student@serverb vacation]$ cd ~/home/ec2-user/Documents/my_bestseller/vacation
[student@serverb vacation]$ ls
mystery_chapter7.odf tv_season2_episode1.ogg
mystery_chapter8.odf tv_season2_episode2.ogg
```
![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image14.png)

14. The authors of chapters 5 and 6 want to experiment with possible
    changes. Copy both files from
    the ~/Documents/my_bestseller/chapters directory to the
    ~/Documents/my_bestseller/changes directory to prevent these changes
    from modifying original files. Navigate to
    the ~/Documents/my_bestseller directory. Use square-bracket pattern
    matching to specify which chapter numbers to match in the filename
    argument of the **cp** command.

```bash
[student@serverb vacation]$ cd ~/Documents/my_bestseller
[student@serverb my_bestseller]$ cp chapters/mystery_chapter\[56\].odf changes
[student@serverb my_bestseller]$ ls chapters
mystery_chapter3.odf mystery_chapter5.odf
mystery_chapter4.odf mystery_chapter6.odf

[student@serverb my_bestseller]$ ls changes
mystery_chapter5.odf mystery_chapter6.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image15.png)

15. Change your current directory to the change’s directory.

> Use the **date +%F** command with command substitution to
> copy mystery_chapter5.odf to a new file which includes the full date.
> The name should have the form mystery_chapter5_YYYY-MM-DD.odf.
>
> Make another copy of mystery_chapter5.odf, appending the current time
> stamp (as the number of seconds since the epoch, 1970-01-01 00:00 UTC)
> to ensure a unique file name. Use command substitution with the **date
> +%s** command to accomplish this.

```bash
[student@serverb my_bestseller]$ cd changes]
[student@serverb changes]$ cp mystery_chapter5.odf \\mystery_chapter5\_\$(date +%F).odf
[student@serverb changes]$ cp mystery_chapter5.odf \\mystery_chapter5\_\$(date +%s).odf
[student@serverb changes]$ ls
mystery_chapter5_1492545076.odf mystery_chapter5.odf
mystery_chapter5_2017-04-18.odf mystery_chapter6.odf
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image16.png)

16. After further review, you decide that the plot changes are not necessary. Delete the changes directory.

> If necessary, navigate to the changes directory and delete all the
> files within the directory. You cannot delete a directory while it is
> the current working directory. Change to the parent directory of
> the change’s directory. Try to delete the empty directory using
> the **rm** command without the -r recursive option. This attempt
> should fail. Finally, use the **rmdir** command to delete the empty
> directory, which will succeed.

```bash
[student@serverb changes]$ rm mystery\*
[student@serverb changes]$ cd ..
[student@serverb my_bestseller]$ rm changes
rm: cannot remove 'changes': Is a directory

[student@serverb my_bestseller]$ rmdir changes
[student@serverb my_bestseller]$ ls
chapters editor vacation
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image17.png)

17. When the vacation is over, the vacation directory is no longer needed. Delete it using the **rm** command with the *recursive* option.

> When finished, return to the student user's home directory.

```bash
[student@serverb my_bestseller]$ rm -r vacation
[student@serverb my_bestseller]$ ls
chapters editor

[student@serverb my_bestseller]$ cd
[student@serverb ~]$
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image18.png)

18. Create a hard link to the ~/Documents/project_plans/season2_project_plan.odf file named ~/Documents/backups/season2_project_plan.odf.back. A hard link will protect against accidental deletion of the original file and will keep the backup file updated as changes are made to the original.

> Notice that the link count is 2 for
> both season2_project_plan.odf.back and season2_project_plan.odf files.

```bash
[student@serverb ~]$ mkdir ~/Documents/backups
[student@serverb ~]$ ln ~/Documents/project_plans/season2_project_plan.odf ~/Documents/backups/season2_project_plan.odf.back

[student@serverb ~]$ ls -lR ~/Documents/
/home/student/Documents/:
total 0
drwxrwxr-x. 2 student student 43 Jan 31 18:59 backups
drwxrwxr-x. 4 student student 36 Jan 31 19:42 my_bestseller
drwxrwxr-x. 2 student student 70 Jan 31 18:20 project_plans

/home/student/Documents/backups:
total 4
-rw-rw-r--. 2 student student 0 Jan 31 19:05
season2_project_plan.odf.back

/home/student/Documents/my_bestseller:
total 0
drwxrwxr-x. 2 student student 118 Jan 31 19:39 chapters
drwxrwxr-x. 2 student student 62 Jan 31 19:38 editor

/home/student/Documents/my_bestseller/chapters:
total 0
-rw-rw-r--. 1 student student 0 Jan 31 19:18 mystery_chapter3.odf
-rw-rw-r--. 1 student student 0 Jan 31 19:18 mystery_chapter4.odf
-rw-rw-r--. 1 student student 0 Jan 31 19:18 mystery_chapter5.odf
-rw-rw-r--. 1 student student 0 Jan 31 19:18 mystery_chapter6.odf

/home/student/Documents/my_bestseller/editor:
total 0
-rw-rw-r--. 1 student student 0 Jan 31 19:18 mystery_chapter1.odf
-rw-rw-r--. 1 student student 0 Jan 31 19:18 mystery_chapter2.odf

/home/student/Documents/project_plans:
total 4
-rw-rw-r--. 1 student student 0 Jan 31 18:20 season1_project_plan.odf
-rw-rw-r--. 2 student student 0 Jan 31 19:05
season2_project_plan.odf]
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image19.png)

19. Exit from serverb.

```bash
[student@serverb ~]$ exit
logout
Connection to serverb closed.
[student@workstation ~]$
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image20.png)

## Evaluation:
> On workstation, run the **lab files-review grade** script to confirm
> success on this lab.

```bash
[student@workstation ~]$ lab files-review grade]
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image21.png)

## Finish:
> On workstation, run the **lab files-review finish** script to finish
> this lab. This script removes all files and directories created
> on serverb during the lab exercise.

```bash
[student@workstation ~]$ lab files-review finish
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/ManagingFilesFromTheCommandLine/image22.png)

> This concludes the lab.

[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)
