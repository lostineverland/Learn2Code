# Learning to Code

  - in Python

    ---slide---

  ## Syllabus

    - Week 1-2: Setup & Computer Basics
    - Week 3-4: Editors & Command Line
    - Week 5: Git (version control)
    - Week 6-8: Python Fundamentals
    - Week 9-11: Real Projects
    - Week 12: Your Domain Application

    ---vertical---
  ### Week by week
    ---vertical---


  ### Week 1: Orientation & Environment Setup

    * Learning Objectives:
      - Assess student technical backgrounds and learning goals
      - Select appropriate environment and editor tracks
      - Complete environment setup and verification
    * Activities:
      - Pre-course technical survey
      - Track selection workshop
      - Environment installation/configuration
      - "Hello World" verification across all tracks
    * Deliverable: Working development environment with successful Python execution

    ---vertical---

  ### Week 2: Getting to Know Your Computer

  Learning Objectives:
  - Understand file systems and directory structures
  - Navigate using both GUI and CLI approaches
  - Recognize differences between operating systems

  Topics:
  - File system hierarchy (`*nix` vs Windows vs macOS)
  - Absolute vs relative paths
  - File permissions basics
  - Environment variables introduction

    ---vertical---

  Activities:
  - File system exploration exercises
  - Create/organize project directory structure
  - Cross-platform path exercises

    ---vertical---

  ### Week 3: Understanding Your Editor

  Learning Objectives:
  - Master basic editing operations in chosen editor
  - Understand syntax highlighting and file types
  - Configure basic settings for Python development

  VSCode Track:
  - Interface navigation
  - Extensions for Python
  - Integrated terminal usage
  - Basic debugging setup
    ---vertical---
  Neovim Track:
  - Modal editing concepts
  - Basic configuration
  - Plugin manager introduction
  - Terminal integration

  Activities:
  - Text editing challenges
  - Configuration customization
  - Python syntax recognition exercises

    ---vertical---

  ### Week 4: Command Line Interface Fundamentals

  Learning Objectives:
  - Navigate file systems via command line
  - Execute basic file operations
  - Understand command syntax and options
  - Use pipes and redirection

  Core Commands:
  - Navigation: pwd, ls, cd
  - File operations: mkdir, touch, cp, mv, rm
  - Text processing: cat, head, tail, grep
  - System info: whoami, date, df, ps

    ---vertical---

  Activities:
  - CLI scavenger hunt
  - File manipulation exercises
  - Command chaining practice

    ---vertical---

  ### Week 5: Revision Control with Git

  Learning Objectives:
  - Understand version control concepts
  - Master basic git workflow
  - Collaborate using GitHub/GitLab
  - Resolve simple merge conflicts

  Git Concepts:
  - Repository, commit, branch, merge
  - Working directory vs staging vs repository
  - Remote repositories and collaboration
  - Basic branching strategies

    ---vertical---

  Activities:
  - Initialize first repository
  - Commit history exercises
  - Collaborative editing project
  - Conflict resolution practice

    ---vertical---

  ### Week 6: Python Basics & Data Structures

  Learning Objectives:
  - Understand Python syntax and indentation
  - Work with fundamental data types
  - Manipulate lists, tuples, dictionaries, sets

    ---vertical---

  Python Fundamentals:
  - Variables and assignment
  - Numbers, strings, booleans
  - Lists: creation, indexing, slicing, methods
  - Tuples: immutability and use cases
  - Dictionaries: key-value pairs, methods
  - Sets: uniqueness and operations

    ---vertical---

  Domain-Specific Examples:
  - Medicine: Patient record dictionaries
  - Finance: Stock price lists, portfolio dictionaries
  - Biology: DNA sequence strings, species sets
  - Architecture: Material property dictionaries

    ---vertical---

  ### Week 7: Control Flow - Conditionals

  Learning Objectives:
  - Implement decision-making logic
  - Use comparison and logical operators
  - Handle multiple conditions with elif/else
  - Apply conditional logic to real problems

    ---vertical---

  Topics:
  - Boolean expressions and truth values
  - if/elif/else statements
  - Comparison operators: ==, !=, <, >, <=, >=
  - Logical operators: and, or, not
  - Nested conditionals

  Domain Applications:
  - Medicine: Patient risk assessment logic
  - Finance: Investment decision trees
  - Environmental: Pollution threshold alerts

    ---vertical---

  ### Week 8: Control Flow - Loops

  Learning Objectives:
  - Automate repetitive tasks with loops
  - Iterate over data structures
  - Control loop execution with break/continue
  - Choose appropriate loop types

    ---vertical---

  Topics:
  - for loops with ranges and iterables
  - while loops for conditional repetition
  - Loop control: break, continue
  - Nested loops and performance considerations
  - List comprehensions introduction

    ---vertical---

  Applications:
  - Data processing workflows
  - Batch file operations
  - Iterative calculations

    ---vertical---

  ### Week 9: Functions - Code Organization

  Learning Objectives:
  - Write reusable code blocks
  - Understand parameters, arguments, return values
  - Apply scope and namespace concepts
  - Document functions effectively

    ---vertical---

  Topics:
  - Function definition and calling
  - Parameters: positional, keyword, default values
  - Return statements and multiple returns
  - Local vs global scope
  - Docstrings and documentation
  - Lambda functions introduction

  Project Focus:
  - Build domain-specific utility functions
  - Create function libraries for repeated tasks

    ---vertical---

  ### Week 10: File I/O and Data Processing

  Learning Objectives:
  - Read and write files programmatically
  - Process CSV and text data
  - Handle file paths cross-platform
  - Implement error handling

    ---vertical---

  Topics:
  - File operations: open, read, write, close
  - CSV module for structured data
  - Path manipulation with pathlib
  - Exception handling with try/except
  - Data cleaning and transformation

  Domain Projects:
  - Medicine: Process patient data files
  - Finance: Analyze transaction records
  - Biology: Parse sequence data files

    ---vertical---

  ### Week 11: Putting It All Together - Integration Project

  Learning Objectives:
  - Combine all learned concepts in a substantial project
  - Apply software development lifecycle
  - Practice debugging and testing
  - Present technical work to peers

    ---vertical---

  Project Requirements:
  - Use git for version control
  - Implement functions for code organization
  - Process external data files
  - Include error handling
  - Create documentation

    ---vertical---

  Domain-Specific Capstone Options:
  - Medicine: Patient data analysis dashboard
  - Finance: Portfolio performance tracker
  - Architecture: Building material calculator
  - Biology: Species data analyzer
  - Environmental: Sensor data processor

    ---vertical---

  ### Week 12: Advanced Topics & Next Steps

  Learning Objectives:
  - Explore advanced Python concepts
  - Understand common libraries for each domain
  - Plan continued learning paths
  - Deploy and share projects

    ---vertical---

  Advanced Topics:
  - Object-oriented programming introduction
  - Popular libraries overview (pandas, numpy, matplotlib)
  - Virtual environments and package management
  - Code testing basics
  - Deployment options

    ---vertical---

  Career Integration:
  - How to continue learning programming
  - Identifying automation opportunities in their field
  - Building a programming portfolio
  - Contributing to open source projects

    ---slide---

  ## Failure Focus
  
    - write the specs of what we want
    - write code until tests pass
  
    ---slide---

  ## Environment

    Cross-platform uniformity:
    - Unix / Linux OS focused
    - WSL2 for Windows users vs native Terminal for Mac users
    - Package manager consistency (brew for Mac, apt/chocolatey for Windows)

    ---slide---

  ## Tracks

    * Environment Tracks:
      - Track A: Docker Local (full system control)
      - Track B: GitHub Codespaces (restricted systems)
      - Track C: GitHub Actions (advanced automation)
    * Editor Tracks:
      - Regular: VSCode (GUI-based)
      - Advanced: Neovim (terminal-based)

    ---slide---

  ## Logistics
  
    - Classes will be no longer than 1 hour
    - homework can begin on hour 2
    - Class Material 
      * GitHub (create account)
      * Slack Channel (Disccord?)
    - Video recordings?
