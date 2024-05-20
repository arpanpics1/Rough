-- Start the Hive CLI or Beeline
-- hive

-- Create first managed table
CREATE TABLE employee (
  id INT,
  name STRING,
  age INT,
  department STRING
);

-- Create second managed table
CREATE TABLE department (
  dept_id INT,
  dept_name STRING,
  location STRING
);

-- Insert records into the employee table
INSERT INTO TABLE employee VALUES
  (1, 'John Doe', 30, 'HR'),
  (2, 'Jane Smith', 35, 'Engineering'),
  (3, 'Sam Brown', 28, 'Sales');

-- Insert records into the department table
INSERT INTO TABLE department VALUES
  (1, 'HR', 'New York'),
  (2, 'Engineering', 'San Francisco'),
  (3, 'Sales', 'Chicago');
