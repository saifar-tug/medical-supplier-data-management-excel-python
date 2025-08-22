# Formula and tasks Summary

Here is the list of Excel formulas and manual tasks I have applied for basic clean and enrichment the dataset `medical_supplier_enhanced.xlsx`. First I renamed it to `medical_supplier_sample.xlsx`, and then cleaned using Excel.

---

## Applied Formulas

### 1. Standardize State Values
```excel
=UPPER(F2)
```
Used to normalize all `practicestate` entries to uppercase (e.g., "ca" -> "CA").

---

### 2. Clean Business Names
```excel
=PROPER(B2)
```
Converts names to proper case. Missing entries were replaced manually with `"Missing"`.

---

### 3. Derive Expiry Status
```excel
=IF(TODAY() + 90 >= L2; "Expiring Soon"; "OK")
```
Flags entries with expiry dates within the next 90 days.

---

### 4. Count Status Entries
```excel
=COUNTIF(N2:N1001; "Expiring Soon")
=COUNTIF(N2:N1001; "OK")
=COUNTIF(B2:B1001; "Missing")
```
Counts used for expiry summary and missing business names.

---

### 5. Force Text Conversion
```excel
=TEXT(N2; "@")
```
Used to clean hidden formatting or non-text issues in `expiry_status`.

---

## Manual Cleaning Tasks

- Formatted `telephonenumber` as plain number (removed decimals/scientific notation)
- Used `Text to Columns` for `supplieslist` (delimiter: `|`)
- Corrected typos in `specialitieslist` (e.g., "Pharamcy" -> "Pharmacy")
- Reviewed and corrected `region` entries
- Applied currency format to `price`

---

## Notes

- Formulas use `;` as the argument separator (for Austrian Excel settings).
- File saved as: `medical_supplier_sample_preprocessed.xlsx`
