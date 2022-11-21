# Linux Toolbox Essentials

To get to know Linux in its diversity, it is useful and necessary to get to know a few tools and to practice using them.
I would like to present here a subjective selection of what I consider to be the most important tools. Each of these tools deserves special attention and consideration. In this brief introduction, I cannot even begin to show the power and possibilities of these tools. I am more interested in showing how they are used in a relevant context and demonstrating the practical value of our toolbox.

For your own and deeper insight and experience, you'll need to set aside at least half an hour for each of these tools, during which you'll become intimately familiar with the options and function. Some of the tools need and deserve several hours. But this is definitely time well spent! If you then start to work with these tools every day, you will quickly find your own way into the world of Linux and open source software.

I assume that you have a Linux workstation or at least a virtual machine in front of you, with which you can follow the steps I have shown. In the examples I use Red Hat Enterprise Linux, but you should be able to do this with any other Linux distribution.

I recommend that you first read this text in its entirety and only then start your own exercises.
In this document all steps and examples are highlighted as 'code', so you can find them quickly and follow them yourself at your own speed.



## Gnome Terminal
Let's start with the Gnome Terminal. 

On the RHEL notebook you can find it under `Applications->Sytem Tools->Terminal`.

In the last millennium, a terminal was a workstation consisting of a text screen and a keyboard connected to the computer. Since then, the term terminal also stands for the text-based interface to the operating system within an otherwise graphical user interface.

After you invoke the Gnome Terminal from the menu, a window appears with a black background and a prompt in white text. You can customize the appearance and some properties of the terminal window to suit your taste or requirements.

The default size of the terminal window is 80x24, which means you have 24 lines of 80 characters each. The window can be dragged with the mouse and resized to any size. With the menu item 'Terminal' you can also select other fixed terminal sizes. In the menu item 'View' the font size can be changed.
Most menu items can also be reached via keyboard shortcuts. For example with the key combination `Shift-Ctrl-T` you can open a second tab with another terminal in the same window. With the key combination `Alt-1` and `Alt-2` you can switch between the first and the second tab. With `Ctrl-PageUp` and `Ctrl-PageDown` you can scroll up and down in a series of tabs.

## bash
In the terminal window you will see a command prompt. This is a string and a marker for text input. The string usually shows my user name and the name of the computer I am working on. It also shows the name of the directory I am currently in. The tilde `~` indicates my home directory.

The command prompt belongs to the most important of all programs in my list, the shell. The shell is a program whose purpose is to start other programs and to provide these programs with a defined runtime environment. 

Usually such a shell is used interactively, so a person sits at the terminal and enters the commands via a keyboard. However, the shell can also run automatically and read the commands from a text file. This text file is called Shellscript or Batch. In such a shell script real programs can be written, with variables, functions, loops and everything that belongs to a computer program. We will deal with reading programs in a later session.

All data, that is programs, texts, pictures or any other information coded in bits and bytes, which are in a Linux system are represented in a single file system. This file system is a tree of directories. The structure of this tree follows the Linux file system standard.

Each user has his own home directory in the `/home` branch of the directory tree. With the shell command `pwd` the current working directory is shown to me. With `cd` I can change to another directory. I can specify the name of the target directory **absolute** with a leading slash or without a slash **relative** to my current directory.

With `cd` without specifying a destination directory I always get to my home directory immediately. With `cd -` I change back to the last used directory.

The shell is an enormously powerful program and it is worthwhile to learn its use and possibilities thoroughly. 

## man
To learn all the details of using a program, there are the manual pages.

With `man bash` the documentation for the shell is displayed. In the document we see that bash is used since 1989 and that it is the successor of the Bourne Shell. This was a very popular and widely used shell for UNIX systems back then. The bash is an improved and all the more popular version. There are other shells for Unix, for example the Korn Shell or the C Shell. The bash contains some of the best features of these other shells, so today we practically only use the bash.

You will need some time to familiarize yourself with the many features of bash. Take that time, it is time well spent. I spent several weeks sometime in 1990 or 1991 very intensively studying bash and porting it to Minix for myself. I would say those hours are certainly among the best investments in my personal development.

The manual page of bash is quite long, you can scroll forward and backward with the keys `Space` and `b`. The keys `PageUp` and `PageDown` have the same function. You can use `/` to enter any search term and use `n` and `N` to navigate between the search results. With `q` for quit you leave the manual page and get back to the command prompt.

With `Ctrl-L` you clear the current content of the terminal window.

## ssh

Linux and Open Source Software have the most importance and develop their full use as server and with network based applications. In the scientific technical area there are also Linux workstations at the workplace, but the most powerful systems are usually located centrally in well-secured and air-conditioned data centers.

To work comfortably from the workstation with and on these server systems we use the tool `ssh user@server.example.org`.

