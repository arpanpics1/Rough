The 100,000 records have been successfully generated with a variety of data types and anomalies. The dataset has been saved as a CSV file, and here are some key statistics for the columns:

ProductID: Sequential IDs from 1 to 100,000.
ProductName: Random product names with some repetition; a total of 1000 unique names.
Category: Contains 97,377 valid categories; the most frequent category is "Toys."
Price: Prices range from -999.78 to 9999.98, with some negative prices as anomalies.
Quantity: Values range from -10 to 1500, with some negative and excessive quantities.
ManufactureDate and ExpirationDate: Datetime values with some future or inconsistent dates.
PhoneNumber: Contains phone numbers, some of which are missing (approx. 50%).
IsBoolean: A field with True/False values and some missing values.
State: Valid US state codes (TX, CA, NY, FL, WA), but 5% of records are missing.
IsWeekend: Boolean field indicating if the manufacture date was a weekend.
IsValid: A "Y" or "N" field for validation status, 50% of records have "N."
SpecialCharField: Introduced special character entries (approx. 50%).
IsNumeric, IsFloat, IsAlphanumeric: Fields containing various numeric and alphanumeric values, with some missing.




1. Rule: Uniqueness
Field: ProductID
Condition: Each ProductID must be unique.
Outcome: No duplicate values should exist for ProductID. Any duplicates will violate this rule.
2. Rule: Non-null Check
Fields: ProductName, Category, Price, Quantity, State, PhoneNumber
Condition: These fields should not contain null values.
Outcome: Records with null values will violate this rule.
ProductName: Expected null values ~5%.
Category: Expected invalid categories ~3%.
Price: Expected null values ~2%.
PhoneNumber: Expected missing values ~50%.
3. Rule: Value Range Check
Fields: Price, Quantity
Conditions:
Price should be between 0 and 10,000.
Quantity should be between 0 and 1,000.
Outcome: Negative and extremely high values will fail this check.
Expected anomalies: 2% negative prices and quantities.
4. Rule: Date Consistency
Fields: ManufactureDate, ExpirationDate
Conditions:
ManufactureDate should not be in the future.
ExpirationDate should be after ManufactureDate.
Outcome: Records with future manufacture dates or expiration dates earlier than the manufacture date will violate this rule. ~1% of records have future dates, and ~2% have invalid expiration dates.
5. Rule: Numeric Validation
Fields: IsNumeric, IsFloat
Conditions:
IsNumeric should contain only numeric values.
IsFloat should be a valid floating-point number.
Outcome: Invalid or non-numeric data in these fields will violate the rule. ~5% of values may be invalid (special characters or missing data).
6. Rule: Alphanumeric Validation
Field: IsAlphanumeric
Condition: Values should only contain alphanumeric characters.
Outcome: Records with non-alphanumeric characters or null values will fail this check. ~5% of records might contain special characters.
7. Rule: Valid Category
Field: Category
Condition: Should contain only valid categories (Electronics, Furniture, Clothing, Toys, Books).
Outcome: Invalid categories or misspelled values will violate the rule. ~3% of records have invalid categories.
8. Rule: Boolean Validation
Field: IsBoolean
Condition: Values should only be True or False.
Outcome: Any null or non-boolean values will violate this rule. ~30% of records are expected to have missing or invalid values.
9. Rule: Phone Number Format
Field: PhoneNumber
Condition: The phone number should match the format XXX-XXX-XXXX.
Outcome: Any deviation from this format or missing phone numbers will violate the rule. Expected missing phone numbers ~50%.
10. Rule: State Validation
Field: State
Condition: Should contain only valid US state codes (TX, CA, NY, FL, WA).
Outcome: Any invalid or missing state codes will fail this rule. ~5% of records will have missing or invalid state codes.
11. Rule: Weekend Check
Field: IsWeekend
Condition: Checks if ManufactureDate is a weekend.
Outcome: Correctly identifies if the manufacture date falls on a weekend. No expected anomalies.
12. Rule: Special Character Check
Field: SpecialCharField
Condition: Check if special characters (@, !, etc.) are present.
Outcome: ~50% of records will have special characters. Any missing values in this field will fail the check.
13. Rule: Valid Flag
Field: IsValid
Condition: Should be either Y or N.
Outcome: Any invalid or missing values will violate this rule. ~50% of records have "N."
14. Rule: Blank Field Check
Field: Multiple Fields
Condition: No fields should be completely blank.
Outcome: Fields such as PhoneNumber, State, IsBoolean, IsValid, etc., should not be completely blank.
15. Rule: Null Check
Field: Multiple Fields
Condition: Any field containing None or NaN values will fail.
Outcome: Null values will appear in fields like PhoneNumber, Category, Price, and Quantity.
16. Rule: Positive Value Check
Fields: Price, Quantity
Condition: Values should be greater than 0.
Outcome: Negative or zero values in Price or Quantity will violate this rule.
Example: ~2% of records will have negative values.
17. Rule: Zero Value Check
Fields: Price, Quantity
Condition: Value should be exactly 0.
Outcome: You can use this rule to specifically identify records where Price or Quantity equals 0. This can help detect records with pricing errors or products out of stock.
18. Rule: Greater than 0 Check
Field: Quantity
Condition: Ensure that Quantity is greater than 0.
Outcome: Any negative or zero quantities will violate this rule. ~2% of records may have values less than or equal to 0.
19. Rule: Valid Currency Format
Field: Price
Condition: Check if Price is a valid currency (e.g., two decimal places).
Outcome: Prices with more than two decimal places or invalid values (like negative amounts) will fail this rule. ~1-2% of records may have invalid prices.
20. Rule: Valid Date Format
Fields: ManufactureDate, ExpirationDate
Condition: Date fields should be in a valid format (YYYY-MM-DD).
Outcome: Records with incorrect or invalid date formats will violate this rule. ~1-2% of records may have date formatting issues.
21. Rule: Date Field Must Be Present
Fields: ManufactureDate, ExpirationDate
Condition: Ensure that date fields are not null.
Outcome: Any missing dates will violate this rule. ~5% of records may have null values for dates.
22. Rule: Future Date Check
Fields: ManufactureDate, ExpirationDate
Condition: Ensure that the ManufactureDate is not a future date.
Outcome: Records with future ManufactureDate will fail this check. ~1-2% of records will have future dates.
23. Rule: Valid Boolean Value
Field: IsBoolean
Condition: Values should only be True, False, or null.
Outcome: Any invalid entries (non-boolean values like strings or numbers) will fail this rule. ~30% of records may have missing or invalid values.
24. Rule: Valid Phone Number Format
Field: PhoneNumber
Condition: Validate the phone number format (XXX-XXX-XXXX).
Outcome: Invalid phone numbers (e.g., missing digits, wrong format) will fail the rule. ~50% of records may have null or invalid phone numbers.
25. Rule: Alphabetic Characters Only
Field: Category
Condition: Ensure the category contains only alphabetic characters.
Outcome: Categories containing numbers or special characters will violate this rule. ~5% of records may have invalid values (misspellings, special characters).
26. Rule: Valid State Code
Field: State
Condition: Ensure the state code is a valid two-letter US state abbreviation.
Outcome: Invalid or missing state codes will violate this rule. ~5% of records may have invalid or missing state codes.
27. Rule: Special Character Detection
Field: SpecialCharField
Condition: Identify fields that contain special characters (e.g., @, #, $).
Outcome: Records with no special characters or null values in this field will violate the rule. ~50% of records contain special characters.
28. Rule: Valid Flag (Y/N)
Field: IsValid
Condition: Value must be either Y or N.
Outcome: Invalid entries (non-Y/N values) or null values will violate this rule. ~50% of records contain "N".
29. Rule: Valid Alphanumeric Characters
Field: IsAlphanumeric
Condition: Validate that the field contains only alphanumeric characters (no special characters or spaces).
Outcome: Invalid values containing special characters or spaces will violate this rule. ~5% of records may contain invalid values.
30. Rule: Is Blank or Null
Fields: Multiple Fields (ProductName, Category, PhoneNumber, State, etc.)
Condition: Check if the field is completely blank or null.
Outcome: Records with null or blank values in critical fields will violate this rule. Expect 5-10% blank values in fields like PhoneNumber, State.
31. Rule: Valid Email Address
Field: (If an email field exists)
Condition: Validate that the field contains a valid email format.
Outcome: Invalid or incorrectly formatted email addresses will violate this rule. (~N/A in current dataset).
32. Rule: Valid Quantity vs Stock Status
Field: Quantity, StockStatus
Condition: If Quantity is zero, StockStatus should indicate "Out of Stock."
Outcome: Inconsistent data between Quantity and StockStatus will violate this rule. (Potential future expansion).
