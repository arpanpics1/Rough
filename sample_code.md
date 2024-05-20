-- Start the Hive CLI or Beeline
-- hive

-- Create external table
CREATE EXTERNAL TABLE external_employee (
  id INT,
  name STRING,
  age INT,
  department STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
LOCATION '/user/hive/external/employee_data';
