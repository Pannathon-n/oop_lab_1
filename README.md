# Data Processing Lab

## Lab Overview

This lab demonstrates a simple yet powerful data processing system that loads CSV data and performs filtering and aggregation operations. The system is designed to handle tabular data with a functional programming approach, allowing for chainable operations on datasets. It showcases core data manipulation concepts like filtering rows based on conditions and performing aggregate calculations on columns.

Key features:
- CSV data loading and parsing
- Functional-style data filtering
- Mathematical aggregations (average, max, count, etc.)
- Chainable operations for complex queries
- Type handling and error resilience

## Project Structure
project
- main.py # Main implementation file with all classes and test cases
- Cities.csv # Sample data file 
- README.md # This documentation file

The project consists of two main classes:
- `DataLoader`: Handles file I/O and CSV parsing
- `Table`: Core data structure for data manipulation operations

## Design Overview

### DataLoader Class

The `DataLoader` class is responsible for loading and parsing CSV data files.

**Attributes:**
- `base_path`: Path object representing the base directory for data files

**Key Methods:**

- `__init__(self, base_path=None)`
  - Initializes the DataLoader with an optional base path
  - If no path provided, uses the directory of the current file

- `load_csv(self, filename)`
  - Loads a CSV file and returns contents as a list of dictionaries
  - Each dictionary represents a row with column headers as keys
  - Parameters: `filename` - name of the CSV file to load
  - Returns: List of dictionaries containing the parsed data

### Table Class

The `Table` class represents a data table and provides methods for data manipulation.

**Attributes:**
- `name`: String identifier for the table
- `dict_list`: List of dictionaries representing the table rows

**Key Methods:**

- `__init__(self, name, dict_list)`
  - Initializes a Table with a name and data
  - Parameters: `name` - table name, `dict_list` - list of row dictionaries

- `filter(self, condition_func)`
  - Filters rows based on a condition function
  - Parameters: `condition_func` - lambda function that takes a row dict and returns boolean
  - Returns: New Table instance containing only the filtered rows
  - Example: `table.filter(lambda x: x['country'] == 'Germany')`

- `aggregate(self, agg_func, column_name)`
  - Performs aggregation on a specified column
  - Parameters: 
    - `agg_func` - aggregation function (lambda) that takes a list and returns a value
    - `column_name` - name of the column to aggregate
  - Returns: Result of the aggregation operation
  - Handles type conversion from string to float for numerical operations

## How to Test and Run Your Code

### Prerequisites
- Python 3.6 or higher
- CSV data file named `Cities.csv` in the same directory

### Sample Cities.csv Format
Your CSV file should have a structure similar to:
```csv
city,country,temperature
Berlin,Germany,10.5
Madrid,Spain,15.2
Rome,Italy,18.7
...