Everything is a file, Linux and other Unix-like Operating systems maintain a consistency by treating everything as a file (even the hardware devices). The keyboard, mouse, printers, monitor, hard disk, processes, even the directories are treated as files in Linux. The regular files contain data such as text (text files), music, videos (multimedia files) etc. Set aside the regular data, there are some other data about these files, such as their size, ownership, permissions, timestamp etc. This meta-data about a file is managed with a data structure known as an inode (index node).
What is an inode in Linux?

Every Linux file or directory (from a technical point of view, there’s no real difference between them) has an inode, and this inode contains all of the file’s metadata (that is, all the administrative data needed to read a file is stored in its inode). For example, the inode contains a list of all the blocks in which a file is stored, the owner information for that file, permissions and all other attributes that are set for the file. In a sense, you could say that a file really is the inode, and names are attached to these inodes to make it easier for humans to work with them.

Inode limits is per filesystem and decided at filesystem creation time. Maximum directory size is filesystem dependent and thus the exact limit differs. For better performance make your directories smaller by sorting files into subdirectories rather having one large directory.
1. What is an inode number?

An inode is an entry in inode table, containing information ( the metadata ) about a regular file and directory. An inode is a data structure on a traditional Unix-style file system such as ext3 or ext4. Linux extended filesystems such as ext2 or ext3 maintain an array of these inodes: the inode table. This table contains list of all files in that filesystem. The individual inodes in inode table have a unique number (unique to that filesystem), the inode number. Diving deep into the inode, an inode stores:

    File type: regular file, directory, pipe etc.
    Permissions to that file: read, write, execute
    Link count: The number of hard link relative to an inode
    User ID: owner of file
    Group ID: group owner
    Size of file: or major/minor number in case of some special files
    Time stamp: access time, modification time and (inode) change time
    Attributes: immutable' for example
    Access control list: permissions for special users/groups
    Link to location of file
    Other metadata about the file

Note that inode does not store name of the file but its content only.
2. How to check inode in Linux

If you want to have a look at inodes, on an Ext file system you can use some commands to check the properties of the file system and files that are used in it.
a. Display file data information

You can display the inode data on a file or directory by using stat command. You need to indicate the name of the file.

#### stat hello

    File: ‘hello’
    Size: 66 Blocks: 8 IO Block: 4096 regular file
    Device: fd01h/64769d Inode: 530461 Links: 2
    Access: (0774/-rwxrwxr--) Uid: ( 0/ root) Gid: ( 0/ root)
    Access: 2017-05-15 20:12:32.540352591 +0000
    Modify: 2017-05-15 20:12:16.901527357 +0000
    Change: 2017-05-19 17:41:37.394470321 +0000
    Birth: -

The stat output tells you the various time-stamps of the file, its ownership and permissions, and where it’s stored. The file’s data is kept in the disk block, which is shown in the inode’s stat command output.

You can choose to list only the inode number of a file with the --format option as below

#### stat --format=%i hello

    530461

#### b. Print the index number of files

The ls command is used to list file/folder information. The -i option with ls displays the inode number of each file. We can combine it with -l option to list information in detail

    ls -il
    total 140984
    520170 dr-xrw-rw- 2 linoadmin linoadmin   4096 Mar  9  2013 asciiquarium_1.1
    263206 -rwxr-xr-x 1 linoadmin linoadmin   15436 Mar  9  2013 asciiquarium.tar.gz
    519187 drwxr----- 2 root      root        4096 Apr 13 01:35 baba
    258717 -rwSr--r-- 1 root      root        5747 Apr 25 01:45 bootstrap
    655799 drwxr-xr-x 2 root      root        4096 May 16 17:46 course
    528927 drwxr-xr-x 3 root      root        4096 Apr 29 00:29 environments

The first column gives the inode number. You can display a particular file's inode as below

#### ls -i continue.sh 

    519450 continue.sh

#### c. Display filesystem inode space information

By default, df command summarizes available and used disk space. You can instead receive a report on available and used inodes by passing the -i or --inodes option.

    df -i
    Filesystem      Inodes  IUsed   IFree IUse% Mounted on
    /dev/vda1      1292800 126091 1166709   10% /
    devtmpfs         60205    319   59886    1% /dev
    tmpfs            62556      1   62555    1% /dev/shm
    tmpfs            62556    367   62189    1% /run
    /dev/vda2          128     13     115   11% /mnt/vda2
    tmpfs            62556      1   62555    1% /run/user/0