The name *Secure Shell* is a bit misleading, because ssh itself only provides the network functionality to connect to an sshd server. By default, a shell is automatically started on the remote site, typically bash. However, any other program can be invoked with ssh. The name ssh refers to another tool, `rsh` (remote shell) which basically serves the same purpose. However, the network connection with rsh is not automatically and in any case strongly encrypted. This has proven to be a serious security risk, so today ssh is used as a successor with strong security features.

The connection to the remote terminal can basically be authenticated by a simple user/password login procedure. Already during login all keystrokes are transmitted encrypted. Nevertheless, password authentication is generally prohibited by many servers. Instead, a previously exchanged ssh-key is expected for authentication. Such a key is generated with `ssh-keygen`. The private part of the key must be kept secure. The public part, however, can then be passed on without risk.

## sudo

The role-rights model of Linux allows a fairly good protection of system resources from unauthorized access and accidental corruption by interactive users. However, this model assumes that users regularly use a personal account and only work with greater privileges when necessary and in as well-controlled an environment as possible.

This controlled environment is provided by the `sudo` tool.

With `man sudo` and `man sudoers` a quite good overview of function and performance of this tool is given.

## ls
All data in the Linux system is organized in the one big file system. To get an overview here, there is the tool ls. With `ls` the content of a directory is displayed.

Without further arguments simply the content of the current working directory is listed. Above we saw that the internal bash command `pwd` shows the name and path of this directory.

The root directory, where the whole filesystem tree starts, is denoted by `/`. `ls /` displays the contents of this root directory.

To get additional information about the properties of the listed objects in a directory, ls can be called with additional options. I get a list of all options with `ls --help`.

If, like here, the output of a program to the standard output of the terminal goes beyond a screen content, the Gnome terminal offers the possibility to scroll back and forward in the content with `Shift-PageUp` and `Shift-PageDown`. In other terminal programs, this feature may be missing altogether or may be associated with other keyboard shortcuts.

It is worthwhile to understand and try all possible options of ls. For example, with `ls -l` we get a long listing in which the file type, access rights, number of subdirectories, owner and group as well as the size and date of last modification are shown.

Objects whose name starts with a dot are not displayed in a simple listing. To also see the hidden files in the listing, the `ls -a` option must be specified.

As a normal user I do not have the right to see all data. Even less I can change data. Only in my home directory I own all data and have all rights.

## find

If I want to, I can use a recursive listing to show me the whole file system tree, at least for all areas where I have the rights to read and execute on the directories.

But to search for all files that have something to do with bash, for example, this is a rather complex method. Much better for this purpose is the tool `find / -name bash\*`.

## mkdir

For example, I can create new directories in my home directory.

`mkdir -p exercises/tools`

I can immediately change to this directory as a new working directory with `cd` and then work in it.

To save me typing the directory name twice, I can just type `Esc-.` on the command line of bash. Then the last argument of the last command line appears automatically. Instead of `cd exercises/tools` I just type `cd Esc-.`. Just try it, after a while you will use this `Esc-.` automatically.

As I said, it is worth to invest some time in learning bash. This time will be paid back second by second during your life.

With bash I can also create a whole list of directories in a single call.

`mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}`

## vim 
If I want to edit an existing text file or create a new one, I need a text editor. In 1976 Bill Joy wrote the UNIX program vi for this purpose. An improved version of this editor is included in every Linux system under the name `vim`.

Also for vim there is a manual page `man vim`. Furthermore, **in** the editor I can get very detailed information on how to use the editor with the command `:help`. Also for vim it is worth to invest a few hours in studying the different functions. Unlike other editors, the central functions have been proven and stable for many decades. Find out for yourself why this editor is established as a standard for all UNIX and Linux systems.

As a first introduction: The editor works in different modes. The program starts in command mode where keystrokes trigger certain actions. With the command `i` the editor changes to the insert mode, where all keystrokes are inserted at the current cursor position. With the `Esc` key the editor changes back to the command mode.
With `x` I delete the character under the cursor, with `D` I delete the line from the cursor to the end of the line, with `dd` I delete the whole line. With `p` I can insert the deleted line below the cursor again, with `P` the line is inserted above.
With `:w` the file is written and with `:q` I leave the editor.

## view 
If I want to prevent that I change an existing file by mistake, I can also call the editor under the name view. Then it starts automatically in read only mode.

## less 
Another way to just display files without editing them is to use a so called pager. `less` is such a tool. Without realizing it we already got to know it when calling `man`. Less is the default pager and is automatically used by man to display the manual pages. The tool `man` itself is 'only' for formatting the documents marked in `nroff` format for a certain output device, in this case the standard pager less.

## chmod
For my own files and directories I can determine which rights my group and the other users have on these objects. For this there is the tool `chmod`.
The manual page `man chmod` also explains the meaning of the different permissions.

