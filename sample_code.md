SELECT 
    CASE 
        WHEN EXTRACT(YEAR FROM date_column) % 4 = 0 AND EXTRACT(YEAR FROM date_column) % 100 <> 0 OR EXTRACT(YEAR FROM date_column) % 400 = 0 THEN
            CASE 
                WHEN EXTRACT(MONTH FROM date_column) = 2 AND COUNT(DISTINCT date_column) = 29 THEN 'PASS'
                WHEN EXTRACT(MONTH FROM date_column) IN (4, 6, 9, 11) AND COUNT(DISTINCT date_column) = 30 THEN 'PASS'
                WHEN EXTRACT(MONTH FROM date_column) IN (1, 3, 5, 7, 8, 10, 12) AND COUNT(DISTINCT date_column) = 31 THEN 'PASS'
                WHEN EXTRACT(MONTH FROM date_column) = 2 AND COUNT(DISTINCT date_column) = 28 THEN 'FAIL'
                ELSE 'FAIL'
            END
        ELSE
            CASE 
                WHEN EXTRACT(MONTH FROM date_column) = 2 AND COUNT(DISTINCT date_column) = 28 THEN 'PASS'
                WHEN EXTRACT(MONTH FROM date_column) IN (4, 6, 9, 11) AND COUNT(DISTINCT date_column) = 30 THEN 'PASS'
                WHEN EXTRACT(MONTH FROM date_column) IN (1, 3, 5, 7, 8, 10, 12) AND COUNT(DISTINCT date_column) = 31 THEN 'PASS'
                ELSE 'FAIL'
            END
    END AS Rule_condition
FROM table_name
GROUP BY EXTRACT(YEAR FROM date_column), EXTRACT(MONTH FROM date_column);
