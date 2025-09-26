# ATC Code Hierarchy - Swedish & English

This repository provides a clean, structured, and tidy dataset of the Anatomical Therapeutic Chemical (ATC) classification system. The data includes full hierarchical descriptions for each ATC code in both Swedish and English, making it ready for immediate use in data analysis, research, and application development.

A key feature of this dataset is the explicit separation of veterinary products into a distinct hierarchical level (`sv0`/`en0`), making comparisons between human and veterinary therapeutic groups straightforward.

## Key Features

-   **Bilingual**: Provides descriptions in both Swedish (`sv`) and English (`en`).
-   **Tidy Format**: One row per ATC code, perfect for analysis in tools like R, Python, and Excel.
-   **Hierarchical Structure**: Each code is broken down into its parent levels (e.g., `sv0`, `sv1`, `sv2` etc.), saving you the complex task of parsing the tree structure.
-   **Explicit Veterinary Classification**: Veterinary codes (starting with `Q`) are clearly identified in their own columns.
-   **Ready to Use**: The data is provided in a single CSV file: `atc_hierarchy.csv`.

## Understanding the ATC Hierarchy

The ATC system is structured into five levels. Veterinary medicines use the same system but are prefixed with the letter Q. This dataset represents that structure in the following columns:

-   **Level 0 (`sv0`, `en0`)**: An optional level indicating **Veterinary Use** (`Veterinära preparat`). This is only present for codes starting with `Q`. For all other codes, this is `NA`.
-   **Level 1 (`sv1`, `en1`)**: The **Anatomical Main Group**, indicated by a letter (e.g., A - Alimentary tract and metabolism).
-   **Level 2 (`sv2`, `en2`)**: The **Therapeutic Subgroup**, indicated by two digits.
-   **Level 3 (`sv3`, `en3`)**: The **Pharmacological/Therapeutic Subgroup**, indicated by a letter.
-   **Level 4 (`sv4`, `en4`)**: The **Chemical/Pharmacological/Therapeutic Subgroup**, indicated by a letter.
-   **Level 5 (`sv5`, `en5`)**: The **Chemical Substance Group**, indicated by two digits.

## Data Structure

The main data file (`atc_hierarchy.csv`) contains the following columns:

| Column | Description                                                               | Example (for `QA01A`)                            |
| :----- | :------------------------------------------------------------------------ | :----------------------------------------------- |
| `atc`  | The specific ATC code.                                                    | `QA01A`                                          |
| `sv0`  | **Veterinary Use Indicator** (Swedish). Is `NA` for non-veterinary codes. | `Veterinära preparat`                            |
| `en0`  | **Veterinary Use Indicator** (English). Is `NA` for non-veterinary codes. | `Veterinary products`                            |
| `sv1`  | Level 1: Anatomical Main Group (Swedish).                                 | `Matsmältningsorgan och ämnesomsättning`         |
| `en1`  | Level 1: Anatomical Main Group (English).                                 | `Alimentary tract and metabolism`                |
| `sv2`  | Level 2: Therapeutic Subgroup (Swedish).                                  | `Medel vid mun- och tandsjukdomar`               |
| `en2`  | Level 2: Therapeutic Subgroup (English).                                  | `Stomatological preparations`                    |
| `...`  | And so on for levels 3, 4 and 5 (`sv3`, `en3`, etc.).                     | ...                                              |

## Example Data

Here is a snapshot of `atc_hierarchy.csv` showing both a human (`A01AA01`) and a veterinary (`QA01A`) code:

```csv
atc,sv0,en0,sv1,en1,sv2,en2,sv3,en3,sv4,en4,sv5,en5
"A01AA01",NA,NA,"Matsmältningsorgan och ämnesomsättning","Alimentary tract and metabolism","Medel vid mun- och tandsjukdomar","Stomatological preparations","Medel vid mun- och tandsjukdomar","Stomatological preparations","Medel mot karies","Caries prophylactic agents","Natriumfluorid","Sodium fluoride"
"QA01A","Veterinära preparat","Veterinary products","Matsmältningsorgan och ämnesomsättning","Alimentary tract and metabolism","Medel vid mun- och tandsjukdomar","Stomatological preparations","Medel vid mun- och tandsjukdomar","Stomatological preparations",NA,NA,NA,NA
```

## Data Source

The raw data for this dataset is sourced from the Swedish Medical Products Agency (Läkemedelsverket), specifically from the **National Substance Register for Medicinal Products (NSL) 2.0**.

-   **Official Source:** [National Substance Register for Medicinal Products (NSL)](https://www.lakemedelsverket.se/en/e-services-and-forms/substance-register-and-product-register/national-substance-register-for-medicinal-products-nsl)

The data was accessed in September 2025. The subsequent processing and structuring into the final hierarchical format was done this [XML to JSON converter](https://jsonformatter.org/xml-to-json), DuckDB (to read JSON), and then finally R with Tidyverse tools.

---
*This is an unofficial, processed dataset intended for research and development purposes.*
