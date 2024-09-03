# create25files_script

script = nano createfiles.sh
Permission = chmod +x createfiles.sh
run script = ./createfiles.sh

#!/bin/bash

# Your name
yourName="YourName"  # Replace 'YourName' with your actual name

# Find the biggest number already used in the file names
max_number=$(ls ${yourName}[0-9]* 2>/dev/null | grep -o '[0-9]*' | sort -n | tail -1)

# If there are no files yet, start with 0
if [ -z "$max_number" ]; then
    max_number=0
fi

# Create 25 new files with the next numbers
for i in $(seq 1 25); do
    new_number=$((max_number + i))
    touch "${yourName}${new_number}"
done

# Show the files in the folder
ls -l "${yourName}"*