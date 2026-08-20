# Library Book Cataloguing Agent Instructions

The given working directory contains multiple PDF files. These PDF files contain the title pages and back title pages of books. Based on the content in these PDFs, extract the necessary bibliographic details required for library book cataloguing.

**Instructions:**

1. **Input:** Process all PDF files present in the working directory.
    
2. **Accession/Barcode Number:** Use the **filename** (without extension) of each PDF as the Accession/Barcode Number.
    
3. **Language Handling:** The content inside the PDF files may be in **English, Hindi, or Gujarati**. Handle all three languages appropriately during extraction.
4. **Installing Dependencies:** To conduct this task if any dependencies/softwares need to be installed then first check whether it is installed or not, if not then only install them.
    
5. **Metadata Extraction:** Extract the following bibliographic details from each PDF (wherever available):
    
    - Title
    - Author(s)
    - Publisher
    - Place of Publication
    - Year of Publication
    - Edition
    - ISBN
    - Subject/Topic
    - Language
    - Number of Pages (if available)
    - Price
    - Series (if any)
    - Call Number (if available or generate based on available info)
    - Shelving Location
6. **Excel File Output:**
    
    - Create an Excel file (`.xlsx`) with all extracted metadata structured in columns.
        
    - The columns must be mapped to **MARC21 format-based fields** so that the data can be directly used for populating MARC21 records.
        
    - Each row in the Excel file should represent one book (one PDF).
        
    - Include the following MARC21 field mappings as column headers (at minimum):
        
        |Excel Column|MARC21 Field|
        |---|---|
        |Accession/Barcode Number|952$p|
        |Title|245$a|
        |Subtitle|245$b|
        |Author (Primary)|100$a|
        |Author (Additional)|700$a|
        |Publisher|260$b / 264$b|
        |Place of Publication|260$a / 264$a|
        |Year of Publication|260$c / 264$c|
        |Edition|250$a|
        |ISBN|020$a|
        |Subject|650$a|
        |Language|041$a / 008|
        |Call Number|082$a / 092$a|
        |Shelving Location|952$c|
        |Price|952$g|
        |Supplier|952$e|
        |Acquisition Date|952$d|
        |Home Library|952$a|
        |Holding Library|952$b|
        |Item Type|952$y|
        
7. **MARC21 (.mrc) File Output:**
    
    - Based on the Excel file data, generate a **binary MARC21 `.mrc` file**.
        
    - The `.mrc` file must be fully **compliant with the Koha Library Management System** so that it can be directly imported into Koha without errors.
        
    - Populate the **952 field** (Koha holdings/item information) with the following subfields:
        
        |Subfield|Value|
        |---|---|
        |952$a|`GVP` (Home Library Code)|
        |952$b|`GVP` (Holding Library Code)|
        |952$c|Shelving Location|
        |952$y|`BK` (Item Type — Book)|
        |952$o|Call Number|
        |952$p|Barcode (Filename without extension)|
        |952$g|Price|
        |952$e|Supplier|
        |952$d|Acquisition Date|
        
    - Ensure the following **standard MARC21 fields** are also populated where data is available:
        
        - **Leader** — Set appropriately for a book record (`00000nam a2200000 i 4500`)
        - **001** — Control Number (use filename/barcode)
        - **003** — `GVP`
        - **008** — Fixed-length data (language, year, country, etc.)
        - **020** — ISBN
        - **041** — Language Code
        - **082** — Dewey Decimal Classification (if derivable)
        - **100** — Main Entry (Author)
        - **245** — Title Statement
        - **250** — Edition Statement
        - **260/264** — Publication Information
        - **300** — Physical Description
        - **650** — Subject Added Entry
        - **700** — Added Entry (Additional Authors)
        - **942** — Koha item type (`$c BK`)
        - **952** — Koha Holdings Information (as detailed above)
8. **Output Files Required:**
    
    - ✅ `cataloguing_data.xlsx` — Excel file with MARC21-mapped metadata
    - ✅ `catalogue_records.mrc` — Binary MARC21 file ready for Koha import

---

**Notes:**

- If any field data is not found or not clearly readable in the PDF, leave that field **blank** in the Excel and **skip or leave empty** in the `.mrc` record. Do not guess or hallucinate values.
- Ensure the `.mrc` file uses proper **MARC21 binary encoding** (ISO 2709 format) to be compatible with Koha's import tool (`Stage MARC records for import`).
- While populating the Authors render the Last Name then comma(,) and then remaining name. For example if Author Name is K. M. Munshi then write Munshi, K. M. 
- Repeat the Added Entry (Additional Authors) same as Authors.
- Populate the Subject Added Entry in excel as well.
- Handle **multilingual content** (English/Hindi/Gujarati) carefully, preserving the original script where needed.
