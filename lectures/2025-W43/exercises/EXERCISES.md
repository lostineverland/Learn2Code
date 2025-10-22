# Command Line Practice Exercises

Complete these exercises using the data files in the `data/` directory. Work through them in order - they progress from basic to advanced.

## Getting Started

1. Navigate to the exercises directory:
   ```bash
   cd lectures/2025-W43/exercises
   ```

2. Explore the available data:
   ```bash
   ls -R data/
   ```

3. Always verify where you are:
   ```bash
   pwd
   ```

---

## Beginner Exercises

### Exercise 1: Basic Navigation

**Goal:** Get comfortable moving around directories.

```bash
# Navigate to the medicine directory
cd data/medicine

# List all files
ls -l

# View your location
pwd

# Go back up one level
cd ..

# Go to biology directory
cd biology

# Return to exercises root
cd ../..
```

**Tasks:**
- Navigate to each data directory (medicine, finance, architecture, biology, general)
- List the files in each
- Count how many CSV files exist in the medicine directory

### Exercise 2: Viewing Files

**Goal:** Practice different ways to view file contents.

```bash
cd data/general

# View entire file
cat sample.txt

# View first 5 lines
head -5 names.txt

# View last 5 lines
tail -5 numbers.txt

# View file with scrolling
less sample.txt  # Press 'q' to quit
```

**Tasks:**
- View the first 10 lines of `data/medicine/patients.csv`
- View the last 5 lines of `data/biology/observations.csv`
- Count total lines in `data/general/names.txt`

### Exercise 3: Counting and Searching

**Goal:** Use `wc` and `grep` to analyze files.

```bash
cd data/medicine

# Count lines in a file
wc -l patients.csv

# Search for a pattern
grep "Diabetes" patients.csv

# Count matching lines
grep -c "Diabetes" patients.csv

# Case-insensitive search
grep -i "diabetes" patients.csv
```

**Tasks:**
- How many patients have diabetes? (Hint: use grep -c)
- How many total patients are in the file? (Hint: subtract 1 for header)
- Find all entries for "Dr. Williams"

---

## Intermediate Exercises

### Exercise 4: Using Pipes

**Goal:** Combine commands to solve problems.

```bash
cd data/finance

# Count high-value transactions
grep "Investment" transactions.csv | wc -l

# View and count
cat transactions.csv | grep "Debit" | grep "Groceries"

# Sort and view unique values
cut -d',' -f6 transactions.csv | sort | uniq
```

**Tasks:**
- Find all Investment transactions and count them
- List all unique account IDs from transactions.csv
- Find the top 5 most frequent transaction types

### Exercise 5: Sorting and Filtering

**Goal:** Process data with `sort`, `cut`, and `uniq`.

```bash
cd data/biology

# Extract specific columns
cut -d',' -f1,3,4 observations.csv | head -10

# Sort by species
sort -t',' -k4 observations.csv > sorted_observations.csv

# Find unique species
cut -d',' -f4 observations.csv | sort | uniq

# Count observations per species
cut -d',' -f4 observations.csv | sort | uniq -c | sort -rn
```

**Tasks:**
- List all unique species observed
- Count how many times each species was observed
- Extract just the dates and locations from observations.csv

### Exercise 6: Redirection

**Goal:** Save command outputs to files.

```bash
cd data/architecture

# Save list to file
ls -l > files_list.txt

# Append to file
echo "End of list" >> files_list.txt

# Extract in-progress projects
grep "In Progress" projects.csv > active_projects.csv

# Count them
wc -l active_projects.csv
```

**Tasks:**
- Create a file with all "In Progress" projects
- Create a file with all projects over $2,000,000
- Save a list of all unique client names

---

## Advanced Exercises

### Exercise 7: Complex Data Processing

**Medicine:** Analyze patient medications

```bash
cd data/medicine

# Find diabetic patients
grep -i "diabetes" patients.csv | cut -d',' -f1 > diabetic_ids.txt

# Count their medications
# (This requires manually checking medication records)

# Or create a summary
grep -i "diabetes" patients.csv | cut -d',' -f1,2,3,5 > diabetic_summary.csv
```

**Tasks:**
- Create a list of all patients over 65
- Count how many patients are taking Metformin
- Find all lab results marked as "High" or "Critical"

### Exercise 8: Finance Analysis

```bash
cd data/finance

# Find high-value transactions (>$10,000)
awk -F',' '$4 > 10000 {print $0}' transactions.csv > high_value.csv

# Calculate by type (Credit vs Debit)
grep ",Credit," transactions.csv | wc -l
grep ",Debit," transactions.csv | wc -l

# Extract specific account's transactions
grep "ACC-1001" transactions.csv > acc_1001_history.csv
```

