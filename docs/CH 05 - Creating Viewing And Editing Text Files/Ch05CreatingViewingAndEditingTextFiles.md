---
title: Chapter 5 Creating Viewing and Editing Text Files
author: Marko Shaffer
date: 2023-06-04 11:00:00 +0800
categories: [Red Hat System Administration I, Linux Fundamentals - ITEC 200]
tags: [Linux, Red Hat, System Administration, ITEC200]     # TAG names should always be lowercase
---
[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)

# Chapter 5 Creating, Viewing, and Editing Text Files
> Red Hat System Administration I 8.2
>
> Information Technology, Franklin University
>
> ITEC 200: Linux Fundamentals
>
> Professor Kagan Ulucay
>
> 6/4/2023

## Outcomes:
> In this lab you will edit a text file, using the **vim** editor.
> 
> - Use Vim to perform file editing.
> 
> - Use visual mode to simplify file editing.

## Workstation Login:
Log in to workstation as student using student as the password.

|          | Franklin VM: | Standard User Account: | The Student's Root Account: |
|----------|--------------|------------------------|-----------------------------|
| Username | kiosk        | student                | root                        |
| Password | redhat       | student                | redhat                      |

> On workstation, run the **lab edit-review start** command.

```bash
[student@workstation ~]$ lab cli-review start
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image1.png)

## How TO:
1.  Redirect a long listing of all content in the student's home
    directory, including hidden directories and files, into a file
    named editing_final_lab.txt.

> Note: The output may not exactly match the examples shown.
>
> On workstation, from the student home directory, use the **ls -al** 
> command to redirect a long listing of all content to a file
> named editing_final_lab.txt.

```bash
[student@workstation ~]$ ls -al > editing_final_lab.txt
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image2.png)

2.  Edit the file using Vim.

```bash
[student@workstation ~]$ vim editing_final_lab.txt
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image3.png)


3.  Remove the first three lines. Enter line-based visual mode with uppercase V.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image4.png)

> Use the arrow keys to position the cursor at the first character in
> the first row. Enter line-based visual mode with **Shift**+**V**. Move
> down using the down arrow key twice to select the first three rows.
> Delete the rows with **x**.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image5.png)

4.  **Remove columns on the first line. Enter visual mode with
    lowercase v. Lowercase v selects characters on a single line only.
    The columns after -rw- should be deleted.**

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image6.png)

> Use the arrow keys to position the cursor at the first character.
> Enter visual mode using lowercase **v**. Use the arrow keys to
> position the cursor at the last character. Delete the selection
> with **x**.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image7.png)

5.  Remove columns, and the subsequent dot (".") on the remaining
    lines. Use the visual block mode. Enter visual block with the
    control sequence Ctrl+V. Use this key sequence to select a block of
    characters on multiple lines. The columns after -rw- should be
    deleted.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image8.png)
 
> Use the arrow keys to position the cursor at the first character.
> Enter visual mode using the control sequence **Ctrl**+**V**. Use the
> arrow keys to position the cursor at the last character of the column
> on the last line. Delete the selection with **x**.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image9.png)

6.  Use visual block mode to remove the fourth column.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image10.png)

> Use the arrow keys to position the cursor at the first character of
> the fourth column. Enter visual block mode using **Ctrl**+**V**. Use
> the arrow keys to position the cursor at the last character and row of
> the fourth column. Delete the selection with **x**.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image11.png)

7.  Use visual block mode to remove the time column, leaving the month
    and day on all lines.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image12.png)

> Use the arrow keys to position the cursor at the first character.
> Enter visual block mode using Ctrl+V. Use the arrow keys to position
> the cursor at the last character and row of the time column. Delete
> the selection with x.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image13.png)

8.  Remove the Desktop and Public rows. Enter visual line mode with
    uppercase V.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image14.png)

> Use the arrow keys to position the cursor at any character on
> the Desktop row. Enter visual mode with uppercase **V**. The full line
> is selected. Delete the selection with **x**. Repeat for
> the Public row.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image15.png)

9.  Use the :wq command to save and exit the file. Make a backup,
    using the date (in seconds) to create a unique file name.

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image16.png)

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image17.png)

> The following copy command is very long and should be entered as a
> single line.

```bash
[student@workstation ~]$ cp editing_final_lab.txt editing_final_lab_$(date +%s).txt
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image18.png)

10. Append a dashed line to the file. The dashed line should contain
    at least 12 dashes. The following echo command is very long and
    should be entered on a single line.

```bash
[student@workstation ~]$ echo "----------------------------------------" >> editing_final_lab.txt
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image19.png)

11. Append a directory listing of the Documents directory. List the
    directory listing on the terminal and send it to
    the editing_final_lab.txt file with one command line.

```bash
[student@workstation ~]$ ls Documents/ | tee -a editing_final_lab.txt lab_review.txt
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image20.png)

12. Confirm that the directory listing is at the bottom of the lab
    file.
```bash
[student@workstation ~]$ cat editing_final_lab.txt
-rw- 1 student 310 Jan 21 .bash_history
-rw- 1 student 18 Oct 12 .bash_logout
-rw- 1 student 141 Oct 12 .bash_profile
-rw- 1 student 312 Oct 12 .bashrc
drwx 8 student 201 Jan 14 .cache
drwx 10 student 203 Jan 14 .config
drwx 2 student 6 Jan 14 Documents
drwx 2 student 6 Jan 14 Downloads
-rw- 1 student 0 Jan 22 editing_final_lab.txt
-rw- 1 student 16 Jan 14 .esd_auth
-rw- 1 student 310 Jan 14 .ICEauthority
drwx 3 student 19 Jan 14 .local
drwx 2 student 6 Jan 14 Music
drwx 2 student 6 Jan 14 Pictures
drwx 3 student 19 Jan 14 .pki
drwx 2 student 73 Jan 14 .ssh
drwx 2 student 6 Jan 14 Templates
drwx 2 student 6 Jan 14 Videos
-rw- 1 student 1095 Jan 14 .viminfo
------------------------------------
lab_review.txt
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image21.png)

## Evaluation:

> On workstation, run **lab help-review grade** to confirm success of this exercise.

```bash
[student@workstation ~]$ lab help-review grade
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image22.png)


## Finish:

> On workstation, run the **lab help-review finish** script to complete this exercise.

```bash
[student@workstation ~]$ lab help-review finish
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/CreatingViewingAndEditingTextFiles/image23.png)

> This concludes the lab.

[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)
