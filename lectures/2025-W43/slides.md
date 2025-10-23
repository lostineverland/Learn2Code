## Command Line Part I

  - Login to GitHub
  - go to CodeSpaces
  > https://github.com/codespaces

Notes:
  - 2 references added:
    - CLI Tutorial
    - Plain Text Project

    ---slide---

  - Why?
    - GUI vs. CLI
    - Learning Curve
    - Repeatable
    - Scriptable
    - Automatable

    ---slide---

  - Unix Principle
  > Write programs that do one thing and do it well. Write programs to work together.

    ---slide---

  Instead of one program that can "process data," Unix gives you:
  - `grep` - finds patterns in text
  - `sort` - puts lines in order
  - `uniq` - removes duplicates
  - `wc` - counts words, lines, characters
  - `head`/`tail` - shows the beginning or end of files

  Each tool is simple. The power comes from **combining** them.

    ---slide---

  ## Programs
  - A program is simply **a set of instructions that tells the computer what to do**.
  - GUI: you double-click an app icon, you're running a program
  - CLI: you type a command in the terminal, you're also running a program.

    ---slide---

  ### Programs Have Three Parts

  1. **Input** - Data going in (keyboard typing, files, network data)
  2. **Processing** - The program does something with that data
  3. **Output** - Results coming out (displayed on screen, saved to files, sent over network)

    ---slide---

  ### Example: A Simple Program

  ```bash
  date
  ```

  - **Input**: Current time from your computer's clock
  - **Processing**: Formats the time in human-readable form
  - **Output**: Displays the date and time

Notes:
  - date -I
  - date -Ihours
  - date -Iseconds

    ---slide---

  ## How Programs Are Accessible

  When you type a command like `python` or `git`, how does your computer know where to find that program?

  ```bash
  echo $PATH
  which git
  ```
    ---slide---

  ### Executable Files

  Programs are just files on your computer. But not all files can be run as programs. Executable files are special files that:
  - Contain instructions your computer can understand
  - Have permission to be executed
  - Live in specific locations your system knows about

  ```bash
  ls -l $(which git)
  ```

    ---slide---
    ---slide---