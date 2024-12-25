# Chmod

## Introduction

`chmod` is a command in Linux and other Unix-like operating systems that allows you to change the permissions of a file or directory. The name `chmod` stands for "change mode", and it is used to change the access permissions of a file or directory.

permissions are divided into three categories:

- **User**: The owner of the file or directory.
- **Group**: A group of users that have been assigned to the file or directory.
- **Others**: All other users on the system.

## Syntax

The basic syntax of the `chmod` command is as follows:

```bash
chmod [options] mode file
```

## Symbolic (Text) Mode

The symbolic mode is a combination of the letters `u` (user), `g` (group), `o` (others), `a` (all), `r` (read), `w` (write), `x` (execute), and the operators `+` (add), `-` (remove), and `=` (set exact permissions).

```bash
chmod [OPTIONS] [ugoa...][[+-=][rwxXstugo...]...][,...] FILE
```

### Examples

- Give the owner read and write permissions:
```bash
chmod u+rw file.txt
```

- Remove the execute permission from the group:
```bash
chmod g-x file.txt
```


## Numeric Mode

The numeric mode is a three-digit octal number. Each digit represents the permissions for the owner, group, and others.

```bash
chmod [OPTIONS] MODE FILE
```

The NUMBER can be a 3 or 4-digits number:

Each digit in the NUMBER represents the permissions for the owner, group, and others, respectively.

- r (read) = 4
- w (write) = 2
- x (execute) = 1
- no permission = 0

### Examples

- Owner: rwx=4+2+1=7
- Group: r-x=4+0+1=5
- Others: r-x=4+0+1=5

```bash
chmod 755 file.txt
```

## Reference

- [Linux chmod Command](https://linuxize.com/post/chmod-command-in-linux/)