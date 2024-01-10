# Xenonstack-task-Linux
# internsctl - Custom Linux Command

## Description

`internsctl` is a custom Linux command designed for intern operations. This command provides various functionalities to manage CPU information, memory information, user operations, and file details. The current version is v0.1.0.

## Section A

### 1. Manual Page

To view the manual page, execute the following command:

```bash
man internsctl
```

This will display the full documentation and usage guidelines for the command.

### 2. --help Option

To get usage examples and help information, use the following command:

```bash
internsctl --help
```

This will provide you with necessary usage guidelines and examples.

### 3. --version Option

To see the version of the command, execute:

```bash
internsctl --version
```

## Section B

### Part1 | Level Easy

#### a. Get CPU Information

To obtain CPU information, use the following command:

```bash
internsctl cpu getinfo
```

The output will be similar to the information obtained from the `lscpu` command.

#### b. Get Memory Information

To retrieve memory information, run the following command:

```bash
internsctl memory getinfo
```

The output will be similar to the information obtained from the `free` command.

### Part2 | Level Intermediate

#### a. Create User

To create a new user with login access, use:

```bash
internsctl user create <username>
```

This command will create a user with access to the Linux system and their home directory.

#### b. List Regular Users

To list all regular users, execute:

```bash
internsctl user list
```

#### c. List Users with Sudo Permissions

To list users with sudo permissions, use:

```bash
internsctl user list --sudo-only
```

### Part3 | Advanced Level

#### Get File Information

To get information about a file, execute:

```bash
internsctl file getinfo <file-name>
```

The output will be displayed in the specified format.

#### Using Options for Specific Information

- To obtain the size of the specified file only:

```bash
internsctl file getinfo --size <file-name>
```

- To obtain the permissions of the specified file only:

```bash
internsctl file getinfo --permissions <file-name>
```

- To obtain the owner of the specified file only:

```bash
internsctl file getinfo --owner <file-name>
```

- To obtain the last modified time of the specified file only:

```bash
internsctl file getinfo --last-modified <file-name>
```

```bash
#!/bin/bash

# internsctl - Custom Linux Command for Intern Operations

# Function to display the manual page
display_manual() {
    echo "internsctl(1) - Custom Linux Command for Intern Operations"
    echo
    echo "NAME"
    echo "    internsctl - Manage intern operations"
    echo
    echo "SYNOPSIS"
    echo "    internsctl [OPTIONS] [ARGUMENTS]"
    echo
    echo "DESCRIPTION"
    echo "    internsctl is a custom Linux command for managing intern operations."
    echo
    echo "OPTIONS"
    echo "    --help        Display this help message"
    echo "    --version     Display the version of internsctl"
    echo
    echo "EXAMPLES"
    echo "    internsctl --help"
    echo "    internsctl --version"
    echo "    internsctl cpu getinfo"
    echo "    internsctl user create <username>"
    echo "    internsctl user list --sudo-only"
    echo "    internsctl file getinfo [options] <file-name>"
    echo
    echo "AUTHOR"
    echo "    Your Name <your.email@example.com>"
}

# Function to display the help message
display_help() {
    echo "Usage: internsctl [OPTIONS] [ARGUMENTS]"
    echo "Manage intern operations."
    echo
    echo "OPTIONS:"
    echo "    --help        Display this help message"
    echo "    --version     Display the version of internsctl"
    echo
    echo "EXAMPLES:"
    echo "    internsctl --help"
    echo "    internsctl --version"
    echo "    internsctl cpu getinfo"
    echo "    internsctl user create <username>"
    echo "    internsctl user list --sudo-only"
    echo "    internsctl file getinfo [options] <file-name>"
    echo
    echo "AUTHOR"
    echo "    Your Name <your.email@example.com>"
}

# Function to display the version
display_version() {
    echo "internsctl v0.1.0"
}

# Function to get file information
get_file_info() {
    if [ -z "$1" ]; then
        echo "Error: Missing file name"
        display_help
        exit 1
    fi

    echo "Getting information for file: $1"
    # Add your logic here to get file information
}

# Main script

# Check for the number of arguments
if [ "$#" -eq 0 ]; then
    display_help
    exit 1
fi

# Parse command line arguments
while [[ $# -gt 0 ]]; do
    case "$1" in
        --help)
            display_help
            exit 0
            ;;
        --version)
            display_version
            exit 0
            ;;
        file)
            shift
            case "$1" in
                getinfo)
                    shift
                    get_file_info "$1"
                    exit 0
                    ;;
                *)
                    echo "Error: Unknown subcommand '$1' for 'file'"
                    display_help
                    exit 1
                    ;;
            esac
            ;;
        *)
            echo "Error: Unknown option '$1'"
            display_help
            exit 1
            ;;
    esac
    shift
done
```
