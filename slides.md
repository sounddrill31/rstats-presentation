---
theme: default
background: https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80
class: text-center
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
transition: slide-left
title: R Programming - File Operations
mdc: true
---

# R Programming
## File Operations Mastery
### Writing & Reading Data with Confidence

*Master the fundamentals of data I/O in R*

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer bg-blue-500 text-white hover:bg-blue-600">
    Start Learning <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: two-cols
---

# 📝 Writing Files
- Creating CSV files
- Exporting data frames
- Text file output
- Best practices

::right::

# 📖 Reading Files
- CSV data import
- Text file processing
- Excel file handling
- Data validation

*Interactive demos with real code and data examples*

---
layout: two-cols
---

# Creating Your First CSV File

Understanding the basics of structured data output

```r {1-8|9-10|11-13}
# Create a sample dataset
students <- data.frame(
  Name = c("Alice", "Bob", "Carol", "David"),
  Age = c(22, 24, 23, 25),
  Grade = c(88, 92, 85, 90),
  Major = c("CS", "Math", "Physics", "CS")
)

# Write to CSV file
write.csv(students, "students.csv", row.names = FALSE)

# Verify the file was created
file.exists("students.csv")
print("CSV file created successfully!")
```

*Try the code in your R environment and observe the output*

::right::

**Sample Output: students.csv**
```csv
Name,Age,Grade,Major
Alice,22,88,CS
Bob,24,92,Math
Carol,23,85,Physics
David,25,90,CS
```

💡 **Key Points:**
- Use `row.names = FALSE` to avoid index column
- Data frame structure translates directly to CSV
- Always verify file creation with `file.exists()`

---

# Live Demo: CSV Writing

<iframe src="https://www.google.com" width="100%" height="500" class="border rounded-lg"></iframe>

---
layout: two-cols
---

# Reading Text Files

Processing unstructured text data

```r {1-3|4-7|8-12|13-16}
# Read entire file as character vector
text_content <- readLines("report.txt")
print(text_content)

# Read specific number of lines
first_three <- readLines("report.txt", n = 3)
print(first_three)

# Process line by line
con <- file("report.txt", "r")
lines <- readLines(con)
close(con)

# Extract specific information
numeric_lines <- grep("[0-9]+", text_content, value = TRUE)
print(numeric_lines)
```

*Try the code in your R environment and observe the output*

::right::

**Sample Data: report.txt**
```text
Student Performance Report
==========================
Total students: 4
Average grade: 88.75

Department Analysis
==================
CS: 2 students
Math: 1 student  
Physics: 1 student
```

💡 **Text Processing Tips:**
- `readLines()` for line-by-line access
- Use `grep()` for pattern matching
- Always close file connections
- Process incrementally for large files

---

# Live Demo: Text File Reading

<iframe src="https://www.google.com" width="100%" height="500" class="border rounded-lg"></iframe>

*Work with text files and pattern extraction*


---
layout: two-cols
---

# CSV File Handling

Working with spreadsheet data in CSV

```r {2|5-13}
# Read CSV-like data structure
inventory <- read.csv("inventory.csv")
head(inventory)

# Data analysis and visualization
total_value <- inventory$Price * inventory$Stock
inventory$Total <- total_value

# Create visualizations
barplot(inventory$Total, names.arg = inventory$Product, 
        col = "orange", main = "Inventory Value")
pie(inventory$Stock, labels = inventory$Product, 
    main = "Stock Distribution")
```

*Try the code in your R environment and observe the output*

::right::

**Sample Data: inventory.csv**
```csv
Product,Price,Stock,Category
Laptop,999.99,15,Electronics
Mouse,29.99,100,Accessories
Monitor,299.99,25,Electronics
Keyboard,79.99,50,Accessories
Headphones,199.99,30,Electronics
Cable,15.99,200,Accessories
```

- Always check data structure with `str()`
- Validate row/column counts
- Use `stringsAsFactors = FALSE` for modern R

---

# Live Demo: CSV-style Data

<iframe src="https://www.google.com" width="100%" height="500" class="border rounded-lg"></iframe>

*Handle spreadsheet-like data structures*

---
layout: two-cols
---

# Excel File Handling

Working with spreadsheet data (TODO: Make excel)

```r {6|9-17}
# For Excel files, we'll simulate with CSV
# In practice, use: library(readxl)
# excel_data <- read_excel("file.xlsx")

# Read Excel-like data structure
inventory <- read.csv("inventory.csv")
head(inventory)

# Data analysis and visualization
total_value <- inventory$Price * inventory$Stock
inventory$Total <- total_value

# Create visualizations
barplot(inventory$Total, names.arg = inventory$Product, 
        col = "orange", main = "Inventory Value")
pie(inventory$Stock, labels = inventory$Product, 
    main = "Stock Distribution")
```

*Try the code in your R environment and observe the output*

::right::

**Sample Data: inventory.xlsx** (csv representation)
```csv
Product,Price,Stock,Category
Laptop,999.99,15,Electronics
Mouse,29.99,100,Accessories
Monitor,299.99,25,Electronics
Keyboard,79.99,50,Accessories
Headphones,199.99,30,Electronics
Cable,15.99,200,Accessories
```

💡 **Excel Integration:**
- Use `readxl` package for true Excel files
- CSV format works for most Excel needs
- Include `fileEncoding = "UTF-8"` for special characters
- Visualize inventory data with bar and pie charts

---

# Live Demo: Excel-style Data

<iframe src="https://www.google.com" width="100%" height="500" class="border rounded-lg"></iframe>

*Handle spreadsheet-like data structures*

---
layout: two-cols
class: text-center
---

# Best Practices Summary

## 📝 Writing Guidelines
- Use meaningful filenames
- Include headers in CSV files
- Set `row.names = FALSE` for clean output
- Handle special characters with encoding
- Create backup copies of important data

::right::

## 📖 Reading Guidelines
- Always validate file existence
- Check data structure with `str()`
- Handle missing values appropriately
- Use consistent column types
- Implement error handling

---
layout: center
class: text-center
---

# 🎉 Congratulations!

## You've Mastered R File Operations

### ✅ Writing Skills
- CSV creation

### ✅ Reading Skills  
- CSV import
- Text processing
- Excel handling

### ✅ Best Practices
- Quality checks
- Error handling
- Consistent workflows
- Documentation