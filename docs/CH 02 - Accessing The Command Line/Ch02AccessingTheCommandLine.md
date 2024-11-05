---
title: Chapter 2 Accessing the Command Line Lab
author: Marko Shaffer
date: 2023-05-28 11:00:00 +0800
categories: [Red Hat System Administration I, Linux Fundamentals - ITEC 200]
tags: [Linux, Red Hat, System Administration, ITEC200]     # TAG names should always be lowercase
---

# Chapter 2: Accessing the Command Line Lab 
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

> In this lab, you will use the Bash shell to execute commands.
>
> - Successfully run simple programs using the Bash shell command line.
>
> - Execute commands used to identify file types and display parts of text files.
>
> - Practice using some Bash command history "shortcuts" to more efficiently repeat commands or parts of commands.

## Workstation Login:
> Log in to the workstation as username student using student as the
password.

|          | Franklin VM: | Standard User Account: | The Student's Root Account: |
|----------|--------------|------------------------|-----------------------------|
| Username | kiosk        | student                | root                        |
| Password | redhat       | student                | redhat                      |

> On the workstation, run the **lab cli-review start** script to set up a
clean lab environment. The script also copies the zcat file to the
student's home directory.

```bash
[student@workstation ~]$ lab cli-review start
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image1.png)

## How TO:
1.  Use the **date** command to display the current time and date.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image2.png)

2.  Display the current time in 12-hour clock time (for example,
    11:42:11 AM). Hint: The format string that displays that output
    is %r.

> Use the +%r argument with the **date** command to display the current
> time in 12-hour clock time.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image3.png)

3.  What kind of file is /home/student/zcat? Is it readable by humans?

> Use the **file** command to determine its file type.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image4.png)

4.  Use the **wc** command and Bash shortcuts to display the size
    of zcat.

> The **wc** command can be used to display the number of lines, words,
> and bytes in the zcat script. Instead of retyping the file name, use
> the Bash history shortcut **Esc**+**.** (the
> keys **Esc** and **.** pressed at the same time) to reuse the argument
> from the previous command.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image5.png)

5.  Display the first 10 lines of zcat.

> The **head** command displays the beginning of the file. Try using
> the **Esc**+**.** shortcut again.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image6.png)

6.  Display the last 10 lines of the zcat file.

> Use the **tail** command to display the last 10 lines of
> the zcat file.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image7.png)
7.  Repeat the previous command exactly with three or fewer keystrokes.

> Repeat the previous command exactly. Either press the **UpArrow** key
> once to scroll back through the command history one command and then
> press **Enter** (uses two keystrokes), or enter the shortcut
> command **!!** and then press **Enter** (uses three keystrokes) to run
> the most recent command in the command history . (Try both.)

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image8.png)

8.  Repeat the previous command, but use the -n 20 option to display the
    last 20 lines in the file. Use command-line editing to accomplish
    this with a minimal number of keystrokes.

> **UpArrow** displays the previous command. **Ctrl**+**A** makes the
> cursor jump to the beginning of the
> line. **Ctrl**+**RightArrow** jumps to the next word, then add the -n
> 20 option and hit **Enter** to execute the command.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image9.png)

9.  Use the shell history to run the **date +%r** command again.

> Use the **history** command to display the list of previous commands
> and to identify the specific **date** command to be executed.
> Use **!*number*** to run the command, where *number* is the command
> number to use from the output of the **history** command.
>
> Note that your shell history may be different from the following
> example. Determine the command number to use based on the output of
> your own **history** command.

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image10.png)

## Evaluation:

On workstation, run the **lab cli-review grade** script to confirm
success on this exercise.

```bash
[student@workstation ~]$ lab cli-review grade
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image11.png)

# Finish:

On workstation, run the **lab cli-review finish** script to complete the
lab.

```bash
[student@workstation ~]$ lab cli-review finish
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/AccessingTheCommandLine/image12.png)

This concludes the lab.
