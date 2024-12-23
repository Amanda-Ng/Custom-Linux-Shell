# Cook: A Simplified `make` Program for Parallel Task Scheduling

## Introduction

The **Cook** program is a simplified version of `make` that schedules and executes tasks based on dependencies, leveraging Unix/POSIX system calls. It enables parallel execution of jobs up to a specified maximum, ensuring task dependencies are respected.

This program was developed to familiarize users with:

- **Process management:** forking, executing, and reaping processes.
- **Signal handling:** managing inter-process communication using signals.
- **I/O redirection:** using system calls like `dup2`.
- **Concurrency:** scheduling parallel tasks efficiently within constraints.
- **Unix programming:** working with C libraries and system calls.

## Features

- Executes a series of tasks specified in a **cookbook file**.
- Manages task dependencies and processes tasks in the correct order.
- Utilizes parallelism to maximize efficiency, constrained by a configurable number of "cooks".
- Implements pipelines for tasks with multiple steps.
- Handles I/O redirection for task steps.

## Usage

cook [-f cookbook] [-c max_cooks] [main_recipe_name]

### Arguments:

- `-f cookbook`: Specifies the cookbook file. Defaults to `cookbook.ckb` in the current directory if omitted.
- `-c max_cooks`: Sets the maximum number of parallel cooks (default is 1, for sequential execution).
- `main_recipe_name`: Specifies the main recipe to be executed. If omitted, the first recipe in the cookbook is used.

## Cookbook File Format

The cookbook file defines recipes and tasks in a format inspired by Makefiles:

- Each recipe starts with a header: `recipe_name: sub_recipe1 sub_recipe2 ...`.
- Task definitions follow, listing commands to be executed for the recipe.
- Tasks may include input/output redirection or pipelines using `|`, `<`, and `>`.
