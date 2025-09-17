---
theme: default
background: https://images.pexels.com/photos/186464/pexels-photo-186464.jpeg
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
## File Operations in R Stats
### Writing & Reading Data with Confidence

*Walk through the fundamentals of data I/O in R*

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer text-white hover:bg-blue-600">
    Start Learning <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="absolute bottom-4 left-4 text-xs opacity-50">
Photo by Burak The Weekender: 
https://www.pexels.com/photo/white-android-tablet-turned-on-displaying-a-graph-186464/
</div>

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/sounddrill31/rstats-presentation" target="_blank" alt="GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
layout: two-cols-header
---

# Objectives

In this section, we'll explore essential file handling techniques in data processing workflows.
- These objectives cover both output and input operations to manage data effectively.
- Understanding these skills will enhance your ability to work with various file formats seamlessly.
- These will be demonstrated with real, working examples!

::right::
### 📝 Writing Files
- Creating CSV files

::left::

### 📖 Reading Files
- CSV data import
- Text file processing
- Excel file handling
- Data validation

---
layout: two-cols-header
---

# Creating Your First CSV File

Understanding the basics of structured data output

::left::
```r {1-8|9-10|11-13|*}
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

💡 **Key Points:**
- Use `row.names = FALSE` to avoid index column
- Data frame structure translates directly to CSV
- Always verify file creation with `file.exists()`

**Sample Output: students.csv**
```csv
Name,Age,Grade,Major
Alice,22,88,CS
Bob,24,92,Math
Carol,23,85,Physics
David,25,90,CS
```

---
layout: iframe

# the web page source
url: https://examdawn.pages.dev/jupyterlite/dist/repl/index.html?kernel=webR&code=%23%20Create%20a%20sample%20dataset%0Astudents%20%3C-%20data.frame(%0A%20%20Name%20%3D%20c(%22Alice%22%2C%20%22Bob%22%2C%20%22Carol%22%2C%20%22David%22)%2C%0A%20%20Age%20%3D%20c(22%2C%2024%2C%2023%2C%2025)%2C%0A%20%20Grade%20%3D%20c(88%2C%2092%2C%2085%2C%2090)%2C%0A%20%20Major%20%3D%20c(%22CS%22%2C%20%22Math%22%2C%20%22Physics%22%2C%20%22CS%22)%0A)%0A%0A%23%20Write%20to%20CSV%20file%0Awrite.csv(students%2C%20%22%2Ftmp%2Fstudents.csv%22%2C%20row.names%20%3D%20FALSE)%0A%0A%23%20Verify%20the%20file%20was%20created%0Afile.exists(%22students.csv%22)%0Aprint(%22CSV%20file%20created%20successfully!%22)&execute=1 
---
Please wait for it to load
---
layout: two-cols-header
---

# Reading Text Files

Processing unstructured text data

::left::

```r {2,6|10-11|*}
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
- `readLines()` for line-by-line access
- Use `grep()` for pattern matching
- Always close file connections
- Process incrementally for large files

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

---
layout: iframe

# the web page source
url: https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=%23%20Read%20entire%20file%20as%20character%20vector%0Atext_content%20%3C-%20readLines(%22https%3A%2F%2Fraw.githubusercontent.com%2Fsounddrill31%2Frstats-presentation%2Frefs%2Fheads%2Fmain%2Freport.txt%22)%0Aprint(text_content)%0A%0A%23%20Read%20specific%20number%20of%20lines%0Afirst_three%20%3C-%20readLines(%22https%3A%2F%2Fraw.githubusercontent.com%2Fsounddrill31%2Frstats-presentation%2Frefs%2Fheads%2Fmain%2Freport.txt%22%2C%20n%20%3D%203)%0Aprint(first_three)%0A%0A%23%20Process%20line%20by%20line%0Acon%20%3C-%20file(%22https%3A%2F%2Fraw.githubusercontent.com%2Fsounddrill31%2Frstats-presentation%2Frefs%2Fheads%2Fmain%2Freport.txt%22%2C%20%22r%22)%0Alines%20%3C-%20readLines(con)%0Aclose(con)%0A%0A%23%20Extract%20specific%20information%0Anumeric_lines%20%3C-%20grep(%22%5B0-9%5D%2B%22%2C%20text_content%2C%20value%20%3D%20TRUE)%0Aprint(numeric_lines)&execute=1
---
---
layout: two-cols-header
---

# CSV File Handling

Working with spreadsheet data in CSV

