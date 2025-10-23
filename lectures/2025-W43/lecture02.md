# Command Line

## The Unix Philosophy: Do One Thing Well

In the 1970s, the creators of Unix established a simple but powerful principle:

> Write programs that do one thing and do it well. Write programs to work together.

This philosophy shapes how we interact with computers through the command line. Instead of having one massive program that tries to do everything, Unix systems provide many small, focused tools that can be combined in creative ways.

### The Philosophy in Practice

Instead of one program that can "process data," Unix gives you:
- `grep` - finds patterns in text
- `sort` - puts lines in order
- `uniq` - removes duplicates
- `wc` - counts words, lines, characters
- `head`/`tail` - shows the beginning or end of files

Each tool is simple. The power comes from **combining** them.

## What Are Programs?

A program is simply **a set of instructions that tells the computer what to do**. When you double-click an app icon, you're running a program. When you type a command in the terminal, you're also running a program.

### Programs Have Three Parts

1. **Input** - Data going in (keyboard typing, files, network data)
2. **Processing** - The program does something with that data
3. **Output** - Results coming out (displayed on screen, saved to files, sent over network)

### Example: A Simple Program

```bash
date
```

- **Input**: Current time from your computer's clock
- **Processing**: Formats the time in human-readable form
- **Output**: Displays the date and time

Try it in your terminal right now. That's a program.

### Types of Programs

