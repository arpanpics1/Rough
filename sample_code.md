SELECT 
CASE 
    WHEN 
        (EXTRACT(YEAR FROM date_column) % 4 = 0 AND EXTRACT(YEAR FROM date_column) % 100 <> 0 OR EXTRACT(YEAR FROM date_column) % 400 = 0 AND EXTRACT(MONTH FROM date_column) = 2 AND 
        (SELECT COUNT(DISTINCT date_column) FROM table_name WHERE EXTRACT(MONTH FROM date_column) = 2 AND EXTRACT(YEAR FROM date_column) = EXTRACT(YEAR FROM date_column)) = 29) 
    OR 
        (EXTRACT(MONTH FROM date_column) = 2 AND (SELECT COUNT(DISTINCT date_column) FROM table_name WHERE EXTRACT(MONTH FROM date_column) = 2 AND EXTRACT(YEAR FROM date_column) = EXTRACT(YEAR FROM date_column)) = 28)
    OR 
        (EXTRACT(MONTH FROM date_column) IN (4, 6, 9, 11) AND (SELECT COUNT(DISTINCT date_column) FROM table_name WHERE EXTRACT(MONTH FROM date_column) = EXTRACT(MONTH FROM date_column) AND EXTRACT(YEAR FROM date_column) = EXTRACT(YEAR FROM date_column)) = 30)
    OR 
        (EXTRACT(MONTH FROM date_column) IN (1, 3, 5, 7, 8, 10, 12) AND (SELECT COUNT(DISTINCT date_column) FROM table_name WHERE EXTRACT(MONTH FROM date_column) = EXTRACT(MONTH FROM date_column) AND EXTRACT(YEAR FROM date_column) = EXTRACT(YEAR FROM date_column)) = 31)
    THEN 'PASS'
    ELSE 'FAIL'
END AS Rule_condition
FROM table_name
GROUP BY EXTRACT(YEAR FROM date_column), EXTRACT(MONTH FROM date_column);
