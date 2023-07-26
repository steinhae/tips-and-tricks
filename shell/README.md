# Shell Commands to Remember

This document contains a list of important and frequently used shell commands. 

## SSH and Tar 

The command below uses SSH to connect to a remote server and tar to compress a directory. The compressed file is then piped back and extracted on the local machine.

```bash
ssh [USER]@[HOST] "tar -C [PATH] -zc [DIR]" | tar xz
```