This information can be helpful if a partition has very many small files, which can deplete available inodes sooner than they deplete available disk space.

#### d. List the contents of the filesystem superblock

You can use tune2fs -l command to displays all information related to inode.

    tune2fs -l /dev/sda6 | grep inode
    Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super  large_file huge_file uninit_bg dir_nlink extra_isize
    Free inodes:              2224350
    First inode:              11
    Journal inode:            8
    First orphan inode:       1575905
    Journal backup:           inode blocks

#### e. Manipulate the filesystem meta data

you can see the contents of an inode as it exists on an Ext4 file system with debugfs command.  You need to use the stat command that is available in the file system debugger to show the contents of the inode. When done, use exit to close the debugfs environment.

Make sure files on the file system cannot be accessed while working in debugfs. You should consider remounting the file system using mount -o remount /yourfilesystem

    debugfs /dev/sda1
    debugfs 1.42.13 (17-May-2015)
    debugfs: stat <19>
    Inode: 19 Type: regular
    Mode: 0644 Flags: 0x0
    Generation: 2632480000
    User: 0 Group: 0 Size: 8211957
    File ACL: 0 Directory ACL: 0
    Links: 1 Blockcount: 16106
    Fragment: Address: 0 Number: 0 Size: 0
    ctime: 0x48176267 -- Tue Apr 29 14:01:11 2008
    atime: 0x485ea3e9 -- Sun Jun 22 15:11:37 2008
    mtime: 0x48176267 -- Tue Apr 29 14:01:11 2008

    BLOCKS:
    (0-11):22749-22760, (IND):22761, (12-267):22762-23017, (DIND):23018, (IND):23019,
    (268-523):23020-23275, (IND):23276, (524-779):23277-23532, (IND):23533, (780-1035
    ):23534-23789, (IND):23790, (1036-1291):23791-24046, (IND):24047, (1292-1547):
    24048-24303,(IND):24304, (1548-1803):24305-24560, (IND):24561, (1804-1818):24562

You can use debugfs to undelete a file by using its inode and indicating a file

#### 2. Inode structure for directory

As stated above, the directories in Linux are also treated as files. Directory is special file that maps a file name to its inode number (this mapping is called directory entry or dentry). So when we say that a directory contains files and other directories, we mean that this directory is mapping those files and directories (directories are special files, so they also need mapping to their inode numbers) to their inode numbers. This is the reason why a directory cannot hold two files with same name, because it cannot map one name with two different inode numbers.

    ls -ld test/
    drwxr-xr-x 3 root root 4096 Apr 13 01:43 test/

As a file is mapped to its inode by its parent directory, then how is top most directory, (i.e. / directory) mapped to its inode? The inode number of / directory is fixed, and is always 2.

    stat /
    File: '/'
    Size: 4096 Blocks: 8 IO Block: 4096 directory
    Device: 806h/2054d Inode: 2 Links: 27
    Access: (0755/drwxr-xr-x) Uid: ( 0/ root) Gid: ( 0/ root)
    Access: 2017-05-20 01:40:01.565097799 +0100
    Modify: 2017-05-20 01:27:33.651924301 +0100
    Change: 2017-05-20 01:27:33.651924301 +0100
    Birth: -

#### 3. Links and index number in Linux

In the output of ls -l, the column following the permissions and before owner is the link count. Link count is the number of hard links to a file. To understand hard links, we begin with links. A link is a pointer to another file. In Linux world, two types of links exist:

#### a. Symbolic links (or soft links)

The symbolic link is a separate file whose contents point to the linked-to file. To create a symbolic link, use the ln command with the option -s. When using the ln command, make sure that you first refer to the name of the original file and then to the name of the link you want to create.

    ln -s /home/bobbin/sync.sh filesync

Here filesync is a symbolic link to sync.sh. Think about it as a shortcut. Editing filesync is like directly edit the original file but it's really what happen. If we delete or move the original file, the link will be broken and our filesync file will not be longer available.

The ls -l command shows that the resulting file is a symbolic link. This is indicated by the letter l in the first position of the ls -l output and also by the arrow at the end of the listing, which indicates the file the name is referring to.

    ls -l filesync 
    lrwxrwxrwx 1 root root 20 Apr 7 06:08 filesync -> /home/bobbin/sync.sh

The contents of a symbolic link are the name of target file only. You can see that the permissions on the symbolic link are completely open. This is because the permissions are not managed