**Tasks:**
- Find all transactions over $5,000
- Count Credit vs Debit transactions
- List all transactions for investment accounts
- Find the date range of all transactions

### Exercise 9: Biology Data

**DNA Sequence Analysis:**

```bash
cd data/biology

# Count sequences
grep -c "^>" sequences.fasta

# Find human sequences
grep "human" sequences.fasta

# Count human sequences
grep -c "human" sequences.fasta

# Extract human sequence headers
grep ">.*human" sequences.fasta
```

**Environmental Data:**

```bash
# Species with most observations
cut -d',' -f4 observations.csv | sort | uniq -c | sort -rn | head -5

# Count by location
cut -d',' -f3 observations.csv | sort | uniq -c

# Filter by weather
grep "Clear" observations.csv | wc -l
```

**Tasks:**
- Count total DNA sequences
- How many are human sequences?
- Which species has the most observations?
- List all observations from Site_A

### Exercise 10: Log File Analysis

```bash
cd data/general/logs

# Count errors
grep -c "ERROR" system.log

# Find all warnings
grep "WARNING" system.log

# Count by severity
echo "Errors: $(grep -c ERROR system.log)"
echo "Warnings: $(grep -c WARNING system.log)"
echo "Info: $(grep -c INFO system.log)"

# Extract just the timestamps and error messages
grep "ERROR" system.log | cut -d' ' -f1,2,5-
```

**Tasks:**
- How many ERROR entries in system.log?
- How many WARNING entries?
- What time did the first error occur?
- Find all entries about "backup"

---

## Challenge Exercises

### Challenge 1: Multi-File Analysis

Create a report combining data from multiple files:

```bash
cd data/medicine

# Count total patients
echo "Total Patients: $(tail -n +2 patients.csv | wc -l)"

# Count total appointments
echo "Total Appointments: $(tail -n +2 appointments.csv | wc -l)"

# Count total lab results
echo "Total Lab Results: $(tail -n +2 lab_results.csv | wc -l)"
```

### Challenge 2: Data Transformation

Extract and reformat data:

```bash
cd data/finance

# Create a summary by month
cut -d',' -f3 transactions.csv | cut -c1-7 | sort | uniq -c

# Count transactions per account
cut -d',' -f2 transactions.csv | tail -n +2 | sort | uniq -c | sort -rn
```

### Challenge 3: Cross-Domain Integration

Combine techniques across different data sets:

1. Find the most active project in architecture/projects.csv
2. Identify which species is most commonly observed in biology
3. Calculate transaction volume by category in finance
4. Determine the most common diagnosis in medicine

### Challenge 4: Automation Script

Create a file called `daily_report.sh`:

```bash
#!/bin/bash
echo "Daily Data Report - $(date)"
echo "================================"
echo ""
echo "Medicine:"
echo "  Total Patients: $(tail -n +2 data/medicine/patients.csv | wc -l)"
echo ""
echo "Finance:"
echo "  Total Transactions: $(tail -n +2 data/finance/transactions.csv | wc -l)"
echo ""
echo "Biology:"
echo "  Total Observations: $(tail -n +2 data/biology/observations.csv | wc -l)"
```

Make it executable and run it:
```bash
chmod +x daily_report.sh
./daily_report.sh
```

---

## Tips for Success

1. **Always test with ls or echo first**
   ```bash
   # Before: rm *.csv
   # Test with: ls *.csv
   ```

2. **Use head to preview results**
   ```bash
   grep "pattern" file.csv | head -5
   ```

3. **Save intermediate results**
   ```bash
   grep "filter" data.csv > filtered.csv
   # Then work with filtered.csv
   ```

4. **Build pipelines step by step**
   ```bash
   # Start simple
   cat file.csv
   # Add filtering
   cat file.csv | grep "pattern"
   # Add sorting
   cat file.csv | grep "pattern" | sort
   # Add counting
   cat file.csv | grep "pattern" | sort | uniq -c
   ```

5. **Use man and --help**
   ```bash
   man grep
   sort --help
   ```

## Verification

Check your understanding:

- [ ] Can you navigate to any directory quickly?
- [ ] Can you find specific data with grep?
- [ ] Can you count occurrences with wc and uniq?
- [ ] Can you extract specific columns with cut?
- [ ] Can you sort data by different columns?
- [ ] Can you redirect output to files?
- [ ] Can you chain multiple commands with pipes?
- [ ] Can you analyze log files?

## Next Steps

After completing these exercises:
1. Try the challenge exercises
2. Create your own datasets
3. Write shell scripts to automate common tasks
4. Explore advanced tools like `awk` and `sed`

## Need Help?

- Check the main lecture notes: `../lecture02.md`
- Use `man <command>` for detailed help
- Ask your instructor or classmates
- Practice, practice, practice!
