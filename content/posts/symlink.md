---
author: ["Munjung Kim"]
title: "How to use symbolic link"
date: "2024-06-08"
description: ""
summary: "Symlink is a file that links the path to another directory. It is helpful to manage the disk space efficiently. "
tags: [ "linux"]
categories: ["tools"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
math: true
---


## What is Symlink?

Symlink is a file that points to the original file or directory path. 


## Why Should We Use Symlink?
By using symlink, you can avoid duplicating data, organize files efficiently, and save disk space.

## Example

### Hypothetical File Structure

Suppose you have the following directory strucrture on your computer:

```
/home/
│
├── user/
│   ├── documents/
│   │   ├── report.txt
│   │   └── notes.txt
│   │
│   └── projects/
│       └── project1/
│           ├── data.csv
│           └── analysis.py
```

### Creating a Symlink

Let's say you frequently need to access `data.csv` from the `projects/project1/` directory while working in the `documents` directory. To make this easier, you can create a symlink in `documents` folder that points directly to `data.csv`.
From your terminal, you would first navigate to the documents directory:


###  Commands to Create the Symlink

First, you should go to the directory (`documents`) that you want to link the targeted file (`data.csv`). 

```
cd /home/user/documents
```

Then, you can createw the symlink by using the following command:

```linux
ln -s ../projects/project1/data.csv data_link.csv
```

### Updated File Structure with Symlink

Now your directory structure looks like this:

```
/home/
│
├── user/
│   ├── documents/
│   │   ├── report.txt
│   │   ├── notes.txt
│   │   └── data_link.csv -> ../projects/project1/data.csv
│   │
│   ├── photos/
│   │   └── vacation/
│   │       ├── img001.jpg
│   │       └── img002.jpg
│   │
│   └── projects/
│       └── project1/
│           ├── data.csv
│           └── analysis.py
```

## How the Symlink Works?

The symlink `data_link.csv` in the `documents` directory doesn't contain the data itself but is merely a reference to `data.csv` located in `/home/user/projects/project1/`. When you access `data_link.csv`, the operating system redirects you to the original `data.csv` file. If `data.csv` is updated, those changes will appear when accessing it through `data_link.csv` as well.

## Viewing the Contents of the Symlink

If you run a command to view the contents of `data_link.csv`, such as:

```
cat data_link.csv
```

This will display the contents of `data.csv`, because the symlink directs to that file. 

## What Happens When the Linked File is Deleted?

When the target of symbolic link (symlink) is deleted, the symlink becomes whawt is commonly referred to as a "dangling link" or "broken link". This means that the symlink still exists but points to a non-existent file or directory.

To prevent issues related to danglink symlinks, especially in scripts or automated systems, it's good practice to check that a symlink's target exits before accessing it. 


## How to Check the Existing Symlinks?

If you want to see details about files and symlinks in a directory, you could use `ls -l` like this:

```
ls -l /path/to/directory
```