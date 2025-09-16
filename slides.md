---
theme: default
background: https://source.unsplash.com/1920x1080/?data,statistics
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## R Statistics Presentation
  File operations and data manipulation in R with live demonstrations
drawings:
  persist: false
transition: slide-left
title: R Statistics - File Operations & Data Manipulation
mdc: true
---

# R Statistics
## File Operations & Data Manipulation

Interactive presentation with live R demonstrations

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---
transition: fade-out
---

# What we'll cover

<Toc maxDepth="1"></Toc>

---
transition: slide-left
layout: two-cols
---

# Reading Text Files in R

Working with plain text files is fundamental in R data analysis.

::right::

## Common Methods

- `readLines()` - Read lines as character vector
- `read.table()` - Read structured text data  
- `scan()` - Read data into vectors
- `read.delim()` - Read delimited files

<iframe 
  src="https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=# Reading a simple text file%0A# Create sample data%0Adata <- c('Name,Age,Score', 'Alice,25,95', 'Bob,30,87', 'Carol,28,92')%0Awrite(data, 'sample.txt')%0A%0A# Read the file%0Alines <- readLines('sample.txt')%0Aprint(lines)&execute=1"
  width="100%" 
  height="300" 
  frameborder="0">
</iframe>

---
transition: slide-left
layout: two-cols
---

# Reading CSV Files in R

CSV (Comma Separated Values) files are the most common data format in data science.

::right::

## Key Functions

- `read.csv()` - Standard CSV reader
- `read.csv2()` - For semicolon-separated files
- `read_csv()` from readr package (faster)

<iframe 
  src="https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=# Reading CSV files%0A# Create sample CSV data%0Adata <- data.frame(%0A  Name = c('Alice', 'Bob', 'Carol', 'David'),%0A  Age = c(25, 30, 28, 35),%0A  Score = c(95, 87, 92, 89)%0A)%0A%0A# Write to CSV%0Awrite.csv(data, 'sample.csv', row.names = FALSE)%0A%0A# Read the CSV file%0Adf <- read.csv('sample.csv')%0Aprint(df)%0Astr(df)&execute=1"
  width="100%" 
  height="350" 
  frameborder="0">
</iframe>

---
transition: slide-left
layout: two-cols
---

# Reading Excel Files in R

Excel files require special packages but are very common in business environments.

::right::

## Popular Packages

- `readxl` - Read Excel files (.xls, .xlsx)
- `openxlsx` - Read and write Excel files
- `XLConnect` - Comprehensive Excel interface

<iframe 
  src="https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=# Working with Excel-like data%0A# Since webR doesn't support Excel packages directly,%0A# we'll simulate Excel data reading%0A%0A# Create a data frame similar to Excel structure%0Aexcel_like_data <- data.frame(%0A  Product = c('Laptop', 'Mouse', 'Keyboard', 'Monitor'),%0A  Price = c(999.99, 25.50, 75.00, 299.99),%0A  Quantity = c(10, 50, 30, 15),%0A  Category = c('Electronics', 'Accessories', 'Accessories', 'Electronics')%0A)%0A%0Aprint('Simulated Excel Data:')%0Aprint(excel_like_data)%0A%0A# Calculate total value%0Aexcel_like_data$Total <- excel_like_data$Price * excel_like_data$Quantity%0Aprint('With calculated totals:')%0Aprint(excel_like_data)&execute=1"
  width="100%" 
  height="350" 
  frameborder="0">
</iframe>

---
transition: slide-left
layout: two-cols
---

# Writing Files in R

Saving your processed data is crucial for reproducible analysis.

::right::

## Output Formats

- `write.csv()` - Write CSV files
- `write.table()` - Write delimited files
- `writeLines()` - Write text lines
- `save()` / `saveRDS()` - Save R objects

<iframe 
  src="https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=# Writing files in R%0A# Create sample dataset%0Asales_data <- data.frame(%0A  Date = as.Date(c('2023-01-01', '2023-01-02', '2023-01-03')),%0A  Sales = c(1500, 2300, 1800),%0A  Region = c('North', 'South', 'East')%0A)%0A%0Aprint('Original data:')%0Aprint(sales_data)%0A%0A# Write to CSV%0Awrite.csv(sales_data, 'sales_output.csv', row.names = FALSE)%0A%0A# Verify by reading back%0Averify_data <- read.csv('sales_output.csv')%0Aprint('Verified data from file:')%0Aprint(verify_data)%0A%0A# Write custom text file%0Asummary_text <- paste('Total Sales:', sum(sales_data$Sales))%0AwriteLines(summary_text, 'summary.txt')%0A%0A# Read the summary%0Asummary_read <- readLines('summary.txt')%0Aprint(paste('Summary:', summary_read))&execute=1"
  width="100%" 
  height="350" 
  frameborder="0">
</iframe>

---
transition: slide-left
layout: two-cols
---

# Data Structure Preview

Understanding your data structure is essential before analysis.

::right::

## Key Functions

- `str()` - Display structure
- `head()` - First few rows
- `summary()` - Statistical summary
- `dim()` - Dimensions

<iframe 
  src="https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=# Data structure exploration%0A# Create a comprehensive dataset%0Astudent_data <- data.frame(%0A  StudentID = 1:20,%0A  Name = paste('Student', 1:20),%0A  Math = rnorm(20, mean = 85, sd = 10),%0A  Science = rnorm(20, mean = 82, sd = 12),%0A  English = rnorm(20, mean = 88, sd = 8),%0A  Grade = sample(c('A', 'B', 'C'), 20, replace = TRUE)%0A)%0A%0A# Preview structure%0Aprint('Data Structure:')%0Astr(student_data)%0A%0Aprint('First 6 rows:')%0Ahead(student_data)%0A%0Aprint('Statistical Summary:')%0Asummary(student_data)%0A%0Aprint('Dataset Dimensions:')%0Adim(student_data)&execute=1"
  width="100%" 
  height="350" 
  frameborder="0">
