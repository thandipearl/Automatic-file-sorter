# Automatic-file-sorter

# Automatic File Sorter in File Explorer

An automated Python scripting solution designed to instantly clean, organize, and manage cluttered directories. This project demonstrates how to use Python's built-in operating system libraries to eliminate manual file management workflows by automatically sorting files into dedicated asset folders based on their file extensions.

## Project Overview

Cluttered folders (such as "Downloads" or active local working directories) slow down productivity and complicate data retrieval. This script acts as a localized automation agent that scans a target path, dynamically detects unorganized files, creates an optimized subdirectory structure, and moves files into their respective homes without human intervention.

## Core Logic & Architecture

The automation operates via a two-phase loop structure:
1. **Directory Auditing & Creation:** Checks the designated path for required structural folders (`csv files`, `pdf files`, `docx files`, `image files`, etc.). If a folder is missing, the script dynamically initializes it using safe operating system methods.
2. **File Extension Mapping:** Iterates through every object in the parent directory, reads its file format syntax, verifies that the file doesn't already exist in the destination path, and executes a clean, secure file migration.

## Tech Stack & Libraries

* **Python 3.x** – Core programming language
* **`os` Module** – For scanning workspace environments, validating local paths, and directory generation
* **`shutil` Module** – For executing high-level, secure file transfer and migration actions

## How It Works (Code Breakdown)

```python
import os, shutil

# Define target working directory
path = r"H:/when they ask for my transcript/"
file_name = os.listdir(path)

# Initialize standardized folder taxonomy 
folder_names = ['csv files', 'large files', 'text files', 'pdf files', 'docx files', 'image files']

# Step 1: Automate sub-folder creation
for loop in range(0, 6):
    if not os.path.exists(path + folder_names[loop]):
       os.makedirs(path + folder_names[loop])

# Step 2: Parse and safely migrate files based on specific file extensions
for file in file_name:
    if ".csv" in file and not os.path.exists(path + 'csv files/' + file):
       shutil.move(path + file, path + 'csv files/' + file)
    elif ".PNG" in file and not os.path.exists(path + 'image files/' + file):
       shutil.move(path + file, path + 'image files/' + file)
    elif ".xlsx" in file and not os.path.exists(path + 'text files/' + file):
       shutil.move(path + file, path + 'text files/' + file)
    elif ".pdf" in file and not os.path.exists(path + 'pdf files/' + file):
       shutil.move(path + file, path + 'pdf files/' + file)
    elif ".docx" in file and not os.path.exists(path + 'docx files/' + file):
       shutil.move(path + file, path + 'docx files/' + file)
    else:
        print("There are files in this path that were not moved!")
