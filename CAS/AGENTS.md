## Objective:
Open the following academic journal websites ONE BY ONE using Playwright, navigate to their Current/Latest Issue, and extract  bibliographic details of all individual articles listed in that issue.

## Target Journal Websites:
1. https://journal.gujaratvidyapith.org/index.php/vp
2. https://indianjournals.com/journals/LH

## STRICT RULES - READ CAREFULLY BEFORE STARTING:

### URL Control Rules (MOST IMPORTANT):
- You must process ONLY ONE journal at a time
- Complete ALL extraction work for Journal 1 FULLY before 
  moving to Journal 2
- While working on Journal 1, you are STRICTLY FORBIDDEN 
  from navigating to any URL that does not belong to 
  Journal 1's domain
- While working on Journal 2, you are STRICTLY FORBIDDEN 
  from navigating to any URL that does not belong to 
  Journal 2's domain
- NEVER open or switch to another journal's URL 
  while extraction of current journal is still in progress
- If you accidentally land on a wrong URL/domain, 
  immediately go BACK to the correct journal URL 
  and continue extraction
- Do NOT follow any recommended articles, related journals, 
  or sidebar links that lead to other journal websites
- Do NOT click on any advertisement or promotional links
- Only follow links that belong to the CURRENT journal's 
  article pages for the current issue being processed

### Allowed URL Patterns:
- For Journal 1:
  * Allowed: https://journal.gujaratvidyapith.org/index.php/vp*
  * NOT Allowed: Any other journal URL 

- For Journal 2:
  * Allowed: https://indianjournals.com/journals/LH*
  * NOT Allowed: Any other journal URL   

---

## Step-by-Step Instructions:

### Step 1: Browser Automation (Playwright MCP)
- Launch a visible browser using Playwright MCP
- Before opening any URL, note down the target journal 
  URL and remember it throughout the extraction process
- Open Journal 1 URL first
- On the journal website:
  * Navigate to the "Current Issue" or "Latest Issue" section
  * Note down the exact Volume, Issue, and Year shown
  * Note down the exact URL of the current issue page
  * Wait for the page to fully load before extracting data
  * Scroll down completely to load all article listings
  * Handle cookie consent popups or overlays if they appear 
    (click Accept/Close to dismiss them)
  * Do NOT click on any link that leads outside 
    the current journal domain

### Step 2: Article List Collection (Before Individual Extraction)
- Before opening individual article pages, FIRST collect 
  and save a complete list of ALL article URLs/links 
  listed on the current issue page of the journal
- Save this list in memory before proceeding
- This ensures you do not lose track of remaining 
  articles if navigation occurs
- Verify each saved article URL belongs to the 
  correct journal domain before visiting it
- Total count of articles found must be noted before 
  starting individual article extraction

### Step 3: Data Extraction (Article by Article)
- Process articles ONE BY ONE from your saved list
- For each article:
  * Open the article URL from your saved list
  * Verify the URL matches the correct journal domain
  * If wrong URL detected → Go back → Pick correct URL
  * Extract all required fields
  * Mark article as DONE in your tracking list
  * Go back to the issue page OR open next article 
    from your saved list
  * DO NOT follow any other links on the article page

- Extract the following details for EVERY article:
  ✔ Journal Name
  ✔ Volume Number
  ✔ Issue Number
  ✔ Article Title
  ✔ Author Name(s) — all authors, comma separated
  ✔ Keywords — all keywords, comma separated
  ✔ Abstract — full abstract text if available else write 'Abstract Not Available'
  ✔ Page Numbers — (e.g. 123-145)

- If any field is not available, mark it as "Not Available"

### Step 4: Journal Completion Checkpoint
- After extracting all articles from Journal 1:
  * Print/Log: "Journal 1 extraction COMPLETE. 
    Total articles extracted: [X]"
  * Save all extracted data for Journal 1 in memory
  * Close or reset the browser tab
  * Only THEN open Journal 2 URL
  * Repeat Steps 1 to 3 for Journal 2

### Step 5: Data Organization
- Organize all extracted data journal-wise
- Within each journal, sort articles by page numbers 
  in ascending order
- Maintain strict separation between journals 
  during organization
- Maintain the language script as it is and write it using UTF.

### Step 6: PDF Generation - Newsletter Format
After ALL journals are fully extracted and data is 
organized, create a single professionally formatted 
PDF file named:
"Journal_Current_Issue_Newsletter.pdf"

#### PDF Layout and Formatting:

**Overall Style:**
- Newsletter style format
- Clean, academic, and professional appearance
- Use a two-column layout for article details 
  where appropriate
- Add a decorative header and footer on each page

**PDF Structure:**

[PAGE 1 - COVER PAGE]
- Use ADINET transparent logo (adomet_logo.png) in center
- Newsletter Title: "CUCOLIS"
- Subtitle: "CURRENT CONTENTS FOR LIBRARY AND INFORMATION SCIENCE"
- Period: (today's Month and Year)
- List of Journals covered in this newsletter
  with their Volume and Issue details
- A horizontal divider line

[FOR EACH JOURNAL - New Section starts on a new page]

► JOURNAL HEADER BLOCK:
  - Main Heading (Large, Bold, Colored): Journal Name
  - Sub Heading: Volume [X] | Issue [X] | Year [XXXX]
  - Publisher Name (if available)
  - Journal ISSN (if available)
  - Source URL of the journal
  - A thick horizontal divider line below the header

► FOR EACH ARTICLE under that journal:
  - Article Serial Number (e.g., Article 1, Article 2...)
  - Title        → Bold, larger font size
  - Author(s)    → Italic font
  - DOI          → Displayed as clickable hyperlink
  - Page Numbers → Displayed inline 
                   (e.g., Pages: 123-145)
  - Keywords     → Label in bold followed by keywords
                   (Keywords: word1, word2, word3)
  - Abstract     → Label "Abstract:" in bold, 
                   followed by full abstract text 
                   in normal font
  - A thin horizontal divider line after each article

► JOURNAL SECTION FOOTER:
  - Total number of articles extracted for that journal


[LAST PAGE - Summary]
- Total journals processed
- Total articles extracted (journal-wise breakdown)

- Data source URLs

## Output File:
- File Name: Journal_Current_Issue_Newsletter.pdf
- Save in the folder Output
- Ensure PDF is properly formatted and readable


## Final Important Rules:

1. STRICT JOURNAL ISOLATION: 
   - Never mix data of one journal with another
   - Never open Journal 2 URL while Journal 1 is still being processed
   - Never follow links to other journals found on the current journal page

2. ARTICLE TRACKING:
   - Always maintain a counter of (Articles Found vs Articles Extracted)
   - Do not stop extraction until both counts match

3. URL VERIFICATION:
   - Before visiting any URL, check if it belongs to the currently active journal domain
   - If not matching → SKIP that URL → Continue with next article from saved list

4. ERROR HANDLING:
   - If a page fails to load → Retry 2 times → If still failing → Mark as "Page Load Failed" 
     and move to next article
   - If a journal website blocks automated access → Note it in the PDF → Move to next journal

5. DO NOT:
   - Do not click on "Related Articles" links
   - Do not try to open any Fulltext link or PDF file
   - Do not click on "Recommended for You" links
   - Do not click on other journal name links found on the page
   - Do not navigate to publisher homepage
   - Do not follow any link outside the current journal's issue page
