# Freshworks Software Academy + Pupilfirst

Hello there!

In this test, we want to see how you implement a command-line (CLI) program that lets you manage your todos.

The specification for this problem is written down as tests. Since we haven't actually implemented anything, the tests are currently failing. You have to solve the problem by implementing the application and getting all the tests to pass.

Here's a video that shows how your application should work when you're done:

https://vimeo.com/490621534

## Getting started

1. Install Ruby: You need to have ruby installed in your computer for this problem.

   You may already have Ruby installed on your computer. You can check inside a terminal by typing:

   ```
   ruby -v
   ```

   This should output some information on the installed Ruby version.
   You can also install ruby by following these instructions: https://www.ruby-lang.org/en/documentation/installation/

2. You are expected to write the code in `todo.rb` file.

3. Once you are done with the changes you should be able to execute the todo app by running the following command from the terminal.

   **On Windows:**

   ```
   .\todo.bat
   ```

   **On Linux, or macOS:**

   ```
   ./todo.sh
   ```

## Run Automated Tests

### 1. Install Node.js

You need to have npm installed in your computer for this problem. It comes with Node.js and you can get it by installing Node from https://nodejs.org/en/

### 2. Install dependencies

Run `npm install` to install all dependencies.

### 3. Create Create symbolic link to the executable file

#### On Windows

To create a symbolic link on Windows, you'll need to run either the Windows Command Prompt, or Windows Powershell **with administrator privileges**. To do so, right-click on the icon for Command Prompt, or Powershell, and choose the _"Run as Administrator"_ option.

**Command Prompt:**

```
> mklink todo todo.bat
```

**Powershell:**

```
> cmd /c mklink todo todo.bat
```

#### On Linux, or macOS:

Run the following command in your shell:

```
$ ln -s todo.sh todo
```

### 4. Try running tests.

Now run `npm test` and you will see all the tests failing. As you fill in each functionality, you can re-run the tests to see them passing one by one.

## A Note about `/` for Windows Users

In the following sections, you'll see many commands prefixed with `./`, or paths containing the `/` (forward-slash) character.

If you're using the Windows _Command Prompt_, then you'll need to replace `/` with `\` (back-slash) for these commands and paths to work as expected.

On Windows _Powershell_, these substitutions are not required.

## Known Issues

A few notes to help you avoid any hiccups while implementing the programming challenge:

1. If you are on Windows, you might have difficulty getting the tests to pass because of newline UTF encoding issues. If you get stuck, please [refer to the thread here](https://github.com/nseadlc-2020/package-todo-cli-task/issues/12).

2. The tests can fail between 12am and 5.30am (early morning IST). This is because the test parses the date from your system time in UTC format, while in certain programming languages the date and time functions use the local timezone (IST). Accounting for this in the tests will make it more complex and need extra dependencies, so we have kept it intentionally simple. So if you run into this specific problem, you can submit your code as is with the transient date mismatch, or you can change your code to use UTC. Either options are fine.

3. In Windows machines, the `make` command might not exist and can prevent you from running the tests. This can be fixed [by using WSL, or installing MinGW, among other options](https://stackoverflow.com/questions/32127524/how-to-install-and-use-make-in-windows).

## Specification

1. The app can be run in the console with `./todo`.

2. The app should read from and write to a `todo.txt` text file. Each todo item occupies a single line in this file. Here is an example file that has 2 todo items.

```txt
water the plants
change light bulb
```

3. When a todo item is completed, it should be removed from `todo.txt` and instead added to the `done.txt` text file. This file has a different format:

    ```txt
    x 2020-06-12 the text contents of the todo item
    ```

    1. the letter x
    2. the current date (UTC/GMT) in `yyyy-mm-dd` format
    3. the original text

    The date when the todo is marked as completed is recorded in the `yyyy-mm-dd` format (ISO 8601). For example, a date like `15th August, 2020` is represented as `2020-08-15`.

4. The application must open the files `todo.txt` and `done.txt` from where the app is run, and not where the app is located. For example, if we invoke the app like this:

    ```
    $ cd /path/to/plans
    $ /path/to/apps/todo ls
    ```

    The application should look for the text files in `/path/to/plans`, since that is the user’s current directory.

## Usage

### 1. Help

Executing the command without any arguments, or with a single argument `help` prints the CLI usage.

```
$ ./todo help
Usage :-
$ ./todo add "todo item"  # Add a new todo
$ ./todo ls               # Show remaining todos
$ ./todo del NUMBER       # Delete a todo
$ ./todo done NUMBER      # Complete a todo
$ ./todo help             # Show usage
$ ./todo report           # Statistics
```

### 2. List all pending todos

Use the `ls` command to see all the todos that are not yet complete. The most recently added todo should be displayed first.

```
$ ./todo ls
[2] change light bulb
[1] water the plants
```

### 3. Add a new todo

Use the `add` command. The text of the todo item should be enclosed within double quotes (otherwise only the first word is considered as the todo text, and the remaining words are treated as different arguments).

```
$ ./todo add "the thing i need to do"
Added todo: "the thing i need to do"
```

### 4. Delete a todo item

Use the `del` command to remove a todo item by its number.

```
$ ./todo del 3
Deleted todo #3
```

Attempting to delete a non-existent todo item should display an error message.

```
$ ./todo del 5
Error: todo #5 does not exist. Nothing deleted.
```

### 5. Mark a todo item as completed

Use the `done` command to mark a todo item as completed by its number.

```
$ ./todo done 1
Marked todo #1 as done.
```

Attempting to mark a non-existed todo item as completed will display an error message.

```
$ ./todo done 5
Error: todo #5 does not exist.
```

### 6. Generate a report

Use the `report` command to see the latest tally of pending and completed todos.

```
$ ./todo report
yyyy-mm-dd Pending : 1 Completed : 4
```

## Before submitting your work...

Once you're done working on this app, create a new ZIP file of this directory after removing any binary files, or dependencies like `node_modules` from your directory. The zipped directory should contain only text files like the `todo.rb`, `README.md`, etc.

Use your full name as the name of the ZIP file, and upload your work as a DM to _Hari_ on Slack.
