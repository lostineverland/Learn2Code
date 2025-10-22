# Command Line Exercises - Practice Data

This directory contains sample datasets for practicing command line skills. Each subdirectory contains domain-specific data relevant to different fields.

## Directory Structure

```
exercises/
├── README.md (this file)
├── data/
│   ├── medicine/       # Healthcare and medical data
│   ├── finance/        # Financial transactions and reports
│   ├── architecture/   # Design files and project data
│   ├── biology/        # DNA sequences and field observations
│   └── general/        # General practice files
└── solutions/          # Example solutions to exercises
```

## Quick Start

1. Navigate to the exercises directory:
   ```bash
   cd lectures/2025-W43/exercises
   ```

2. Explore the available datasets:
   ```bash
   ls data/
   ```

3. Choose a domain and start practicing:
   ```bash
   cd data/medicine
   ls -la
   ```

## Available Datasets

### Medicine (`data/medicine/`)
- `patients.csv` - Patient demographics and diagnoses
- `lab_results.csv` - Laboratory test results
- `medications.csv` - Medication prescriptions
- `appointments.csv` - Appointment scheduling data

### Finance (`data/finance/`)
- `transactions.csv` - Financial transactions
- `accounts.csv` - Account information
- `monthly_reports/` - Directory with monthly financial reports
- `quarterly_summaries.txt` - Quarterly financial summaries

### Architecture (`data/architecture/`)
- `projects.csv` - Project information and status
- `drawings/` - Directory with drawing file listings
- `materials.csv` - Materials and specifications
- `client_info.txt` - Client contact information

### Biology (`data/biology/`)
- `sequences.fasta` - DNA sequences in FASTA format
- `observations.csv` - Field observation data
- `species.csv` - Species information
- `measurements.csv` - Environmental measurements

### General (`data/general/`)
- `sample.txt` - Simple text file for basic operations
- `names.txt` - List of names for sorting practice
- `numbers.txt` - Numeric data
- `mixed_data.csv` - General CSV file
- `logs/` - Sample log files

## Practice Exercises

### Beginner Level

1. **Navigation**: Move between directories and list contents
2. **File Viewing**: Use `cat`, `head`, `tail`, `less` to view files
3. **Counting**: Use `wc` to count lines, words, characters
4. **Searching**: Use `grep` to find specific patterns

### Intermediate Level

5. **Filtering**: Extract specific columns with `cut`
6. **Sorting**: Sort data with `sort`
7. **Unique Values**: Find unique entries with `uniq`
8. **Piping**: Chain commands together with `|`

### Advanced Level

9. **Text Processing**: Use `awk` for complex data manipulation
10. **Batch Operations**: Process multiple files at once
11. **Reporting**: Generate summary reports combining multiple commands
12. **Automation**: Create reusable command sequences

## Example Workflows

### Medicine: Find Diabetic Patients
```bash
cd data/medicine
grep -i "diabetes" patients.csv > diabetic_patients.csv
wc -l diabetic_patients.csv
```

### Finance: High-Value Transactions
```bash
cd data/finance
awk -F',' '$4 > 10000 {print $0}' transactions.csv > high_value.csv
```

### Biology: Count DNA Sequences
```bash
cd data/biology
grep -c "^>" sequences.fasta
```

### Architecture: List Project Status
```bash
cd data/architecture
cut -d',' -f2,4 projects.csv | grep "In Progress"
```

## Tips

- Always use `pwd` to know where you are
- Use `ls -la` to see all files including hidden ones
- Use Tab completion to avoid typos
- Test commands with `echo` or `ls` before running destructive operations
- Make backups before modifying data: `cp file.csv file.csv.backup`

## Need Help?

- Check the main lecture notes in `../lecture02.md`
- Use `man <command>` to read the manual
- Use `<command> --help` for quick reference
- Ask your instructor or classmates

## License

This data is for educational purposes only. All datasets are fictional and generated for teaching command line skills.