::left::
```r {2|5-13|*}
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

- Always check data structure with `str()`
- Validate row/column counts
- Use `stringsAsFactors = FALSE` for modern R

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

---
layout: iframe

# the web page source
url: https://examdawn.pages.dev/jupyterlite/dist/repl/index.html?kernel=webR&code=%23%20Read%20CSV-like%20data%20structure%0Ainventory%20%3C-%20read.csv(%22https%3A%2F%2Fraw.githubusercontent.com%2Fsounddrill31%2Frstats-presentation%2Frefs%2Fheads%2Fmain%2Finventory.csv%22)%0Ahead(inventory)%0A%0A%23%20Data%20analysis%20and%20visualization%0Atotal_value%20%3C-%20inventory%24Price%20*%20inventory%24Stock%0Ainventory%24Total%20%3C-%20total_value%0A%0A%23%20Create%20visualizations%0Abarplot(inventory%24Total%2C%20names.arg%20%3D%20inventory%24Product%2C%20%0A%20%20%20%20%20%20%20%20col%20%3D%20%22orange%22%2C%20main%20%3D%20%22Inventory%20Value%22)%0Apie(inventory%24Stock%2C%20labels%20%3D%20inventory%24Product%2C%20%0A%20%20%20%20main%20%3D%20%22Stock%20Distribution%22)&execute=1

---
---
layout: two-cols-header
---

# Excel File Handling

Working with spreadsheet data (TODO: Make excel)
::left::
```r {6|9-17|*}
# For Excel files, we'll simulate with CSV
# In practice, use: library(readxl)
# excel_data <- read_excel("file.xlsx")

# Read Excel-like data structure
library(readxl)
inventory <- read_excel("file.xlsx")
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
- Use `readxl` package for true Excel files
- CSV format works for most Excel needs
- Include `fileEncoding = "UTF-8"` for special characters
- Visualize inventory data with bar and pie charts

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
---
layout: iframe

# the web page source
url: https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=%23%20For%20Excel%20files%2C%20we%27ll%20simulate%20with%20CSV%0A%23%20In%20practice%2C%20use%3A%20library(readxl)%0A%23%20excel_data%20%3C-%20read_excel(%22https%3A%2F%2Fraw.githubusercontent.com%2Fsounddrill31%2Frstats-presentation%2Frefs%2Fheads%2Fmain%2Finventory.xlsx%22)%0A%0A%23%20Read%20Excel-like%20data%20structure%0Alibrary(readxl)%0Atemp_file%20%3C-%20tempfile(fileext%20%3D%20%22.xlsx%22)%0A%0A%23%202.%20Download%20the%20Excel%20file%20from%20the%20URL%20into%20the%20temporary%20file%0Adownload.file(%0A%20%20%22https%3A%2F%2Fraw.githubusercontent.com%2Fsounddrill31%2Frstats-presentation%2Frefs%2Fheads%2Fmain%2Finventory.xlsx%22%2C%0A%20%20destfile%20%3D%20temp_file%2C%0A%20%20mode%20%3D%20%22wb%22%0A)%0A%0A%23%203.%20Read%20the%20Excel%20file%20from%20the%20temporary%20file%20path%0Ainventory%20%3C-%20read_excel(temp_file)%0A%0Ahead(inventory)%0A%0A%23%20Data%20analysis%20and%20visualization%0Atotal_value%20%3C-%20inventory%24Price%20*%20inventory%24Stock%0Ainventory%24Total%20%3C-%20total_value%0A%0A%23%20Create%20visualizations%0Abarplot(inventory%24Total%2C%20names.arg%20%3D%20inventory%24Product%2C%20%0A%20%20%20%20%20%20%20%20col%20%3D%20%22orange%22%2C%20main%20%3D%20%22Inventory%20Value%22)%0Apie(inventory%24Stock%2C%20labels%20%3D%20inventory%24Product%2C%20%0A%20%20%20%20main%20%3D%20%22Stock%20Distribution%22)&execute=1
---
---
layout: two-cols-header
class: text-center
---

# Best Practices Summary

::left:: 
## 📝 Writing Guidelines
Use meaningful filenames  
Include headers in CSV files  
Set `row.names = FALSE` for clean output  
Handle special characters with encoding  
Create backup copies of important data  

::right::

## 📖 Reading Guidelines
Always validate file existence  
Check data structure with `str()`  
Handle missing values appropriately  
Use consistent column types  
Implement error handling  

---
layout: two-cols-header
class: text-center
---

# 🎉 Congratulations!

Presentation by Souhrud Reddy

## You've Mastered R File Operations

::left:: 
### ✅ Writing Skills
CSV creation  


::right::
### ✅ Reading Skills  
CSV handling  
Text handling  
Excel handling  