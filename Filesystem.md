# The Linux Filesystem

## Definitions:

* **Partition:** A physically contiguous section of the hard disk, allocated for a specific purpose. 

* **Filesystem:** A method for storing and finding files on a hard disk. A filesystem is located within a partition, unless symbolic links are used. 


## Differences Between Linux and Windows:
|                                  | Windows     | Linux                  |
| -------------------------------- | ----------- | ---------------------- |
| Partition                        | Disk1       | /dev/sda1              |
| Filesystem Type                  | NTFS/VFAT   | EXT3/EXT4/XFS/BTRFS... |
| Mounting Parameters              | DriveLetter | MountPoint             |
| Base Folder (where OS is stored) | C:\         | /                      |

- - - -

## The FHS (Filesystem Hierarchy Standard)

![Image of the FHS Root Directory](FHS.jpg)

Files that are important to Linux systems are stored according to a standard layout called the FHS, which has long been maintained by the Linux organization. Having a standard makes it easier to move between distributions without having to re-learn system organization. 

### Few Key Features:

* The '/' character seperates paths and doesn't have drive letters.

* Multiple drives and/or partitions are mounted as directories in the filesystem. 

* Removable media will be found in the '/run/media' directory.

*  Many systems distinguish between core utilities needed for system operation and other utilities by placing the latter in directories under '/usr'.

- - - - -

## Key Directories:

| Directory Name | Usage |
| -------------- | ----- |
| **/bin** | Contains executable binaries, essential commands used to boot up the system, and essential commands required by all system users. |
| **/boot** | Contains the few essential files needed to boot the system. For every alternative kernel installed, there are 4 corresponding elements: '*vmlinuz*', the compressed Linux kernel required for booting, '*initramfs*', the initial file system required for booting, '*config*', the kernel configuration file, and '*System.map*', the Kernel symbol table. GRUB files are also located here. |
| **/dev** | Contains device nodes created by the udev device manager, such as a printer or hard disk partition. It is empty when not mounted. |
| **/etc** | The home for system-wide configuration files,such as user accounts and files telling where to go on the the network to obtain IP address mappings. Only the superuser can modify files there. |
| **/home** | Stores the home directories for each user, except the root user. |
| **/lib** | Contains libraries for the essential programs in */bin* and */sbin*. Some Linux systems contain a */lib64* filesystem containing the 64-bit libraries. The */lib* filesystem would contain the 32-bit libraries. Also contains kernel modules such as device drivers. |
| **/media** (**/run**) | Contains mounted removable media. |
| **/mnt** | Used for temporarily mounting filesystems. Can be used on removable media, but is more often used for network file systems (NFSs). |
| **/opt** | Optional application software packages. |
| **/proc** | Called a pseudo-filesystem because it has no permanent presence anywhere on the disk. Contains virtual files consisting of runtime system information that permit viewing constantly changing kernel data. |
| **/root** | The home directory of the root user. |
| **/sys** | Virtual pseudo-filesystem giving information about the system and the hardware. Can be used to alter system parameters and for debugging purposes. |
| **/srv** | Site-specific data served up by the system. Seldom used. |
| **/tmp** | Temporary files; on some distributions erased across a reboot and/or may actually be a ramdisk in memory. |
| **/usr** | Multi-user applications, utilities and data. Contains non-essential versions of some key directories. |
| **/sbin** | Contains essential binaries related to system administration. | 
| **/var** | Contains files that expected to change in size and content as the system is running, such as print queues, database files, and temporary files. Network services directories are also found here. |

- - - - -

## Mounting and Unmounting a Filesystem:

Mounting is very useful to make files and directories on a storage device available for users to access via the file system. Before being able to use a filesystem, it needs to be mounted to the filesystem tree at a mount point (directory). If a filesystem
is mounted on a non-empty directory. The contents of that directory are covered up and not accessible until the filesystem is unmounted.

```bash
    sudo mount { pathname } /home
```

In the example above, the specified directory will be mounted onto the home directory.

```bash
    sudo umount /home
```

The directory can be unmounted by specifying *umount*, not **unmount**.

```bash
    df -Th
``` 

For the filesystem to be automatically mounted every time during startup, the filesystem table located at */etc/fstab* needs to be modified. **disk-free** will display information about mounted filesystems, including filesystem type and usage statistics. 

- - - - -

## NFS (Network File System):

NFS provides an easy way to share content across devices connected by a local network.  

```bash
    sudo systemcl start nfs
    studo systemcl enable nfs
```

The above commands start NFS and enable NFS at startup, respectively. To enable a directory to be exported, it must
be added to the */etc/exports* file. 

**Examples:**
> /projects *.example.com(rw) 

/projects is hosted on example.com for reading and writing.
  
> /projects 192.168.0.3(rwx)

/projects is available to the specified client IP address on the local network for reading, writing, and execution.

```bash
    exportfs -av
    sudo systemctl restart nfs
```

Once the */etc/exports* file has been modified, Linux can be notified of the file changes, or the NFS program can be restarted. Restarting does take much longer, though.

```bash
    mount example.com:/projects ~/user-projects
```

Once the files have been exported, the client machine must mount the exported directory by using **mount**.