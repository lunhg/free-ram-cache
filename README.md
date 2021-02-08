# FREE-RAM-CACHE

*free-ram* is a `bash` script to automatically free ram cache, according [this procedure](https://www.tecmint.com/clear-ram-memory-cache-buffer-and-swap-space-on-linux). You can choose to free:

    - Page cache
    - Dentries and inodes
    - Page cache / dentries and inodes
    - swap

# Instalation

```bash
$ git clone https://github.com/lunhg/free-ram-cache.git
$ cd free-ram-cache
$ chmod 755 free-ram-cache
```

You can move it to your file system (e.g., `/usr/local/bin`)

## Usage

WARNING: this script require `su` authentication (not `sudo`).

```
Free ram space
Usage: free-ram [OPTIONS, [ARGS]] <file>

Options

-h | --help                show this message
-v | --version             show version
-c | --cache=[ARG]         clear ram cache
                           (
                             1=page-cache;
                             2=dentries and inodes;
                             3=page-cache, dentries and inodes
                           )
-s | --swap                clear swap
```

As [tecmint's editor](https://www.tecmint.com/author/avishek/):

> If you have to clear the disk cache, the first command is safest in enterprise and production as “...echo 1 > ….” will clear the PageCache only. It is not recommended to use third option above “...echo 3 >” in production until you know what you are doing, as it will clear PageCache, dentries and inodes.
> Is it a good idea to free Buffer and Cache in Linux that might be used by Linux Kernel?
>
> When you are applying various settings and want to check, if it is actually implemented specially on I/O-extensive benchmark, then you may need to clear buffer cache. You can drop cache as explained above without rebooting the System i.e., no downtime required.

So,  test first  with:

```bash
$ ./free-ram-cache --cache=1
# OR
$ ./free-ram-cache --cache=1 --swap
# Then check it
$ free -h
```
