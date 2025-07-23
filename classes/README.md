# 📊 Smart Downloader & Data Extractor Toolkit

This toolkit offers modular, reusable Python classes and functions for downloading, extracting, and transforming web-based and local data files into pandas DataFrames. It’s ideal for data analysts, data scientists, and developers working with JSON, HTML, or CSV files from online sources.

---

## 🧰 1. Setting Up Environment

```python
import os
import io
import json
import zipfile
import mimetypes
import requests
import pandas as pd
These are essential libraries for:

File operations (os, io, zipfile, mimetypes)

Web requests and parsing (requests, json)

Data manipulation (pandas)

2. SmartDownloader Class

class SmartDownloader:
🔧 Features:
Download files from any valid URL.

Auto-detect file format (.json, .csv, .html).

Convert data into pandas.DataFrame automatically.

🔍 Methods:
download(): Downloads file from the web.

to_dataframe(): Converts the downloaded file to a DataFrame.

fetch(): Combines download and conversion into one step
Example:
df = SmartDownloader(url="https://example.com/data.csv").fetch()

python

def dict_create(list_dict):
    ...
🔧 What It Does:
Converts a list of dictionaries into a dictionary of lists.

🔄 Example Input:
python

[{'a': 1, 'b': 2}, {'a': 3, 'b': 4}]
✅ Output:
python

{'a': [1, 3], 'b': [2, 4]}
Useful for cleaning JSON or API data into DataFrame-ready formats.

📝 4. WikipediaTableDownloader Class
python
class WikipediaTableDownloader:
    ...
🔧 Features:
Scrapes all tables from a given Wikipedia URL.

Lets you select a specific table by index.

Converts it into a DataFrame.

Saves it as a CSV if desired.

🔍 Methods:
fetch_tables(): Downloads all HTML tables.

select_table(index): Selects a specific table.

save_csv(): Saves the selected table.

get_dataframe(): Returns the selected table as a DataFrame.

✅ Example:
python
wiki = WikipediaTableDownloader("https://en.wikipedia.org/wiki/List_of_countries_by_GDP_(nominal)")
df = wiki.fetch_tables().select_table(0).get_dataframe()
💾 5. Saving & Additional Conversion Tools
✅ save_csv Class

class save_csv:
    ...
Takes a DataFrame and a file name.

Saves the DataFrame to .csv using .save_csv() method.

✅ one_dict() Function

def one_dict(list_dict):
    ...
Same as dict_create() — converts a list of dictionaries into a dictionary of lists.

📌 Example Workflow

# Download and load a CSV file into DataFrame
df = SmartDownloader("https://example.com/data.csv").fetch()

# Save it to a CSV file
save_csv("output.csv", df).save_csv()

# Extract Wikipedia table
wiki_df = WikipediaTableDownloader("https://en.wikipedia.org/wiki/List_of_...").fetch_tables().select_table(0).get_dataframe()
📂 Output
All downloads are saved locally.

Cleaned datasets are in pandas DataFrame format.

Tables can be exported to CSV easily.

✅ Use Cases
Web scraping Wikipedia tables

Converting JSON API responses to DataFrames

Saving analysis-ready CSVs

Quick EDA from remote sources