When comparing the symbolic link and the original file, you will notice a clear difference between them.

    ls -il /home/bobbin/sync.sh filesync 
    258674 lrwxrwxrwx 1 root root 20 Apr 7 06:08 filesync -> /home/bobbin/sync.sh
    517333 -rw-r----- 1 root root 5 Apr 7 06:09 /home/bobbin/sync.sh

The original file is just a name that is connected directly to the inode, and the symbolic link refers to the name. The size of the symbolic link is the number of bytes in the name of the file it refers to, because no other information is available in the symbolic link.

#### b. Hard links

To get an idea of what a hard link is, it is important to understand that the identity of a file is its inode number, not its name. A hard link is a name that references an inode. It means that if file1 has a hard link named file2, then both of these files refer to same inode. So, when you create a hard link for a file, all you really do is add a new name to an inode. To do this, use the ln command without option.

    ls -l /home/bobbin/sync.sh  
    -rw-r----- 1 root root 5 Apr 7 06:09 /home/bobbin/sync.sh

    #### ln /home/bobbin/sync.sh synchro

Now let's compare the two files

    ls -il /home/bobbin/sync.sh synchro 
    517333 -rw-r----- 2 root root 5 Apr 7 06:09 /home/bobbin/sync.sh
    517333 -rw-r----- 2 root root 5 Apr 7 06:09 synchro

The interesting thing about hard links is that there is no difference between the original file and the link: they are just two names connected to the same inode.

As you must have noted, unlike soft links, hard links are no special files. Now, link count is the number a file has been hard linked. So a link count increases after creating a hard link as you can see in the above figure. These hard links have two limitations:

The directories cannot be hard linked. Linux does not permit this to maintain the acyclic tree structure of directories.
A hard link cannot be created across filesystems. Both the files must be on the same filesystems, because different filesystems have different independent inode tables (two files on different filesystems, but with same inode number will be different).

#### 3. How to find hard link in Linux

You can retrieve all filename which point to an inode number. It means that you can retrieve hard links because it is the only type of link where we can have some filenames which point to the same content (inode). You can do it with the -inum option of find command as below

    find / -inum 517333
    /home/bobbin/sync.sh
    /root/synchro

With this, you can know which filenames point to the data information so, retrieve all hard link relative to a specific inode number

#### 4. Linux operations with files and its relation with inodes

Most of the operations (such as copy) performed on soft links will affect the actual linked file (with the exception of rm or mv commands, which remove (or move) soft link itself)

Here are some file operations in which inodes play their vital role:

#### a. copy files

When we copy a file, a new file with a new inode is created.

#### cp myfile ..

    ls -li myfile ../myfile
    2501 -rw------- 1 raghu raghu 36 Jun 25 20:12 myfile
    3746 -rw------- 1 raghu raghu 36 Jan 11 12:05 ../myfile

#### b. move files

When moving across filesystems, mv command proceeds as cp command above, with the exception that the original file is removed from its location. But when moving within a filesystem, the inode does not change, only the directory mapping of the inode is changed, the actual data on the hard disk (contents of the file) does not move.

    ls -li samplefile.txt
    2497 -rw------- 1 raghu raghu 22 Jun 25 20:12 samplefile.txt

Now let's move the file and check the result

#### mv samplefile.txt ..

    ls -li ../samplefile.txt
    2497 -rw------- 1 raghu raghu 22 Jun 25 20:12 ../samplefile.txt

#### c. remove files

When rm command is issued, first it checks the link count of the file. If the link count is greater than 1, then it removes that directory entry and decreases the link count. Still, data is present, nor is the inode affected. And when link count is 1, the inode is deleted from the inode table, inode number becomes free, and the data blocks that this file was occupying are added to the free data block list.

    ls -li myfile myfile.hardlink
    2501 -rw------- 2 raghu raghu 36 Jun 25 2012 myfile
    2501 -rw------- 2 raghu raghu 36 Jun 25 2012 myfile.hardlink

Let's delete the file and check the result

#### rm myfile.hardlink

    ls -li myfile
    2501 -rw------- 1 raghu raghu 36 Jun 25 2012 myfile

You can see that the number of inode is decreased.
Conclusion

Every Linux file has an inode, and the inode contains all properties of the file, but not the file name. A symbolic link is like a shortcut which points to the original file while a hard link is like a copy of the file that is synchronized continuously. There is no difference between the original file and the hard link; they both refer to the same. You can do some manipulations on inode.


https://linoxide.com/linux-command/linux-inode/
