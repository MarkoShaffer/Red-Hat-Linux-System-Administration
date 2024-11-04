---
title: Chapter 4 Getting Help in Red Hat Enterprise Linux
author: Marko Shaffer
date: 2023-06-04 11:00:00 +0800
categories: [Red Hat System Administration I, Linux Fundamentals - ITEC 200]
tags: [Linux, Red Hat, System Administration, ITEC200]     # TAG names should always be lowercase
---

# Chapter 4 Getting Help in Red Hat Enterprise Linux
# Red Hat System Administration I 8.2
> Information Technology, Franklin University
> ITEC 200: Linux Fundamentals
> Professor Kagan Ulucay
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
> Log in toÂ workstationÂ asÂ studentÂ usingÂ studentÂ as the password.

|          | Franklin VM: | Standard User Account: | The Student's Root Account: |
|----------|--------------|------------------------|-----------------------------|
| Username | kiosk        | student                | root                        |
| Password | redhat       | student                | redhat                      |

> OnÂ the workstation, run theÂ **lab cli-review start**Â script to set up a
clean lab environment. The script also copies theÂ zcatÂ file toÂ the
student's home directory.

[```bash
[student@workstation ~]$ lab cli-review start
```

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image1.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

```bash
[student@workstation ~]$ lab help-review start
```

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image2.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

## How To:
1.  **On workstation, determine how to prepare a man page for printing.
    Specifically, find what format or rendering language is used for
    printing.

> Use theÂ **man man**Â command to determine how to prepare a man page for
> printing.
>
> [student@worksation ~]$ man man
>
> *...output omitted...*

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image3.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> PressÂ **q**Â to quit the man page.

Note: **man**Â usesÂ **-t**Â to prepare a man page for printing, using
PostScript.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image4.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

2.  **Create a formatted output file of theÂ passwdÂ man page. Call the
    fileÂ passwd.ps. Determine the file content format. Inspect the
    contents of theÂ passwd.psÂ file.

> Note: Create formatted output of theÂ **passwd**Â man page using the
> following command:
>
> [student@workstation \$\]\$ man -t passwd \> passwd.ps
>
> TheÂ **\>**Â symbolÂ *redirects*Â the contents of the man page to
> theÂ passwd.psÂ file. This command is taught in more detail in a
> following chapter.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image5.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> **Use theÂ man -tÂ command to create a formatted file of theÂ passwdÂ man
> page.
>
> [student@workstation ~]$ man -t passwd \> passwd.ps
>
> [student@workstation ~]$ ls -al
>
> *...output omitted...*
>
> -rw-rw-r--. 1 student student 19947 Feb 26 11:14 passwd.ps
>
> *...output omitted...*

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image6.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> **Use theÂ fileÂ command to determine the file content format.
>
> [student@workstation ~]$ file /home/student/passwd.ps
>
> passwd.ps: **PostScript** document text conforming DSC level 3.0

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image7.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> **Use theÂ lessÂ command to view theÂ /home/student/passwd.psÂ file.
>
> [student@workstation ~]$ less /home/student/passwd.ps
>
> %!PS-Adobe-3.0
>
> %%Creator: groff version 1.22.3
>
> %%CreationDate: Tue Feb 26 11:14:40 2019
>
> %%DocumentNeededResources: font Times-Roman
>
> %%+ font Times-Bold
>
> %%+ font Times-Italic
>
> %%+ font Symbol
>
> %%DocumentSuppliedResources: procset grops 1.22 3
>
> *...output omitted...*

Note: The output ofÂ **file**Â asserts that the file is in the PostScript
format, and you have confirmed it by viewing its contents. Notice the
header lines of PostScript information. UseÂ **q**Â to quit
theÂ **less**Â command.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image8.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image9.png”){: width=“972” height=“589” }
style="width:7.5in;height:5.65in" />man

3.  **UsingÂ man, learn the commands used for viewing and printing
    PostScript files.

> UsingÂ **man**Â learn the commands used for viewing and printing
> PostScript files.
>
> [student@workstation ~\]# man -k postscript viewer
>
> **evince (1)** - GNOME document viewer
>
> evince-previewer (1) - show a printing preview of PostScript and PDF
> documents
>
> evince-thumbnailer (1) - create png thumbnails from PostScript and PDF
> documents
>
> gcm-viewer (1) - GNOME Color Manager Profile Viewer Tool
>
> gnome-logs (1) - log viewer for the systemd journal
>
> grops (1) - PostScript driver for groff
>
> pango-view (1) - Pango text viewer
>
> pluginviewer (8) - list loadable SASL plugins and their properties

Note: Using multiple words with theÂ **-k**Â option finds man pages
matchingÂ *either*Â word; those with "postscript"Â *or*Â "viewer" in their
descriptions. Notice theÂ **evince**(1) commands in the output.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image10.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

