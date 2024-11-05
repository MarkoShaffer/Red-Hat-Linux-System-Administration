---
title: Chapter 4 Getting Help in Red Hat Enterprise Linux
author: Marko Shaffer
date: 2023-06-04 11:00:00 +0800
categories: [Red Hat System Administration I, Linux Fundamentals - ITEC 200]
tags: [Linux, Red Hat, System Administration, ITEC200]     # TAG names should always be lowercase
---
[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)

# Chapter 4: Getting Help in Red Hat Enterprise Linux
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
> In this lab, you will look up information to help you complete tasks in man pages and GNU Info documents.
>
> - Locate relevant commands by searching man pages and Info nodes.
> 
> - Learn new options for commonly used documentation commands.
> 
> - Use appropriate tools to view and print documentation and other
  non-text formatted files.

## Workstation Login:
> Log in to workstation as student using student as the password.

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

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image1.png)

```bash
[student@workstation ~]$ lab help-review start
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image2.png)

## How To:
1.  On workstation, determine how to prepare a man page for printing.
    Specifically, find what format or rendering language is used for
    printing.

> Use the **man man** command to determine how to prepare a man page for
> printing.

```bash
[student@worksation ~]$ man man
...output omitted...
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image3.png)

> Press **q** to quit the man page.
>
>Note: **man** uses **-t** to prepare a man page for printing, using
>PostScript.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image4.png)

2.  Create a formatted output file of the passwd man page. Call the
    file passwd.ps. Determine the file content format. Inspect the
    contents of the passwd.ps file.

> Note: Create formatted output of the **passwd** man page using the
> following command:

```bash
[student@workstation ~]$ man -t passwd > passwd.ps
```

> The **>** symbol *redirects* the contents of the man page to
> the passwd.ps file. This command is taught in more detail in a
> following chapter.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image5.png)

> Use the man -t command to create a formatted file of the passwd man page.

```bash
[student@workstation ~]$ man -t passwd > passwd.ps
[student@workstation ~]$ ls -al
...output omitted...
-rw-rw-r--. 1 student student 19947 Feb 26 11:14 passwd.ps
...output omitted...
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image6.png)

> Use the file command to determine the file content format.

```bash
[student@workstation ~]$ file /home/student/passwd.ps
/home/student/passwd.ps: PostScript document text conforming DSC level 3.0
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image7.png)

> Use the less command to view the /home/student/passwd.ps file.

```bash
[student@workstation ~]$ less /home/student/passwd.ps
%!PS-Adobe-3.0
%%Creator: groff version 1.22.3
%%CreationDate: Tue Feb 26 11:14:40 2019
%%DocumentNeededResources: font Times-Roman
%%+ font Times-Bold
%%+ font Times-Italic
%%+ font Symbol
%%DocumentSuppliedResources: procset grops 1.22 3
...output omitted...
```

Note: The output of **file** asserts that the file is in the PostScript
format, and you have confirmed it by viewing its contents. Notice the
header lines of PostScript information. Use **q** to quit
the **less** command.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image8.png)

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image9.png)

3.  Using **man** learn the commands used for viewing and printing PostScript files.

```bash
[student@workstation ~]$ man -k postscript viewer
evince (1) - GNOME document viewer
evince-previewer (1) - show a printing preview of PostScript and PDF documents
evince-thumbnailer (1) - create png thumbnails from PostScript and PDF documents
gcm-viewer (1) - GNOME Color Manager Profile Viewer Tool
gnome-logs (1) - log viewer for the systemd journal
grops (1) - PostScript driver for groff
pango-view (1) - Pango text viewer
pluginviewer (8) - list loadable SASL plugins and their properties
```
Note: Using multiple words with the **-k** option finds man pages
matching *either* word; those with "postscript" *or* "viewer" in their
descriptions. Notice the **evince**(1) commands in the output.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image10.png)

4.  Learn how to use the evince(1) viewer in preview mode. Also,
    determine how to open a document starting on a specific page.

