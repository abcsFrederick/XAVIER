# <code>xavier <b>unlock</b></code>

## 1. About

The `xavier` executable is composed of several inter-related sub commands. Please see `xavier -h` for all available options.

This part of the documentation describes options and concepts for <code>xavier <b>unlock</b></code> sub command in more detail. With minimal configuration, the **`unlock`** sub command enables you to unlock a pipeline output directory.

If the pipeline fails ungracefully, it maybe required to unlock the working directory before proceeding again. Snakemake will inform a user when it maybe necessary to unlock a working directory with an error message stating: `Error: Directory cannot be locked`.

Please verify that the pipeline is not running before running this command. If the pipeline is currently running, the workflow manager will report the working directory is locked. The is the default behavior of snakemake, and it is normal. Do NOT run this command if the pipeline is still running! Please kill the master job and it's child jobs prior to running this command.

Unlocking xavier pipeline output directory is fast and easy! In its most basic form, <code>xavier <b>unlock</b></code> only has _one required input_.

## 2. Synopsis

```text
$ xavier unlock [-h] --output OUTPUT
```

The synopsis for this command shows its parameters and their usage. Optional parameters are shown in square brackets.

A user **must** provide an output directory to unlock via `--output` argument. After running the unlock sub command, you can resume the build or run pipeline from where it left off by re-running it.

Use you can always use the `-h` option for information on a specific command.

### 2.1 Required Arguments

`--output OUTPUT`

> **Output directory to unlock.**  
> _type: path_
>
> Path to a previous run's output directory. This will remove a lock on the working directory. Please verify that the pipeline is not running before running this command.  
> **_Example:_** `--output /data/$USER/WES_hg38`

### 2.2 Options

Each of the following arguments are optional and do not need to be provided.

`-h, --help`

> **Display Help.**  
> _type: boolean_
>
> Shows command's synopsis, help message, and an example command
>
> **_Example:_** `--help`

## 3. Example

```bash
# Step 0.) Grab an interactive node (do not run on head node)
sinteractive --mem=8g -N 1 -n 4
module purge
module load ccbrpipeliner

# Step 1.) Unlock a pipeline output directory
xavier unlock --output /data/$USER/xavier_hg38
```
