#!/bin/bash

# Define the input file containing the HDFS file list
INPUT_FILE="hdfs_files.txt"

# Output file to store the extracted information
OUTPUT_FILE="processed_files.txt"

# Clear the output file if it exists
> "$OUTPUT_FILE"

# Read the input file line by line
while IFS= read -r line
do
    # Check if the line contains file details (starts with a dash, indicating file permissions)
    if [[ $line =~ ^- ]]; then
        # Extract file size, date, and file name using awk
        file_size=$(echo "$line" | awk '{print $5}')
        file_date=$(echo "$line" | awk '{print $6, $7}')
        file_name=$(echo "$line" | awk '{for(i=8;i<=NF;i++) printf $i" "; print ""}')

        # Print the extracted details
        echo "File Size: $file_size, Date: $file_date, File Name: $file_name"

        # Append the details to the output file
        echo "$file_size, $file_date, $file_name" >> "$OUTPUT_FILE"
    fi
done < "$INPUT_FILE"