> Use the **man evince** command to learn how to use the viewer in
> preview mode.

```bash
[student@workstation ~]$ man evince
*...output omitted...*
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image11.png)

> Press **q** to quit the man page.

> Note: The -w (or --preview) option opens evince in preview mode.
> The -i option is used to specify a starting page.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image12.png)

5.  View your PostScript file using the various evince options you
    researched. Close your document file when you are finished.

> Use the **evince** command to open /home/student/passwd.ps

```bash
[student@workstation ~]$ evince /home/student/passwd.ps
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image13.png)

> Use the **evince -w /home/student/passwd.ps** command to open the file
> in preview mode.

```bash
[student@workstation ~]$ evince -w /home/student/passwd.ps
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image14.png)

> Use the **evince -i 3 /home/student/passwd.ps** command to open the
> file at page 3.

```bash
[student@workstation ~]$ evince -i 3 /home/student/passwd.ps
```

> Note: While normal **evince** mode allows full screen and presentation
> style viewing, the **evince** preview mode is useful for quick
> browsing and printing. Notice the **print icon** at the top.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image15.png)

6.  Using the man command, research lp(1) to determine how to print
    any document starting on a specific page. Without actually entering
    any commands (because there are no printers), learn the syntax, in
    one command, to print only pages 2 and 3 of your PostScript file.

> Use the **man lp** command to determine how to print specific pages of
> a document.

```bash
[student@workstation ~]$ man lp

*...output omitted...*
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image16.png)

> Press **q** to quit the man page.
>
> Note: From lp(1), you learn that the -P option specifies pages.
> The lp command spools to the *default* printer, sending only the page
> range starting on 2 and ending on 3. Therefore, one valid answer
> is **lp passwd.ps -P 2-3**.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image17.png)

7.  Using pinfo, look for GNU Info documentation about the evince viewer.

> Use the **pinfo command** to look for GNU Info documentation about
> the **evince** viewer.

```bash
[student@workstation ~]$ pinfo evince
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image18.png)

> Note: Notice that the evince(1) man page displays instead.
> The **pinfo** document viewer looks for a relevant man page when no
> appropriate GNU documentation node exists for the requested topic.
> Press **q** to quit.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image19.png)

8.  Using Firefox, open the system's package documentation directory
    and browse into the man-db package subdirectory. View the provided
    manuals.

> Use **firefox /usr/share/doc** to view system documentation. Browse to
> the man-db subdirectory. Click on the manuals to view them.

```bash
[student@workstation ~]$ firefox /usr/share/doc
```

> Note: Bookmarks can be made for any frequently used directory. After
> browsing to the man-db directory, click to open and view the text
> version of the manual, then close it. Click to open the PostScript
> version. As observed earlier, **evince** is the system's default
> viewer for PostScript and PDF documents. You may wish to return to
> these documents later to become more knowledgeable about **man**. When
> finished, close the **evince** viewer.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image20.png)

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image21.png)

9.  Using the Firefox browser, locate and browse to
    the initscripts package subdirectory. View the sysconfig.txt file,
    which describes important system configuration options stored in
    the /etc/sysconfig directory.

> In the Firefox browser, locate the initscripts package subdirectory.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image22.png)

> Notice how useful a browser is for locating and viewing local system
> documentation. Close the document and Firefox when finished.

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image23.png)

## Evaluation:

> On workstation, run **lab help-review grade** to confirm success of this exercise.

```bash
[student@workstation ~]$ lab help-review grade
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image24.png)

## Finish:

> On workstation, run the **lab help-review finish** script to complete this exercise.

```bash
[student@workstation ~]$ lab help-review finish
```

![Desktop View](/assets/files/SchoolProjects/ITEC200/GettingHelpInRedHatEnterprisLinux/image25.png)

> This concludes the lab.

[Back To TOC](https://github.com/MarkoShaffer/Red-Hat-Linux-System-Administration/blob/main/)