**Command-line programs** (what we're learning):
- Run in the terminal
- Text input and output
- Fast and automatable
- Examples: `ls`, `grep`, `git`, `python`

**Graphical programs** (what you're used to):
- Windows, buttons, menus
- Mouse and keyboard input
- Examples: Word, Chrome, Photoshop

The same tasks can often be done either way, but command-line programs are easier to automate and combine.

## How Programs Are Accessible

When you type a command like `python` or `git`, how does your computer know where to find that program?

### Executable Files

Programs are just files on your computer. But not all files can be run as programs. Executable files are special files that:
- Contain instructions your computer can understand
- Have permission to be executed
- Live in specific locations your system knows about

### The PATH: How Your Computer Finds Programs

Your computer has a special variable called `PATH` that lists directories where programs live. When you type a command, your computer searches these directories in order until it finds a matching program.

**View your PATH:**
```bash
echo $PATH
```

You'll see something like:
```
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

These are directories separated by colons (`:`). Common locations:
- `/usr/bin` - Standard system programs
- `/usr/local/bin` - User-installed programs
- `/bin` - Essential system programs

### Finding Programs

**Check if a program exists and where it lives:**
```bash
which python
which git
which grep
```

**See what a program is:**
```bash
type ls
type cd
type python
```

**Find out more about a program:**
```bash
file $(which python)
```

### Installing New Programs

When you install software, the installer typically:
1. Copies the program file to a directory in your PATH (like `/usr/local/bin`)
2. Makes the file executable
3. Now you can run it from anywhere by typing its name

### Understanding Commands vs Programs

Not everything you type is a program file:
- **Programs**: `ls`, `grep`, `python` (actual files on disk)
- **Built-in commands**: `cd`, `echo`, `alias` (built into the shell itself)
- **Aliases**: Shortcuts you or your system define

Use `type <command>` to find out what something is.

---

**Key Takeaways:**
- Unix philosophy: small, focused tools that combine well
- Programs are executable files that process input into output
- Your PATH tells the computer where to find programs
- Use `which` and `type` to discover what commands actually are

<!-- Class ended here -->


## Standard Streams: How Programs Communicate

Every program has three communication channels built in. Understanding these is crucial for using the command line effectively.

### The Three Standard Streams

1. **stdin (Standard Input)** - Channel 0
   - Where the program reads input from
   - Usually your keyboard
   - Can be redirected from files or other programs

2. **stdout (Standard Output)** - Channel 1
   - Where the program writes normal output
   - Usually your screen
   - Can be redirected to files or other programs

3. **stderr (Standard Error)** - Channel 2
   - Where the program writes error messages
   - Usually your screen (same as stdout)
   - Separate channel so errors don't mix with normal output

### Why Three Channels?

Having separate channels for output and errors lets you:
- Save results to a file while still seeing errors on screen
- Process successful output without error messages getting in the way
- Chain programs together while handling errors appropriately

### Seeing Streams in Action

**Normal output goes to stdout:**
```bash
echo "Hello, World!"
```

**Errors go to stderr:**
```bash
ls /nonexistent_directory
```

**Some programs read from stdin:**
```bash
cat
# Type something and press Enter
# Press Ctrl+D to end input
```

## Piping and Composition: The Unix Superpower

Now we get to the real magic: connecting programs together. This is where the Unix philosophy shines.

### The Pipe Operator: `|`

The pipe `|` takes the stdout of one program and feeds it as stdin to another program.

**Basic syntax:**
```bash
program1 | program2
```

The output of `program1` becomes the input of `program2`.

### Simple Example

**Count the number of files in a directory:**
```bash
ls | wc -l
```

- `ls` lists files (stdout)
- `|` pipes that list to...
- `wc -l` counts lines (stdin)

### Building Chains

You can chain as many programs as you want:

```bash
ls -l | grep ".txt" | wc -l
```

1. `ls -l` - list all files with details
2. `grep ".txt"` - filter only lines containing ".txt"
3. `wc -l` - count how many matches

### Real-World Examples

**Find your most used commands:**
```bash
history | awk '{print $2}' | sort | uniq -c | sort -rn | head -10
```

Let's break it down:
1. `history` - show all commands you've typed
2. `awk '{print $2}'` - extract just the command names
3. `sort` - put them in order
4. `uniq -c` - count duplicates
5. `sort -rn` - sort by count, highest first
6. `head -10` - show top 10

**Find large files:**
```bash
du -h ~ | sort -h | tail -20
```

1. `du -h ~` - disk usage in home directory, human readable
2. `sort -h` - sort by human-readable sizes
3. `tail -20` - show the 20 largest

### Domain-Specific Examples

**Medicine - Analyze patient data:**
```bash
cat patients.csv | grep "diabetes" | cut -d',' -f1,3 | sort
```
Extract diabetic patients, get their ID and age, sort them.

**Finance - Find high-value transactions:**
```bash
cat transactions.csv | awk -F',' '$3 > 10000 {print}' | wc -l
```
Count transactions over $10,000.

**Biology - Process DNA sequences:**
```bash
cat sequences.txt | grep "^>.*human" | wc -l
```
Count human DNA sequences in FASTA format.

### Why This Matters

Instead of writing one big program that does everything, you combine small tools:
- Each tool does one thing well
- Tools are reusable in different combinations
- Easy to understand and debug each step
- Flexible - change one part without rewriting everything

### Try It Yourself

**Exercise 1:** List all text files in your current directory and count them.
```bash
ls *.txt | wc -l
```

**Exercise 2:** Find which programs you have installed that start with 'git':
```bash
ls /usr/bin | grep "^git"
```

**Exercise 3:** See your 5 most recently modified files:
```bash
ls -lt | head -6 | tail -5
```
(The `head -6` gets the first 6 lines, including the header, then `tail -5` gets the last 5)

### The Power of Composition

Once you understand pipes, you can solve complex problems by combining simple tools. This is the essence of Unix philosophy in action.

## Basic Navigation: Finding Your Way Around

Before you can work with files, you need to know where you are and how to move around.

### Your Location: The Working Directory

At any moment, you're "in" a specific directory (folder). This is your **working directory** or **current directory**.

**Find out where you are:**
```bash
pwd
```
(Print Working Directory)

You'll see something like:
```
/Users/yourname/Documents
```

This is an **absolute path** - the full address from the root of your filesystem.

### The Directory Tree

Your filesystem is organized like an upside-down tree:
```
/                          (root - the top of everything)
├── Users/
│   ├── yourname/
│   │   ├── Documents/
│   │   ├── Downloads/
│   │   └── Desktop/
├── bin/                   (programs)
├── etc/                   (configuration)
└── tmp/                   (temporary files)
```

### Changing Directories

**Move to a different directory:**
```bash
cd /Users/yourname/Documents
cd ~/Documents              # ~ means your home directory
cd Documents                # relative path (from where you are now)
```

**Go back to your home directory:**
```bash
cd ~
cd         # cd with no arguments goes home
```

**Go up one level:**
```bash
cd ..
```

**Go to the previous directory:**
```bash
cd -
```

### Special Directory Symbols

- `.` - Current directory
- `..` - Parent directory (one level up)
- `~` - Your home directory
- `/` - Root directory (top of filesystem)
- `-` - Previous directory

### Listing Files

**See what's in the current directory:**
```bash
ls
```

**List with details:**
```bash
ls -l
```
Shows permissions, size, date, owner.

**Show hidden files:**
```bash
ls -a
```
Files starting with `.` are hidden by default.

**Combine flags:**
```bash
ls -la
ls -lah    # h = human-readable file sizes
```

**List a specific directory:**
```bash
ls ~/Documents
ls /usr/bin
```

### Understanding `ls -l` Output

```bash
$ ls -l
drwxr-xr-x  5 carlos  staff   160 Oct 21 10:30 Documents
-rw-r--r--  1 carlos  staff  1234 Oct 20 15:45 report.txt
```

Breaking down that line:
- `d` or `-` - directory or file
- `rwxr-xr-x` - permissions (we'll cover this later)
- `5` or `1` - number of links
- `carlos` - owner
- `staff` - group
- `160` or `1234` - size in bytes
- `Oct 21 10:30` - last modified date
- `Documents` or `report.txt` - name

### Practical Navigation Tips

**See where a command will take you before going there:**
```bash
pwd
ls ../Projects
cd ../Projects
pwd
```

**View tree structure (if tree is installed):**
```bash
tree -L 2    # show 2 levels deep
```

**Quick directory navigation:**
```bash
cd ~/Documents
cd ~/Downloads
cd -           # back to Documents
cd -           # back to Downloads
```

### Try It Yourself

1. Find your current location: `pwd`
2. List files here: `ls -la`
3. Go to your home directory: `cd ~`
4. Look around: `ls`
5. Go into Documents: `cd Documents`
6. Go back up: `cd ..`
7. See where you are: `pwd`

## File Operations: Creating, Moving, and Deleting

Now that you can navigate, let's learn to manipulate files and directories.

### Creating Directories

**Make a new directory:**
```bash
mkdir project
mkdir ~/Documents/notes
```

**Make nested directories:**
```bash
mkdir -p projects/python/data-analysis
```
The `-p` flag creates parent directories as needed.

### Creating Files

**Create an empty file:**
```bash
touch file.txt
touch notes.md data.csv
```

`touch` updates a file's timestamp if it exists, or creates it if it doesn't.

**Create a file with content:**
```bash
echo "Hello, World!" > greeting.txt
```

### Copying Files

**Copy a file:**
```bash
cp source.txt destination.txt
cp report.pdf ~/Documents/
```

**Copy a directory and its contents:**
```bash
cp -r project/ project-backup/
```
The `-r` flag means "recursive" - copy everything inside.

**Copy multiple files to a directory:**
```bash
cp file1.txt file2.txt file3.txt ~/Documents/
```

### Moving and Renaming

`mv` does both moving and renaming (they're the same operation).

**Rename a file:**
```bash
mv oldname.txt newname.txt
```

**Move a file:**
```bash
mv report.pdf ~/Documents/
```

**Move and rename:**
```bash
mv old.txt ~/Documents/new.txt
```

**Move multiple files:**
```bash
mv file1.txt file2.txt file3.txt ~/Documents/
```

### Deleting Files

**Delete a file:**
```bash
rm unwanted.txt
```

**Delete multiple files:**
```bash
rm file1.txt file2.txt file3.txt
```

**Delete with confirmation:**
```bash
rm -i important.txt
```
The `-i` flag asks before deleting (interactive mode).

### Deleting Directories

**Delete an empty directory:**
```bash
rmdir empty-folder
```

**Delete a directory and all its contents:**
```bash
rm -r old-project/
```

**Delete with confirmation for each file:**
```bash
rm -ri old-project/
```

### Danger Zone: Commands That Can't Be Undone

⚠️ **There is no "Trash" or "Recycle Bin" with `rm`** - files are gone forever.

**Never run these commands without thinking:**
```bash
rm -rf /          # Tries to delete EVERYTHING (usually blocked)
rm -rf ~          # Deletes your entire home directory
rm -rf .          # Deletes current directory
rm -rf *          # Deletes everything in current directory
```

**Safe practices:**
1. Use `ls` first to see what you're about to delete
2. Use `-i` flag for confirmation
3. Double-check paths before pressing Enter
4. Start with specific files, not wildcards

### Wildcards and Pattern Matching

**Delete all text files:**
```bash
rm *.txt
```

**Copy all Python files:**
```bash
cp *.py ~/backup/
```

**Common wildcards:**
- `*` - matches anything
- `?` - matches single character
- `[abc]` - matches a, b, or c
- `[0-9]` - matches any digit

**Examples:**
```bash
ls *.txt          # all files ending in .txt
ls file?.txt      # file1.txt, fileA.txt, but not file10.txt
ls report_[0-9].pdf   # report_1.pdf through report_9.pdf
```

### Best Practices

**Before deleting, check what matches:**
```bash
ls *.log          # see what would be deleted
rm *.log          # now delete them
```

**Use tab completion to avoid typos:**
```bash
rm very-long-filename-with-typos.txt  # type "rm very" then hit TAB
```

**Test with `echo` first:**
```bash
echo rm *.txt     # shows what would be executed
rm *.txt          # actually execute
```

### Practical Examples

**Organize downloaded files:**
```bash
mkdir ~/Downloads/pdfs
mv ~/Downloads/*.pdf ~/Downloads/pdfs/
```

**Backup before editing:**
```bash
cp important.py important.py.backup
# edit important.py
```

**Clean up temporary files:**
```bash
ls *.tmp          # check what will be deleted
rm *.tmp          # delete them
```

### Try It Yourself

```bash
# Create a test directory structure
mkdir -p ~/practice/backup
cd ~/practice

# Create some files
touch file1.txt file2.txt notes.md

# Copy a file
cp file1.txt file1-copy.txt

# Move a file
mv file2.txt backup/

# List everything
ls
ls backup/

# Clean up (when you're done practicing)
cd ~
rm -r ~/practice
```

## Getting Help: You Don't Need to Memorize Everything

The command line has built-in documentation. Learning to use it makes you self-sufficient.

### The Manual: `man`

Almost every command has a manual page (man page).

**View the manual for a command:**
```bash
man ls
man grep
man cp
```

**Navigation inside `man`:**
- `Space` - next page
- `b` - previous page
- `/pattern` - search for "pattern"
- `n` - next search result
- `q` - quit

**Manual sections:**
- NAME - what the command does
- SYNOPSIS - how to use it
- DESCRIPTION - detailed explanation
- OPTIONS - all the flags and what they do
- EXAMPLES - usage examples (if included)

### Quick Help: `--help`

Most commands support a `--help` flag for quick reference.

```bash
ls --help
grep --help
git --help
```

This is faster than `man` when you just need to remember a flag.

### Finding Commands: `apropos`

Don't know which command does what you need? Search the man pages.

**Search for commands related to a topic:**
```bash
apropos copy          # find commands about copying
apropos compress      # find compression tools
apropos network       # find network-related commands
```

`apropos` searches the NAME and DESCRIPTION sections of all man pages.

### Which to Use When?

- **`man`** - When you need complete documentation
- **`--help`** - When you need a quick reminder
- **`apropos`** - When you don't know what command to use
- **`type` / `which`** - When you need to find where a command is

### Examples

**Learning a new command:**
```bash
# Find commands related to disk usage
apropos disk usage

# Read the manual for one
man du

# Try it with quick help
du --help

# Use it
du -h ~/Documents
```

**Remembering flags:**
```bash
# What flags does grep have?
man grep          # complete reference
grep --help       # quick list
```

### Online Resources

When man pages aren't enough:
- **tldr pages** - Simplified, practical examples (install with `brew install tldr` or `apt install tldr`)
- **explainshell.com** - Paste a command, get explanation
- **Stack Overflow** - Real-world problems and solutions

### Try `tldr` (if installed)

```bash
tldr tar
tldr find
tldr git-commit
```

Much more beginner-friendly than man pages!

### Practical Workflow

1. Don't know what command to use? → `apropos keyword`
2. Found a command, need overview? → `command --help`
3. Need detailed info? → `man command`
4. Still confused? → Google or Stack Overflow

### Remember

**You don't need to memorize commands.** Professional programmers look things up constantly. The skill is knowing:
- How to find the information
- How to read documentation
- How to test commands safely

## Redirection: Controlling Input and Output

Remember the three standard streams? Now we'll learn to redirect them.

### Output Redirection: `>`

Send stdout to a file instead of the screen.

**Save output to a file:**
```bash
ls -l > file_list.txt
echo "Hello, World!" > greeting.txt
date > timestamp.txt
```

⚠️ **Warning:** `>` overwrites the file if it exists!

### Append Instead of Overwrite: `>>`

Add to the end of a file without deleting what's there.

```bash
echo "First line" > log.txt
echo "Second line" >> log.txt
echo "Third line" >> log.txt
```

### Input Redirection: `<`

Read input from a file instead of the keyboard.

```bash
wc -l < file.txt        # count lines
sort < names.txt        # sort a file
```

Most programs can also take a filename as an argument:
```bash
wc -l file.txt          # does the same thing
sort names.txt          # also the same
```

### Redirect Errors: `2>`

Send stderr to a file.

```bash
ls /nonexistent 2> errors.txt
```

The `2` refers to file descriptor 2 (stderr).

### Redirect Both stdout and stderr

**Send both to the same file:**
```bash
command > output.txt 2>&1
```

Or in modern shells:
```bash
command &> output.txt
```

**Send them to different files:**
```bash
command > output.txt 2> errors.txt
```

### Discard Output: `/dev/null`

`/dev/null` is a special file that discards everything written to it. Think of it as a black hole.

**Run a command silently:**
```bash
command > /dev/null          # discard stdout
command 2> /dev/null         # discard stderr
command &> /dev/null         # discard everything
```

### Combining Pipes and Redirection

You can use both together!

```bash
ls -l | grep ".txt" > text_files.txt
cat file.txt | sort | uniq > sorted_unique.txt
```

### Practical Examples

**Save a list of installed programs:**
```bash
ls /usr/bin > ~/programs.txt
```

**Create a log file:**
```bash
echo "$(date): Script started" >> script.log
./my_script.sh >> script.log 2>&1
echo "$(date): Script finished" >> script.log
```

**Backup command output:**
```bash
du -h ~ > ~/disk_usage_$(date +%Y%m%d).txt
```

**Filter and save:**
```bash
grep "error" /var/log/system.log > errors_only.txt
```

**Keep errors, hide output:**
```bash
command > /dev/null 2> errors.txt
```

### Domain-Specific Examples

**Medicine - Extract patient IDs:**
```bash
cat patients.csv | cut -d',' -f1 > patient_ids.txt
```

**Finance - Save high-value transactions:**
```bash
awk -F',' '$3 > 10000' transactions.csv > high_value.csv
```

**Biology - Create filtered sequence file:**
```bash
grep "^>.*human" sequences.fasta > human_sequences.fasta
```

### Here Documents: `<<`

For multi-line input, use a "here document":

```bash
cat > note.txt << EOF
This is line 1
This is line 2
This is line 3
EOF
```

Type your content, then type `EOF` on its own line to end.

### Cheat Sheet

| Operator | Purpose | Example |
|----------|---------|---------|
| `>` | Redirect stdout (overwrite) | `ls > list.txt` |
| `>>` | Redirect stdout (append) | `echo "hi" >> log.txt` |
| `<` | Redirect stdin | `sort < names.txt` |
| `2>` | Redirect stderr | `cmd 2> err.txt` |
| `2>&1` | Redirect stderr to stdout | `cmd > all.txt 2>&1` |
| `&>` | Redirect both (modern) | `cmd &> all.txt` |
| `|` | Pipe stdout to next command | `ls | grep txt` |

### Try It Yourself

```bash
# Create a file with redirection
echo "Apple" > fruits.txt
echo "Banana" >> fruits.txt
echo "Cherry" >> fruits.txt

# Sort and save
sort fruits.txt > sorted_fruits.txt

# Count lines and save
wc -l fruits.txt > count.txt

# Combine operations
cat fruits.txt | sort | uniq > unique_sorted_fruits.txt

# Clean up
rm fruits.txt sorted_fruits.txt count.txt unique_sorted_fruits.txt
```

## Tab Completion: Type Less, Make Fewer Mistakes

The `Tab` key is your best friend on the command line. It saves typing and prevents typos.

### Basic Tab Completion

Start typing and press `Tab` - the shell completes what you started.

**Complete a command:**
```bash
gre[Tab]    # completes to "grep"
pyth[Tab]   # completes to "python"
```

**Complete a filename:**
```bash
ls ~/Doc[Tab]       # completes to ~/Documents/
cat very-lon[Tab]   # completes long filenames
```

### What Happens When You Press Tab

1. **One match:** Completes immediately
2. **Multiple matches:** Shows nothing (press Tab again to see options)
3. **No matches:** Nothing happens (probably a typo)

**See all possibilities:**
Press `Tab` twice to see all options.

```bash
ls /usr/b[Tab][Tab]
# Shows: bin/  local/bin/
```

### Completing Paths

Tab completion works through directories:

```bash
cd ~/Doc[Tab]/proj[Tab]/pyth[Tab]
# Builds: ~/Documents/projects/python/
```

You can navigate complex paths with minimal typing!

### Completing Arguments

Many shells can complete command arguments too.

```bash
git check[Tab]      # completes to "checkout"
git checkout ma[Tab]  # completes to branch name "main"
```

### Pro Tips

**Use Tab constantly:**
- Less typing
- Fewer typos
- Confirms the file/command exists
- Faster than typing full names

**After a few characters, hit Tab:**
```bash
# Instead of typing:
cd /Users/carlos/Documents/projects/python-scripts/

# Type this and use Tab:
cd /U[Tab]/c[Tab]/D[Tab]/pr[Tab]/py[Tab]
```

**If Tab doesn't complete, you probably have a typo.**

### Special Case: Spaces in Filenames

Tab completion automatically escapes spaces:

```bash
cd My\ Documents    # what you type manually
cd My[Tab]          # Tab adds the backslash automatically
```

### Bash vs Zsh

**Bash:**
- Tab twice to see options
- Basic completion for files and commands

**Zsh** (increasingly common on macOS):
- More intelligent completion
- Can complete arguments, flags, and more
- Shows options in a navigable menu
- Suggests corrections for typos

### Try It Yourself

1. Type `cd ~/D` then hit Tab - does it complete to Documents?
2. Type `ls /u` then Tab twice - see what directories exist
3. Type the first few letters of a file in your current directory, then Tab
4. Try completing a long command: `python --ve` then Tab

### Why This Matters

Tab completion:
- **Saves time** - 50% less typing
- **Prevents errors** - can't typo if the shell completes it
- **Confirms existence** - if it completes, the file/command exists
- **Speeds learning** - discover commands and files by exploring completions

**Get in the habit:** After typing 3-4 characters, press Tab. It becomes muscle memory.

## Escape Hatch: When Things Go Wrong

The command line gives you power, but sometimes you need to take back control. Here's how to recover when things go sideways.

### Stop a Running Command: Ctrl+C

If a command is taking too long or doing something you didn't intend:

**Press `Ctrl+C`** - Sends an interrupt signal to stop the program.

```bash
# This command will run forever
cat /dev/random | hexdump

# Press Ctrl+C to stop it
^C
```

Most programs will stop immediately and cleanly.

### When Ctrl+C Doesn't Work

Some programs ignore `Ctrl+C`. If that happens:

1. Press `Ctrl+Z` - Suspends the program (pauses it)
2. Type `jobs` - See background/suspended jobs
3. Type `kill %1` - Kill job number 1

Or find and kill the process:
```bash
ps aux | grep program_name
kill <process_id>
```

### Clear a Messed Up Line: Ctrl+U

Typed a command and it's all wrong?

**Press `Ctrl+U`** - Clears everything before the cursor.

```bash
$ this is a really long messed up command that^U
$ _
```

### Clear the Screen: Ctrl+L or `clear`

Terminal cluttered with output?

**Press `Ctrl+L`** or type `clear` - Clears the screen.

### Undo Accidental Input: Ctrl+C

Started typing a command you don't want to run?

**Press `Ctrl+C`** - Cancels the current line and gives you a fresh prompt.

### Exit an Interactive Program

Different programs have different exit keys:

- **General:** `Ctrl+D` (signals end-of-input)
- **`less` / `man`:** Press `q`
- **`vi` / `vim`:** Type `:q` then Enter (or `:q!` to quit without saving)
- **`nano`:** `Ctrl+X`
- **Python/Node REPL:** `Ctrl+D` or type `exit()`

### Recover from "Command Not Found" in Middle of Pipe

If a command in the middle of a long pipe fails:
```bash
cat file.txt | typo | sort | uniq
# bash: typo: command not found
```

Don't retype everything! Use the up arrow to get the line back, then fix the typo.

### Fix Broken Terminal Display

Sometimes output gets garbled and your terminal looks wrong.

**Type `reset`** then press Enter (you might not see what you're typing).

```bash
reset
```

This reinitializes your terminal.

### Cancel an Accidental `rm` Command

If you pressed Enter on a dangerous `rm` command:

**There's no undo.** Files are gone.

**Prevention is key:**
1. Use `-i` flag for confirmation: `rm -i *.txt`
2. Test with `echo` first: `echo rm *.txt`
3. Use `ls` to preview: `ls *.txt` before `rm *.txt`

### "I Can't Type Anything" - Ctrl+S and Ctrl+Q

**Accidentally pressed `Ctrl+S`?** This freezes terminal output.

**Press `Ctrl+Q`** to unfreeze it.

### Directory Doesn't Exist Error

```bash
$ cd ~/Documnets
bash: cd: /Users/carlos/Documnets: No such file or directory
```

**Solutions:**
- Press Up arrow, fix the typo
- Use Tab completion next time to avoid typos

### Permission Denied

```bash
$ rm /usr/bin/python
rm: /usr/bin/python: Permission denied
```

**Don't blindly use `sudo`!** First ask:
- Should I be able to delete this?
- Is this file in a system directory?
- Do I really want to do this?

Only use `sudo` if you're certain you need elevated privileges for a legitimate reason.

### Useful Keyboard Shortcuts Summary

| Shortcut | Action |
|----------|--------|
| `Ctrl+C` | Stop current command |
| `Ctrl+D` | Exit / End of input |
| `Ctrl+L` | Clear screen |
| `Ctrl+U` | Clear line before cursor |
| `Ctrl+K` | Clear line after cursor |
| `Ctrl+A` | Jump to start of line |
| `Ctrl+E` | Jump to end of line |
| `Ctrl+R` | Search command history |
| `Ctrl+Z` | Suspend current program |
| Up/Down | Navigate command history |
| `Tab` | Auto-complete |

### Practice Getting Unstuck

Try these (so you know how to escape):

```bash
# Start an infinite loop, then Ctrl+C to stop
yes

# Start cat waiting for input, then Ctrl+D to end
cat

# Suspend a program with Ctrl+Z
sleep 100
# Press Ctrl+Z, then type: jobs
# Kill it: kill %1
```

### Remember

**Don't panic.** When something goes wrong:
1. Try `Ctrl+C`
2. If that doesn't work, `Ctrl+Z` then `kill %1`
3. If you can't type, try `Ctrl+Q`
4. If display is garbled, type `reset`
5. If all else fails, close the terminal and start fresh

You can't break your computer with normal commands. Worst case, you close the terminal and reopen it.

## Common Pitfalls: Learn from Others' Mistakes

Here are the most common mistakes beginners make (so you can avoid them).

### 1. Spaces in Commands

**Wrong:**
```bash
cd My Documents        # Tries to cd to "My" with "Documents" as second argument
```

**Right:**
```bash
cd "My Documents"      # Use quotes
cd My\ Documents       # Or escape the space
cd My[Tab]             # Or use Tab completion (adds escape automatically)
```

### 2. Case Sensitivity

Unix is case-sensitive. These are all different:
```bash
file.txt
File.txt
FILE.TXT
```

**Common error:**
```bash
$ cd documents
bash: cd: documents: No such file or directory
# The directory is actually "Documents" with capital D
```

### 3. Confusing `rm` and `rmdir`

```bash
rm myfile.txt          # Deletes a file
rmdir mydir/           # Only works on EMPTY directories
rm -r mydir/           # Deletes directory and contents
```

Don't use `rmdir` on directories with files - it won't work and you'll be confused.

### 4. Forgetting to Check Before Deleting

**Bad practice:**
```bash
rm *.log    # Hope you meant that!
```

**Good practice:**
```bash
ls *.log    # Check what matches first
rm *.log    # Now delete
```

### 5. Working in the Wrong Directory

```bash
$ rm important.txt
rm: important.txt: No such file or directory
```

**Always know where you are:**
```bash
pwd                    # Where am I?
ls                     # What's here?
rm important.txt       # Now delete
```

### 6. Misunderstanding Wildcards

```bash
$ rm * .txt           # DISASTER: Deletes everything, then tries to delete ".txt"
$ rm *.txt            # Correct: Deletes all .txt files
```

No space between `*` and `.txt`!

### 7. Not Using Quotes with Special Characters

**Problem:**
```bash
echo Hello World > file.txt    # Creates file.txt with "Hello World"
echo Hello       World         # echo receives two arguments, collapses spaces
```

**Solution:**
```bash
echo "Hello       World"       # Preserves spaces
```

### 8. Forgetting Flags Are Case-Sensitive

```bash
ls -l    # Lowercase L - long format
ls -L    # Uppercase L - follow symbolic links
```

These do completely different things!

### 9. Copy/Paste Errors

Copying commands from websites can include hidden characters or wrong quotes.

**If a command looks right but doesn't work:**
- Retype it manually
- Check for smart quotes: `"` vs `"`
- Look for hidden characters

### 10. Not Reading Error Messages

Error messages tell you exactly what's wrong:

```bash
$ cd /User/carlos
bash: cd: /User/carlos: No such file or directory
       ^^^ This tells you the problem - wrong path
```

Read the error. It usually says exactly what's wrong.

### 11. Using `sudo` Without Understanding

**Don't:**
```bash
$ rm important.txt
rm: important.txt: Permission denied
$ sudo rm important.txt    # BAD: Don't blindly use sudo!
```

**Do:**
```bash
$ rm important.txt
rm: important.txt: Permission denied
# Ask yourself: WHY don't I have permission?
# Should I be deleting this file?
# Is it in a system directory?
```

`sudo` gives you superuser powers. With great power comes great responsibility.

### 12. Forgetting Current Directory Syntax

```bash
$ python script.py           # If script.py is in current directory
python: can't open file 'script.py'

$ ./script.py                # Correct for executable scripts
$ python ./script.py         # Also works
```

### 13. Not Escaping Special Characters in Filenames

Avoid these in filenames:
- Spaces
- `*`, `?`, `[`, `]`
- Quotes (`"`, `'`)
- Backslash (`\`)

**Good filenames:**
```bash
my-report.pdf
data_2024.csv
final-version-2.txt
```

**Bad filenames:**
```bash
my report (draft).pdf        # Spaces and parentheses
file*.txt                     # Wildcard in name
"quote"file.txt              # Quotes in name
```

### 14. Overwriting Files Accidentally

```bash
$ important-data.csv
$ cat data.csv > important-data.csv    # OOPS! Overwrites the file
```

**Prevention:**
- Make backups first: `cp important.csv important.csv.backup`
- Use `>>` to append instead of `>`
- Check if file exists: `ls important.csv`

### 15. Not Using History

Don't retype long commands!

```bash
# Press Up arrow to get previous commands
# Press Ctrl+R to search history
# Type: history | grep keyword
```

### Quick Tips to Avoid Mistakes

1. **Always `pwd` before destructive operations**
2. **Test with `echo` or `ls` first**
3. **Use Tab completion to avoid typos**
4. **Read error messages carefully**
5. **Make backups before editing/deleting**
6. **Start with small, specific commands**
7. **When in doubt, use `-i` flag for confirmation**

## Practical Examples by Domain

Let's see how command line skills apply to different fields. These examples use real-world scenarios from your domains.

### Medicine & Healthcare

**Scenario: Analyzing patient data from CSV files**

```bash
# Count total patients
wc -l patients.csv

# Find all diabetic patients
grep -i "diabetes" patients.csv > diabetic_patients.csv

# Extract patient IDs and ages
cut -d',' -f1,3 patients.csv | sort -t',' -k2 -n > patients_by_age.csv

# Find patients over 65
awk -F',' '$3 > 65 {print $1, $2, $3}' patients.csv > elderly_patients.txt

# Count patients by diagnosis
cut -d',' -f4 patients.csv | sort | uniq -c | sort -rn > diagnosis_counts.txt

# Create backup before analysis
cp patients.csv patients_$(date +%Y%m%d).backup
```

**Scenario: Processing medical imaging filenames**

```bash
# Rename all DICOM files with consistent naming
for file in *.dcm; do
    mv "$file" "patient_001_$file"
done

# Find all MRI scans from 2024
ls -l | grep "MRI" | grep "2024" > mri_2024_list.txt

# Count different imaging types
ls *.dcm *.jpg *.png 2>/dev/null | grep -o '\.[^.]*$' | sort | uniq -c
```

### Finance

**Scenario: Processing transaction data**

```bash
# Find transactions over $10,000
awk -F',' '$3 > 10000 {print $0}' transactions.csv > high_value.csv

# Calculate total transaction value (column 3)
awk -F',' '{sum+=$3} END {print "Total:", sum}' transactions.csv

# Find all transactions from specific account
grep "ACC-12345" transactions.csv | wc -l

# Extract unique account IDs
cut -d',' -f2 transactions.csv | sort -u > unique_accounts.txt

# Transactions by month
cut -d',' -f1 transactions.csv | cut -c1-7 | sort | uniq -c

# Generate daily report
echo "Transaction Report - $(date)" > report.txt
echo "Total transactions: $(wc -l < transactions.csv)" >> report.txt
echo "High value (>10k): $(awk -F',' '$3>10000' transactions.csv | wc -l)" >> report.txt
```

**Scenario: Organizing financial reports**

```bash
# Create directory structure for fiscal year
mkdir -p FY2024/{Q1,Q2,Q3,Q4}/{Jan,Feb,Mar}

# Move PDF reports to appropriate quarters
mv *_Q1_*.pdf FY2024/Q1/
mv *_Q2_*.pdf FY2024/Q2/

# Find all reports from last month
find . -name "*.pdf" -mtime -30 > recent_reports.txt
```

### Architecture

**Scenario: Managing CAD and design files**

```bash
# List all AutoCAD files with sizes
ls -lh *.dwg *.dxf | sort -k5 -h

# Find large files (over 100MB)
find . -name "*.dwg" -size +100M -exec ls -lh {} \;

# Create project structure
mkdir -p project_2024/{drawings,renderings,specifications,client_docs}

# Backup before major changes
tar -czf project_backup_$(date +%Y%m%d).tar.gz project_2024/

# Find all rendering files modified today
find . -name "*.png" -o -name "*.jpg" -mtime -1

# Count files by extension
ls -1 | grep -o '\.[^.]*$' | sort | uniq -c | sort -rn
```

**Scenario: Version control for designs**

```bash
# Create dated versions
cp floor_plan.dwg floor_plan_$(date +%Y%m%d).dwg

# Find all versions of a file
ls -lt floor_plan_*.dwg

# Compare file sizes to see which version is newest
ls -lS design_*.pdf | head -5
```

### Biology & Environmental Science

**Scenario: Processing DNA sequence files**

```bash
# Count sequences in FASTA file
grep -c "^>" sequences.fasta

# Extract only human sequences
grep -A 1 "^>.*human" sequences.fasta > human_sequences.fasta

# Count nucleotides in each sequence
awk '/^>/{if(seq){print name, length(seq)}; name=$0; seq=""; next} {seq=seq$0} END {print name, length(seq)}' sequences.fasta

# Find sequences containing specific pattern
grep -B 1 "ATCGATCG" sequences.fasta

# Split large FASTA file into smaller chunks
split -l 1000 large_sequences.fasta chunk_
```

**Scenario: Analyzing field data**

```bash
# Environmental sensor data - find temperature extremes
awk -F',' '$3 > 35 || $3 < -10 {print $0}' sensor_data.csv > extreme_temps.csv

# Count observations by species
cut -d',' -f2 wildlife_observations.csv | sort | uniq -c | sort -rn

# Combine multiple data files
cat site1.csv site2.csv site3.csv > all_sites.csv

# Remove duplicate observations
sort observations.csv | uniq > unique_observations.csv

# Extract GPS coordinates
cut -d',' -f4,5 field_data.csv > coordinates.txt
```

### General Research & Data Analysis

**Common tasks across all fields:**

```bash
# Quick statistics on numeric data (column 3)
awk '{sum+=$3; sumsq+=$3*$3} END {print "Mean:", sum/NR, "StdDev:", sqrt(sumsq/NR - (sum/NR)^2)}' data.txt

# Remove header row from CSV
tail -n +2 data.csv > data_no_header.csv

# Add line numbers to file
nl -ba data.txt > numbered_data.txt

# Convert CSV to tab-separated
tr ',' '\t' < data.csv > data.tsv

# Preview large file (first and last 10 lines)
(head -10; echo "..."; tail -10) < large_file.txt

# Count unique values in column
cut -f2 data.txt | sort -u | wc -l
```

### Key Takeaway

The command line isn't just for programmers - it's a powerful tool for:
- Processing data files quickly
- Automating repetitive tasks
- Analyzing large datasets
- Organizing files systematically
- Creating reproducible workflows

The same basic commands (`grep`, `awk`, `cut`, `sort`) solve problems across all domains.

## Hands-On Exercises

Practice these exercises to build your command line skills. Start with the basics and work your way up.

### Exercise 1: Navigation Basics

**Goal:** Get comfortable moving around the filesystem.

```bash
# 1. Find where you are
pwd

# 2. Go to your home directory
cd ~

# 3. List everything, including hidden files
ls -la

# 4. Go to Documents
cd Documents

# 5. Go back to previous directory
cd -

# 6. Go up one level
cd ..

# 7. Check where you are now
pwd
```

### Exercise 2: Creating a Project Structure

**Goal:** Create a realistic project directory structure.

```bash
# Create a project with subdirectories
mkdir -p my_research/{data,scripts,results,docs}

# Navigate into it
cd my_research

# Verify structure
ls -l

# Create some files
touch data/experiment_1.csv
touch data/experiment_2.csv
touch scripts/analyze.py
touch docs/README.md

# List everything recursively
ls -R

# Clean up when done
cd ..
rm -r my_research
```

### Exercise 3: Working with Files

**Goal:** Practice creating, copying, moving, and deleting files.

```bash
# Create a practice directory
mkdir cli_practice
cd cli_practice

# Create some sample files
echo "Apple" > fruits.txt
echo "Banana" >> fruits.txt
echo "Cherry" >> fruits.txt
echo "Date" >> fruits.txt

# View the file
cat fruits.txt

# Copy the file
cp fruits.txt fruits_backup.txt

# Create a sorted version
sort fruits.txt > fruits_sorted.txt

# Count lines
wc -l fruits.txt

# Rename a file
mv fruits_backup.txt my_fruits.txt

# Clean up
cd ..
rm -r cli_practice
```

### Exercise 4: Using Pipes

**Goal:** Combine commands to solve problems.

```bash
# Count files in /usr/bin
ls /usr/bin | wc -l

# Find commands with "python" in the name
ls /usr/bin | grep python

# Show your 10 most recent commands
history | tail -10

# Find your 5 most used commands
history | awk '{print $2}' | sort | uniq -c | sort -rn | head -5

# Count how many different file types in current directory
ls | grep -o '\.[^.]*$' | sort | uniq -c
```

### Exercise 5: Redirection

**Goal:** Control where output goes.

```bash
# Create test directory
mkdir redirect_practice
cd redirect_practice

# Capture output
ls -l ~ > home_contents.txt

# Append more output
echo "=== End of list ===" >> home_contents.txt

# View what you saved
cat home_contents.txt

# Try redirecting errors
ls /nonexistent 2> errors.txt

# Check the error file
cat errors.txt

# Clean up
cd ..
rm -r redirect_practice
```

### Exercise 6: Pattern Matching with Wildcards

**Goal:** Use wildcards to work with multiple files.

```bash
mkdir wildcard_practice
cd wildcard_practice

# Create several files
touch report1.txt report2.txt report3.txt
touch data1.csv data2.csv
touch notes.md

# List only .txt files
ls *.txt

# List only files starting with "report"
ls report*

# Count .txt files
ls *.txt | wc -l

# Copy all .csv files to a new directory
mkdir csv_files
cp *.csv csv_files/

# Clean up
cd ..
rm -r wildcard_practice
```

### Exercise 7: Real-World Data Processing

**Goal:** Simulate processing a data file.

```bash
mkdir data_analysis
cd data_analysis

# Create a sample CSV file
cat > data.csv << EOF
Name,Age,Department,Salary
Alice,34,Engineering,95000
Bob,45,Marketing,75000
Carol,28,Engineering,85000
David,52,Sales,70000
Eve,31,Engineering,90000
EOF

# View the file
cat data.csv

# Count total entries (excluding header)
tail -n +2 data.csv | wc -l

# Extract just names
cut -d',' -f1 data.csv

# Find Engineering department
grep "Engineering" data.csv

# Sort by name
tail -n +2 data.csv | sort > sorted_data.csv

# Extract just salaries
cut -d',' -f4 data.csv | tail -n +2

# Clean up
cd ..
rm -r data_analysis
```

### Exercise 8: Command History and Shortcuts

**Goal:** Get fast with the keyboard.

```bash
# Run a command
echo "Practice makes perfect"

# Press Up arrow - get the previous command
# Press Enter - run it again

# Type: echo "test"
# Press Ctrl+A - cursor jumps to start
# Press Ctrl+E - cursor jumps to end
# Press Ctrl+U - clears the line

# Press Ctrl+R, then type "echo" - search your history
# Press Ctrl+R again - cycle through matches
# Press Enter when you find what you want

# Try tab completion
cd ~/D[Tab]    # Should complete to Documents
```

### Exercise 9: Getting Help

**Goal:** Learn to find information on your own.

```bash
# Read the manual for ls
man ls
# Press 'q' to quit

# Get quick help
ls --help | less
# Press 'q' to quit

# Find commands related to "copy"
apropos copy

# What is the grep command?
man grep | head -20
```

### Exercise 10: Putting It All Together

**Goal:** Complete workflow exercise.

```bash
# 1. Create a project
mkdir my_project
cd my_project

# 2. Create directory structure
mkdir -p {data,analysis,reports}

# 3. Create sample data
echo -e "ID,Value\n1,100\n2,200\n3,300" > data/values.csv

# 4. Process the data
cat data/values.csv | tail -n +2 | cut -d',' -f2 > analysis/values_only.txt

# 5. Create a report
echo "Data Analysis Report" > reports/summary.txt
echo "===================" >> reports/summary.txt
echo "Total entries: $(tail -n +2 data/values.csv | wc -l)" >> reports/summary.txt
echo "Generated on: $(date)" >> reports/summary.txt

# 6. View your report
cat reports/summary.txt

# 7. Create a backup
cd ..
tar -czf my_project_backup.tar.gz my_project/

# 8. Verify backup exists
ls -lh my_project_backup.tar.gz

# 9. Clean up
rm -r my_project
rm my_project_backup.tar.gz
```

### Challenge Exercises

For those wanting more practice:

1. **File Organization:** Download 20 random files to your Downloads folder, then write commands to organize them by file type into subdirectories.

2. **Log Analysis:** Find or create a log file, then extract all error messages, count how many times each error occurs, and save the top 10 to a report.

3. **Batch Renaming:** Create 10 files with spaces in their names, then write commands to rename them all to use underscores instead.

4. **Data Merging:** Create 3 CSV files with the same columns, merge them, remove duplicates, and sort by a specific column.

5. **Find and Replace:** Use `sed` to find and replace text across multiple files (requires learning `sed` - an advanced topic).

### Tips for Practice

- **Type everything yourself** - don't copy/paste
- **Make mistakes** - that's how you learn
- **Use `--help` and `man`** when stuck
- **Start over if confused** - repetition builds muscle memory
- **Time yourself** - try to get faster at common tasks