</iframe>

---
transition: slide-left
layout: two-cols
---

# Interactive Data Manipulation

Click through different data operations to see results.

::right::

## Operations Available

1. Filter data
2. Sort data  
3. Create new columns
4. Group and summarize

<iframe 
  src="https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=# Interactive data manipulation%0A# Create sample dataset%0Aemployee_data <- data.frame(%0A  Name = c('Alice', 'Bob', 'Carol', 'David', 'Eve', 'Frank'),%0A  Department = c('Sales', 'IT', 'HR', 'Sales', 'IT', 'HR'),%0A  Salary = c(50000, 70000, 55000, 48000, 75000, 52000),%0A  Years = c(3, 5, 2, 7, 4, 6)%0A)%0A%0Aprint('Original Data:')%0Aprint(employee_data)%0A%0A# Filter: High earners (> 55000)%0Ahigh_earners <- employee_data[employee_data$Salary > 55000, ]%0Aprint('High Earners (Salary > 55000):')%0Aprint(high_earners)%0A%0A# Sort by salary%0Asorted_data <- employee_data[order(employee_data$Salary, decreasing = TRUE), ]%0Aprint('Sorted by Salary (Descending):')%0Aprint(sorted_data)%0A%0A# Create new column: Salary per year%0Aemployee_data$SalaryPerYear <- employee_data$Salary / employee_data$Years%0Aprint('With Salary per Year ratio:')%0Aprint(employee_data)&execute=1"
  width="100%" 
  height="350" 
  frameborder="0">
</iframe>

---
transition: slide-left
layout: two-cols
---

# Final Visualization

Let's create a comprehensive graph from our data operations.

::right::

## Visualization Steps

1. Load and prepare data
2. Calculate aggregations
3. Create professional plot
4. Add styling and labels

<iframe 
  src="https://examdawn.pages.dev/jupyterlite/dist/repl/?kernel=webR&code=# Final comprehensive visualization%0A# Create realistic sales dataset%0Aset.seed(123)%0Asales_data <- data.frame(%0A  Month = factor(month.abb[1:12], levels = month.abb),%0A  Sales_2023 = round(rnorm(12, mean = 15000, sd = 3000), 0),%0A  Sales_2024 = round(rnorm(12, mean = 18000, sd = 3500), 0)%0A)%0A%0A# Calculate percentage growth%0Asales_data$Growth <- round(((sales_data$Sales_2024 - sales_data$Sales_2023) / sales_data$Sales_2023) * 100, 1)%0A%0Aprint('Sales Data with Growth:')%0Aprint(sales_data)%0A%0A# Create a detailed plot%0Apar(mfrow = c(2, 2), mar = c(4, 4, 3, 2))%0A%0A# Plot 1: Sales comparison%0Abarplot(rbind(sales_data$Sales_2023, sales_data$Sales_2024),%0A        beside = TRUE,%0A        names.arg = sales_data$Month,%0A        col = c('lightblue', 'darkblue'),%0A        main = 'Sales Comparison 2023 vs 2024',%0A        ylab = 'Sales ($)',%0A        legend = c('2023', '2024'))%0A%0A# Plot 2: Growth rate%0Abarplot(sales_data$Growth,%0A        names.arg = sales_data$Month,%0A        col = ifelse(sales_data$Growth > 0, 'green', 'red'),%0A        main = 'Monthly Growth Rate (%)',%0A        ylab = 'Growth (%)')%0A%0A# Plot 3: Line trend%0Aplot(1:12, sales_data$Sales_2023, type = 'o', col = 'blue',%0A     main = 'Sales Trends', xlab = 'Month', ylab = 'Sales',%0A     ylim = c(min(sales_data$Sales_2023, sales_data$Sales_2024),%0A              max(sales_data$Sales_2023, sales_data$Sales_2024)))%0Alines(1:12, sales_data$Sales_2024, type = 'o', col = 'red')%0Alegend('topright', c('2023', '2024'), col = c('blue', 'red'), lty = 1)%0A%0A# Plot 4: Summary statistics%0Asummary_stats <- data.frame(%0A  Year = c('2023', '2024'),%0A  Total = c(sum(sales_data$Sales_2023), sum(sales_data$Sales_2024)),%0A  Average = c(mean(sales_data$Sales_2023), mean(sales_data$Sales_2024))%0A)%0A%0Abarplot(summary_stats$Total,%0A        names.arg = summary_stats$Year,%0A        col = c('lightcoral', 'lightseagreen'),%0A        main = 'Total Sales by Year',%0A        ylab = 'Total Sales ($)')%0A%0Aprint('Summary Statistics:')%0Aprint(summary_stats)&execute=1"
  width="100%" 
  height="400" 
  frameborder="0">
</iframe>

---
layout: center
class: text-center
---

# Thank You!

## Key Takeaways

✅ **Reading Files**: Text, CSV, and Excel data import  
✅ **Writing Files**: Saving processed data in various formats  
✅ **Data Structure**: Understanding and exploring your datasets  
✅ **Live Demos**: Interactive R coding with webR  
✅ **Visualizations**: Creating meaningful plots and charts  

### Resources
- [R Documentation](https://www.r-project.org/other-docs.html)
- [webR Project](https://docs.r-wasm.org/webr/latest/)
- [RStudio Cheat Sheets](https://posit.co/resources/cheatsheets/)

<div class="pt-12">
  <span @click="$slidev.nav.restart" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    <carbon:restart class="inline"/> Restart Presentation
  </span>
</div>

---