## yumdownloader
There are many ways to download files from the internet to my home directory. If I want to download the source code and all control files to build one of the programs included in RHEL to my home directory, I can use the yumdownloader tool.
 
`yumdownloader --source bash`
loads the source RPM package from Red Hat from the internet. This works for all programs installed from RPM packages, provided the system has a valid Red Hat subscription.

If the yumdownloader program is not already installed on your system, the yum-utils package must be installed.

## rpm
It can happen that I want to download the source RPM for a certain program installed in my RHEL system and the package is not found. This is usually because the program is installed as part of a larger package with a completely different name.

For example the tool `chmod` is such a case. To find out which package the program belongs to, I can use the Red Hat Package Manager tool: `rpm -qf /usr/bin/chmod` gives me **coreutils** as package name.

To unpack a source RPM package fetched with yumdownloader, I also use `rpm -i coreutils*.src.rpm`.
When unpacking, all files are automatically installed in my home directory in the subdirectory `rpmbuild`. Coincidentally, I created this in `mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}` earlier.
If this directory does not exist it will be created automatically when unpacking the source RPM.

The directory `ls ~/rpmbuild/SOURCES` contains all the source code that Red Hat used to build the executable program. The directory `ls ~/rpmbuild/SPECS` contains the control file for the RPM build system, which contains the specification for the automatic build.

Most SOURCES files are relatively small patches. Patches are changes made to the sources during the build. The actual source package is the file with the extension `tar.xz`.
This is a TAR archive compressed with `xz`.

## tar
`tar` is a tool and a file format that was developed for UNIX as early as 1979. The name refers to its original function for writing and reading data backups on magnetic tapes. However, it can also be used to edit archive files on a hard disk.

```
cd ~/rpmbuild/BUILD
tar xvf ../SOURCES/coreutils*.tar.xz
```

## cp 
If I want to make my own changes to the source code to adapt the program to my ideas and requirements, I should make a copy beforehand and thus keep the original state for comparison. For copying we have the tool 'cp'. Also here there are a lot of options and it is worth to study the manual page `man cp` in detail.

I recursively copy all coreutils sources in archive mode:

```
cp -a coreutils-*/ coreutils.tmp
cd Esc-.
```

This will keep all file permissions, links and attributes in the copy.

Now I can change and try all kinds of things in the copy.

For example I can change the tool `whoami` so that it doesn`t just throw my username at me. I want to introduce a new **polite** option in which I am addressed a little more friendly.

```
vim coreutils.tmp/src/whoami.c 
/* TODO: add new polite option to be more human friendly */
/* TODO: in polite mode, reply with full name if available */
```
 

## diff
If after a while I don't know exactly what I changed, I can use the `diff` tool to display all changes.

```
diff -only coreutils-* coreutils.tmp
```

I can also save these changes in a file to be able to reproduce them later. For this I use the output redirection of the shell:

```
diff -only coreutils-* coreutils.tmp >write-polite.patch
```
## patch

I can now apply this patch to the unmodified sources:

```
cd coreutils-*
patch -p1 --verbose -i ../write-polite.patch
```
## mv 

When I am satisfied with the result, I can add the new patch to the sources and adjust the RPM specification to include my change in the next release.

```
cd ..
mv write-polite.patch ../SOURCES/
```

## rm 

If I change my mind, I can delete the patch:

```
rm -i ~/rpmbuild/SOURCES/write-polite.patch
```

With the interactive option I am asked for each file separately if I really want to delete it.

## rmdir 

For deleting directories there is a separate tool, `rmdir`.

However, this tool actually works only and exclusively on directories. If there is only one other file in the directory, this tool leaves the directory unchanged. This is quite logical. If you call `rmdir` you will get exactly that. The tool is not called *rmdirandeveythinginside*.

To delete a directory with all its contents quickly and radically we use `rm -fr` instead.

Before such a radical step it is always useful to pause for a moment to make sure that nothing important is lost. The Linux file system has no net and no double bottom to bring back once deleted files. Reconstructing data on the block device underneath the file system is extremely costly and insecure, so it should be avoided at all costs.

## git

Distributing source code to open source projects via source packages, as we have seen with `yumdownload`, is only one of many possibilities. In practice, for collaborative work on large projects, the way to go is via a version control system on a public server on the Internet.

As a format and tool for version control `git` has become generally accepted. Public servers on which open source projects can manage their development with `git` are for example GitHub, GitLab and SourceForge.

The sources of an open source project can therefore usually be found with a simple call to 
`git clone https://github.com/shetze/Linux-for-Career-Changers.git`
directly and first hand from the *home* server of the respective project. 

## grep 
## sort 
## head 
## tail 
## strace
