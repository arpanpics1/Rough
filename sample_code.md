CREATE TABLE product_data_quality_test (
    ProductID INT,
    ProductName STRING,
    Category STRING,
    Price DECIMAL(10,2),
    Quantity INT,
    ManufactureDate TIMESTAMP,
    ExpirationDate TIMESTAMP,
    PhoneNumber STRING,
    IsBoolean BOOLEAN,
    State STRING,
    IsWeekend BOOLEAN,
    IsValid STRING,
    SpecialCharField STRING,
    IsNumeric STRING,
    IsFloat STRING,
    IsAlphanumeric STRING
)
STORED AS PARQUET;