4.  **Learn how to use theÂ evince(1) viewer in preview mode. Also,
    determine how to open a document starting on a specific page.

> Use theÂ **man evince**Â command to learn how to use the viewer in
> preview mode.
>
> [student@workstation ~]$ man evince**
>
> *...output omitted...*

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image11.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

PressÂ **q**Â to quit the man page.

Note: TheÂ -wÂ (orÂ --preview) option opensÂ evinceÂ in preview mode.
TheÂ -iÂ option is used to specify a starting page.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image12.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

5.  **View your PostScript file using the variousÂ evinceÂ options you
    researched. Close your document file when you are finished.

> Use theÂ **evince**Â command to openÂ /home/student/passwd.ps
>
> [student@workstation ~]$ evince /home/student/passwd.ps

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image13.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> Use theÂ **evince -w /home/student/passwd.ps**Â command to open the file
> in preview mode.
>
> [student@workstation ~]$ evince -w /home/student/passwd.ps

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image14.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> Use theÂ **evince -i 3 /home/student/passwd.ps**Â command to open the
> file at page 3.
>
> [student@workstation ~]$ evince -i 3 /home/student/passwd.ps
>
> Note: While normalÂ **evince**Â mode allows full screen and presentation
> style viewing, theÂ **evince**Â preview mode is useful for quick
> browsing and printing. Notice theÂ **print icon**Â at the top.
>
> ![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image15.png”){: width=“972” height=“589” }
> style="width:7.5in;height:5.65in" />

6.  **Using theÂ manÂ command, researchÂ lp(1) to determine how to print
    any document starting on a specific page. Without actually entering
    any commands (because there are no printers), learn the syntax, in
    one command, to print only pages 2 and 3 of your PostScript file.

> Use theÂ **man lp**Â command to determine how to print specific pages of
> a document.
>
> [student@workstation ~]$ man lp
>
> *...output omitted...*

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image16.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> PressÂ **q**Â to quit the man page.
>
> Note: FromÂ lp(1), you learn that theÂ -PÂ option specifies pages.
> TheÂ lpÂ command spools to theÂ *default*Â printer, sending only the page
> range starting on 2 and ending on 3. Therefore, one valid answer
> isÂ **lp passwd.ps -P 2-3**.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image17.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

7.  **UsingÂ pinfo, look for GNU Info documentation about
    theÂ evinceÂ viewer**.

> Use theÂ **pinfo command**Â to look for GNU Info documentation about
> theÂ **evince**Â viewer.
>
> [student@workstation ~]$ pinfo evince

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image18.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> Note: Notice that theÂ evince(1) man page displays instead.
> TheÂ **pinfo**Â document viewer looks for a relevant man page when no
> appropriate GNU documentation node exists for the requested topic.
> PressÂ **q**Â to quit.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image19.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

8.  **UsingÂ Firefox, open the system's package documentation directory
    and browse into theÂ man-dbÂ package subdirectory. View the provided
    manuals.

> UseÂ **firefox /usr/share/doc**Â to view system documentation. Browse to
> theÂ man-dbÂ subdirectory. Click on the manuals to view them.
>
> [student@workstation ~]$ firefox /usr/share/doc
>
> Note: Bookmarks can be made for any frequently used directory. After
> browsing to theÂ man-dbÂ directory, click to open and view the text
> version of the manual, then close it. Click to open the PostScript
> version. As observed earlier,Â **evince**Â is the system's default
> viewer for PostScript and PDF documents. You may wish to return to
> these documents later to become more knowledgeable aboutÂ **man**. When
> finished, close theÂ **evince**Â viewer.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image20.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

<table>
<caption>manufactured viewport for HTML img</caption>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th style="text-align: center;"><blockquote>
<p>![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image21.png”){: width=“972” height=“589” }
style="width:10.66667in;height:3.34375in" /></p>
</blockquote></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

9.  Using theÂ FirefoxÂ browser, locate and browse to
    theÂ initscriptsÂ package subdirectory. View theÂ sysconfig.txtÂ file,
    which describes important system configuration options stored in
    theÂ /etc/sysconfigÂ directory.

> In theÂ FirefoxÂ browser, locate theÂ initscriptsÂ package subdirectory.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image22.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

> Notice how useful a browser is for locating and viewing local system
> documentation. Close the document andÂ FirefoxÂ when finished.

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image23.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

## Evaluation:

OnÂ workstation, runÂ **lab help-review grade**Â to confirm success of this
exercise.

> [student@workstation ~]$ lab help-review grade

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image24.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

## Finish:

OnÂ workstation, run theÂ **lab help-review finish**Â script to complete
this exercise.

> [student@workstation ~]$ lab help-review finish

![Desktop View](.\assets\files\SchoolProjects\ITEC200\GettingHelpInRedHatEnterprisLinux/image25.png”){: width=“972” height=“589” }
_Full screen width and center alignment_

This concludes the lab.
