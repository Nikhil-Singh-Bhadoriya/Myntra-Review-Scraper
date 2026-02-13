# Myntra Review Scraper Project

## Overview
This project is a **web scraping application** that automatically extracts product information and customer reviews from Myntra (an Indian e-commerce platform). It uses Selenium WebDriver for browser automation and BeautifulSoup for HTML parsing.

---

## Approach & Methodology

### 1. **Technology Stack**
   - **Selenium WebDriver**: Automates Chrome browser to navigate and load dynamic content
   - **BeautifulSoup (bs4)**: Parses HTML and extracts specific data elements
   - **Python**: Core programming language
   - **Chrome Browser**: Used with automated driver for web navigation

### 2. **High-Level Workflow**

```
Browser Setup → Product Search → Extract Product Details → 
Navigate to Reviews → Parse Reviews → Extract User Feedback → Display Results
```

### 3. **Step-by-Step Process**

#### **Phase 1: Browser Initialization**
- Initialize Chrome WebDriver with optimized options
- Configure to avoid detection as a bot (disable automation flags)
- Set headless mode optional (currently disabled for visibility)

#### **Phase 2: Product Search**
- Navigate to Myntra search URL with query: `"anouk kurta"`
- Wait for page to load (5-second delay for content rendering)
- Fetch HTML source using `driver.page_source`

#### **Phase 3: Extract Product Link**
- Parse HTML using BeautifulSoup
- Find all product containers with class `results-base`
- Extract the first product's anchor tag href
- Construct full product URL

#### **Phase 4: Product Details Extraction**
- Navigate to the product page using the extracted link
- Parse product page HTML
- Extract:
  - **Product Title**: From `<title>` tag
  - **Overall Rating**: From div with class `index-overallRating`
  - **Price**: From span with class `pdp-price`

#### **Phase 5: Reviews Navigation**
- Find the "Reviews" link on product page (class: `detailed-reviews-allReviews`)
- Extract and navigate to the reviews page URL

#### **Phase 6: Review Data Scraping**
- Parse reviews page HTML
- Find all review containers (class: `detailed-reviews-userReviewsContainer`)
- For each review, extract:
  - **User Name**: From div with class `user-review-left`
  - **Review Date**: From the same div's second span element
  - **User Rating**: From span with class `user-review-starRating`
  - **Review Comment**: From div with class `user-review-reviewTextWrapper`

#### **Phase 7: Data Display**
- Format and print extracted review data
- Output format: `Date:{date}, Rating:{rating}, Name:{name}, Comment:{comment}`

---

## Key Features

✅ **Automated Browser Control**: Selenium handles JavaScript-heavy content loading  
✅ **HTML Parsing**: BeautifulSoup efficiently extracts specific elements  
✅ **Anti-Bot Detection**: Chrome options configured to avoid detection  
✅ **Error Handling**: Try-except blocks for graceful failure management  
✅ **Data Extraction**: Pulls product details and customer reviews  
✅ **Scalable**: Can be modified to scrape multiple products  

---

## Code Architecture

### Main Components:

| Component | Purpose |
|-----------|---------|
| **Cell 1-2** | Import libraries and initialize Chrome WebDriver |
| **Cell 3-8** | Navigate to product search and extract product link |
| **Cell 9-11** | Extract product metadata (title, rating, price) |
| **Cell 12-13** | Navigate to reviews page |
| **Cell 14-17** | Parse review HTML and extract user data |
| **Cell 18** | Display formatted review output |

---

## Dependencies

```
selenium>=4.0.0
beautifulsoup4>=4.9.0
requests>=2.25.0
```

---

## Usage

1. **Search Product**: Modify `product = "anouk kurta"` variable to search for different items
2. **Run Notebook**: Execute cells sequentially from top to bottom
3. **View Results**: Review extracted data in cell outputs

---

## Important Notes

⚠️ **Web Scraping Ethics**: Use responsibly and respect Myntra's Terms of Service  
⚠️ **Rate Limiting**: Add delays between requests to avoid server overload  
⚠️ **Dynamic Content**: Selenium is essential because Myntra loads content with JavaScript  
⚠️ **Maintenance**: HTML selectors may change if Myntra updates their website structure  

---

## Challenges Addressed

1. **Dynamic Content Loading**: Selenium waits for JavaScript to render content
2. **Bot Detection**: Chrome options configured to avoid anti-bot mechanisms
3. **Element Locating**: Specific CSS classes used to target correct HTML elements
4. **Session Management**: WebDriver properly closed after use (`driver.quit()`)

