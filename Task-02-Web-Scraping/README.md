# Task 02: Automated Web Scraping & Data Extraction Pipeline

## Project Overview

This project implements an automated web scraping pipeline using Python. It collects book information from [Books to Scrape](https://books.toscrape.com/), a website provided for practicing web scraping.

The pipeline retrieves product listing pages, extracts selected book attributes, converts the extracted information into a structured Pandas DataFrame, and exports the results to a CSV file.

## Data Source

- Website: https://books.toscrape.com/
- Target: Public book catalogue pages
- Pagination: Follows the website's `Next` link, subject to the configured maximum page count.

## Data Fields

| Field | Description |
|---|---|
| `Title` | Book title |
| `Price_GBP` | Book price in GBP, stored as a numeric value |
| `Numeric_Rating` | Star rating converted to a number from 1 to 5 |
| `Availability_Status` | Availability text shown on the listing |
| `URL` | Absolute URL of the book detail page |

## Technologies

- Python
- Requests – sends HTTP requests to retrieve page content
- BeautifulSoup (with lxml) – parses HTML and selects product elements
- Pandas – stores extracted records in a DataFrame and exports CSV
- urllib.parse – resolves relative links into absolute URLs
- time – adds a delay between page requests
- Google Colab – notebook execution environment

## Pipeline Workflow

1. Send an HTTP GET request to the catalogue page.
2. Parse the returned HTML with BeautifulSoup.
3. Select product cards using the `article.product_pod` CSS selector.
4. Extract each book's title, price, rating, availability, and product URL.
5. Follow the pagination link to process subsequent pages.
6. Store extracted records in a Pandas DataFrame.
7. Export the dataset as `extracted_books.csv`.

## How to Run

1. Open `PROGREE_Task_02_Web_Scraping.ipynb` in Google Colab.
2. Run the installation/import cells if included in the notebook.
3. Run the scraping function cell.
4. Execute the pipeline call:

   ```python
   book_df = run_scraping_pipeline(max_pages=50)
   display(book_df.head(10))
   ```

5. Download the generated CSV file from the Colab session.

## Output

The notebook generates:

- `extracted_books.csv` – structured dataset containing the extracted book records.

The actual number of records depends on successful page requests and the website's current catalogue. Verify the row count and inspect the CSV after running the notebook.

## Limitations

- The pipeline depends on the source website's HTML structure and CSS selectors.
- Network failures or changes to the website may interrupt extraction.
- The maximum page count is configurable; the default project run is set to 50 pages.
- This project uses CSV storage rather than a database.

## Responsible Use

This project uses the Books to Scrape practice website. Requests are made with a delay between pages. Always review a website's terms and scraping policies before collecting data from other websites.

## Project Files

```text
Task-02-Web-Scraping/
├── PROGREE_Task_02_Web_Scraping.ipynb
├── extracted_books.csv
└── README.md
```

Add the executed Colab notebook and generated CSV to this folder before submitting the task.